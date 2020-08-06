---
title: Configurer le niveau (tous) pour les hiérarchies d’attribut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698694"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a>Configurer le niveau (Tous) des hiérarchies d'attributs
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , le niveau (tous) est un niveau facultatif, généré par le système. Il contient un seul membre dont la valeur est l'agrégation des valeurs de tous les membres du niveau situé juste en dessous. Ce membre est appelé membre Tous. Ce membre est créé par le système et il ne figure pas dans la table de dimension. Étant donné que le membre du niveau (Tous) se trouve au sommet d'une hiérarchie, sa valeur est l'agrégation consolidée des valeurs de tous les membres de la hiérarchie. Le membre Tous sert souvent de membre par défaut d'une hiérarchie.  
  
 La présence d'un niveau (Tous) dans une hiérarchie d'attributs dépend de la valeur de la propriété `IsAggregatable` de l'attribut, et la présence d'un niveau (Tous) dans une hiérarchie définie par l'utilisateur dépend de la propriété `IsAggregatable` de l'attribut au niveau le plus élevé de la hiérarchie définie par l'utilisateur. Si la propriété `IsAggregatable` a la valeur `True`, il existera un niveau (Tous). Au contraire, une hiérarchie n'a pas de niveau (Tous) si sa propriété `IsAggregatable` a la valeur `False`.  
  
## <a name="establishing-the-topmost-level"></a>Établissement du niveau le plus élevé  
 Si la propriété `IsAggregatable` de l'attribut source d'un niveau d'une hiérarchie a la valeur `False`, aucun niveau agrégeable ne peut apparaître dans la hiérarchie au-dessus de ce niveau. Un niveau non agrégeable doit être le niveau le plus élevé d'une hiérarchie, ou la propriété `IsAggregatable` des attributs sources des niveaux qui sont au-dessus de lui doit aussi avoir la valeur `False`.  
  
## <a name="all-member-and-all-level"></a>Membre Tous et niveau (Tous)  
 Le membre unique du niveau (Tous) est appelé membre Tous. La `AttributeAllMemberName` propriété d’une dimension spécifie le nom du membre tous pour les attributs d’une dimension. La propriété `AllMemberName` d'une hiérarchie spécifie le nom du membre Tous de cette hiérarchie.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un membre par défaut](attribute-properties-define-a-default-member.md)  
  
  
