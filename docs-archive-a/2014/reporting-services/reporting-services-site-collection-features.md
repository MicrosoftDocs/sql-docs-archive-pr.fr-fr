---
title: Fonctionnalités de la collection de sites Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9475ee323222b800a9c4b9a86e737fdd161e7a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700794"
---
# <a name="reporting-services-site-collection-features"></a>Fonctionnalités de collection de sites de Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit trois fonctionnalités de collection de sites SharePoint. Les fonctionnalités prennent en charge l’environnement de création de rapports général du mode SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], une fonctionnalité du complément [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition, et les opérations de gestion de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans l’Administration centrale de SharePoint.  
  
## <a name="site-collection-features"></a>Fonctionnalités de la collection de sites  
 Le tableau ci-dessous décrit les fonctionnalités de la collection de sites [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|**Fonctionnalité Administration centrale du serveur de rapports**|Active les fonctionnalités de gestion de l'intégration avec un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Cette fonctionnalité est uniquement installée et utilisée dans la collection de sites Administration centrale de SharePoint.<br /><br /> La fonctionnalité d’intégration du serveur de rapports est automatiquement activée dans la collection de sites administration centrale de SharePoint après l’installation du [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] complément pour les produits SharePoint. Dans certaines circonstances, vous devrez activer la fonctionnalité manuellement. Pour activer la fonctionnalité de serveur de rapports, utilisez les pages [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] de la page Paramètres du site de l'Administration centrale de SharePoint.<br /><br /> La version [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et les versions ultérieures du complément pour les produits SharePoint activent la fonctionnalité d’intégration du serveur de rapports pour toutes les collections de sites existantes pendant l’installation du complément. En outre, la fonctionnalité sera automatiquement active pour les nouvelles collections de sites.|  
|**Fonctionnalité d'intégration du serveur de rapports**|Active les rapports enrichis à l’aide [!INCLUDE[msCoName](../includes/msconame-md.md)] de[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Cette fonctionnalité est activée par défaut.|  
|**Fonctionnalité d'intégration de Power View**|Active l'exploration interactive de données et la présentation visuelle dans les classeurs PowerPivot et les bases de données tabulaires Analysis Services.<br /><br /> Cette fonctionnalité est accessible via les menus contextuels des sources de données suivantes :<br /><br /> .rdlx<br /><br /> .rsds<br /><br /> fichier de connexion .bism<br /><br /> <br /><br /> Si [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] n'apparaît pas dans les menus contextuels, vérifiez que **Fonctionnalité d'intégration de Power View** est activé.<br /><br /> Cette fonctionnalité est désactivée par défaut.|  
  
## <a name="see-also"></a>Voir aussi  
 [Activer le serveur de rapports et les fonctionnalités d’intégration de Power View dans SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Paramètres et fonctionnalités du site Reporting Services&#40;en mode SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
