---
title: Unités de sauvegarde (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8abbba087679d263c00484764ecf445d6e5a006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710687"
---
# <a name="backup-devices-sql-server"></a>Unités de sauvegarde (SQL Server)
  Au cours d’une opération de sauvegarde sur une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les données sauvegardées (la *sauvegarde*) sont écrites sur une unité de sauvegarde physique. Cette unité de sauvegarde physique est activée dès l'écriture de la première sauvegarde dans un jeu de supports. Les sauvegardes sur un jeu comprenant une ou plusieurs unités de sauvegarde constituent un seul jeu de supports.  
  
 **Dans cette rubrique :**  
  
-   [Termes et définitions](#TermsAndDefinitions)  
  
-   [Utilisation d'unités de sauvegarde sur disque](#DiskBackups)  
  
-   [Utilisation de périphériques à bandes](#TapeDevices)  
  
-   [Utilisation d'une unité de sauvegarde logique](#LogicalBackupDevice)  
  
-   [Supports de sauvegarde en miroir](#MirroredMediaSets)  
  
-   [Archivage des sauvegardes SQL Server](#Archiving)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> Termes et définitions  
 disque de sauvegarde  
 Support de stockage sur disque dur ou autre qui renferme un ou plusieurs fichiers de sauvegarde. Un fichier de sauvegarde est un fichier de système d'exploitation classique.  
  
 jeu de supports  
 Ensemble ordonné de supports de sauvegarde (bandes ou fichiers disque) qui utilise un type et un nombre fixes d'unités de sauvegarde. Pour plus d’informations sur les supports de sauvegarde, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
 unité de sauvegarde physique  
 Soit un lecteur de bande, soit un fichier disque fourni par le système d'exploitation. Vous pouvez réaliser une sauvegarde sur 1 à 64 unités de sauvegarde. Si une sauvegarde nécessite plusieurs unités de sauvegarde, les unités doivent toutes correspondre à un seul type d'unité (disque ou bande).  
  
 Les sauvegardes SQL Server peuvent également être écrites dans le service de stockage d’objets blob Azure, en plus d’un disque ou d’une bande.  
  
##  <a name="using-disk-backup-devices"></a><a name="DiskBackups"></a>Utilisation des unités de sauvegarde sur disque  
 **Dans cette section :**  
  
-   [Définition d'un fichier de sauvegarde selon son nom physique (Transact-SQL)](#BackupFileUsingPhysicalName)  
  
-   [Spécification du chemin d'accès d'un fichier de sauvegarde sur disque](#BackupFileDiskPath)  
  
-   [Sauvegarde dans un fichier sur un partage réseau](#NetworkShare)  
  
 Si un fichier disque se remplit pendant qu'une opération de sauvegarde ajoute une sauvegarde au jeu de supports, l'opération de sauvegarde échoue. La taille maximale d'un fichier de sauvegarde est fonction de l'espace libre disponible sur l'unité de disque ; la taille appropriée d'une unité de sauvegarde sur disque dépend donc de la taille de vos sauvegardes.  
  
 Une unité de sauvegarde sur disque peut être une simple unité de disque, telle qu'un lecteur ATA. Une autre solution envisageable consiste à utiliser une unité de disque échangeable à chaud qui vous permettrait de remplacer de manière transparente un disque saturé sur l'unité par un disque vide. Un disque de sauvegarde peut désigner un disque local sur le serveur ou un disque distant correspondant à une ressource réseau partagée. Pour savoir comment utiliser un disque distant, consultez la section [Sauvegarde dans un fichier sur un partage réseau](#NetworkShare), plus loin dans cette rubrique.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les outils de gestion offrent une excellente souplesse de gestion des unités de sauvegarde sur disque, car ils génèrent automatiquement un nom horodaté dans le fichier disque.  
  
> [!IMPORTANT]  
>  À titre de recommandation, il est préférable que le disque de sauvegarde ne soit pas le même que les disques de données ou de journal de la base de données. Ce paramètre est primordial pour garantir l'accès aux sauvegardes en cas d'échec du disque de données ou de journal.  
  
###  <a name="specifying-a-backup-file-by-using-its-physical-name-transact-sql"></a><a name="BackupFileUsingPhysicalName"></a>Spécification d’un fichier de sauvegarde à l’aide de son nom physique (Transact-SQL)  
 La syntaxe [BACKUP](/sql/t-sql/statements/backup-transact-sql) de base permettant de spécifier un fichier de sauvegarde d'après son nom d'unité physique est la suivante :  
  
 BACKUP DATABASE *nom_base_de_données*  
  
 TO DISK **=** { **’** _nom_unité_sauvegarde_physique_ **’**  |  **@** _nom_unité_sauvegarde_physique_var_ }  
  
 Par exemple :  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 Pour spécifier une unité de disque physique dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , la syntaxe de base est la suivante :  
  
 RESTORE { DATABASE | LOG } *nom_base_de_données*  
  
 FROM DISK **=** { **’** _nom_unité_sauvegarde_physique_ **’**  |  **@** _nom_unité_sauvegarde_physique_var_ }  
  
 Par exemple,  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="specifying-the-path-of-a-disk-backup-file"></a><a name="BackupFileDiskPath"></a>Spécification du chemin d’accès d’un fichier de sauvegarde sur disque  
 Lorsque vous spécifiez un fichier de sauvegarde, entrez son chemin d'accès complet et le nom du fichier. Si vous spécifiez uniquement le nom du fichier ou un chemin d'accès relatif au moment de la sauvegarde d'un fichier, celui-ci est copié dans le répertoire de sauvegarde par défaut. Ce répertoire de sauvegarde par défaut est C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup, où *n* est le numéro de l’instance du serveur. Par conséquent, pour l'instance de serveur par défaut, le répertoire de sauvegarde par défaut est : C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup.  
  
 Pour éviter toute ambiguïté, en particulier dans les scripts, il est recommandé de spécifier explicitement le chemin d'accès du répertoire de sauvegarde dans chaque clause DISK. Cependant, cette exigence prend moins d'importance si vous utilisez l'Éditeur de requête. Dans ce cas, si vous êtes certain que le fichier de sauvegarde réside dans le répertoire de sauvegarde par défaut, vous pouvez omettre le chemin d'accès d'une clause DISK. Par exemple, l'instruction `BACKUP` suivante sauvegarde la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans le répertoire de sauvegarde par défaut.  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  L'emplacement par défaut est stocké dans la clé de Registre **BackupDirectory** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**.  
  
###  <a name="backing-up-to-a-file-on-a-network-share"></a><a name="NetworkShare"></a>Sauvegarde dans un fichier sur un partage réseau  
 Pour permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'accéder au fichier disque distant, le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit bénéficier d'un accès au partage réseau. Cette situation implique que vous disposiez des autorisations nécessaires aux opérations de sauvegarde pour écrire sur le partage réseau et aux opérations de restauration pour lire à partir de ce dernier. La disponibilité des lecteurs réseau et des autorisations dépend du contexte dans lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté :  
  
-   Pour sauvegarder un lecteur réseau lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute via un compte d'utilisateur de domaine, le lecteur partagé doit être mappé sur un lecteur réseau dans la session où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté. Si vous démarrez Sqlservr.exe à partir de la ligne de commande, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] voit tous les lecteurs réseau que vous avez mappés dans votre session de connexion.  
  
-   Lorsque vous exécutez Sqlservr.exe en tant que service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute dans une autre session qui n'a aucun lien avec votre session de connexion. La session dans laquelle un service s'exécute peut avoir ses propres lecteurs mappés (bien que ce ne soit généralement pas le cas).  
  
-   Il est possible de se connecter au compte de service réseau à l'aide du compte d'ordinateur plutôt qu'avec un compte d'utilisateur de domaine. Pour autoriser des sauvegardes sur un lecteur partagé à partir d'ordinateurs spécifiques, accordez l'accès aux comptes de ces ordinateurs. Tant que le processus Sqlservr.exe chargé d'écrire la sauvegarde bénéficie d'un accès, peu importe si l'utilisateur exécutant la commande BACKUP dispose d'un accès ou non.  
  
    > [!IMPORTANT]  
    >  La sauvegarde de données sur un réseau peut être sujette à des erreurs du réseau ; c'est pourquoi nous vous conseillons de vérifier l'opération de sauvegarde après l'avoir menée à terme si vous utilisez un disque distant. Pour plus d’informations, consultez [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a>Définition d'un nom UNC (Universal Naming Convention)  
 Pour préciser un partage réseau dans une opération de sauvegarde ou de restauration, vous devez utiliser le nom UNC (Universal Naming Convention) complet du fichier de l'unité de sauvegarde. Un nom UNC se présente sous la forme **\\\\** _nom_système_ **\\** _nom_partage_ **\\** _chemin_ **\\** _nom_fichier_.  
  
 Par exemple :  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="using-tape-devices"></a><a name="TapeDevices"></a>Utilisation de périphériques à bandes  
  
> [!NOTE]  
>  La prise en charge des unités de sauvegarde sur bande sera supprimée dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.  
  
 **Dans cette section :**  
  
-   [Définition d'une bande de sauvegarde selon son nom physique (Transact-SQL)](#BackupTapeUsingPhysicalName)  
  
-   [Options de sauvegarde et de restauration propres aux bandes (Transact-SQL)](#TapeOptions)  
  
-   [Gestion des bandes ouvertes](#OpenTapes)  
  
 La sauvegarde de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur bande exige un lecteur ou des lecteurs de bandes pris en charge par le système d'exploitation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Qui plus est, pour le lecteur de bande en question, nous vous conseillons d'utiliser uniquement des bandes recommandées par le fabricant du lecteur. Pour plus d'informations sur l'installation d'un lecteur de bande, veuillez vous reporter à la documentation du système d'exploitation Windows.  
  
 Avec un lecteur de bande, une opération de sauvegarde peut remplir une bande et se poursuivre sur une autre. Chaque bande contient un en-tête de support. Le premier support employé est la *bande initiale*. Chaque bande successive est une *bande magnétique de sauvegarde consécutive* , dotée d'un numéro de séquence supérieur d'une unité par rapport à la bande précédente. Par exemple, un support de sauvegarde associé à quatre périphériques à bandes contient au moins quatre bandes initiales (et, si la base de données ne tient pas dessus, quatre séries de bandes magnétiques de sauvegarde consécutive). Lorsque vous ajoutez un jeu de sauvegarde, vous devez monter la dernière bande de la série. Si la dernière bande n'est pas montée, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] cherche jusqu'à la fin de la bande montée puis vous demande de changer de bande. À ce moment-là, montez la dernière bande.  
  
 Les unités de sauvegarde sur bande sont utilisées comme les unités de disques avec les exceptions suivantes :  
  
-   Le périphérique à bandes doit être connecté physiquement à l'ordinateur qui exécute une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La sauvegarde sur des bandes à distance n'est pas prise en charge.  
  
-   Si une unité de sauvegarde sur bande est remplie lors de l'opération de sauvegarde mais que davantage de données restent à écrire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous demande d'insérer une nouvelle bande et de poursuivre l'opération de sauvegarde après chargement d'une nouvelle bande.  
  
###  <a name="specifying-a-backup-tape-by-using-its-physical-name-transact-sql"></a><a name="BackupTapeUsingPhysicalName"></a>Spécification d’une bande de sauvegarde à l’aide de son nom physique (Transact-SQL)  
 La syntaxe [BACKUP](/sql/t-sql/statements/backup-transact-sql) de base permettant de spécifier une bande de sauvegarde selon le nom d'unité physique du lecteur de bande est la suivante :  
  
 BACKUP { DATABASE | LOG } *nom_base_de_données*  
  
 TO TAPE **=** { **’** _nom_unité_sauvegarde_physique_ **’**  |  **@** _nom_unité_sauvegarde_physique_var_ }  
  
 Par exemple :  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 Pour spécifier une unité de bande physique dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , la syntaxe de base est la suivante :  
  
 RESTORE { DATABASE | LOG } *nom_base_de_données*  
  
 FROM TAPE **=** { **’** _nom_unité_sauvegarde_physique_ **’**  |  **@** _nom_unité_sauvegarde_physique_ }  
  
###  <a name="tape-specific-backup-and-restore-options-transact-sql"></a><a name="TapeOptions"></a>Options de sauvegarde et de restauration propres aux bandes (Transact-SQL)  
 Pour faciliter la gestion des bandes, l'instruction BACKUP fournit les options de bande suivantes :  
  
-   { NOUNLOAD | **UNLOAD** }  
  
     Vous pouvez contrôler si une bande de sauvegarde est déchargée automatiquement à partir du lecteur de bande après une opération de sauvegarde ou de restauration. UNLOAD/NOUNLOAD est un paramètre de session qui reste en vigueur jusqu'à la fin de la session ou tant qu'il n'est pas réinitialisé par le choix de l'option opposée à celle en cours d'utilisation.  
  
-   { **REWIND** | NOREWIND }  
  
     Vous pouvez contrôler si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] laisse la bande ouverte après l'opération de sauvegarde ou de restauration ou bien libère et rembobine la bande une fois qu'elle est remplie. Le comportement par défaut est de rembobiner la bande (REWIND).  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe et les arguments de BACKUP, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql). Pour plus d’informations sur la syntaxe et les arguments de RESTORE, consultez respectivement [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) et [RESTORE, arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
###  <a name="managing-open-tapes"></a><a name="OpenTapes"></a>Gestion des bandes ouvertes  
 Pour afficher une liste des périphériques à bandes ouverts et l’état des demandes de montage, interrogez la vue de gestion dynamique [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) . Cette vue affiche toutes les bandes ouvertes. Elle inclut les bandes en cours d'utilisation provisoirement inactives et en attente de la prochaine opération BACKUP ou RESTORE.  
  
 Si une bande a, accidentellement, été laissée ouverte, le moyen le plus rapide de la libérer consiste à utiliser la commande suivante : RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_. Pour plus d’informations, consultez [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).  
  
## <a name="using-the-azure-blob-storage-service"></a>Utilisation du service de stockage d’objets BLOB Azure  
 Les sauvegardes SQL Server peuvent être écrites dans le service Stockage Blob Azure.  Pour plus d’informations sur l’utilisation du service de stockage d’objets BLOB Azure pour vos sauvegardes, consultez [SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
##  <a name="using-a-logical-backup-device"></a><a name="LogicalBackupDevice"></a>Utilisation d’une unité de sauvegarde logique  
 Une *unité de sauvegarde logique* est un nom facultatif défini par l’utilisateur qui pointe vers une unité de sauvegarde physique spécifique (un fichier disque ou un lecteur de bande). Une unité de sauvegarde logique vous permet d'utiliser l'indirection au moment de référencer l'unité de sauvegarde physique correspondante.  
  
 La définition d'une unité de sauvegarde logique implique d'affecter un nom logique à une unité physique. Par exemple, vous pouvez définir une unité logique, AdventureWorksBackups, pour qu’elle pointe vers le fichier Z:\SQLServerBackups\AdventureWorks2012.bak ou le lecteur de bande \\\\.\tape0. Les commandes de sauvegarde et de restauration peuvent ensuite spécifier AdventureWorksBackups comme unité de sauvegarde au lieu de DISK = ’Z:\SQLServerBackups\AdventureWorks2012.bak’ ou TAPE = ’\\\\.\tape0’.  
  
 Le nom d'unité logique doit être unique parmi toutes les unités de sauvegarde logiques résidant sur l'instance de serveur. Pour afficher les noms d’unités logiques existantes, interrogez l’affichage catalogue [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) . Cet affichage affiche le nom de chaque unité de sauvegarde logique et décrit le type et le nom de fichier physique ou le chemin d'accès de l'unité de sauvegarde physique correspondante.  
  
 Une fois définie une unité de sauvegarde logique, dans une commande BACKUP ou RESTORE, spécifiez l'unité de sauvegarde logique à la place du nom physique de l'unité. Par exemple, l'instruction suivante sauvegarde la base de données `AdventureWorks2012` dans l'unité de sauvegarde logique `AdventureWorksBackups` .  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  Dans une instruction BACKUP ou RESTORE spécifique, le nom de l'unité de sauvegarde logique et celui de l'unité de sauvegarde physique sont interchangeables.  
  
 Un avantage de l'unité de sauvegarde logique est sa plus grande simplicité d'utilisation par rapport à un chemin d'accès long. Le recours à une unité de sauvegarde logique peut être utile si vous envisagez d'écrire une série de sauvegardes dans le même chemin d'accès ou sur un lecteur de bande. Les unités de sauvegarde logiques s'avèrent particulièrement utiles pour l'identification des unités de sauvegarde sur bande.  
  
 Vous pouvez rédiger un script de sauvegarde pour l'utilisation d'une unité de sauvegarde logique spécifique. Vous pouvez ainsi passer à une nouvelle unité de sauvegarde physique sans modifier le script. Ce changement implique le processus suivant :  
  
1.  La suppression de l'unité de sauvegarde logique d'origine.  
  
2.  La définition d'une nouvelle unité de sauvegarde logique qui utilise le nom d'origine de l'unité mais mappe à une unité de sauvegarde physique différente. Les unités de sauvegarde logiques s'avèrent particulièrement utiles pour l'identification des unités de sauvegarde sur bande.  
  
##  <a name="mirrored-backup-media-sets"></a><a name="MirroredMediaSets"></a>Jeux de supports de sauvegarde en miroir  
 La mise en miroir des jeux de supports de sauvegarde permet de réduire l'impact des dysfonctionnements des unités de sauvegarde. Ces dysfonctionnements représentent une menace particulièrement sérieuse car une sauvegarde constitue la dernière protection possible contre une perte de données. À mesure que la taille des bases de données augmente, le risque de perte irrécupérable d'une sauvegarde suite à la défaillance d'une unité ou d'un support de sauvegarde se fait plus présent. La mise en miroir des supports de sauvegarde accroît la fiabilité des sauvegardes en permettant la redondance de l'unité de sauvegarde physique. Pour plus d'informations, consultez [Jeux de supports de sauvegarde en miroir &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).  
  
> [!NOTE]  
>  Les jeux de supports de sauvegarde en miroir sont uniquement pris en charge dans [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] et versions ultérieures.  
  
##  <a name="archiving-sql-server-backups"></a><a name="Archiving"></a>Archivage SQL Server sauvegardes  
 Nous vous recommandons de recourir à un utilitaire de sauvegarde système des fichiers pour archiver les sauvegardes sur disque et stocker les archives hors site. L'avantage du disque est que vous pouvez utiliser le réseau pour écrire les sauvegardes archivées sur un disque hors site. Le service Stockage Blob Azure peut être utilisé comme option d’archivage hors site.  Chargez les sauvegardes sur disque ou écrivez directement les sauvegardes dans le service Stockage Blob Azure.  
  
 Une autre approche d'archivage courante consiste à écrire des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un disque de sauvegarde local, à les archiver sur des bandes, puis à stocker les bandes hors site.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour spécifier une unité de disque (SQL Server Management Studio)**  
  
-   [Spécifier un disque ou une bande comme destination de sauvegarde &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 **Pour spécifier un périphérique à bandes (SQL Server Management Studio)**  
  
-   [Spécifier un disque ou une bande comme destination de sauvegarde &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 **Pour définir une unité logique de sauvegarde**  
  
-   [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)  
  
 **Pour utiliser une unité logique de sauvegarde**  
  
-   [Spécifier un disque ou une bande comme destination de sauvegarde &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
-   [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 **Pour afficher des informations sur les unités de sauvegarde**  
  
-   [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 **Pour supprimer une unité logique de sauvegarde**  
  
-   [sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [Supprimer une unité de sauvegarde &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server, objet Unité de sauvegarde](../performance-monitor/sql-server-backup-device-object.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Plans de maintenance](../maintenance-plans/maintenance-plans.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql)   
 [Jeux de supports de sauvegarde en miroir &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  
