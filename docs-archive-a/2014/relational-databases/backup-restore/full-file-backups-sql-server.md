---
title: Sauvegardes de fichiers complètes (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backing up [SQL Server], files or filegroups
- backups [SQL Server], files or filegroups
- full recovery model [SQL Server], full file backups
- file backups [SQL Server], full
- files [SQL Server], backing up
- filegroups [SQL Server], backing up
- file backups [SQL Server]
ms.assetid: a716bf8d-0c5a-490d-aadd-597b3b0fac0c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e2e45dc68afa4d464aa3931075a1c1b3be792e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612441"
---
# <a name="full-file-backups-sql-server"></a><span data-ttu-id="63a2d-102">Sauvegardes de fichiers complètes (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63a2d-102">Full File Backups (SQL Server)</span></span>
  <span data-ttu-id="63a2d-103">Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui contiennent plusieurs fichiers ou groupes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="63a2d-104">Les fichiers d'une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être sauvegardés et restaurés individuellement.</span><span class="sxs-lookup"><span data-stu-id="63a2d-104">The files in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database can be backed up and restored individually.</span></span> <span data-ttu-id="63a2d-105">De plus, vous pouvez spécifier un groupe de fichiers entier au lieu de spécifier chaque fichier constitutif individuellement.</span><span class="sxs-lookup"><span data-stu-id="63a2d-105">Also, you can specify a whole filegroup instead of specifying each constituent file individually.</span></span> <span data-ttu-id="63a2d-106">Notez que si un fichier dans un groupe de fichiers est hors connexion (par exemple parce que le fichier est en cours de restauration), la totalité du groupe de fichiers est hors connexion et ne peut être sauvegardée.</span><span class="sxs-lookup"><span data-stu-id="63a2d-106">Note that if any file in a filegroup is offline (for example, because the file is being restored), the whole filegroup is offline and cannot be backed up.</span></span>  
  
 <span data-ttu-id="63a2d-107">Des sauvegardes de fichiers de groupes de fichiers en lecture seule peuvent être associées à des sauvegardes partielles.</span><span class="sxs-lookup"><span data-stu-id="63a2d-107">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="63a2d-108">Les sauvegardes partielles incluent tous les groupes de fichiers en lecture-écriture et, éventuellement, un ou plusieurs groupes de fichiers en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="63a2d-108">Partial backups include all the read/write filegroups and, optionally, one or more read-only filegroups.</span></span> <span data-ttu-id="63a2d-109">Pour plus d’informations, consultez [Sauvegardes partielles &#40;SQL Server&#41;](partial-backups-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="63a2d-109">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="63a2d-110">Une sauvegarde de fichiers peut servir de *base différentielle* pour des sauvegardes différentielles de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-110">A file backup can serve as the *differential base* for differential file backups.</span></span> <span data-ttu-id="63a2d-111">Pour plus d’informations, consultez [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="63a2d-111">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63a2d-112">Les sauvegardes complètes de fichiers sont généralement appelées *sauvegardes de fichiers*, sauf quand elles sont comparées explicitement à des *sauvegardes différentielles de fichiers*.</span><span class="sxs-lookup"><span data-stu-id="63a2d-112">Full file backups are typically called *file backups*, except when they are being explicitly compared with *differential file backups*.</span></span>  
  
 <span data-ttu-id="63a2d-113">**Dans cette rubrique :**</span><span class="sxs-lookup"><span data-stu-id="63a2d-113">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="63a2d-114">Avantages des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-114">Benefits of File Backups</span></span>](#Benefits)  
  
-   [<span data-ttu-id="63a2d-115">Inconvénients des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-115">Disadvantages of File Backups</span></span>](#Disadvantages)  
  
-   [<span data-ttu-id="63a2d-116">Vue d'ensemble des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-116">Overview of File Backups</span></span>](#Overview)  
  
-   [<span data-ttu-id="63a2d-117">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="63a2d-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-file-backups"></a><a name="Benefits"></a> <span data-ttu-id="63a2d-118">Avantages des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-118">Benefits of File Backups</span></span>  
 <span data-ttu-id="63a2d-119">Les sauvegardes de fichiers présentent les avantages suivants par rapport aux sauvegardes de base de données :</span><span class="sxs-lookup"><span data-stu-id="63a2d-119">File backups offer the following advantages over database backups:</span></span>  
  
-   <span data-ttu-id="63a2d-120">L'utilisation de sauvegardes de fichiers peut augmenter la vitesse de récupération, car elle vous permet de restaurer uniquement les fichiers endommagés sans restaurer le reste de la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-120">Using file backups can increase the speed of recovery by letting you restore only damaged files, without restoring the rest of the database.</span></span>  
  
     <span data-ttu-id="63a2d-121">Par exemple, si une base de données est constituée de plusieurs fichiers situés sur des disques différents et qu'un disque est défectueux, seul le fichier du disque défectueux doit être restauré.</span><span class="sxs-lookup"><span data-stu-id="63a2d-121">For example, if a database consists of several files that are located on different disks and one disk fails, only the file on the failed disk has to be restored.</span></span> <span data-ttu-id="63a2d-122">Le fichier endommagé peut être restauré rapidement, l'opération prenant moins de temps que la restauration d'une base de données entière.</span><span class="sxs-lookup"><span data-stu-id="63a2d-122">The damaged file can be quickly restored, and recovery is faster than it would be for an entire database.</span></span>  
  
-   <span data-ttu-id="63a2d-123">Les sauvegardes de fichiers permettent une grande flexibilité dans la planification et la gestion des supports par rapport aux sauvegardes de bases de données complètes, lesquelles peuvent devenir impossibles à gérer si les bases de données sont particulièrement volumineuses.</span><span class="sxs-lookup"><span data-stu-id="63a2d-123">File backups increase flexibility in scheduling and media handling over full database backups, which for very large databases can become unmanageable.</span></span> <span data-ttu-id="63a2d-124">Cette flexibilité accrue des sauvegardes de fichiers ou de groupes de fichiers est également utile pour les bases de données volumineuses contenant des données avec différentes caractéristiques de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="63a2d-124">The increased flexibility of file or filegroup backups is also useful for large databases that contain data that has varying update characteristics.</span></span>  
  
##  <a name="disadvantages-of-file-backups"></a><a name="Disadvantages"></a> <span data-ttu-id="63a2d-125">Inconvénients des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-125">Disadvantages of File Backups</span></span>  
  
-   <span data-ttu-id="63a2d-126">Le principal inconvénient des sauvegardes de fichiers par rapport aux sauvegardes de bases de données complètes est la complexité administrative supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="63a2d-126">The primary disadvantage of file backups compared to full database backups is the additional administrative complexity.</span></span> <span data-ttu-id="63a2d-127">Les tâches de gestion et de suivi d'un jeu complet de sauvegardes prennent beaucoup de temps et peuvent dépasser l'espace nécessaire pour les sauvegardes de bases de données complètes.</span><span class="sxs-lookup"><span data-stu-id="63a2d-127">Maintaining and keeping track of a complete set of these backups can be a time-consuming task that might outweigh the space requirements of full database backups.</span></span>  
  
-   <span data-ttu-id="63a2d-128">Une défaillance du support peut rendre une base de données complète irrécupérable s'il n'existe aucune sauvegarde du fichier endommagé.</span><span class="sxs-lookup"><span data-stu-id="63a2d-128">A media failure can make a complete database unrecoverable if a damaged file lacks a backup.</span></span> <span data-ttu-id="63a2d-129">Vous devez donc gérer un jeu complet de sauvegardes de fichiers et, en modes de restauration complète et de récupération utilisant les journaux de transactions, une ou plusieurs sauvegardes de journaux qui couvrent au minimum l'intervalle entre la première sauvegarde de fichiers complète et la dernière.</span><span class="sxs-lookup"><span data-stu-id="63a2d-129">You must therefore maintain a complete set of file backups, and, for the full/bulk-logged recovery model, one or more log backups covering minimally the interval between the first full file backup and last full file backup.</span></span>  
  
##  <a name="overview-of-file-backups"></a><a name="Overview"></a> <span data-ttu-id="63a2d-130">Vue d'ensemble des sauvegardes de fichiers</span><span class="sxs-lookup"><span data-stu-id="63a2d-130">Overview of File Backups</span></span>  
 <span data-ttu-id="63a2d-131">Une sauvegarde complète de fichiers sauvegarde toutes les données d'un ou de plusieurs fichiers ou groupes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-131">A full file backup backs up all the data in one or more files or filegroups.</span></span> <span data-ttu-id="63a2d-132">Par défaut, les sauvegardes de fichiers contiennent suffisamment d'enregistrements de journaux pour restaurer par progression le fichier jusqu'à la fin de l'opération de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="63a2d-132">By default, file backups contain enough log records to roll forward the file to the end of the backup operation.</span></span>  
  
 <span data-ttu-id="63a2d-133">La sauvegarde d'un fichier ou d'un groupe de fichiers en lecture seule est identique pour chaque mode de récupération.</span><span class="sxs-lookup"><span data-stu-id="63a2d-133">Backing up a read-only file or filegroup is the same for every recovery model.</span></span> <span data-ttu-id="63a2d-134">En mode de restauration complète, un jeu complet de sauvegardes complètes de fichiers associé à un nombre suffisant de sauvegardes de journaux pour couvrir toutes les sauvegardes de fichiers est équivalent à une sauvegarde complète de la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-134">Under the full recovery model, a complete set of full file backups, together with enough log backups to span all the file backups, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="63a2d-135">Une seule opération de sauvegarde de fichier peut être effectuée à la fois.</span><span class="sxs-lookup"><span data-stu-id="63a2d-135">Only one file backup operation can occur at a time.</span></span> <span data-ttu-id="63a2d-136">Vous pouvez sauvegarder plusieurs fichiers à la fois, mais cette procédure peut augmenter la durée de récupération si vous avez besoin de restaurer un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="63a2d-136">You can back up multiple files in one operation, but this might extend the recovery time if you only have to restore a single file.</span></span> <span data-ttu-id="63a2d-137">Cela tient au fait que toute la sauvegarde devra être lue pour localiser ce fichier.</span><span class="sxs-lookup"><span data-stu-id="63a2d-137">This is because to locate that file, the whole backup is read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63a2d-138">Les fichiers individuels peuvent être restaurés à partir d'une sauvegarde de base de données. Toutefois, la localisation et la restauration d'un fichier à partir d'une sauvegarde de base de données prennent plus de temps qu'à partir d'une sauvegarde de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-138">Individual files can be restored from a database backup; however, locating and restoring a file takes longer from a database backup than from a file backup.</span></span>  
  
### <a name="file-backups-and-the-simple-recovery-model"></a><span data-ttu-id="63a2d-139">Sauvegardes de fichiers et le mode de récupération simple</span><span class="sxs-lookup"><span data-stu-id="63a2d-139">File Backups and the Simple Recovery Model</span></span>  
 <span data-ttu-id="63a2d-140">En mode de récupération simple, vous devez sauvegarder conjointement tous les fichiers en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="63a2d-140">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="63a2d-141">Vous pouvez ainsi garantir que la base de données peut être restaurée dans un état cohérent dans le temps.</span><span class="sxs-lookup"><span data-stu-id="63a2d-141">This makes sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="63a2d-142">Plutôt que de spécifier individuellement chaque fichier ou groupe de fichier en lecture-écriture, utilisez l'option READ_WRITE_FILEGROUPS.</span><span class="sxs-lookup"><span data-stu-id="63a2d-142">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="63a2d-143">Cette option sauvegarde tous les groupes de fichiers en lecture-écriture dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-143">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="63a2d-144">Une sauvegarde qui est créée en spécifiant READ_WRITE_FILEGROUPS est appelée une « sauvegarde partielle ».</span><span class="sxs-lookup"><span data-stu-id="63a2d-144">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a partial backup.</span></span> <span data-ttu-id="63a2d-145">Pour plus d’informations, consultez [Sauvegardes partielles &#40;SQL Server&#41;](partial-backups-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="63a2d-145">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
### <a name="file-backups-and-the-full-recovery-model"></a><span data-ttu-id="63a2d-146">Sauvegardes de fichiers et mode de récupération complète</span><span class="sxs-lookup"><span data-stu-id="63a2d-146">File Backups and the Full Recovery Model</span></span>  
 <span data-ttu-id="63a2d-147">En mode de récupération complète, vous devez sauvegarder le journal des transactions, sans tenir compte du reste de votre stratégie de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="63a2d-147">Under the full recovery model, you must back up the transaction log, regardless of the rest of your backup strategy.</span></span> <span data-ttu-id="63a2d-148">Un jeu complet de sauvegardes complètes de fichiers associé à un nombre suffisant de sauvegardes de journaux pour couvrir toutes les sauvegardes de fichiers à partir de la première sauvegarde de fichiers, est équivalent à une sauvegarde complète de la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-148">A complete set of full file backups, together with enough log backups to span all the file backups from the start of the first file backup, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="63a2d-149">La restauration d'une base de données à l'aide seulement de sauvegardes de journaux et de fichiers peut être complexe.</span><span class="sxs-lookup"><span data-stu-id="63a2d-149">Restoring a database using just file and log backups can be complex.</span></span> <span data-ttu-id="63a2d-150">Aussi, dans la mesure du possible, il est recommandé d'effectuer une sauvegarde complète de base de données et de commencer les sauvegardes des journaux avant la première sauvegarde de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-150">Therefore, if it is possible, it is a best practice to perform a full database backup and start the log backups before the first file backup.</span></span> <span data-ttu-id="63a2d-151">La figure ci-dessous illustre une stratégie dans laquelle une sauvegarde complète de base de données est effectuée (à l'instant t1) peu après la création de la base de données (à l'instant t0).</span><span class="sxs-lookup"><span data-stu-id="63a2d-151">The following illustration shows a strategy in which a full database backup is taken (at time t1) soon after the database is created (at time t0).</span></span> <span data-ttu-id="63a2d-152">Cette première sauvegarde de base de données permet aux sauvegardes des journaux de transactions de démarrer.</span><span class="sxs-lookup"><span data-stu-id="63a2d-152">This first database backup enables transaction log backups to start.</span></span> <span data-ttu-id="63a2d-153">Les sauvegardes des journaux de transactions sont planifiées à intervalles définis.</span><span class="sxs-lookup"><span data-stu-id="63a2d-153">Transaction log backups are scheduled to occur at set intervals.</span></span> <span data-ttu-id="63a2d-154">Les sauvegardes de fichiers sont effectuées à l'intervalle qui répond au mieux aux besoins de l'entreprise concernant la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-154">File backups occur at whatever interval best meets the business requirements for the database.</span></span> <span data-ttu-id="63a2d-155">Cette figure montre la sauvegarde individuelle de chacun des quatre groupes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-155">This illustration shows each of the four filegroups being backed up one at a time.</span></span> <span data-ttu-id="63a2d-156">L'ordre de leur sauvegarde (A, C, B, A) correspond aux besoins de l'entreprise concernant la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-156">The order in which they are backed up (A, C, B, A) reflects the business requirements of the database.</span></span>  
  
 <span data-ttu-id="63a2d-157">![Stratégie combinant les sauvegardes de base de données, de fichier et de fichier journal](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Stratégie combinant les sauvegardes de base de données, de fichier et de fichier journal")</span><span class="sxs-lookup"><span data-stu-id="63a2d-157">![Strategy combining database, file, and log backups](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Strategy combining database, file, and log backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63a2d-158">En mode de restauration complète, vous devez restaurer par progression le journal des transactions lors de la restauration d'une sauvegarde de fichiers en lecture-écriture pour que le fichier soit cohérent avec le reste de la base de données.</span><span class="sxs-lookup"><span data-stu-id="63a2d-158">Under the full recovery model, you must roll forward the transaction log when restoring a read/write file backup to make sure that the file is consistent with the rest of the database.</span></span> <span data-ttu-id="63a2d-159">Pour éviter de restaurer par progression de nombreuses sauvegardes du journal des transactions, envisagez l'utilisation de sauvegardes différentielles de fichiers.</span><span class="sxs-lookup"><span data-stu-id="63a2d-159">To avoid rolling forward a lot of transaction log backups, consider using differential file backups.</span></span> <span data-ttu-id="63a2d-160">Pour plus d’informations, consultez [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="63a2d-160">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="63a2d-161">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="63a2d-161">Related Tasks</span></span>  
 <span data-ttu-id="63a2d-162">**Pour créer une sauvegarde d'un fichier ou d'un groupe de fichiers**</span><span class="sxs-lookup"><span data-stu-id="63a2d-162">**To create a file or filegroup backup**</span></span>  
  
-   [<span data-ttu-id="63a2d-163">Sauvegarder des fichiers et des groupes de fichiers &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63a2d-163">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="63a2d-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="63a2d-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63a2d-165">Les sauvegardes de fichiers ne sont pas prises en charge par l'Assistant Plan de maintenance.</span><span class="sxs-lookup"><span data-stu-id="63a2d-165">File backups are not supported by the Maintenance Plan Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a2d-166"> Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63a2d-166">See Also</span></span>  
 <span data-ttu-id="63a2d-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63a2d-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="63a2d-168">[Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-168">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="63a2d-169">[Sauvegarde et restauration : interopérabilité et coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-169">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="63a2d-170">[Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-170">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="63a2d-171">[Restaurations de fichiers &#40;mode de récupération simple&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-171">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="63a2d-172">[Restaurations de fichiers &#40;mode de récupération complète&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-172">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="63a2d-173">[Restauration en ligne &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63a2d-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="63a2d-174">Restaurations fragmentaires &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63a2d-174">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  