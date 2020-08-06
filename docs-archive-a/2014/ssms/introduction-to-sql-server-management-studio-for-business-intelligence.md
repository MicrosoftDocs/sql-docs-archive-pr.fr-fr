---
title: Présentation de SQL Server Management Studio pour Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
author: stevestein
ms.author: sstein
ms.openlocfilehash: fdb2a0645ad299fc355066d56b1cc371757f5b5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702296"
---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Introduction à SQL Server Management Studio pour Business Intelligence
  Pour accéder, configurer, gérer et administrer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], utilisez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Même si les trois technologies de décisionnel reposent sur [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], les tâches d'administration associées à chacune d'entre elle sont légèrement différentes.  
  
> [!NOTE]  
>  Pour créer et modifier des solutions [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , utilisez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], et non [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] est un environnement de développement basé sur [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Gestion des solutions Analysis Services à l'aide de SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] vous permet de gérer des objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , par exemple effectuer des sauvegardes et le traitement d’objets.  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] fournit un projet Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans lequel vous pouvez développer et enregistrer des scripts écrits dans une syntaxe MDX (Multidimensional Expressions) et XMLA (XML for Analysis). Ces projets Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] servent à effectuer les tâches de gestion ou recréer des objets, tels que les bases de données et les cubes, sur des instances [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Par exemple, vous pouvez développer un script XMLA dans un projet de Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui crée directement des objets sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] existante. Les projets de Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent être enregistrés au sein d'une solution et intégrés avec un système de contrôle de code source.  
  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , consultez [Analysis Services le projet de Scripts dans SQL Server Management Studio](https://docs.microsoft.com/analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Gestion des solutions Integration Services à l'aide de SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] vous permet d’utiliser le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour gérer les packages et surveiller les packages en cours d’exécution. Vous pouvez également utiliser [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour organiser des packages en dossiers, exécuter des packages, importer et exporter des packages, migrer des packages DTS (Data Transformation Services) et mettre à jour des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Gestion des projets Reporting Services à l'aide de SQL Server Management Studio  
 Utiliser SQL Server Management Studio pour activer les fonctionnalités de Reporting Services, administrer le serveur et les bases de données, et gérer des rôles et des travaux.  
  
 Vous gérez des planifications partagées à l'aide du dossier Planifications partagées et gérer des bases de données du serveur de rapports (ReportServer, ReportServerTempdb). Vous créez également un RSExecRole dans la base de données système Master lorsque vous déplacez une base de données du serveur de rapports vers une SQL Server nouvelle ou différente Moteur de base de données ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] ). Pour plus d'informations sur ces tâches, consultez les rubriques suivantes :  
  
-   [Reporting Services pour SQL Server Management Studio &#40;SSRS&#41;](../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
-   [Administrer une base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../reporting-services/report-server/report-server-database-ssrs-native-mode.md)  
  
-   [Créer le rôle RSExecRole](../reporting-services/security/create-the-rsexecrole.md)  
  
 Vous gérez également le serveur en activant et configurant différentes fonctionnalités, en définissant les valeurs par défaut du serveur, et en gérant des rôles et des travaux. Pour plus d'informations sur ces tâches, consultez les rubriques suivantes :  
  
-   [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../reporting-services/tools/set-report-server-properties-management-studio.md)  
  
-   [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](../reporting-services/security/role-definitions-create-delete-or-modify.md)  
  
-   [Activer et désactiver l'impression côté client pour Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles multidimensionnels à l’aide de SQL Server Data Tools &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt)   
 [Reporting Services SQL Server Data Tools &#40;SSDT&#41;](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)  
  
  
