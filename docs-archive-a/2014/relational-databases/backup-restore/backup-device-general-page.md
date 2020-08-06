---
title: Unité de sauvegarde (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601522"
---
# <a name="backup-device-general-page"></a>Unité de sauvegarde (page Général)
  Utilisez la page **Général** pour spécifier ou afficher les propriétés générales d'une unité logique de sauvegarde.  
  
 **Pour utiliser SQL Server Management Studio pour afficher le contenu d'une unité de sauvegarde**  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Options  
 **Nom du périphérique**  
 Permet d'afficher le nom d'une unité logique de sauvegarde existante ou de spécifier le nom d'une nouvelle unité logique de sauvegarde.  
  
 **Bande**  
 Permet d’afficher ou de sélectionner l’unité à bande de destination dans la liste **Bande** . Cette option est disponible uniquement si un lecteur de bande est connecté à l’ordinateur qui exécute l’instance du moteur de base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> [!NOTE]  
>  Les unités de sauvegarde sur bande situées sur des ordinateurs distants ne sont pas des destinations de sauvegarde valides.  
  
 **File**  
 Permet d'afficher le fichier de destination d'une unité logique de sauvegarde existante ou de spécifier un fichier de destination pour une nouvelle unité logique de sauvegarde.  
  
-   S'il s'agit d'une unité logique de sauvegarde existante, le chemin d'accès du fichier de sauvegarde s'affiche. Le champ **Fichier** n'est pas modifiable et le bouton Parcourir n'est pas disponible.  
  
-   S'il s'agit d'une nouvelle unité logique de sauvegarde, vous devez fournir le chemin d'accès du fichier de sauvegarde pour lequel vous définissez l'unité logique de sauvegarde. Il n'est pas nécessaire que le fichier existe déjà.  
  
     Pour spécifier un fichier de sauvegarde local, vous pouvez cliquer sur le bouton Parcourir à droite de la zone de texte **Fichier** . Ensuite, dans la boîte de dialogue **Rechercher les fichiers de base de données** , naviguez jusqu'aux emplacements des lecteurs fixes de l'ordinateur exécutant l'instance de serveur. Si le fichier de sauvegarde n'existe pas déjà, vous devez taper le nom du fichier que vous souhaitez utiliser dans le champ **Nom de fichier** de cette boîte de dialogue.  
  
     Vous pouvez également modifier le champ **Fichier** manuellement pour remplacer le chemin d'accès, le nom de fichier et l'extension par défaut. Pour spécifier un fichier distant en tant que destination de sauvegarde, tapez son nom complet UNC (Universal Naming Convention). Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Étant donné que la sauvegarde de données sur un réseau peut faire l'objet d'erreurs réseau, nous vous recommandons de vérifier l'opération de sauvegarde lorsqu'elle est terminée. Pour plus d’informations, consultez [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).  
  
## <a name="remarks"></a>Notes   
 Les sauvegardes sur un jeu comprenant une ou plusieurs unités de sauvegarde constituent un seul jeu de supports. Un *support de sauvegarde* est un ensemble ordonné de supports de sauvegarde (bandes ou fichiers disques) sur lequel une ou plusieurs opérations de sauvegarde ont été écrites en utilisant un type et un nombre fixes d'unités de sauvegarde. Pour plus d’informations sur les supports de sauvegarde, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
 L'unité physique de sauvegarde correspondant à une unité logique de sauvegarde est initialisée lorsque la première sauvegarde sur support de sauvegarde est écrite sur l'unité logique de sauvegarde. Si l'unité physique de sauvegarde est un fichier qui n'existe pas déjà, il est créé à ce moment-là.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Spécifier un disque ou une bande comme destination de sauvegarde &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Supprimer une unité de sauvegarde &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
-   [Définir la date d’expiration d’une sauvegarde &#40;SQL Server&#41;](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les fichiers de données et les fichiers journaux dans un jeu de sauvegarde &#40;SQL Server&#41;](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
