---
title: Scripts et PowerShell avec Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610971"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Scripts et PowerShell avec Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prend en charge un large éventail de scénarios de développement et de gestion via script, notamment l'utilitaire de ligne de commande rs.exe, les applets de commande PowerShell pour les serveurs de rapports en mode SharePoint et l'exploitation du modèle d'objet [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] de PowerShell pour le mode natif et le mode SharePoint.

-   Les administrateurs peuvent écrire les scripts dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] pour automatiser le déploiement et la gestion d'une installation du serveur de rapports. Les administrateurs peuvent également générer et exécuter des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] qui créent, configurent et mettent à jour une base de données du serveur de rapports. Les administrateurs peuvent aussi utiliser les fonctionnalités d'enregistrement et de lecture de scripts de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour automatiser les tâches régulières de maintenance.

-   Les développeurs peuvent créer des applications personnalisées incluant des scripts. Vous pouvez exécuter des scripts qui effectuent des appels au service Web Report Server. Pratiquement chaque opération que vous pouvez écrire en code managé peut également l'être écrite sous forme de script.

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prend en charge le script .NET [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] comme langage de script pouvant être traité par l'utilitaire RS.exe, un hôte de script qui s'exécute sur le serveur de rapports.

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Exemples et applets de commande PowerShell du mode SharePoint de Reporting Services
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Le mode SharePoint inclut des applets de commande [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] pour l'administration des serveurs de rapports.

-   La section[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) inclut les exemples suivants :

    -   Créer une application de service et un proxy

    -   Analyse et mise à jour d'une extension de remise

    -   Obtenir et définir les propriétés de la base de données d'application Reporting Services, par exemple le délai d'expiration de la base de données

    -   Extensions de données Liste

## <a name="reporting-services-object-model-and-powershell-samples"></a>Exemples du modèle d'objet Reporting Services et de Powershell
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")

 Appel du modèle d'objet principal par PowerShell, valide en grande partie pour les modes natif et SharePoint, comme les tâches de migration et d'abonnement, et d'autres exemples associés de tâches d'abonnement dans SQL15.

-   [Utiliser PowerShell pour modifier et répertorier les propriétaires d’abonnements Reporting Services, et exécuter un abonnement](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).

-   [Utilisation de PowerShell pour créer une machine virtuelle Azure avec un serveur de rapports en mode natif](https://msdn.microsoft.com/library/azure/dn449661.aspx).

-   Consultez la section « Accéder aux classes WMI à l’aide de PowerShell » dans [Accéder au fournisseur WMI de Reporting Services](access-the-reporting-services-wmi-provider.md).

-   [Comment administrer SSRS à l'aide de PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin

## <a name="rsexe-scripting-samples"></a>Exemples de scripts RS.exe

-   [Exemple Reporting Services rs.exe script pour migrer le contenu entre les serveurs de rapports](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).

-   Pour obtenir des exemples supplémentaires de script, d'application et d'extension, consultez les [exemples de produit SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).

## <a name="see-also"></a>Voir aussi
 [Utilitaire deRS.exe &#40;](rs-exe-utility-ssrs.md) script de [déploiement et de tâches d’administration SSRS&#41;script](script-deployment-and-administrative-tasks.md) [avec l’utilitaire rs.exe et le service Web](script-with-the-rs-exe-utility-and-the-web-service.md)


