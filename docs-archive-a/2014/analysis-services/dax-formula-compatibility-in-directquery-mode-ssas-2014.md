---
title: Compatibilité des formules DAX en mode DirectQuery (SSAS 2014) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604268"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a>Compatibilité des formules DAX en mode DirectQuery (SSAS 2014)
Le langage DAX (Data Analysis expression) peut être utilisé pour créer des mesures et d’autres formules personnalisées à utiliser dans des modèles tabulaires Analysis Services, des [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] modèles de données dans des classeurs Excel et des modèles de données Power bi Desktop. Dans la plupart des aspects, les modèles que vous créez dans ces environnements sont identiques et vous pouvez utiliser les mêmes mesures, relations et indicateurs de performance clés, etc. Toutefois, si vous créez un modèle tabulaire Analysis Services et que vous le déployez en mode DirectQuery, certaines restrictions s’appliquent aux formules que vous pouvez utiliser. Cette rubrique fournit une vue d’ensemble de ces différences, répertorie les fonctions qui ne sont pas prises en charge dans le modèle SQL Server 2014 Analysis Services tabulaires au niveau de compatibilité 1100 ou 1103 et en mode DirectQuery, et répertorie les fonctions prises en charge, mais qui peuvent retourner des résultats différents.  
  
Dans cette rubrique, nous utilisons le terme *modèle en mémoire* pour faire référence aux modèles tabulaires, qui sont des données en mémoire cache entièrement hébergées sur un serveur Analysis Services s’exécutant en mode tabulaire. Nous utilisons les *modèles DirectQuery* pour faire référence aux modèles tabulaires qui ont été créés et/ou déployés en mode DirectQuery. Pour plus d’informations sur le mode DirectQuery, consultez [mode DirectQuery (SSAS tabulaire)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a>Différences entre le mode en mémoire et le mode DirectQuery  
Les requêtes sur un modèle déployé en mode DirectQuery peuvent retourner des résultats différents de ceux du même modèle déployé en mode en mémoire. En effet, avec DirectQuery, les données sont interrogées directement à partir d’une banque de données relationnelle et les agrégations requises par les formules sont effectuées à l’aide du moteur relationnel approprié, au lieu d’utiliser le moteur d’analyse en mémoire xVelocity (VertiPaq) pour le stockage et le calcul.  
  
Par exemple, il existe des différences dans la façon dont certaines banques de données relationnelles gèrent les valeurs numériques, les dates, les valeurs Null, etc.  
  
En revanche, le langage DAX est prévu pour émuler le mieux possible le comportement des fonctions dans Microsoft Excel. Par exemple, lorsque vous gérez des valeurs Null, des chaînes vides et des valeurs zéro, Excel tente de fournir la meilleure réponse quel que soit le type de données exact, et par conséquent le moteur xVelocity en fait de même. Toutefois, lorsqu'un modèle tabulaire est déployé en mode DirectQuery et transmet des formules à une source de données relationnelle pour l'évaluation, les données doivent être traitées selon la sémantique de la source de données relationnelle, qui nécessite généralement une gestion distincte des chaînes vides et des valeurs Null. Pour cette raison, la même formule peut retourner un résultat différent une fois évaluée sur des données en mémoire cache et sur des données extraites seulement de la banque de données relationnelle.  
  
En outre, certaines fonctions ne peuvent pas être utilisées du tout en mode DirectQuery, car le calcul exige que les données du contexte actuel soient envoyées à la source de données relationnelle en tant que paramètre. Par exemple, les mesures d’un [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] classeur utilisent souvent des fonctions d’intelligence temporelle qui font référence à des plages de dates disponibles dans le classeur. En général, ces formules ne peuvent pas être utilisées en mode DirectQuery.  
  
## <a name="semantic-differences"></a>Différences sémantiques  
Cette section répertorie les types de différences sémantiques que vous pouvez attendre, et décrit toutes les limitations qui peuvent s'appliquer à l'utilisation des fonctions ou aux résultats de la requête.  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a>Comparaisons  
Dans les modèles en mémoire, DAX prend en charge les comparaisons de deux expressions qui se résolvent en valeurs scalaires de types de données différents. Toutefois, les modèles qui sont déployés en mode DirectQuery utilisent les types de données et les opérateurs de comparaison du moteur relationnel, et peuvent donc retourner des résultats différents.  
  
Les comparaisons suivantes retournent toujours une erreur quand elles sont utilisées dans un calcul sur une source de données de DirectQuery :  
  
-   Type de données numérique comparé à tout type de données string  
  
-   Type de données numérique comparé à une valeur booléenne  
  
-   Tout type de données string comparé à une valeur booléenne  
  
DAX est généralement plus indulgent avec les incompatibilités de type de données dans les modèles en mémoire, et tente d’effectuer une conversion de type implicite des valeurs jusqu’à deux fois, comme le décrit cette section. Toutefois, les formules envoyées à une banque de données relationnelle en mode DirectQuery sont évaluées plus strictement, selon les règles du moteur relationnel, et sont plus susceptibles d'échouer.  
  
**Comparaisons de chaînes et de nombres**  
EXEMPLE : `"2" < 3`  
  
La formule compare une chaîne de texte à un nombre. L’expression est **true** en mode DirectQuery et dans les modèles en mémoire.  
  
Dans un modèle en mémoire, le résultat est **true** car les nombres sous forme de chaînes sont implicitement convertis en type de données numérique pour les comparaisons avec d’autres nombres. SQL effectue aussi un cast implicite des nombres sous forme de texte en nombres afin de les comparer aux types de données numériques.  
  
Notez que cela représente un changement de comportement de la première version de [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , qui retourne la **valeur false**, car le texte « 2 » est toujours considéré comme supérieur à n’importe quel nombre.  
  
**Comparaison de texte avec une valeur booléenne**  
EXEMPLE : `"VERDADERO" = TRUE`  
  
Cette expression compare une chaîne de texte avec une valeur booléenne. En général, pour les modèles DirectQuery ou en mémoire, la comparaison d'une valeur de chaîne avec une valeur booléenne provoque une erreur. Les seules exceptions à cette règle sont quand la chaîne contient le mot **true** ou le mot **false**; si la chaîne contient une de ces valeurs, une conversion en valeur booléenne est effectuée et la comparaison a lieu, donnant le résultat logique.  
  
**Comparaison de valeurs Null**  
EXEMPLE : `EVALUATE ROW("X", BLANK() = BLANK())`  
  
Cette formule compare l'équivalent SQL d'une valeur Null avec une valeur Null. Elle retourne **true** dans les modèles en mémoire et DirectQuery ; un approvisionnement est effectué dans le modèle DirectQuery pour assurer un comportement similaire au modèle en mémoire.  
  
Notez que dans Transact-SQL une valeur Null n'est jamais égale à une valeur Null. Toutefois, dans DAX, un espace est égal à un autre espace. Ce comportement est le même pour tous les modèles en mémoire. Il est important de noter que le mode DirectQuery utilise la plupart de la sémantique SQL Server ; mais, dans ce cas il s'en sépare en lui donnant un nouveau comportement dans les comparaisons NULL.  
  
### <a name="casts"></a><a name="bkmk_Casts"></a>Casts  
  
Il n'existe aucune fonction cast telle que dans DAX, mais les casts implicites sont effectués dans nombre de comparaisons et d'opérations arithmétiques. La comparaison ou l'opération arithmétique détermine le type de données du résultat. Par exemple :  
  
-   Les valeurs booléennes sont traitées en tant que valeurs numériques dans les opérations arithmétiques, telles que TRUE + 1, ou la fonction MIN appliquée à une colonne de valeurs booléennes. Une opération NOT retourne également une valeur numérique.  
  
-   Les valeurs booléennes sont toujours traitées comme des valeurs logiques dans les comparaisons et quand elles sont utilisées avec EXACT, AND, OR, &amp;&amp;||.  
  
**Conversion d'une chaîne en valeur booléenne**  
Dans les modèles en mémoire et DirectQuery, les casts sont autorisés aux valeurs booléennes de ces chaînes uniquement : **""** (chaîne vide), **"true"**, **"false"**; où une chaîne vide est convertie en valeur false.  
  
Les conversions en type de données booléen d'une autre chaîne génèrent une erreur.  
  
**Conversion d'une chaîne en date/heure**  
En mode DirectQuery, les conversions des représentations sous forme de chaîne des dates et heures en valeurs **datetime** réelles se comportent de la même façon que dans SQL Server.  
  
Pour plus d’informations sur les règles régissant les casts de types de données String en **DateTime** dans [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] les modèles, consultez la [référence de syntaxe DAX](/dax/dax-syntax-reference).
  
Les modèles qui utilisent la banque de données en mémoire utilisent une plage plus limitée de formats de texte pour les dates que les formats de chaîne pour les dates prises en charge par SQL Server. Toutefois, DAX prend en charge les formats de date et d'heure personnalisés.  
  
**Conversion d'une chaîne en d'autres valeurs non booléennes**  
Lors de la conversion de chaînes en valeurs non booléennes, le mode DirectQuery se comporte de la même manière que SQL Server. Pour plus d’informations, consultez [CAST et CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).  
  
**Conversion de nombres en chaîne non autorisée**  
EXEMPLE : `CONCATENATE(102,",345")`  
  
La conversion de nombres en chaînes n'est pas autorisée dans SQL Server.  
  
Cette formule retourne une erreur dans les modèles tabulaires et en mode DirectQuery. Cependant, la formule produit un résultat dans [!INCLUDE[ssGemini](../includes/ssgemini-md.md)].  
  
**Aucune prise en charge de deux tentatives de conversion dans DirectQuery**  
Les modèles en mémoire tentent souvent une deuxième conversion lorsque la première échoue. Cela ne se produit jamais en mode DirectQuery.  
  
EXEMPLE : `TODAY() + "13:14:15"`  
  
Dans cette expression, le premier paramètre est de type **datetime** et le deuxième paramètre est de type **string**. Toutefois, les conversions en combinant les opérandes sont gérées différemment. DAX effectue une conversion de type implicite de **string** en **double**. Dans les modèles en mémoire, le moteur de formule tente de convertir le type directement en **double**et, si cette tentative échoue, il essaie de convertir la chaîne en **datetime**.  
  
En mode DirectQuery, seule la conversion directe de **string** en **double** est appliquée. Si cette conversion échoue, la formule retourne une erreur.  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a>Fonctions mathématiques et opérations arithmétiques  
Certaines fonctions mathématiques retournent des résultats différents en mode DirectQuery, en raison de différences dans le type de données sous-jacent ou des conversions qui peuvent être appliquées dans les opérations. En outre, les restrictions décrites ci-dessus relatives à la plage de valeurs autorisée peuvent affecter les résultats des opérations arithmétiques.  
  
**Ordre d'ajout**  
Lorsque vous créez une formule qui ajoute une série de nombres, un modèle en mémoire peut traiter les nombres dans un ordre différent de celui d'un modèle DirectQuery.  Par conséquent, lorsque vous avez de très grands nombres positifs et de très grands nombres négatifs, vous pouvez obtenir une erreur dans une opération et des résultats dans une autre opération.  
  
**Utilisation de la fonction POWER**  
EXEMPLE : `POWER(-64, 1/3)`  
  
En mode DirectQuery, la fonction POWER ne peut pas utiliser de valeurs négatives comme base une fois élevée à un exposant fractionnaire. Il s'agit du comportement attendu dans SQL Server.  
  
Dans un modèle en mémoire, la formule retourne -4.  
  
**Opérations numériques de dépassement de capacité**  
Dans Transact-SQL, les opérations qui génèrent un dépassement de capacité numérique génèrent une erreur de dépassement de capacité ; par conséquent, les formules qui génèrent un dépassement de capacité génèrent également une erreur en mode DirectQuery.  
  
Toutefois, la même formule utilisée dans un modèle en mémoire retourne un entier sur huit octets. Cela est dû au fait que le moteur de formule ne recherche pas les dépassements de capacité numériques.  
  
**Les fonctions LOG avec des espaces retournent des résultats différents**  
SQL Server gère les valeurs Null et les espaces différemment du moteur xVelocity. Par conséquent, la formule suivante retourne une erreur en mode DirectQuery, mais retourne Infinity (-INF) en mode in-Memory.  
  
`EXAMPLE: LOG(blank())`  
  
Les mêmes limitations s'appliquent aux autres fonctions logarithmiques : LOG10 et LN.  
  
Pour plus d’informations sur le type de données **blank** dans DAX, consultez [Spécification de syntaxe DAX pour PowerPivot](/dax/dax-syntax-reference).
  
**Division par 0 et division par un espace**  
En mode DirectQuery, la division par zéro (0) ou la division par BLANK aura toujours pour résultat une erreur. SQL Server ne prend pas en charge la notion d'infini, et comme le résultat naturel de toute division par 0 est l'infini, le résultat est une erreur. Toutefois, SQL Server prend en charge la division par des valeurs Null, et le résultat doit toujours être égal à une valeur Null.  
  
Plutôt que de retourner des résultats différents pour ces opérations, en mode DirectQuery, les deux types d'opérations (division par zéro et division par une valeur Null) retournent une erreur.  
  
Notez que dans Excel et dans les modèles [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , la division par zéro retourne également une erreur. La division par un espace retourne un espace.  
  
Les expressions suivantes sont toutes valides dans les modèles en mémoire, mais échouent en mode DirectQuery :  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
L'expression `BLANK/BLANK` est un cas spécial qui retourne `BLANK` dans les modèles en mémoire et en mode DirectQuery.  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a>Plages numériques et de date/heure prises en charge  
Les formules dans [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] les modèles tabulaires et en mémoire sont soumises aux mêmes limitations qu’Excel en ce qui concerne les valeurs maximales autorisées pour les nombres réels et les dates. Toutefois, des différences peuvent survenir lorsque la valeur maximale est retournée à partir d'un calcul ou d'une requête, ou lorsque les valeurs sont converties, castées, arrondies ou tronquées.  
  
-   Si des valeurs des types **Currency** et **Real** sont multipliées, et que le résultat est supérieur à la valeur maximale possible, en mode DirectQuery, aucune erreur n’est générée et une valeur Null est retournée.  
  
-   Dans les modèles en mémoire, aucune erreur n'est générée, mais la valeur maximale est retournée.  
  
En général, étant donné que les plages de dates acceptées sont différentes pour Excel et SQL Server, les résultats peuvent être garantis pour correspondre uniquement lorsque les dates sont dans la plage de dates commune, qui compris les dates suivantes :  
  
-   Première date : 1er mars 1990  
  
-   Dernière date : 31 décembre 9999  
  
Si les dates utilisées dans les formules n'appartiennent pas à cette plage, la formule génère une erreur ou les résultats ne correspondent pas.  
  
**Valeurs à virgule flottante prises en charge par CEILING**  
EXEMPLE : `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`  
  
L'équivalent Transact-SQL de la fonction DAX CEILING prend uniquement en charge les valeurs avec une grandeur de 10^19 ou inférieure. Une règle empirique consiste à utiliser des valeurs en virgule flottante pour le type **bigint**.  
  
**Datepart fonctionne avec des dates qui sont hors limites**  
Les résultats en mode DirectQuery sont garantis pour correspondre à ceux des modèles en mémoire uniquement lorsque la date utilisée comme argument se trouve dans la plage de dates valide. Si ces conditions ne sont pas satisfaites, une erreur est générée, ou la formule retourne des résultats différents dans DirectQuery et dans le mode en mémoire.  
  
EXEMPLE : `MONTH(0)` ou `YEAR(0)`  
  
En mode DirectQuery, les expressions retournent 12 et 1899, respectivement.  
  
Dans les modèles en mémoire, les expressions retournent 1 et 1900, respectivement.  
  
EXEMPLE :  `EOMONTH(0.0001, 1)`  
  
Les résultats de cette expression ne correspondent que lorsque les données fournies comme paramètre se trouvent dans la plage de dates valide.  
  
EXEMPLE : `EOMONTH(blank(), blank())` ou `EDATE(blank(), blank())`  
  
Les résultats de cette expression doivent être identiques en mode DirectQuery et en mode en mémoire.  
  
**Troncation des valeurs d'heure**  
EXEMPLE : `SECOND(1231.04097222222)`  
  
En mode DirectQuery, le résultat est tronqué, selon les règles de SQL Server, et l'expression renvoie la valeur 59.  
  
Dans les modèles en mémoire, les résultats de chaque opération temporaire sont arrondis ; par conséquent, l'expression renvoie la valeur 0.  
  
L'exemple suivant montre comment cette valeur est calculée :  
  
1.  La fraction de l'entrée (0,04097222222) est multipliée par 24.  
  
2.  La valeur d'heure obtenue (0,98333333328) est multipliée par 60.  
  
3.  La valeur de minute obtenue est 58,9999999968.  
  
4.  La fraction de la valeur de minute (0,9999999968) est multipliée par 60.  
  
5.  La valeur de seconde obtenue (59,999999808) est arrondie au chiffre supérieur (60).  
  
6.  60 correspond à 0.  
  
**Type de données d'heure SQL non pris en charge**  
Les modèles en mémoire ne prennent pas en charge l’utilisation du nouveau type de données SQL **Time** . En mode DirectQuery, les formules qui référencent les colonnes de ce type de données retournent une erreur. Les colonnes de données d'heure ne peuvent pas être importées dans un modèle en mémoire.  
  
Toutefois, dans [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] et dans les modèles mis en cache, parfois le moteur convertit la valeur d’heure en un type de données acceptable, et la formule retourne un résultat.  
  
Ce comportement affecte toutes les fonctions qui utilisent une colonne de date comme paramètre.  
  
### <a name="currency"></a><a name="bkmk_Currency"></a>Accès  
En mode DirectQuery, si le résultat d’une opération arithmétique est de type **Currency**, la valeur doit être dans la plage suivante :  
  
-   Minimum : -922337203685477,5808  
  
-   Maximum : 922337203685477,5807  
  
**Combinaison de types de données Currency et REAL**  
EXEMPLE : `Currency sample 1`  
  
Si des types **Currency** et **Real** sont multipliés et que le résultat est supérieur à 9223372036854774784 (0x7ffffffffffffc00), le mode DirectQuery ne génère pas d’erreur.  
  
Dans un modèle en mémoire, une erreur est générée si la valeur absolue du résultat est supérieure à 922337203685477,4784.  
  
**L'opération génère une valeur hors limites**  
EXEMPLE : `Currency sample 2`  
  
Si des opérations sur deux valeurs monétaires quelconques génèrent une valeur qui est en dehors de la plage spécifiée, une erreur est générée dans les modèles en mémoire, mais pas dans les modèles DirectQuery.  
  
**Combinaison du type de données Currency avec d'autres types de données**  
La division de valeurs monétaires par des valeurs d'autres types numériques peut entraîner des résultats différents.  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a>Fonctions d’agrégation  
Les fonctions statistiques sur une table avec une ligne retournent des résultats différents. Les fonctions d'agrégation sur les tables vides se comportent différemment dans les modèles en mémoire et en mode DirectQuery.  
  
**Fonctions statistiques sur une table avec une seule ligne**  
Si la table utilisée comme argument contient une seule ligne, en mode DirectQuery, les fonctions statistiques telles STDEV et VAR retournent une valeur Null.  
  
Dans un modèle en mémoire, une formule qui utilise STDEV ou VAR sur une table avec une seule ligne retourne une erreur de division par zéro.  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a>Fonctions de texte  
Étant donné que les banques de données relationnelles fournissent différents types de données texte par rapport à Excel, vous pouvez voir des résultats différents lors de la recherche de chaînes ou lorsque vous utilisez des sous-chaînes. La longueur des chaînes peut également être différente.  
  
En général toutes les fonctions de manipulation de chaînes qui utilisent des colonnes de taille fixe comme arguments peuvent avoir des résultats différents.  
  
De plus, dans SQL Server, certaines fonctions de texte prennent en charge des arguments supplémentaires qui ne sont pas fournis dans Excel. Si la formule requiert l'argument manquant vous pouvez obtenir des résultats différents ou des erreurs dans le modèle en mémoire.  
  
**Les opérations qui retournent un caractère en utilisant LEFT, RIGHT, etc., peuvent retourner le caractère correct mais avec une casse différente, ou aucun résultat**  
EXEMPLE : `LEFT(["text"], 2)`  
  
En mode DirectQuery, la casse du caractère qui est retourné est toujours exactement la même que celle de la lettre stockée dans la base de données. Toutefois, le moteur xVelocity utilise un algorithme différent pour la compression et l'indexation des valeurs, afin d'améliorer les performances.  
  
Par défaut, le classement Latin1_General est utilisé, qui ne respecte pas la casse mais les accents. Par conséquent, s'il existe plusieurs instances d'une chaîne de texte en minuscules, majuscules, ou casse mixte, toutes les instances sont considérées comme la même chaîne, et seule la première instance de la chaîne est stockée dans l'index. Toutes les fonctions de texte exécutées sur les chaînes stockées récupèrent la partie spécifiée du formulaire indexé. Par conséquent, l'exemple de formule retourne la même valeur pour la colonne entière, à l'aide de la première instance comme entrée.  
  
[Stockage de chaîne et classement dans les modèles tabulaires](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
Ce comportement s'applique également aux autres fonctions de texte, notamment RIGHT, MID, etc.  
  
**La longueur de chaîne affecte les résultats**  
EXEMPLE : `SEARCH("within string", "sample target  text", 1, 1)`  
  
Si vous recherchez une chaîne à l'aide de la fonction SEARCH, et la chaîne cible est plus longue que la chaîne, le mode DirectQuery génère une erreur.  
  
Dans un modèle en mémoire, la chaîne recherchée est retournée, mais sa longueur est tronquée à la longueur du &lt;texte où se fait la recherche&gt;.  
  
EXEMPLE : `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`  
  
Si la longueur de la chaîne de remplacement est supérieure à la longueur de la chaîne d'origine, en mode DirectQuery, la formule retourne la valeur Null.  
  
Dans les modèles en mémoire, la formule suit le comportement d'Excel, qui concatène la chaîne source et la chaîne de remplacement, qui retourne CACalifornia.  
  
**TRIM implicite au milieu de chaînes**  
EXEMPLE : `TRIM(" A sample sentence with leading white space")`  
  
Le mode DirectQuery convertit la fonction DAX TRIM en instruction SQL `LTRIM(RTRIM(<column>))`. Par conséquent, seuls les espaces de début et de fin sont supprimés.  
  
En revanche, la même formule dans un modèle en mémoire supprime les espaces dans la chaîne, d'après le comportement d'Excel.  
  
**RTRIM implicite avec l'utilisation de la fonction LEN**  
EXEMPLE : `LEN('string_column')`  
  
Comme SQL Server, le mode DirectQuery supprime automatiquement les espaces de fin des colonnes de chaîne : autrement dit, il effectue un RTRIM implicite. Par conséquent, les formules qui utilisent la fonction LEN peuvent retourner des valeurs différentes si la chaîne possède des espaces de fin.  
  
**Le mode en mémoire prend en charge des paramètres supplémentaires pour SUBSTITUTE**  
EXEMPLE : `SUBSTITUTE([Title],"Doctor","Dr.")`  
  
EXEMPLE : `SUBSTITUTE([Title],"Doctor","Dr.", 2)`  
  
En mode DirectQuery, vous pouvez utiliser uniquement la version de cette fonction qui a trois (3) paramètres : une référence à une colonne, l'ancien texte et le nouveau texte. Si vous utilisez la deuxième formule, une erreur est générée.  
  
Dans les modèles en mémoire, vous pouvez utiliser un quatrième paramètre facultatif pour spécifier le nombre d'instances de la chaîne à remplacer. Par exemple, vous pouvez remplacer uniquement la deuxième instance, etc.  
  
**Restrictions relatives aux longueurs de chaîne pour les opérations REPT**  
Dans les modèles en mémoire, la longueur d'une chaîne résultant d'une opération en utilisant REPT doit être inférieure à 32 767 caractères.  
  
Cette restriction ne s'applique pas en mode DirectQuery.  
  
**Les opérations de sous-chaîne retournent des résultats différents selon le type de caractère**  
EXEMPLE : `MID([col], 2, 5)`  
  
Si le texte d **varchar** ou **nvarchar**, le résultat de la formule est toujours identique.  
  
Toutefois, si le texte est un caractère de longueur fixe et que la valeur de * &lt; num_chars &gt; * est supérieure à la longueur de la chaîne cible, en mode DirectQuery, un espace est ajouté à la fin de la chaîne de résultat.  
  
Dans un modèle en mémoire, le résultat se termine au dernier caractère de chaîne, sans remplissage.  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a>Fonctions prises en charge en mode DirectQuery  
Les fonctions DAX suivantes peuvent être utilisées en mode DirectQuery, mais avec les qualifications comme décrit dans la section précédente.  
  
**Fonctions de texte**  
  
CONCATENATE  
  
FIND  
  
LEFT  
  
LEN  
  
MID  
  
REPLACE  
  
REPT  
  
RIGHT  
  
SUBSTITUTE  
  
TRIM  
  
**Fonctions statistiques**  
  
COUNT  
  
STDEV.P  
  
STDEV.S  
  
STDEVX.P  
  
STDEVX.S  
  
VAR.P  
  
VAR.S  
  
VARX.P  
  
VARX.S  
  
**Fonctions de date/heure**  
  
DATE  
  
EDATE  
  
EOMONTH  
  
DATE  
  
TEMPS  
  
SECOND  
  
**Fonctions mathématiques et numériques**  
  
CEILING  
  
LN  
  
LOG  
  
LOG10  
  
POWER  
  
**Requêtes de table DAX**  
  
Il existe des limitations lorsque vous calculez des formules par rapport à un modèle DirectQuery à l'aide de requêtes de table DAX. DirectQuery ne prend pas en charge les références à la même colonne deux fois dans une clause ORDER BY. L'instruction Transact-SQL équivalente ne peut pas être créée et la requête échoue.  
  
Dans un modèle en mémoire, la répétition de la clause ORDER BY n'a aucun effet sur les résultats.  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a>Fonctions non prises en charge en mode DirectQuery  
Certaines fonctions DAX ne sont pas prises en charge dans les modèles qui sont déployés en mode DirectQuery. Les raisons pour lesquelles une fonction particulière n'est pas prise en charge peuvent notamment inclure une ou plusieurs de celles indiquées ci-après :  
  
-   Le moteur relationnel sous-jacent ne peut pas effectuer des calculs identiques à ceux effectués par le moteur xVelocity.  
  
-   La formule ne peut pas être convertie en une expression SQL équivalente.  
  
-   Les performances de l'expression convertie et les calculs résultants sont inacceptables.  
  
Les fonctions DAX suivantes ne peuvent pas être utilisées dans les modèles DirectQuery.  
  
**Fonctions PATH**  
  
PATH  
  
PATHCONTAINS  
  
PATHITEM  
  
PATHITEMREVERSE  
  
PATHLENGTH  
  
**Fonctions diverses**  
  
COUNTBLANK  
  
FIXED  
  
FORMAT  
  
RAND  
  
RANDBETWEEN  
  
**Fonctions Time Intelligence : dates de début et de fin**  
  
DATESQTD  
  
DATESYTD  
  
DATESMTD  
  
DATESQTD  
  
DATESINPERIOD  
  
TOTALMTD  
  
TOTALQTD  
  
TOTALYTD  
  
DATESINPERIOD  
  
SAMEPERIODLASTYEAR  
  
PARALLELPERIOD  
  
**Fonctions Time Intelligence : soldes**  
  
OPENINGBALANCEMONTH  
  
OPENINGBALANCEQUARTER  
  
OPENINGBALANCEYEAR  
  
CLOSINGBALANCEMONTH  
  
CLOSINGBALANCEQUARTER  
  
CLOSINGBALANCEYEAR  
  
**Fonctions Time Intelligence : périodes précédente et suivante**  
  
PREVIOUSDAY  
  
PREVIOUSMONTH  
  
PREVIOUSQUARTER  
  
PREVIOUSYEAR  
  
NEXTDAY  
  
NEXTMONTH  
  
NEXTQUARTER  
  
NEXTYEAR  
  
**Fonctions Time Intelligence : périodes et calculs sur les périodes**  
  
STARTOFMONTH  
  
STARTOFQUARTER  
  
STARTOFYEAR  
  
ENDOFMONTH  
  
ENDOFQUARTER  
  
ENDOFYEAR  
  
FIRSTDATE  
  
LASTDATE  
  
DATEADD  
  
## <a name="see-also"></a>Voir aussi  
[Mode DirectQuery (SSAS Tabulaire)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

