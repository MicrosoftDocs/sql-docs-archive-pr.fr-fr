---
title: Désinstaller Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604883"
---
# <a name="uninstall-reporting-services"></a>Désinstaller Reporting Services
  La désinstallation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne supprime pas le contenu que vous avez créé ou la configuration que vous avez modifiée. Toutefois, s'il existe du contenu dont vous avez besoin une fois la désinstallation terminée, il est recommandé de faire des copies de contenu avant de commencer le processus de désinstallation.

## <a name="uninstall-sharepoint-mode"></a>Désinstaller en mode SharePoint
 Lorsque vous désinstallez le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , les éléments suivants sont supprimés :

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et proxy de service.

-   fichiers utilisés pour l'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

 Les applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne sont pas supprimées. Si vous ne souhaitez plus utiliser les applications de service, supprimez-les à l'aide de Windows PowerShell ou de l'Administration centrale de SharePoint.

 Les éléments de rapport et les métadonnées associées ne sont pas supprimés. Ces informations sont contenues dans les bases de données de contenu et de configuration liées aux applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les bases de données ne sont pas supprimées. Migrez-les manuellement vers une autre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Toutefois, si vous ne voulez plus des informations, vous devez supprimer ces bases de données. Pour plus d'informations, consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

 Voici des exemples de noms des trois bases de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui ne sont pas supprimées.

-   **Base de données du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065e

-   **Base de données temporaire du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB

-   **Base de données des alertes du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting

### <a name="uninstall-the-add-in-for-sharepoint-products"></a>Désinstallez le complément pour les produits SharePoint.
 Lorsque vous désinstallez le complément sur un ordinateur, vous pouvez choisir de désinstaller uniquement les fichiers ou de supprimer également la fonctionnalité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs. Pour plus d’informations sur la désinstallation du [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour les produits SharePoint, consultez [installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et sharepoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).

## <a name="uninstall-native-mode"></a>Désinstaller en mode natif
 Lorsque vous désinstallez en mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , tout ce qui **a été créé** ou **modifié** après l'installation est laissé en place. Par exemple, les fichiers de base de données, les fichiers journaux, les fichiers de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les éléments de contenu tels que des rapports et des fichiers de source de données.

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est une fonctionnalité d'instance et par conséquent, elle n'est pas répertoriée dans le Panneau de configuration Windows sous Programmes et fonctionnalités. Pour désinstaller [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif :

1.  Dans le Panneau de configuration Windows, cliquez sur **Programmes et fonctionnalités**.

2.  Dans **Programmes et fonctionnalités** , sélectionnez **Microsoft SQL Server 2012**.

3.  Dans l'Assistant Désinstallation, sélectionnez l'instance qui inclut la fonctionnalité d'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**RS**.

     ![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")

4.  Après avoir sélectionné l'instance, sélectionnez la fonctionnalité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

     ![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")

5.  Terminez l'Assistant.

## <a name="see-also"></a>Voir aussi
 [Désinstaller une instance existante de SQL Server &#40;le programme d’installation&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [installer ou désinstaller le complément PowerPivot pour SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [installer ou désinstaller le complément Reporting Services pour SharePoint &#40;sharepoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)


