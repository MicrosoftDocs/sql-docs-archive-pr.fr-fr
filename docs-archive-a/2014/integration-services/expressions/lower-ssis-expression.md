---
title: LOWER (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 180be8f3cfb5a15eb0fcd6ddd3d63b09fe874af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604650"
---
# <a name="lower-ssis-expression"></a>LOWER (expression SSIS)
  Renvoie une expression de caractères après avoir transformé les caractères majuscules en caractères minuscules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Expression de type caractère à convertir en caractères minuscules.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La fonction LOWER n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *character_expression* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que UPPER effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 La fonction LOWER renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant convertit un littéral de chaîne en caractères minuscules. Le résultat obtenu est « new york ».  
  
```  
LOWER("New York")  
```  
  
 L’exemple suivant convertit tous les caractères de la colonne d’entrée **Color** , à l’exception du premier caractère, en caractères minuscules. Si la colonne Color a pour valeur JAUNE, le résultat obtenu est « Jaune ». Pour plus d’informations, consultez [SUBSTRING &#40;expression SSIS&#41;](substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 L’exemple suivant convertit la valeur de la variable **CityName** en caractères minuscules.  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [UPPER &#40;expression SSIS&#41;](upper-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
