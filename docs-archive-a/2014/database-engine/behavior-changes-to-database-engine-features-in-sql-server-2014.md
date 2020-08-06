---
title: Changements de comportement des fonctionnalités de Moteur de base de données dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9072b851f3512113b23dedc91f8c9b7151136a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700241"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Changements de comportement des fonctionnalités du moteur de base de données de SQL Server 2014
  Cette rubrique décrit les changements de comportement dans le [!INCLUDE[ssDE](../includes/ssde-md.md)]. Les modifications de comportement affectent le mode de fonctionnement ou d'interaction des fonctionnalités dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] par rapport aux versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a>Changements de comportement dans[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les requêtes sur un document XML contenant des chaînes dépassant une certaine longueur (plus de 4020 caractères) peuvent contenir des résultats incorrects. Dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], ces requêtes retournent les résultats corrects.  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a>Changements de comportement dans[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Découverte des métadonnées  
 Les améliorations apportées à à [!INCLUDE[ssDE](../includes/ssde-md.md)] partir de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] permettent à SQLDescribeCol d’obtenir des descriptions plus précises des résultats attendus que ceux retournés par SQLDescribeCol dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Découverte des métadonnées](../relational-databases/native-client/features/metadata-discovery.md).  
  
 L’option [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) pour déterminer le format d’une réponse sans exécuter la requête est remplacée par [sp_describe_first_result_set &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [sys. dm_exec_describe_first_result_set &#40;transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)et [sys. dm_exec_describe_first_result_set_for_object &#40;Transact-SQL ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)&#41;.  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Modifications du comportement dans le script d'une tâche SQL Server Agent  
À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , si vous créez un nouveau travail en copiant le script d’un travail existant, le nouveau travail risque d’affecter par inadvertance le travail existant. Pour créer un nouveau travail à l’aide du script d’un travail existant, supprimez manuellement le paramètre * \@ schedule_uid* qui est généralement le dernier paramètre de la section qui crée la planification du travail dans le travail existant. Vous créez ainsi une planification indépendante pour le nouveau travail sans affecter les travaux existants.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>Assemblage de constantes pour les Fonctions CLR définies par l'utilisateur et les méthodes  
À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , les objets CLR définis par l’utilisateur suivants sont maintenant pliables :  

-   Fonctions CLR définies par l'utilisateur à valeur scalaire déterministes.  
-   Méthodes déterministes des types CLR définis par l'utilisateur.  
  
 Cette amélioration s'efforce d'améliorer les performances lorsque ces fonctions ou méthodes sont appelées plusieurs fois avec les mêmes arguments. Toutefois, cette modification peut générer des résultats inattendus lorsque des fonctions ou méthodes non déterministes ont été marquées comme étant déterministes par erreur. Le déterminisme d'une fonction ou d'une méthode CLR est indiqué par la valeur de la propriété `IsDeterministic` de `SqlFunctionAttribute` ou de `SqlMethodAttribute`.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>Le comportement de la méthode de STEnvelope() a changé avec les types spatiaux vides  
 Le comportement de la méthode `STEnvelope` avec des objets vides est maintenant compatible avec le comportement d'autres méthodes spatiales [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], la méthode `STEnvelope` retournait les résultats suivants lorsqu'elle était appelée avec des objets vides :  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], la méthode `STEnvelope` retourne maintenant les résultats suivants lorsqu'elle est appelée avec des objets vides :  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 Pour déterminer si un objet spatial est vide, appelez la méthode [STIsEmpty &#40;Geometry type de données&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) .  
  
### <a name="log-function-has-new-optional-parameter"></a>La fonction LOG dispose d'un nouveau paramètre facultatif  
 La `LOG` fonction a désormais un paramètre de *base* facultatif. Pour plus d’informations, consultez [journal &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Le calcul des statistiques pour les opérations d'index partitionnés a changé  
Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], les statistiques ne sont pas créées en analysant toutes les lignes de la table lorsqu'un index partitionné est créé ou reconstruit. Au lieu de cela, l’optimiseur de requête utilise l’algorithme d’échantillonnage par défaut pour générer des statistiques. Après la mise à niveau d'une base de données avec des index partitionnés, vous pouvez remarquer une différence dans les données d'histogramme pour ces index. Cette modification du comportement peut ne pas affecter les performances des requêtes. Pour obtenir des statistiques sur les index partitionnés en analysant toutes les lignes de la table, utilisez `CREATE STATISTICS` ou `UPDATE STATISTICS` avec la clause `FULLSCAN`.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>La conversion de type de données par la méthode XML value a changé  
Le comportement interne de la méthode `value` de type de données `xml` a changé. Cette méthode exécute une requête XQuery sur le XML et retourne une valeur scalaire du type de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifié. Le type xs doit être converti en type de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Précédemment, la méthode `value` convertissait en interne la valeur source en type xs:string, puis convertissait le type xs:string en type de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], la conversion en xs:string est ignorée dans les cas suivants :  
  
|Type de données XS source|Type de données SQL Server de destination|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> int<br /><br /> entier<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|TINYINT<br /><br /> SMALLINT<br /><br /> int<br /><br /> bigint<br /><br /> Décimal<br /><br /> numeric|  
|Décimal|Décimal<br /><br /> numeric|  
|float|real|  
|double|float|  
  
 Le nouveau comportement améliore les performances lorsque la conversion intermédiaire peut être ignorée. Toutefois, lorsque la conversion des types de données échoue, des messages d'erreur différents de ceux qui ont été générés lors de la conversion à partir de la valeur xs:string intermédiaire s'affichent. Par exemple, si la méthode value n'a pas réussi à convertir la valeur `int` 100 000 en `smallint`, le message d'erreur précédent était :  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], sans conversion intermédiaire en xs:string, le message d'erreur est :  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>Changement de comportement de sqlcmd.exe en mode XML  
 Vous pouvez modifier le comportement si vous utilisez sqlcmd.exe avec le mode XML ( : commande XML ON) lors de l’exécution d’une commande SELECT * FROM T FOR XML....  
  
### <a name="dbcc-checkident-revised-message"></a>Message modifié par DBCC CHECKIDENT  
 Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , le message retourné par la commande DBCC CHECKIDENT a changé uniquement lorsqu’il est utilisé avec RESEED *new_reseed_value* pour modifier la valeur d’identité actuelle. Le nouveau message est *« vérification des informations d’identité : valeur d’identité actuelle « » \<current identity value> »*. Exécution de DBCC terminée. Si DBCC vous a adressé des messages d'erreur, contactez l'administrateur système. »  
  
 Dans les versions antérieures, le message est *« vérification des informations d’identité : valeur d’identité actuelle « » \<current identity value> , valeur de colonne actuelle « \<current column value> ». Exécution de DBCC terminée. Si DBCC a imprimé des messages d’erreur, contactez votre administrateur système.»* Le message est inchangé lorsque `DBCC CHECKIDENT` est spécifié avec `NORESEED` , sans deuxième paramètre, ou sans valeur de réamorçage. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Le comportement de la fonction exist() la fonction sur le type de données XML a changé  
 Le comportement de la `exist()` fonction a changé lors de la comparaison d’un type de données XML avec une valeur null à 0 (zéro). Prenons l’exemple suivant :  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 Dans les versions antérieures, cette comparaison retournait 1 (true) ; maintenant, elle retourne 0 (zéro, false).  
  
 Les comparaisons suivantes n'ont pas changé :  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications importantes apportées aux fonctionnalités de Moteur de base de données dans SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Fonctionnalités de Moteur de base de données dépréciées dans SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Fonctionnalités de Moteur de base de données abandonnées dans SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
