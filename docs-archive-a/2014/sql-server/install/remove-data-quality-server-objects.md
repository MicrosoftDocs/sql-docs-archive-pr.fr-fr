---
title: Supprimer les objets serveur DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1b7c6dbb-b40e-4822-9caa-608e1056af8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 86ff3558430bdbc501b1d04fe13c6db886c34092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704708"
---
# <a name="remove-data-quality-server-objects"></a>Supprimer les objets serveur DQS
  La désinstallation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou la suppression totale d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ne supprime pas tous les objets [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , notamment les bases de données DQS. Cela signifie que vous ne perdez pas vos données DQS si vous désinstallez le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] à l'aide du programme d'installation de SQL Server. Vous devez supprimer manuellement ces objets [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] une fois le processus de désinstallation terminé.  
  
> [!NOTE]
>  -   Avant de désinstaller [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], pensez à sauvegarder toutes vos bases de connaissances existantes en les exportant vers un fichier .dqsb, puis utilisez ce fichier ultérieurement pour importer toutes les bases de connaissances dans une nouvelle installation [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . L'exportation et l'importation de toutes les bases de connaissances DQS peuvent s'effectuer via l'exécution de DQSInstaller.exe avec les paramètres de ligne de commande appropriés à partir de l'invite de commandes. Pour plus d'informations, consultez [Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).  
> -   Avant de supprimer les bases de données DQS, envisagez de sauvegarder les bases de données si vous souhaitez les conserver et les utiliser ultérieurement pour restaurer les données. Pour plus d’informations, consultez [Gérer des bases de données DQS](../../../2014/data-quality-services/manage-dqs-databases.md).  
  
## <a name="uninstall-data-quality-server-from-a-sql-server-instance"></a>Désinstaller le serveur Data Quality Services d'une instance de SQL Server  
 Si vous désinstallez simplement le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez supprimer manuellement les objets [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] suivants de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une fois le processus de désinstallation du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] terminé :  
  
-   Bases de données DQS_MAIN, DQS_PROJECTS et DQS_STAGING_DATA.  
  
-   \#Connexions #MS_dqs_db_owner_login## et ##MS_dqs_service_login##.  
  
-   Procédure stockée DQInitDQS_MAIN de la base de données master.  
  
 Vous pouvez supprimer ces objets dans SQL Server Management Studio en cliquant avec le bouton droit sur l’objet, puis en cliquant sur **Supprimer** dans le menu contextuel.  
  
> [!IMPORTANT]  
>  Si vous ne faites que désinstaller le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] depuis une instance de serveur SQL à l'aide du paramètre de ligne de commande `-uninstall` à partir de l'invite de commande, tous les objets DQS sont supprimés dans le cadre du processus de désinstallation. Vous ne devez pas les supprimer manuellement après la désinstallation du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]. Pour désinstaller le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] à partir de l'invite de commandes, tapez la commande suivante à l'invite de commandes, puis appuyez sur Entrée :   
> `dqsinstaller.exe -uninstall`  
  
## <a name="uninstall-sql-server-instance-containing-data-quality-server"></a>Désinstaller une instance de SQL Server contenant le serveur Data Quality Services  
 Si vous désinstallez complètement l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], vous devez supprimer manuellement les bases de données DQS_MAIN, DQS_PROJECTS et DQS_STAGING_DATA de votre ordinateur une fois le processus de désinstallation terminé. Pour une installation par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les fichiers de bases de données DQS_MAIN, DQS_PROJECTS et DQS_STAGING_DATA sont disponibles dans C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA.  
  
## <a name="see-also"></a>Voir aussi  
 [Désinstaller une instance existante de SQL Server &#40;programme d’installation&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [Désinstaller SQL Server 2014](uninstall-sql-server.md)  
  
  
