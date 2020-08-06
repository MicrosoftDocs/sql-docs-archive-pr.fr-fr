---
title: SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 943da9018e50e1f287858654d4639035f3aa4532
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613473"
---
# <a name="sql-server-backup-and-restore-with-azure-blob-storage-service"></a>Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure
  Cette rubrique présente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les sauvegardes et les restaurations à partir du [service de stockage d’objets BLOB Azure](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Il fournit également un résumé des avantages de l’utilisation du service BLOB Azure pour stocker les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauvegardes.  
  
 SQL Server prend en charge le stockage des sauvegardes dans le service de stockage d’objets BLOB Azure des manières suivantes :  
  
-   **Gérez vos sauvegardes dans Azure :** À l’aide des mêmes méthodes que celles utilisées pour sauvegarder sur disque et sur bande, vous pouvez maintenant effectuer une sauvegarde dans le stockage Azure en spécifiant l’URL comme destination de sauvegarde.  Utilisez cette fonctionnalité pour sauvegarder ou configurer manuellement votre propre stratégie de sauvegarde comme vous le feriez pour un stockage local ou d'autres options hors site. Cette fonctionnalité est également connue sous le nom **Sauvegarde SQL Server vers une URL**. Pour plus d’informations, consultez [SQL Server Backup to URL](sql-server-backup-to-url.md). Cette fonctionnalité est disponible dans SQL Server 2012 SP1 CU2 ou version ultérieure.  
  
    > [!NOTE]  
    >  Pour les versions SQL Server antérieures à SQL Server 2014, vous pouvez utiliser le complément SQL Server la sauvegarde dans Azure pour créer rapidement et facilement des sauvegardes dans le stockage Azure. Pour plus d'informations, consultez le [centre de téléchargement](https://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Laissez SQL Server gérer les sauvegardes dans Azure :** Configurez SQL Server pour gérer la stratégie de sauvegarde et planifier des sauvegardes pour une ou plusieurs bases de données, ou définissez les valeurs par défaut au niveau de l’instance. Cette fonctionnalité est appelée **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]** . Pour plus d’informations, consultez [SQL Server Managed Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md). Cette fonctionnalité est disponible dans SQL Server 2014 ou version ultérieure.  
  
## <a name="benefits-of-using-the-azure-blob-service-for-ssnoversion-backups"></a>Avantages de l’utilisation du service d’objets BLOB Azure pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauvegardes  
  
-   Stockage hors site flexible, fiable et illimité : le stockage de vos sauvegardes sur le service BLOB Azure peut être une option hors site pratique, flexible et facile d’accès. La création d'un stockage hors site pour vos sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être aussi simple que la modification de vos scripts/tâches existants. En principe, le stockage hors site doit être suffisamment éloigné de l'emplacement de la base de données de production pour empêcher qu'un éventuel sinistre n'affecte tous les emplacements (bases de données hors site et de production). En choisissant de géorépliquer le stockage d'objets blob, vous disposez d'un niveau de protection supplémentaire au cas où un sinistre affecterait l'ensemble de la région. En outre, les sauvegardes restent accessibles à partir de n'importe quel endroit et à tout moment, et vous pouvez y accéder facilement pour les restaurations.  
  
-   Archive de sauvegarde : le service de stockage d’objets BLOB Azure offre une meilleure alternative à l’option de bande souvent utilisée pour archiver les sauvegardes. Le stockage sur bande peut nécessiter le transport physique vers un emplacement hors site, ainsi que des mesures de protection des supports. Le stockage de vos sauvegardes dans le service BLOB Azure offre une option d’archivage instantané, hautement disponible et durable.  
  
-   Aucune surcharge de gestion du matériel : il n’y a aucune surcharge de gestion du matériel avec les services Azure. Ces derniers gèrent le matériel et fournissent une géo-réplication à des fins de redondance et de protection contre les défaillances matérielles.  
  
-   Actuellement, pour les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutant sur une machine virtuelle Azure, la sauvegarde dans les services de stockage BLOB Azure peut être réalisée en créant des disques attachés. Toutefois, le nombre de disques que vous pouvez attacher à une machine virtuelle Azure est limité. Cette limite est de 16 disques pour une instance extra-large et inférieure pour les instances plus petites. En activant une sauvegarde directe dans le stockage d’objets BLOB Azure, vous pouvez contourner la limite de 16 disques.  
  
     En outre, le fichier de sauvegarde qui est maintenant stocké dans le service de stockage d’objets BLOB Azure est directement disponible pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur local ou un autre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutant sur une machine virtuelle Azure, sans qu’il soit nécessaire d’attacher/détacher la base de données ou de télécharger et d’attacher le disque dur virtuel.  
  
-   Avantages en termes de coûts : payez uniquement pour le service utilisé. Peut être économique comme option de sauvegarde et d'archivage hors site. Pour plus d’informations et de liens, consultez la section [Considérations sur la facturation Azure](#Billing) .  
  
##  <a name="azure-billing-considerations"></a><a name="Billing"></a>Considérations sur la facturation Azure :  
 La compréhension des coûts de stockage Azure vous permet de prévoir le coût de création et de stockage des sauvegardes dans Azure.  
  
 La [calculatrice de prix Azure](https://go.microsoft.com/fwlink/?LinkId=277060) peut vous aider à estimer vos coûts.  
  
 **Stockage :** les tarifs sont basés sur l'espace utilisé et sont calculés sur une échelle graduée en fonction du niveau de redondance. Pour plus d’informations, consultez la section **Gestion des données** de l’article [Détails de la tarification](https://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Transferts de données :** Les transferts de données entrants vers Azure sont gratuits. Les transferts sortants sont facturés en fonction de l'utilisation de la bande passante et calculés selon une échelle graduée spécifique à la région. Pour plus d'informations, consultez la section [Transferts de données](https://go.microsoft.com/fwlink/?LinkId=277061) de l'article Détails de la tarification.  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Didacticiel : SQL Server la sauvegarde et la restauration dans le service de stockage d’objets BLOB Azure](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [Sauvegarde SQL Server vers une URL](sql-server-backup-to-url.md)  
  
