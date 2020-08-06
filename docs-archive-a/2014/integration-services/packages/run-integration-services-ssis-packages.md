---
title: Exécution de projets et de packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
- executing packages [Integration Services]
- running packages [Integration Services]
- Integration Services, (See also Integration Services packages)
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c50dc3d7ab909aa43e8f1f0e7017290538ac6476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611140"
---
# <a name="execution-of-projects-and-packages"></a>Exécution de projets et de packages
  Pour exécuter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous pouvez utiliser un outil parmi plusieurs, en fonction de l’endroit où ces packages sont stockés. Ces outils sont répertoriées dans le tableau ci-dessous.  
  
 Pour stocker un package sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous utilisez le modèle de déploiement de projet pour déployer le projet sur le serveur. Pour plus d’informations, consultez [Déployer des projets sur le serveur Integration Services](../deploy-projects-to-integration-services-server.md).  
  
 Pour stocker un package dans le magasin de packages SSIS, la base de données msdb ou dans le système de fichiers, vous utilisez le modèle de déploiement de package. Pour plus d’informations, consultez [déploiement de packages &#40;&#41;SSIS ](legacy-package-deployment-ssis.md).  
  
|Outil|Packages stockés sur le serveur Integration Services|Packages stockés dans le magasin de packages SSIS ou dans la base de données msdb|Packages stockés dans le système de fichiers, hors de l'emplacement qui fait partie du magasin de packages SSIS|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|Non|Non<br /><br /> Vous pouvez cependant ajouter un package existant à un projet du magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] , qui inclut la base de données msdb. L'ajout d'un package existant au projet de cette manière effectue une copie locale du package dans le système de fichiers.|Oui|  
|**SQL Server Management Studio, quand vous êtes connecté à une instance du moteur de base de données qui héberge le serveur Integration Services**<br /><br /> Pour plus d’informations, consultez [Boîte de dialogue d’exécution de package](../execute-package-dialog-box.md)|Oui|Non<br /><br /> Vous pouvez toutefois importer un package vers le serveur à partir de ces emplacements.|Non<br /><br /> Vous pouvez toutefois importer un package vers le serveur à partir du système de fichiers.|  
|**SQL Server Management Studio, quand il est connecté au service Integration Services qui gère le magasin de packages SSIS**|Non|Oui|Non<br /><br /> Vous pouvez cependant importer un package dans le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à partir du système de fichiers.|  
|**dtexec**<br /><br /> Pour plus d'informations, consultez [Utilitaire dtexec](dtexec-utility.md).|Oui|Oui|Oui|  
|**dtexecui**<br /><br /> Pour plus d’informations, consultez [Référence de l’interface utilisateur de l’utilitaire d’exécution de package &#40;DtExecUI&#41;](execute-package-utility-dtexecui-ui-reference.md)|Non|Oui|Oui|  
|**SQL Server Agent**<br /><br /> Vous pouvez utiliser un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier un package.<br /><br /> Pour plus d’informations, consultez [Travaux de l’Agent SQL Server pour les packages](sql-server-agent-jobs-for-packages.md).|Oui|Oui|Oui|  
|**Procédure stockée intégrée**<br /><br /> Pour plus d’informations, consultez [catalog.start_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)|Oui|Non|Non|  
|**API managée en utilisant des types et des membres dans l’espace de noms**  <xref:Microsoft.SqlServer.Management.IntegrationServices>|Oui|Non|Non|  
|**API managée en utilisant des types et des membres dans l’espace de noms**  <xref:Microsoft.SqlServer.Dts.Runtime>|Actuellement impossible|Oui|Oui|  
  
## <a name="execution-and-logging"></a>Exécution et journalisation  
 Les packages[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peuvent être activés pour la journalisation et vous pouvez capturer des informations sur l'exécution dans des fichiers journaux. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md).  
  
 Vous pouvez surveiller des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés et exécutés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l’aide des rapports de fonctionnement. Les rapports sont disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d'informations, consultez [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Planifier un package à l’aide d’SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Exécuter un package dans les outils de données SQL Server](../run-a-package-in-sql-server-data-tools.md)  
  
-   [Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire dtexec](dtexec-utility.md)   
 [Assistant Importation et Exportation SQL Server](../import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)  
  
  
