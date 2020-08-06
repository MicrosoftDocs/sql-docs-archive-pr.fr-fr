---
title: Création de membres calculés dans MDX (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604184"
---
# <a name="building-calculated-members-in-mdx-mdx"></a>Création de membres calculés dans MDX (MDX)
  Dans MDX (Multidimensional Expressions), un membre calculé est un membre qui est résolu par le retour d'une valeur issue du calcul d'une expression MDX. Cette définition anodine couvre un vaste champ d'action. La possibilité de bâtir et d'utiliser des membres calculés dans une requête MDX est un élément fondamental de la manipulation des données multidimensionnelles.  
  
 Vous pouvez créer des membres calculés en n'importe quel point d'une hiérarchie. Vous pouvez également créer des membres calculés qui dépendent non seulement des membres existants d'un cube, mais aussi d'autres membres calculés définis dans la même expression MDX.  
  
 Vous pouvez définir pour un membre calculé l'un des contextes suivants :  
  
-   **Étendue de requête** Pour créer un membre calculé défini en tant que partie d’une requête MDX, et dont l’étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser le membre calculé au sein d'une instruction MDX SELECT. Ainsi, vous pouvez modifier le membre calculé créé à l'aide du mot clé WITH sans porter atteinte à l'instruction SELECT.  
  
     Pour plus d’informations sur l’utilisation du mot clé WITH pour la création de membres calculés, consultez [Création de membres calculés d’étendue de requête &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Étendue de session** Pour créer un membre calculé dont l’étendue est plus vaste que le contexte de la requête, c’est-à-dire dont l’étendue soit la durée de la session MDX, utilisez l’instruction CREATE MEMBER. Un membre calculé défini à l'aide de l'instruction CREATE MEMBER est disponible pour toutes les requêtes MDX de cette session. L'instruction CREATE MEMBER est appropriée par exemple dans le cas d'une application cliente qui réutilise le même jeu dans différentes requêtes.  
  
     Pour plus d’informations sur l’utilisation de l’instruction CREATE MEMBER pour la création de membres calculés dans une session, consultez [Création de membres calculés au niveau de la session &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction CREATe MEMBER &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Référence des fonctions MDX &#40;&#41;MDX](/sql/mdx/mdx-function-reference-mdx)   
 [Instruction SELECT &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
