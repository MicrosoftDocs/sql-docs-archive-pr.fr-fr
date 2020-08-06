---
title: Configurer les propriétés des relations d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601162"
---
# <a name="configure-attribute-relationship-properties"></a>Configurer des propriétés de relations d'attributs
  Le tableau suivant répertorie et décrit les propriétés d'une relation d'attribut.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Attribut|Contient le nom de l'attribut.|  
|Cardinalité|Indique la cardinalité de la relation. Les valeurs sont Many, pour une relation plusieurs-à-un, ou One, pour une relation un-à-un. La valeur par défaut est Many. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , la propriété de cardinalité n’a aucun effet ; son utilisation est réservée à une implémentation ultérieure.|  
|Nom|Contient le nom convivial de l'attribut.|  
|RelationshipType|Indique si les relations de membres changent avec le temps. Les valeurs sont Rigid, qui signifie que les relations entre membres ne changent pas avec le temps, ou Flexible, qui signifie que les relations entre membres changent avec le temps. La valeur par défaut est Flexible. Si vous définissez une relation comme flexible, les agrégations sont supprimées et recalculées dans le cadre de la mise à jour incrémentielle (elles ne sont pas supprimées si seuls de nouveaux membres sont ajoutés). Si vous définissez une relation rigide, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conserve les agrégations une fois la dimension mise à jour de manière incrémentielle. Si une relation rigide change, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère une erreur pendant le traitement incrémentiel. En spécifiant les relations et les propriétés de relations appropriées, vous améliorez les performances de requête et de traitement.|  
|Visible|Détermine la visibilité de la relation d'attribut. Les valeurs sont True ou False. La valeur par défaut est True.|  
  
  
