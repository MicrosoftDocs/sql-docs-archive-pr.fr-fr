---
title: Contenu de FORMAT_STRING (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- formats [Analysis Services], string values
- VALUE property
- formats [Analysis Services], numeric values
- FORMATTED_VALUE property
- FORMAT_STRING contents
ms.assetid: c354c938-0328-4b8e-adc5-3b52fd2a7152
author: minewiskan
ms.author: owend
ms.openlocfilehash: 429d852db6a7613d960c6e85429caefd75b4cfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600264"
---
# <a name="format_string-contents-mdx"></a>Contenu de FORMAT_STRING (MDX)
  La propriété de cellule `FORMAT_STRING` met en forme la propriété de cellule `VALUE`, en créant la valeur de la propriété de cellule `FORMATTED_VALUE`. La propriété de cellule `FORMAT_STRING`, qui traite les valeurs brutes de types chaîne et numérique, applique une expression de format à la valeur afin de retourner une valeur mise en forme pour la propriété de cellule `FORMATTED_VALUE`. Les tableaux suivants détaillent la syntaxe et les caractères de mise en forme utilisés pour traiter les valeurs de type chaîne et numérique.  
  
## <a name="string-values"></a>Valeurs de type chaîne  
 Une expression de format pour une chaîne peut posséder une section, ou deux sections séparées par un point-virgule (;).  
  
|Usage|Résultats|  
|-----------|------------|  
|Une section|La mise en forme s'applique à toutes les valeurs de type chaîne.|  
|Deux sections|La première section s'applique aux données de type chaîne tandis que la seconde s'applique aux valeurs NULL et aux chaînes de longueur zéro ("").|  
  
 Les caractères décrits dans le tableau suivant peuvent apparaître dans la chaîne de format des chaînes de caractères.  
  
|Caractère|Description|  
|---------------|-----------------|  
|@|Représente un espace réservé de caractère qui affiche un caractère ou un espace. Si la chaîne possède un caractère à l'endroit où figure le signe « a » commercial (@) dans la chaîne de format, elle affiche ce caractère. Sinon, un espace est affiché à la place. Les espaces réservés se remplissent de la droite vers la gauche sauf si un point d'exclamation (!) est présent dans la chaîne de format.|  
|&|Représente un espace réservé de caractère qui affiche un caractère ou rien. Si la chaîne possède un caractère à l'endroit où figure le signe « et » commercial (&), la chaîne mise en forme affiche ce caractère. Sinon, rien n'est affiché. Les espaces réservés se remplissent de la droite vers la gauche sauf si un point d'exclamation (!) est présent dans la chaîne de format.|  
|\<|Impose les caractères minuscules. La chaîne mise en forme affiche tous les caractères en minuscules.|  
|>|Impose les caractères majuscules. La chaîne mise en forme affiche tous les caractères en majuscules.|  
|!|Impose le remplissage des espaces réservés de la gauche vers la droite. (Par défaut, ils se remplissent de la droite vers la gauche.)|  
  
## <a name="numeric-values"></a>Valeurs numériques  
 Pour les nombres, une expression de format définie par l'utilisateur peut posséder de une à quatre sections, séparées par des points-virgules. Si l'argument de format contient l'un des formats numériques nommés, une seule section est autorisée.  
  
|Usage|Résultats|  
|-----------|------------|  
|Une section|L'expression de format s'applique à toutes les valeurs.|  
|Deux sections|La première section s'applique aux valeurs positives et aux zéros, et la seconde aux valeurs négatives.|  
|Trois sections|La première section s'applique aux valeurs positives, la deuxième aux valeurs négatives et la troisième aux zéros.|  
|Quatre sections|La première section s'applique aux valeurs positives, la deuxième aux valeurs négatives, la troisième aux zéros et la quatrième aux valeurs NULL.|  
  
 L'exemple suivant possède deux sections : la première définit le format des valeurs positives et des zéros, tandis que la seconde définit le format des valeurs négatives.  
  
```  
"$#,##0;($#,##0)"  
```  
  
 Si vous incluez des points-virgules sans rien entre, la section manquante utilise le format de la valeur positive. Par exemple, le format suivant affiche les valeurs positives et négatives d'après le format défini dans la première section et affiche « Zéro » si la valeur est zéro :  
  
```  
"$#,##0;;\Z\e\r\o"  
```  
  
 Le tableau suivant décrit les caractères qui peuvent figurer dans la chaîne de format des nombres.  
  
|Caractère|Description|  
|---------------|-----------------|  
|None|Affiche le nombre sans mise en forme.|  
|**0**|Représente un espace réservé de chiffre qui affiche un chiffre ou zéro (0).<br /><br /> Si le nombre possède un chiffre là où figure le zéro dans la chaîne de format, la valeur mise en forme affiche ce chiffre. Sinon, zéro est affiché à la place.<br /><br /> Si le nombre contient moins de chiffres que de zéros (de part et d'autre du séparateur décimal) dans l'expression de format, la valeur mise en forme affiche des zéros non significatifs ou à droite.<br /><br /> Si le nombre contient davantage de chiffres à droite du séparateur décimal qu'il n'y a de zéros à droite du séparateur décimal dans l'expression de format, la valeur mise en forme arrondit le nombre à autant de positions décimales qu'il y a de zéros.<br /><br /> Si le nombre comporte davantage de chiffres à gauche du séparateur décimal qu'il n'y a de zéros à gauche du séparateur décimal dans l'expression de format, la valeur mise en forme affiche les chiffres supplémentaires sans modification.|  
|**#**|Représente un espace réservé de chiffre qui affiche un chiffre ou rien.<br /><br /> Si l’expression contient un chiffre à l’emplacement où le signe dièse ( **#** ) apparaît dans la chaîne de format, la valeur mise en forme affiche le chiffre. Sinon, rien n'est affiché à la place.<br /><br /> L' **#** espace réservé de signe dièse () fonctionne comme l’espace réservé de chiffre zéro (**0**), sauf que les zéros de début et de fin ne sont pas affichés si le nombre a un nombre de chiffres inférieur ou égal à celui des caractères situés de **#** part et d’autre du séparateur décimal dans l’expression de format.|  
|**.**|Représente un espace réservé de décimale qui détermine le nombre de chiffres affichés à gauche et à droite du séparateur décimal.<br /><br /> Si l’expression de format contient uniquement **#** des caractères dièse () à gauche du point (**.**), les nombres inférieurs à 1 commencent par un séparateur décimal. Pour afficher un zéro non significatif avec des nombres fractionnaires, utilisez zéro (0) comme premier espace réservé de chiffre à gauche du séparateur décimal.<br /><br /> Le caractère effectivement utilisé comme séparateur décimal dans le résultat mis en forme dépend du format numérique reconnu par votre système.<br /><br /> Remarque : dans certains paramètres régionaux, une virgule est utilisée comme séparateur décimal.|  
|**%**|Représente un espace réservé de pourcentage. L'expression est multipliée par 100. Le caractère de pourcentage ( **%** ) est inséré à l’emplacement où le pourcentage s’affiche dans la chaîne de format.|  
|**,**|Représente un séparateur de milliers qui sépare les milliers des centaines dans un nombre possédant quatre chiffres ou plus à gauche du séparateur décimal.<br /><br /> L’utilisation standard du séparateur de milliers est spécifiée si le format contient un séparateur de milliers entouré par des espaces réservés de chiffres (**0** ou **#**).<br /><br /> La présence de deux séparateurs des milliers contigus, ou d'un séparateur des milliers juste à gauche du séparateur décimal (qu'une décimale soit ou non spécifiée), signifie « changer l'échelle du nombre en le divisant par 1 000, en l'arrondissant le cas échéant ». Par exemple, vous pouvez utiliser la chaîne de format «**##0**,, » pour représenter 100 millions par 100. Les nombres inférieurs à 1 million sont affichés sous forme de 0. Deux séparateurs des milliers adjacents dans toute position autre qu'immédiatement à gauche du séparateur décimal sont traités comme spécifiant l'utilisation d'un séparateur des milliers.<br /><br /> Le caractère effectivement utilisé comme séparateur des milliers dans le résultat mis en forme dépend du format numérique reconnu par votre système.<br /><br /> Remarque : dans certains paramètres régionaux, un point est utilisé comme séparateur de milliers.|  
|**:**|Représente un séparateur horaire qui sépare les heures, les minutes et les secondes lors de la mise en forme de valeurs horaires.<br /><br /> Remarque : dans certains paramètres régionaux, d’autres caractères peuvent être utilisés comme séparateurs d’heure.<br /><br /> Le caractère réel utilisé comme séparateur d'heure dans le résultat mis en forme est déterminé par les paramètres système de votre ordinateur.|  
|**/**|Représente un séparateur de date qui sépare le jour, le mois et l'année lorsque les valeurs de date sont mises en forme.<br /><br /> Le caractère réel utilisé comme séparateur de date dans le résultat mis en forme est déterminé par les paramètres système de votre ordinateur.<br /><br /> Remarque : dans certains paramètres régionaux, d’autres caractères peuvent être utilisés comme séparateurs de date.|  
|**E- E+ e- e+**|Représente le format scientifique.<br /><br /> Si l’expression de format contient au moins un espace réservé de chiffre (**0** ou **#**) à droite de **E-**, **E+**, **e-** ou **e+**, la valeur mise en forme affiche le nombre dans le format scientifique, et E ou e est inséré entre le nombre et son exposant. Le nombre d'espaces réservés à des chiffres à droite détermine le nombre de chiffres dans l'exposant. Utilisez **e** -ou **e-** pour inclure un signe moins à côté des exposants négatifs. Utilisez **E+** ou **e+** pour insérer un signe moins à côté des exposants négatifs et un signe plus à côté des exposants positifs.|  
|**- + $ ( )**|Affiche un caractère littéral.<br /><br /> Pour afficher un caractère autre que l’un de ceux listés, placez une barre oblique inverse ( **\\** ) avant le caractère ou placez-le entre guillemets doubles (**""**).|  
|**\\**|Affiche le prochain caractère de la chaîne de format.<br /><br /> Pour afficher un caractère ayant une signification spéciale sous la forme d’un caractère littéral, placez une barre oblique inverse ( **\\** ) avant le caractère. La barre oblique inverse elle-même n'est pas affichée. L'utilisation d'une barre oblique inverse équivaut à mettre le caractère suivant entre des guillemets doubles. Pour afficher une barre oblique inverse, utilisez deux barres obliques inverses ( **\\\\** ). Exemples de caractères ne pouvant pas être affichés comme caractères littéraux :<br /><br /> Les caractères de mise en forme de la date et de l’heure-**a**, **c**, **d**, **h**, **m**, **n**, **p**, **q**, **s**, **t**, **w**, **y**, **/** et **:**<br /><br /> Caractères de mise en forme numérique- **#** , **0**, **%** , **e**, **e**, **virgule**et **point**<br /><br /> Caractères de mise en forme de chaîne : **@** , **&** , **\<**, **>** et **!**|  
|**ABC**|Affiche la chaîne placée entre les guillemets doubles (**" "**).<br /><br /> Pour codifier l’insertion d’une chaîne dans le format, placez le texte entre Chr(**34**). (Le code de caractère pour un guillemet double est **34**.)|  
  
### <a name="named-numeric-formats"></a>Formats numériques nommés  
 Le tableau suivant identifie les noms de formats numériques prédéfinis :  
  
|Nom de format|Description|  
|-----------------|-----------------|  
|`General Number`|Affiche le nombre sans séparateur de milliers.|  
|`Currency`|Affiche le nombre avec un séparateur de milliers, le cas échéant. Affiche deux chiffres situés à droite du séparateur décimal. Le résultat dépend des paramètres régionaux système.|  
|`Fixed`|Affiche au moins un chiffre à gauche et deux chiffres à droite du séparateur décimal.|  
|`Standard`|Affiche le nombre avec séparateur de milliers, au moins un chiffre à gauche et deux chiffres à droite du séparateur décimal.|  
|`Percent`|Affiche le nombre multiplié par 100 avec un signe de pourcentage (%) ajouté à droite. Affiche toujours deux chiffres situés à droite du séparateur décimal.|  
|`Scientific`|Utilise la notation scientifique standard.|  
|`Yes/No`|Affiche Non si le nombre est 0 ; sinon, affiche Oui.|  
|`True/False`|Affiche False si le nombre est 0 ; sinon, affiche True.|  
|`On/Off`|Affiche Off si le nombre est 0 ; sinon, affiche On.|  
  
## <a name="date-values"></a>Valeurs de date  
 Le tableau suivant décrit les caractères qui peuvent figurer dans les chaînes de format de date et d'heure.  
  
|Caractère|Description|  
|---------------|-----------------|  
|**:**|Représente un séparateur horaire qui sépare les heures, les minutes et les secondes lors de la mise en forme de valeurs horaires.<br /><br /> Le caractère réel utilisé comme séparateur d'heure dans le résultat mis en forme est déterminé par les paramètres système de votre ordinateur.<br /><br /> Remarque : dans certains paramètres régionaux, d’autres caractères peuvent être utilisés comme séparateurs d’heure.|  
|**/**|Représente un séparateur de date qui sépare le jour, le mois et l'année lorsque les valeurs de date sont mises en forme.<br /><br /> Le caractère réel utilisé comme séparateur de date dans le résultat mis en forme est déterminé par les paramètres système de votre ordinateur.<br /><br /> Remarque : dans certains paramètres régionaux, d’autres caractères peuvent être utilisés pour représenter le séparateur de date.|  
|**C**|Affiche, dans l'ordre, la date sous la forme **ddddd** et l'heure sous la forme **ttttt**.<br /><br /> Affiche uniquement les informations de date si le numéro de série de la date ne comporte pas de partie fractionnaire. Affiche uniquement les informations d'heure s'il n'y a pas de partie entière.|  
|**d**|Affiche le jour sous la forme d’un nombre sans zéro non significatif (1-31).|  
|**JJ**|Affiche le jour sous la forme d’un nombre avec un zéro non significatif (01-31).|  
|**ddd**|Affiche le jour sous la forme d’une abréviation (Dim-SAT).|  
|**dddd**|Affiche le jour sous la forme d’un nom complet (dimanche-samedi).|  
|**ddddd**|Affiche la date complète (jour, mois et année), d'après le format de date abrégée défini sur votre système.<br /><br /> Pour Microsoft Windows, le format de date abrégée par défaut est **j/m/aa**.|  
|**dddddd**|Affiche un numéro de série de date complète (jour, mois et année), d'après le format de date complète défini sur votre système.<br /><br /> Pour Windows, le format de date complète par défaut est **mmmm dd, yyyy**.|  
|**w**|Affiche le jour de la semaine sous la forme d'un nombre (de 1 pour dimanche à 7 pour samedi).|  
|**ww**|Affiche la semaine de l’année sous la forme d’un nombre (1-54).|  
|**lecteur**|Affiche le mois sous la forme d’un nombre sans zéro non significatif (1-12).<br /><br /> Si **m** suit immédiatement **h** ou **hh**, les minutes sont affichées au lieu du mois.|  
|**MM**|Affiche le mois sous la forme d’un nombre avec un zéro non significatif (01-12).<br /><br /> Si **m** suit immédiatement **h** ou **hh**, les minutes sont affichées au lieu du mois.|  
|**mmm**|Affiche le mois sous forme abrégée (Jan-Déc).|  
|**mmmm**|Affiche le mois sous la forme d’un nom de mois complet (janvier-décembre).|  
|**question**|Affiche le trimestre de l’année sous la forme d’un nombre (1-4).|  
|**y**|Affiche le jour de l’année sous la forme d’un nombre (1-366).|  
|**YY**|Affiche l’année sous la forme d’un nombre à deux chiffres (00-99).|  
|**AAA**|Affiche l’année sous la forme d’un nombre à quatre chiffres (100-9999).|  
|**h**|Affiche l’heure sous la forme d’un nombre sans zéro non significatif (0-23).|  
|**hh**|Affiche l’heure sous la forme d’un nombre avec des zéros non significatifs (00-23).|  
|**n**|Affiche la minute sous la forme d’un nombre sans zéro non significatif (0-59).|  
|**nn**|Affiche la minute sous la forme d’un nombre avec des zéros non significatifs (00-59).|  
|**x**|Affiche la seconde sous la forme d’un nombre sans zéro non significatif (0-59).|  
|**ss**|Affiche la seconde sous la forme d’un nombre avec des zéros non significatifs (00-59).|  
|**t t t t t**|Affiche l'heure complète (heures, minutes et secondes), dans une mise en forme qui reprend le séparateur horaire défini dans les paramètres horaires de votre système.<br /><br /> Un zéro non significatif apparaît si l'option du zéro non significatif est sélectionnée et si l'heure est antérieure à 10:00, dans le cycle A.M. ou P.M. cycle. Par exemple, 09:59.<br /><br /> Pour Windows, le format d'heure par défaut est **h:mm:ss**.|  
|**AM/PM**|Affiche **AM** en majuscules avec toute heure comprise entre minuit et midi et **PM** en majuscules avec toute heure comprise entre midi et minuit.<br /><br /> Remarque : utilise le format d’horloge sur 12 heures.|  
|**AM/PM**|Affiche **am** en minuscules avec toute heure comprise entre minuit et midi, et **pm** en minuscules avec toute heure comprise entre midi et minuit.<br /><br /> Remarque : utilise le format d’horloge sur 12 heures.|  
|**A/P**|Affiche un **A** majuscule avec toute heure comprise entre minuit et midi et **P** majuscule avec toute heure comprise entre midi et minuit.<br /><br /> Remarque : utilise le format d’horloge sur 12 heures.|  
|**a/p**|Affiche un **a** minuscule avec toute heure comprise entre minuit et midi, et **p** minuscule avec toute heure comprise entre midi et minuit.<br /><br /> Remarque : utilise le format d’horloge sur 12 heures.|  
|**AMPM**|Affiche la constante de chaîne AM telle qu'elle est définie par votre système avec toute heure comprise entre minuit et midi, et la constante de chaîne PM telle qu'elle est définie par votre système avec toute heure comprise entre midi et minuit.<br /><br /> Remarque : utilise le format d’horloge sur 12 heures.<br /><br /> **AMPM** peut être exprimé en majuscules ou en minuscules, mais la casse de la chaîne affichée correspond à la définition de la chaîne dans les paramètres de votre système.<br /><br /> Pour Windows, le format par défaut est **AM/PM**.|  
  
### <a name="named-date-formats"></a>Formats de date nommés  
 Le tableau suivant identifie les noms de formats de date et d'heure prédéfinis :  
  
|Nom de format|Description|  
|-----------------|-----------------|  
|`General Date`|Affiche une date et/ou une heure. Pour les nombres réels, affiche une date et une heure, par exemple, 4/3/93 17:34. En l'absence de partie fractionnaire, affiche uniquement une date, par exemple, 4/3/93. En l'absence de partie entière, affiche uniquement une heure, par exemple, 17:34. Le format de l'affichage de la date est déterminé par vos paramètres système.|  
|`Long Date`|Affiche une date en fonction du format de date longue de votre système.|  
|`Medium Date`|Affiche une date à l'aide du format de date moyen approprié pour la version linguistique de l'application hôte.|  
|`Short Date`|Affiche une date en utilisant le format de date courte de votre système.|  
|`Long Time`|Affiche une heure en utilisant le format d'heure longue de votre système ; comprend généralement les heures, minutes et secondes.|  
|`Medium Time`|Affiche une heure au format 12 heures en utilisant les heures et minutes et l'indicateur AM/PM.|  
|`Short Time`|Affiche une heure au format 24 heures, par exemple 17:45.|  
  
## <a name="see-also"></a>Voir aussi  
 [LANGUE et FORMAT_STRING sur FORMATED_VALUE](mdx-cell-properties-formatted-value-property.md)   
 [Utilisation des propriétés de cellule &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)   
 [Création et utilisation de valeurs de propriété &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
