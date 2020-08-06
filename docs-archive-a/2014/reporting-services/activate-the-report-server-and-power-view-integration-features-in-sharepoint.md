---
title: Activer le serveur de rapports et les fonctionnalités d’intégration de Power View dans SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af5f544e959c039b0bdb85d63d0b94917254d78a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613338"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint
  Les [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fonctionnalités de la collection de sites sont généralement activées par défaut après l’installation du [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] complément pour les produits SharePoint. Dans certaines circonstances, vous devrez activer les fonctionnalités manuellement.  
  
 Si vous installez le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2010 après l'installation du produit SharePoint, la fonctionnalité d'intégration du serveur de rapports et la fonctionnalité d'intégration de vue de remplissage sont uniquement activées pour les collections de sites racine. Pour les autres collections de sites, vous devez activer manuellement les fonctionnalités. Par exemple, si vous avez une collection de sites **http://[nom de mon serveur]/sites/[nom de collection de sites]** vous devez activer manuellement les fonctionnalités de collection de sites [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 S’il n’y a pas de collection de sites racine, le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enregistre un message semblable au suivant.  
  
 « L'application Web SharePoint 80 n'a pas de collection de sites racine »  
  
 Le message se trouve dans le journal d’installation du complément, nommé « RS_SP_ #. log », où # est un nombre incrémenté. Le fichier journal se trouve dans le dossier Temp de l’utilisateur actuel, par exemple C:\Users \\ [nom d’utilisateur] \AppData\Local\Temp. Pour plus d’informations sur les options de journalisation avec le complément, consultez [installer ou désinstaller le complément Reporting Services pour sharepoint &#40;sharepoint 2010 et sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Dans cette rubrique :  
  
-   [Pour activer les fonctionnalités d'intégration de collections de sites Report Server et Power View :](#bkmk_features)  
  
-   [Pour activer ou désactiver la fonctionnalité de collection de sites dans l'Administration centrale de Reporting Services :](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a>Pour activer les fonctionnalités du serveur de rapports et de la collection de sites d’intégration Power View :  
  
1.  Ouvrez votre navigateur sur le site où vous souhaitez activer les fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'intégration Report Server** ou **Fonctionnalité d'intégration de Power View** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver les fonctionnalités, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a>Pour activer ou désactiver Reporting Services fonctionnalité de collection de sites d’administration centrale :  
  
1.  Ouvrez votre navigateur dans l'Administration centrale de SharePoint.  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'administration centrale du serveur de rapports** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver la fonctionnalité, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois la fonctionnalité activée, vous pouvez continuer l'intégration de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
