---
title: Opérations de sauvegarde et de restauration pour Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e895733457fe0c8892294540bbe8345cb121f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612704"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a><span data-ttu-id="56a30-102">Opérations de sauvegarde et de restauration pour Reporting Services</span><span class="sxs-lookup"><span data-stu-id="56a30-102">Backup and Restore Operations for Reporting Services</span></span>
  <span data-ttu-id="56a30-103">Cette rubrique offre une vue d'ensemble de tous les fichiers de données utilisés dans une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , et décrit quand et comment les fichiers doivent être sauvegardés.</span><span class="sxs-lookup"><span data-stu-id="56a30-103">This topic provides an overview of all data files used in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation and describes when and how you should back up the files.</span></span> <span data-ttu-id="56a30-104">L'élaboration d'un plan de sauvegarde et de restauration des fichiers de base de données du serveur de rapports constitue l'étape la plus importante d'une stratégie de récupération.</span><span class="sxs-lookup"><span data-stu-id="56a30-104">Developing a backup and restore plan for the report server database files is the most important part of a recovery strategy.</span></span> <span data-ttu-id="56a30-105">Cependant, une stratégie de récupération plus complète inclut des sauvegardes des clés de chiffrement, des extensions ou assemblys personnalisés, des fichiers de configuration et des fichiers sources pour les rapports et les modèles.</span><span class="sxs-lookup"><span data-stu-id="56a30-105">However, a more comprehensive recovery strategy would include backups of the encryption keys, custom assemblies or extensions, configuration files, and source files for reports and models.</span></span>  
  
 <span data-ttu-id="56a30-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint</span><span class="sxs-lookup"><span data-stu-id="56a30-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>  
  
 <span data-ttu-id="56a30-107">Les opérations de sauvegarde et de restauration sont souvent utilisées pour déplacer partiellement ou intégralement une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="56a30-107">Backup and restore operations are often used to move all or part of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation:</span></span>  
  
-   <span data-ttu-id="56a30-108">Si vous ne déplacez que les bases de données du serveur de rapports, vous pouvez utiliser la sauvegarde et la restauration ou l'attachement et le détachement pour déplacer les bases de données sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56a30-108">If you are moving just the report server databases, you can use backup and restore or attach and detach to relocate the databases on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="56a30-109">Pour plus d’informations, consultez [Déplacement des bases de données du serveur de rapports vers un autre ordinateur &#40;en mode natif SSRS&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="56a30-109">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>  
  
