---
title: 'Liste de vérification du déploiement : installer Reporting Services dans une batterie de serveurs SharePoint existante | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 041e038fdbc3198ff80fad82dd1a05bad2ff6fe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710184"
---
# <a name="deployment-checklist-install-reporting-services-into-an-existing-sharepoint-farm"></a>Liste de vérification du déploiement : Installer Reporting Services dans une batterie de serveurs SharePoint existante
  Les serveurs de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint peuvent être installés dans une nouvelle batterie de serveurs SharePoint ou dans une batterie de serveurs SharePoint existante. Cette rubrique décrit les scénarios possibles et les meilleures pratiques pour l'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une batterie de serveurs SharePoint existante.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant d'exécuter le programme d'installation, examinez les informations suivantes :  
  
|Étape|Lien|  
|----------|----------|  
|Créez ou identifiez les comptes utilisés lors d'un déploiement du serveur de rapports. Vous devez disposer d'un compte de service pour le service Report Server, ainsi que d'informations d'identification pour une connexion à la base de données du serveur de rapports||  
|Déterminez l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargée de l'hébergement de la base de données du serveur de rapports. Vous pouvez utiliser une instance locale ou distante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Choisissez une instance qui se trouve sur un ordinateur disposant d'une capacité de stockage suffisante pour vos rapports.||  
|(Facultatif) Recherchez le nom de la passerelle ou du serveur SMTP qui assure le service de messagerie de votre organisation si vous souhaitez utiliser les fonctions de messagerie du serveur de rapports dans les abonnements|[Configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)|  
|Remarque : Si vous mettez à niveau un ordinateur à partir d’une version CTP précédente [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et que vous aviez apporté des modifications personnalisées aux fichiers de configuration, vous devrez apporter les mêmes modifications aux fichiers de configuration, en suivant la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Les fichiers affectés sont **web.config** et **client.config**.||  
  
## <a name="installation-scenarios"></a>Scénarios d'installation  
 Le tableau suivant décrit les scénarios possibles lorsque vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une batterie de serveurs SharePoint existante. Le mode local permet un rendu local des rapports à partir de la bibliothèque de documents SharePoint sans intégration avec un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint est requis, mais un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne l'est pas. Pour plus d’informations sur le mode local, consultez rapports en mode [local et rapports en mode connecté dans la visionneuse de rapports &#40;Reporting Services en mode SharePoint&#41;](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) et [où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
|Démarrer la configuration|Workflow|Terminer la configuration|Commentaires|  
|----------------------------|--------------|--------------------------|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] en mode local|Installation|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]en mode connecté.||  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] en mode connecté|Mise à niveau sur place|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]en mode connecté.||  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] en mode connecté|Migration|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]en mode connecté.||  
  
## <a name="installation-and-in-place-upgrade-checklist"></a>Installation et liste de vérification de mise à niveau sur place  
 Le tableau suivant résume les étapes, les outils et les informations que vous devez examiner et utiliser pour l'installation :  
  
|Étape|Lien|  
|----------|----------|  
|**Installation et configuration initiale**||  
|Installez le complément SharePoint sur tous les ordinateurs Web frontaux (WFE).|[Ajouter un serveur Web frontal Reporting Services supplémentaire à une batterie](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Installez SQL Server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services et le moteur de base de données.|[Installer Reporting Services mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Créez au moins une application de service SSRS et configurez l'association d'applications de service.|Consultez la section « application de service » dans [installer Reporting Services mode SharePoint pour sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|**Configuration supplémentaire**||  
|Ajoutez les types de contenu SSRS à votre bibliothèque de documents.|[Ajouter des types de contenu de serveur de rapports à une bibliothèque &#40;Reporting Services en mode intégré SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)|  
|Configurez SQL Server Agent|[Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)|  
|Configurez les paramètres de messagerie électronique pour l'application de service|[Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Configurez  le service d'émission de jetons Revendications vers Windows (c2WTS)|[Service d’jetons Revendications vers Windows &#40;C2WTS&#41; et Reporting Services](../../../2014/sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)|  
  
## <a name="migration-checklist"></a>Liste de vérification de migration  
 Voici une liste des étapes de base pour une migration d'une installation existante vers une nouvelle installation.  
  
|Étape|Lien|  
|----------|----------|  
|Installez et configurez votre nouveau serveur. Notamment :<br /><br /> Outil de préparation des produits SharePoint<br /><br /> Produit SharePoint 2010<br /><br /> SharePoint 2010 SP1<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint<br /><br /> Complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2010|[Installer Reporting Services mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Créez au moins une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Sauvegardez les bases de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Sauvegardez les clés de chiffrement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Restaurez la base de données et les clés de chiffrement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Mappez toutes les applications Web aux nouvelles applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|La nouvelle installation **est désormais fonctionnelle**|  
|Supprimez l'intégration URL sur l'ancien serveur.|A partir de l'Administration centrale de SharePoint, dans la page **Paramètres généraux de l'application** , cliquez sur **Intégration de Reporting Services**.|  
|Désinstallez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de l'ancienne installation, si vous le souhaitez.||  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services l’installation en mode SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Aide sur l’utilisation des fonctionnalités de SQL Server BI dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)   
 [Combinaisons prises en charge de SharePoint et Reporting Services Server et des compléments &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
  
