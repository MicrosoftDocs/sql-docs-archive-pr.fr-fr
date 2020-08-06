---
title: Activer la fonctionnalité de File Sync du serveur de rapports dans l’administration centrale de SharePoint | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611619"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint

La fonctionnalité Synchronisation de fichiers de serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilise des gestionnaires d'événements SharePoint pour synchroniser le catalogue du serveur de rapports avec les éléments des bibliothèques de documents. Cette fonctionnalité est particulièrement intéressante lorsque des utilisateurs téléchargent fréquemment des éléments de rapport publiés directement dans des bibliothèques de documents SharePoint. Si la fonctionnalité de synchronisation de fichiers n’est pas activée, le contenu est toujours synchronisé mais pas aussi fréquemment.  
  
La fonctionnalité Synchronisation de fichiers peut être activée dans l’administration des sites SharePoint après installation du complément [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] pour les produits SharePoint.  
  
Cette fonctionnalité peut être activée et désactivée manuellement site par site, mais pas au niveau de la collection de sites.  
  
## <a name="prerequisites"></a>Prérequis  
 Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour SharePoint doit être installé. Si le complément n’est pas installé, la fonctionnalité de synchronisation de fichiers ne sera pas visible dans la liste des fonctionnalités du site.  
  
 Pour vérifier l'installation, consultez la liste des applications installées dans le [!INCLUDE[msCoName](../includes/msconame-md.md)]**Panneau de configuration **Windows. Si le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est installé, suivez les instructions fournies dans cette rubrique pour activer la fonctionnalité de synchronisation de fichiers.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Pour activer ou désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports sur un site  
  
1.  Dans la page principale de votre site, cliquez sur le menu **actions du site** , puis sur **paramètres du site**.  
  
2.  Dans **actions du site**, cliquez sur gérer les **fonctionnalités du site**.  
  
3.  Recherchez **Synchronisation de fichiers de serveur de rapports** dans la liste.  
  
4.  Cliquez sur **Activer**.  
  
> [!NOTE]  
>  Pour désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports, appliquez la même procédure, mais cliquez sur **Désactiver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes liés aux parties de rapports &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Activer le serveur de rapports et les fonctionnalités d’intégration de Power View dans SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
