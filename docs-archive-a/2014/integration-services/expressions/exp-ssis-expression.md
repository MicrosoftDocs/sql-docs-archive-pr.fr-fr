---
title: EXP (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 150c92355ab3e0d3a028c98defe2e2fa9a1bf8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610738"
---
# <a name="exp-ssis-expression"></a>EXP (expression SSIS)
  Renvoie l'exposant en base e d'une expression numérique. La fonction EXP est complémentaire de l'action LN et est parfois appelée « antilogarithme ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types des résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 L'expression numérique est convertie vers le type de données DT_R8 avant le calcul du l'exposant. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Le résultat obtenu est toujours un nombre positif.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction EXP à des valeurs positive, négative, ainsi qu'à la valeur zéro.  
  
```  
EXP(74)  
```  
  
 Renvoie 1,373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Renvoie 1,879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Renvoie 1.  
  
## <a name="see-also"></a>Voir aussi  
 [LOG &#40;expression SSIS&#41;](log-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