-   <span data-ttu-id="56a30-110">Le déplacement d'une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un nouvel ordinateur s'appelle une migration.</span><span class="sxs-lookup"><span data-stu-id="56a30-110">Moving a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new computer is called a migration.</span></span> <span data-ttu-id="56a30-111">Lorsque vous faites migrer une installation, vous exécutez le programme d'installation pour installer une nouvelle instance de serveur de rapports, puis vous copiez les données de l'ancienne instance sur le nouvel ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a30-111">When you migrate an installation, you run Setup to install a new report server instance and then copy instance data to the new computer.</span></span> <span data-ttu-id="56a30-112">Pour plus d'informations sur la migration d'une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="56a30-112">For more information about migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="56a30-113">Mettre à niveau et migrer Reporting Services</span><span class="sxs-lookup"><span data-stu-id="56a30-113">Upgrade and Migrate Reporting Services</span></span>](upgrade-and-migrate-reporting-services.md)  
  
    -   [<span data-ttu-id="56a30-114">Migrer une installation Reporting Services &#40;mode SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="56a30-114">Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;</span></span>](migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [<span data-ttu-id="56a30-115">Faire migrer une installation Reporting Services &#40;mode natif&#41;</span><span class="sxs-lookup"><span data-stu-id="56a30-115">Migrate a Reporting Services Installation &#40;Native Mode&#41;</span></span>](migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a><span data-ttu-id="56a30-116">Sauvegarde des bases de données du serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="56a30-116">Backing Up the Report Server Databases</span></span>  
 <span data-ttu-id="56a30-117">Dans la mesure où un serveur de rapports est un serveur sans état, toutes les données d’application sont stockées dans les bases de données **reportserver** et **reportservertempdb** qui s’exécutent sur une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56a30-117">Because a report server is a stateless server, all application data is stored in the **reportserver** and **reportservertempdb** databases that run on a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span> <span data-ttu-id="56a30-118">Vous pouvez sauvegarder les bases de données **reportserver** et **reportservertempdb** à l’aide de l’une des méthodes de sauvegarde de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prises en charge.</span><span class="sxs-lookup"><span data-stu-id="56a30-118">You can backup the **reportserver** and **reportservertempdb** databases using one of the supported methods for backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="56a30-119">Les recommandations spécifiques aux bases de données du serveur de rapports sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="56a30-119">Recommendations that are specific to the report server databases include the following:</span></span>  
  
-   <span data-ttu-id="56a30-120">Utilisez le mode de récupération complet pour sauvegarder la base de données **reportserver** .</span><span class="sxs-lookup"><span data-stu-id="56a30-120">Use the full recovery model to backup the **reportserver** database.</span></span>  
  
-   <span data-ttu-id="56a30-121">Utilisez le mode de récupération simple pour sauvegarder la base de données **reportservertempdb** .</span><span class="sxs-lookup"><span data-stu-id="56a30-121">Use the simple recovery model to backup the **reportservertempdb** database.</span></span>  
  
-   <span data-ttu-id="56a30-122">Vous pouvez utiliser des planifications de sauvegarde différentes pour chaque base de données.</span><span class="sxs-lookup"><span data-stu-id="56a30-122">You can use different backup schedules for each database.</span></span> <span data-ttu-id="56a30-123">La sauvegarde de **reportservertempdb** présente un seul intérêt, celui de ne pas avoir à recréer la base de données en cas de défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="56a30-123">The only reason to backup the **reportservertempdb** is to avoid having to recreate it if there is a hardware failure.</span></span> <span data-ttu-id="56a30-124">En effet, il est inutile de récupérer les données dans **reportservertempdb**, mais la structure de la table est indispensable.</span><span class="sxs-lookup"><span data-stu-id="56a30-124">In the event of hardware failure, it is not necessary to recover the data in **reportservertempdb**, but you do need the table structure.</span></span> <span data-ttu-id="56a30-125">Si votre base de données **reportservertempdb**est inutilisable, le seul moyen de la récupérer consiste à recréer la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="56a30-125">If you lose **reportservertempdb**, the only way to get it back is to recreate the report server database.</span></span> <span data-ttu-id="56a30-126">Si vous recréez la base de données **reportservertempdb**, il est important qu’elle porte le même nom que la base de données du serveur de rapports primaire.</span><span class="sxs-lookup"><span data-stu-id="56a30-126">If you recreate the **reportservertempdb**, it is important that it have the same name as the primary report server database.</span></span>  
  
 <span data-ttu-id="56a30-127">Pour plus d’informations sur la sauvegarde et la récupération des bases de données relationnelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Sauvegarde et restauration des bases de données SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="56a30-127">For more information about backup and recovery of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="56a30-128">Si votre serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est en mode SharePoint, vous devez également vous occuper de bases de données supplémentaires, notamment les bases de données de configuration SharePoint et la base de données des alertes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56a30-128">If your [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server is in SharePoint mode, there are additional databases to be concerned with, including SharePoint configuration databases and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] alerting database.</span></span> <span data-ttu-id="56a30-129">En mode SharePoint, trois bases de données sont créées pour chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56a30-129">In SharePoint mode, three databases are created for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="56a30-130">Les bases de données **reportserver**, **reportservertempdb**et **dataalerting** .</span><span class="sxs-lookup"><span data-stu-id="56a30-130">The **reportserver**, **reportservertempdb**, and **dataalerting** databases.</span></span> <span data-ttu-id="56a30-131">Pour plus d’informations, consultez [Applications de service SharePoint de sauvegarde et de restauration Reporting Services](../backup-and-restore-reporting-services-sharepoint-service-applications.md).</span><span class="sxs-lookup"><span data-stu-id="56a30-131">For more information see [Backup and Restore Reporting Services SharePoint Service Applications](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span></span>  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="56a30-132">Sauvegarde des clés de chiffrement</span><span class="sxs-lookup"><span data-stu-id="56a30-132">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="56a30-133">Vous devez sauvegarder les clés de chiffrement lorsque vous configurez pour la première fois une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56a30-133">You should backup the encryption keys when you configure a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation for the first time.</span></span> <span data-ttu-id="56a30-134">Vous devez également sauvegarder les clés chaque fois que vous modifiez l'identité des comptes de services ou renommez l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a30-134">You should also backup the keys any time you change the identity of the service accounts or rename the computer.</span></span> <span data-ttu-id="56a30-135">Pour plus d’informations, consultez [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span><span class="sxs-lookup"><span data-stu-id="56a30-135">For more information, see [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span> <span data-ttu-id="56a30-136">Pour les serveurs de rapports en mode SharePoint, consultez la section « gestion des clés » de la rubrique [gérer une application de Service Reporting Services SharePoint](../manage-a-reporting-services-sharepoint-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="56a30-136">For SharePoint mode report servers, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
## <a name="backing-up-the-configuration-files"></a><span data-ttu-id="56a30-137">Sauvegarde des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="56a30-137">Backing Up the Configuration Files</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="56a30-138">utilise des fichiers de configuration pour stocker les paramètres des applications.</span><span class="sxs-lookup"><span data-stu-id="56a30-138">uses configuration files to store application settings.</span></span> <span data-ttu-id="56a30-139">Vous devez sauvegarder les fichiers lorsque vous configurez pour la première fois le serveur, puis lorsque vous avez déployé des extensions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="56a30-139">You should backup the files when you first configure the server and after you deploy any custom extensions.</span></span> <span data-ttu-id="56a30-140">Les fichiers à sauvegarder sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="56a30-140">Files to back up include:</span></span>  
  
-   <span data-ttu-id="56a30-141">RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="56a30-141">Rsreportserver.config</span></span>  
  
-   <span data-ttu-id="56a30-142">Rssvrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="56a30-142">Rssvrpolicy.config</span></span>  
  
-   <span data-ttu-id="56a30-143">Rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="56a30-143">Rsmgrpolicy.config</span></span>  
  
-   <span data-ttu-id="56a30-144">Reportingservicesservice.exe.config</span><span class="sxs-lookup"><span data-stu-id="56a30-144">Reportingservicesservice.exe.config</span></span>  
  
-   <span data-ttu-id="56a30-145">Web.config pour les applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] Report Server et Gestionnaire de rapports.</span><span class="sxs-lookup"><span data-stu-id="56a30-145">Web.config for both the Report Server and Report Manager [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications</span></span>  
  
-   <span data-ttu-id="56a30-146">Machine.config pour [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a30-146">Machine.config for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span></span>  
  
## <a name="backing-up-data-files"></a><span data-ttu-id="56a30-147">Sauvegarde des fichiers de données</span><span class="sxs-lookup"><span data-stu-id="56a30-147">Backing Up Data Files</span></span>  
 <span data-ttu-id="56a30-148">Sauvegardez les fichiers que vous créez et gérez dans le Concepteur de rapports et le Générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="56a30-148">Backup the files that you create and maintain in Report Designer and Model Designer.</span></span> <span data-ttu-id="56a30-149">entre autres les fichiers de définition de rapport (.rdl), de modèle de rapport (.smdl), de source de données partagée (.rds), de vue de données (.dv), de source de données (.ds), de projet de serveur de rapports (.rptproj) et de solution de rapport (.sln).</span><span class="sxs-lookup"><span data-stu-id="56a30-149">These include report definition (.rdl) files, report model (.smdl) files, shared data source (.rds) files, data view (.dv) files, data source (.ds) files, report server project (.rptproj) files, and report solution (.sln) files.</span></span>  
  
 <span data-ttu-id="56a30-150">N'oubliez pas de sauvegarder les fichiers de script (.rss) que vous avez créés pour les tâches d'administration ou de déploiement.</span><span class="sxs-lookup"><span data-stu-id="56a30-150">Remember to backup any script files (.rss) that you created for administration or deployment tasks.</span></span>  
  
 <span data-ttu-id="56a30-151">Vérifiez que vous êtes en possession d'une copie de sauvegarde de tous les assemblys et extensions personnalisés que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="56a30-151">Verify that you have a backup copy of any custom extensions and custom assemblies you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a30-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56a30-152">See Also</span></span>  
 <span data-ttu-id="56a30-153">[Base de données du serveur de rapports &#40;le mode natif SSRS&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="56a30-153">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="56a30-154">[Fichiers de configuration de Reporting Services](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="56a30-154">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="56a30-155">[Utilitaire rskeymgmt &#40;&#41;SSRS](../tools/rskeymgmt-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56a30-155">[rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span></span>  
 <span data-ttu-id="56a30-156">[Copier des bases de données avec la sauvegarde et la restauration](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="56a30-156">[Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span></span>  
 <span data-ttu-id="56a30-157">[Administrer une base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="56a30-157">[Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="56a30-158">Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="56a30-158">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
  
  