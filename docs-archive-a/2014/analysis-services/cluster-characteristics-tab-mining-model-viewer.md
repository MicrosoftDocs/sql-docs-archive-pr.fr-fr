---
title: Onglet caractéristiques du cluster (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602515"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>Onglet Caractéristiques du cluster (Visionneuse de modèle d'exploration de données)
  L’onglet **Caractéristiques du cluster** vous permet d’explorer les caractéristiques d’un cluster dans un modèle de clustering, ou l’ensemble de tous les cas du modèle. Le graphique affiche l'importance de chaque paire attribut-valeur comme caractéristique qui définit le cluster, en comparaison avec d'autres clusters.  
  
 **Pour plus d’informations :** [Algorithme de gestion de clusters Microsoft](data-mining/microsoft-clustering-algorithm.md), [Explorer un modèle à l’aide de Microsoft Sequence Cluster](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans la visionneuse personnalisée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée associée à ce type de modèle, ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les éventuelles visionneuses de plug-in disponibles.  
  
 **Cluster**  
 Choisissez le cluster à afficher, ou choisissez **Remplissage (tout)** pour voir la distribution des attributs du modèle dans son ensemble.  
  
 **Caractéristiques pour\<cluster>**  
 Le graphique contient les colonnes suivantes, qui décrivent les caractéristiques du cluster sélectionné.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable**|Répertorie les attributs du modèle d'exploration de données qui se trouvent dans le cluster sélectionné.|  
|**Valeurs**|Répertorie les valeurs des attributs actuels qui se trouvent dans le cluster sélectionné.|  
|**Risque**|La barre indique la puissance de la paire attribut-valeur comme fonctionnalité de distinction de ce cluster. Si vous pointez la souris sur la barre, vous pouvez consulter la valeur de probabilité, représentée en pourcentage. Elle indique, étant donné cette combinaison d'attributs et de valeurs dans un cas particulier, la probabilité d'appartenance du cas à ce cluster.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
