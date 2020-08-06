---
title: ~ (NOT au niveau du bit) (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611919"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT au niveau du bit) (expression SSIS)
  Effectue une négation au niveau du bit d'un entier. Cet opérateur est applicable aux types de données entier signé et non signé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression*  
 Toute expression valide d'un type de données integer. *integer*_*expression* est un nombre entier transformé en nombre binaire pour l’opération au niveau du bit. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *integer_expression*.  
  
## <a name="remarks"></a>Notes  
 None  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant réalise une opération NOT au niveau du bit ( ~ ) sur le nombre 170 (0000 0000 1010 1010). Le nombre est un entier signé.  
  
```  
  
~ 170  
```  
  
 L'expression renvoie la valeur -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
