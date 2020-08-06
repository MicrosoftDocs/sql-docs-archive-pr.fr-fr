---
title: Mise en cache proactive (boîte de dialogue Propriétés de partition) (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.proactivecaching.f1
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dae559ad1229407ca39744e52d8ee6842069075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708728"
---
# <a name="proactive-caching-partition-properties-dialog-box-ssms"></a>Mise en cache proactive (boîte de dialogue Propriétés de partition) (SSMS)
  Utilisez la page **Mise en cache proactive** de la boîte de dialogue **Propriétés de partition** de SQL Server Management Studio pour définir les propriétés de mise en cache proactive d'une partition d'un groupe de mesures d'un cube d'une base de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 **Paramètre standard**  
 Active le curseur **Paramètre standard** et utilise les paramètres prédéfinis pour le mode de stockage et la mise en cache proactive.  
  
 **Paramètre standard**  
 Sélectionnez un des paramètres prédéfinis dans le tableau suivant.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**ROLAP en temps réel**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage ROLAP.<br /><br /> Active la mise en cache proactive.<br /><br /> Efface la mémoire cache périmée avec une latence de 0 seconde.<br /><br /> Place immédiatement l'objet en ligne.|  
|**HOLAP en temps réel**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage HOLAP.<br /><br /> Active la mise en cache proactive.<br /><br /> Efface la mémoire cache périmée avec une latence de 0 seconde.<br /><br /> Met à jour la mémoire cache lorsque les données changent avec de latence de 0 seconde et sans valeur de remplacement de l'intervalle de latence.<br /><br /> Place immédiatement l'objet en ligne.|  
|**MOLAP à faible latence**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage MOLAP.<br /><br /> Active la mise en cache proactive.<br /><br /> Efface la mémoire cache périmée avec une latence de 30 minutes.<br /><br /> Met à jour la mémoire cache lorsque les données changent avec de latence de 10 secondes et une valeur de remplacement de l'intervalle de latence égale à 10 minutes.<br /><br /> Met à jour la mémoire cache lorsque les données changent avec de latence de 10 secondes et une valeur de remplacement de l'intervalle de latence égale à 10 minutes.<br /><br /> Place immédiatement l'objet en ligne.|  
|**MOLAP à latence moyenne**|Sélectionnez l’objet useBrings en ligne immédiatement.<br /><br /> les paramètres de stockage et de mise en cache proactive suivants :<br /><br /> Mode de stockage MOLAP.<br /><br /> Active la mise en cache proactive.<br /><br /> Efface la mémoire cache périmée avec une latence de 4 heures.<br /><br /> Met à jour la mémoire cache lorsque les données changent avec de latence de 10 secondes et une valeur de remplacement de l'intervalle de latence égale à 10 minutes.<br /><br /> Place immédiatement l'objet en ligne.|  
|**MOLAP automatique**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage MOLAP.<br /><br /> Active la mise en cache proactive.<br /><br /> Met à jour la mémoire cache lorsque les données changent avec de latence de 0 seconde et sans valeur de remplacement de l'intervalle de latence.|  
|**MOLAP planifié**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage MOLAP<br /><br /> Activer la mise en cache proactive<br /><br /> Met périodiquement à jour la mémoire cache avec un intervalle de reconstruction égal à 1 jour|  
|**MOLAP**|Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :<br /><br /> Mode de stockage MOLAP.|  
  
 **Paramètre personnalisé**  
 Sélectionnez cette option pour définir explicitement les options du mode de stockage, de mise en cache proactive et de notification.  
  
 **Options**  
 Affiche la boîte de dialogue **Options de stockage** qui permet de définir explicitement les options du mode de stockage, de la mise en cache proactive et de notification. Pour plus d’informations sur la boîte de dialogue **Options de stockage**, consultez [Boîte de dialogue Options de stockage &#40;Analysis Services - Données multidimensionnelles&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache proactive &#40;les partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Boîte de dialogue Propriétés de partition &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Boîte de dialogue Propriétés de la partition &#40;&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Boîte de dialogue Propriétés de partition &#40;générale&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)   
 [Configuration d’erreur pour le traitement des cubes, des partitions et des dimensions &#40;SSAS-multidimensionnel&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
