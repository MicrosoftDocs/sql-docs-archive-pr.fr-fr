---
title: Mettre à niveau Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603614"
---
# <a name="upgrade-analysis-services"></a>Mettre à niveau Analysis Services
  Utilisez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour mettre à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la mise à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode SharePoint, consultez [mettre à niveau PowerPivot pour SharePoint](upgrade-power-pivot-for-sharepoint.md). Pour plus d’informations sur la mise à niveau d’une instance de SQL Server existante, consultez [mise à niveau vers SQL Server 2014 à l’aide de l’Assistant installation &#40;&#41;d’installation ](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Problèmes de mise à niveau connus  
 Avant d'effectuer la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez les rubriques suivantes :  
  
-   [Notes de publication de SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   Pour savoir quelles [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fonctionnalités et fonctionnalités ont été supprimées, déconseillées ou modifiées, consultez [Analysis Services la compatibilité descendante](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).  
  
## <a name="pre-upgrade-checklist"></a>Liste de contrôle préalable à la mise à niveau  
 Avant d'effectuer la mise à niveau, passez en revue les informations suivantes :  
  
-   [Mises à niveau de la version et de l’édition prises en charge](supported-version-and-edition-upgrades.md)  
  
-   [Configuration matérielle et logicielle requise pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Paramètres de l’outil d’analyse de configuration système](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Sauvegarde et restauration de bases de données Analysis Services](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [Utiliser le Conseiller de mise à niveau pour la préparation des mises à niveau](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Mise à niveau d'Analysis Services  
 Différentes approches s'offrent à vous pour mettre à niveau le serveur et les données :  
  
-   Une **mise à niveau sur place** remplace les fichiers programme existants par les [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fichiers programme. Les bases de données restent au même emplacement. Les dossiers programme sont mis à jour pour refléter le nouveau nom.  
  
-   Une **mise à niveau côte à côte** est une nouvelle installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur le même ordinateur qui a une instance de Analysis Services existante. Vous pouvez déplacer les bases de données vers la nouvelle instance du même ordinateur, puis désinstaller l'ancienne version si vous n'en avez plus l'utilité.  
  
-   Vous pouvez également installer Analysis Services sur le nouveau matériel, puis migrer les bases de données existantes vers ce serveur.  
  
## <a name="in-place-upgrade"></a>Mise à niveau sur place  
 Vous pouvez mettre à niveau une instance existante de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et, dans le cadre du processus de mise à niveau, migrer automatiquement les bases de données existantes de l’ancienne instance vers la nouvelle instance. Comme les métadonnées et les données binaires sont compatibles entre les deux versions, vous conserverez les données après la mise à niveau et vous n'avez pas à migrer les données manuellement.  
  
 Pour mettre à niveau une instance existante, exécutez le programme d'installation et spécifiez le nom de l'instance existante comme nom de la nouvelle instance.  
  
## <a name="upgrading-databases"></a>Mise à niveau des bases de données  
 Les bases de données créées dans les versions antérieures d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécutent sur le serveur mis à niveau sous un ancien paramétrage de niveau de compatibilité de base de données. Le niveau de compatibilité des bases de données créées dans les versions suivantes est 105. Vous pouvez modifier le niveau de compatibilité si vous souhaitez utiliser des fonctionnalités qui nécessitent un niveau de compatibilité de base de données plus récent. Une autre solution consiste à exécuter les bases de données sur le serveur mis à niveau en utilisant les paramètres d'origine. Pour plus d’informations, consultez [définir le niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Compréhension de l’architecture Microsoft OLAP](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture)   
 [Mettre à niveau PowerPivot pour SharePoint](upgrade-power-pivot-for-sharepoint.md)   
 [Installer Analysis Services en mode multidimensionnel et d’exploration de données](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
