---
title: Erreurs de support possibles pendant les opérations de sauvegarde et de restauration (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15691c513aad6027be1063ef566ebdf245ebcc8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705204"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a><span data-ttu-id="6bde9-102">Erreurs de support possibles pendant les opérations de sauvegarde et de restauration (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6bde9-102">Possible Media Errors During Backup and Restore (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6bde9-103">vous donne la possibilité de récupérer une base de données en dépit des erreurs détectées.</span><span class="sxs-lookup"><span data-stu-id="6bde9-103">gives you the option of recovering a database despite detected errors.</span></span> <span data-ttu-id="6bde9-104">Un nouveau et important mécanisme de détection d'erreur est la création facultative d'une somme de contrôle de sauvegarde qui peut être créée par une opération de sauvegarde et validée par une opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="6bde9-104">An important new error-detection mechanism is the optional creation of a backup checksum that can be created by a backup operation and validated by a restore operation.</span></span> <span data-ttu-id="6bde9-105">Vous pouvez déterminer si une opération recherche la présence d'erreurs et si elle s'arrête ou si elle continue en présence d'une erreur.</span><span class="sxs-lookup"><span data-stu-id="6bde9-105">You can control whether an operation checks for errors and whether the operation stops or continues on encountering an error.</span></span> <span data-ttu-id="6bde9-106">Si une sauvegarde contient une somme de contrôle de sauvegarde, les instructions RESTORE et RESTORE VERIFYONLY peuvent rechercher la présence d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="6bde9-106">If a backup contains a backup checksum, RESTORE and RESTORE VERIFYONLY statements can check for errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bde9-107">Les sauvegardes en miroir offrent jusqu'à quatre copies (miroirs) d'un support de sauvegarde, auxquelles vous pouvez recourir pour effectuer une récupération à partir d'erreurs causées par un support endommagé.</span><span class="sxs-lookup"><span data-stu-id="6bde9-107">Mirrored backups provide up to four copies (mirrors) of a media set, providing alternative copies for recovering from errors caused by damaged media.</span></span> <span data-ttu-id="6bde9-108">Pour plus d'informations, consultez [Jeux de supports de sauvegarde en miroir &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="6bde9-108">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
  
  
##  <a name="backup-checksums"></a><a name="BckChecksums"></a> <span data-ttu-id="6bde9-109">Sommes de contrôle de sauvegarde</span><span class="sxs-lookup"><span data-stu-id="6bde9-109">Backup Checksums</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6bde9-110">prend en charge trois types de sommes de contrôle : une somme de contrôle sur les pages, une somme de contrôle dans les blocs de journal et une somme de contrôle de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6bde9-110">supports three types of checksums: a checksum on pages, a checksum in log blocks, and a backup checksum.</span></span> <span data-ttu-id="6bde9-111">Lorsqu'elle génère une somme de contrôle de sauvegarde, l'instruction BACKUP vérifie que les données lues depuis la base de données sont cohérentes avec toute indication de somme de contrôle ou de page endommagée présente dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="6bde9-111">When generating a backup checksum, BACKUP verifies that the data read from the database is consistent with any checksum or torn-page indication that is present in the database.</span></span>  
  
 <span data-ttu-id="6bde9-112">L'instruction BACKUP peut aussi calculer une somme de contrôle de sauvegarde sur le flux de sauvegarde ; si des informations de page endommagée ou de somme de contrôle de page sont présentes dans une page donnée, lors de la sauvegarde de la page, l'instruction BACKUP vérifie également l'état de somme de contrôle et de page endommagée, ainsi que l'ID de la page.</span><span class="sxs-lookup"><span data-stu-id="6bde9-112">The BACKUP statement optionally computes a backup checksum on the backup stream; if page-checksum or torn-page information is present on a given page, when backing up the page, BACKUP also verifies the checksum and torn-page status and the page ID, of the page.</span></span> <span data-ttu-id="6bde9-113">Lorsqu'elle crée une somme de contrôle de sauvegarde, une opération de sauvegarde n'ajoute aucune somme de contrôle aux pages.</span><span class="sxs-lookup"><span data-stu-id="6bde9-113">When creating a backup checksum, a backup operation does not add any checksums to pages.</span></span> <span data-ttu-id="6bde9-114">Les pages sont sauvegardées telles qu'elles existent dans la base de données et ne sont pas modifiées par la sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6bde9-114">Pages are backed up as they exist in the database, and the pages are unmodified by backup.</span></span>  
  
 <span data-ttu-id="6bde9-115">En raison de la charge inhérente à la vérification et à la génération des sommes de contrôle de sauvegarde, l'utilisation de ces sommes peut avoir des répercussions sur les performances.</span><span class="sxs-lookup"><span data-stu-id="6bde9-115">Due to the overhead verifying and generating backup checksums, using backup checksums poses a potential performance impact.</span></span> <span data-ttu-id="6bde9-116">La charge de travail et le débit de sauvegarde peuvent être affectés.</span><span class="sxs-lookup"><span data-stu-id="6bde9-116">Both the workload and the backup throughput may be affected.</span></span> <span data-ttu-id="6bde9-117">Par conséquent, l'utilisation de sommes de contrôle de sauvegarde est facultative.</span><span class="sxs-lookup"><span data-stu-id="6bde9-117">Therefore, using backup checksums is optional.</span></span> <span data-ttu-id="6bde9-118">Lorsque vous décidez de générer des sommes de contrôle pendant une sauvegarde, surveillez attentivement la charge processeur induite, ainsi que l'impact sur les charges de travail simultanées du système.</span><span class="sxs-lookup"><span data-stu-id="6bde9-118">When deciding to generate checksums during a backup, carefully monitor the CPU overhead incurred as well as the impact on any concurrent workload on the system.</span></span>  
  
 <span data-ttu-id="6bde9-119">L'instruction BACKUP ne modifie jamais la page source sur le disque, ni le contenu d'une page.</span><span class="sxs-lookup"><span data-stu-id="6bde9-119">BACKUP never modifies the source page on disk nor the contents of a page.</span></span>  
  
 <span data-ttu-id="6bde9-120">Lorsque les sommes de contrôle de sauvegarde sont activées, une opération de sauvegarde effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bde9-120">When backup checksums are enabled, a backup operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="6bde9-121">Avant d'écrire une page sur le support de sauvegarde, l'opération de sauvegarde vérifie les informations de niveau page : somme de contrôle de page ou détection de page endommagée, si elles existent.</span><span class="sxs-lookup"><span data-stu-id="6bde9-121">Before writing a page to the backup media, the backup operation verifies the page-level information (page checksum or torn page detection), if either exists.</span></span> <span data-ttu-id="6bde9-122">En l'absence d'informations, la sauvegarde ne peut pas vérifier la page.</span><span class="sxs-lookup"><span data-stu-id="6bde9-122">If neither exists, backup cannot verify the page.</span></span> <span data-ttu-id="6bde9-123">Non vérifiées, les pages sont incluses en l'état, et leur contenu est ajouté à la somme de contrôle de sauvegarde globale.</span><span class="sxs-lookup"><span data-stu-id="6bde9-123">Unverified the pages are included as is, and their contents are added to the overall backup checksum.</span></span>  
  
     <span data-ttu-id="6bde9-124">Si l'opération de sauvegarde rencontre une erreur de page pendant la vérification, la sauvegarde échoue.</span><span class="sxs-lookup"><span data-stu-id="6bde9-124">If the backup operation encounters a page error during verification, the backup fails.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6bde9-125">Pour plus d'informations sur les sommes de contrôle de page et sur la détection de page endommagée, consultez l'option PAGE_VERIFY de l'instruction ALTER DATABASE.</span><span class="sxs-lookup"><span data-stu-id="6bde9-125">For more information about page checksums and torn page detection, see the PAGE_VERIFY option of the ALTER DATABASE statement.</span></span> <span data-ttu-id="6bde9-126">Pour plus d’informations, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span><span class="sxs-lookup"><span data-stu-id="6bde9-126">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
2.  <span data-ttu-id="6bde9-127">Que la somme de contrôle de la page soit disponible ou non, BACKUP génère une somme de contrôle de sauvegarde séparée pour le flux de sauvegardes.</span><span class="sxs-lookup"><span data-stu-id="6bde9-127">Regardless of whether page checksums are present, BACKUP generates a separate backup checksum for the backup streams.</span></span> <span data-ttu-id="6bde9-128">Les opérations de restauration peuvent éventuellement utiliser cette somme de contrôle pour vérifier que la sauvegarde n'est pas endommagée.</span><span class="sxs-lookup"><span data-stu-id="6bde9-128">Restore operations can optionally use the backup checksum to validate that the backup is not corrupted.</span></span> <span data-ttu-id="6bde9-129">La somme de contrôle de sauvegarde est stockée sur le support de sauvegardes et non pas dans les pages de base de données.</span><span class="sxs-lookup"><span data-stu-id="6bde9-129">The backup checksum is stored on the backup media, not on the database pages.</span></span> <span data-ttu-id="6bde9-130">Elle peut en option être utilisée lors de la restauration.</span><span class="sxs-lookup"><span data-stu-id="6bde9-130">The backup checksum can optionally be used at restore time.</span></span>  
  
3.  <span data-ttu-id="6bde9-131">Le jeu de sauvegarde est signalé comme contenant des sommes de contrôle de sauvegarde (dans la colonne **has_backup_checksums** de **msdb..backupset)** .</span><span class="sxs-lookup"><span data-stu-id="6bde9-131">The backup set is flagged as containing backup checksums (in the **has_backup_checksums** column of **msdb..backupset)**.</span></span> <span data-ttu-id="6bde9-132">Pour plus d’informations, consultez [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6bde9-132">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
 <span data-ttu-id="6bde9-133">Au cours d'une opération de restauration, si des sommes de contrôle de sauvegarde sont présentes sur le support de sauvegarde, par défaut, les instructions RESTORE et RESTORE VERIFYONLY vérifient les sommes de contrôle de sauvegarde et les sommes de contrôle de page.</span><span class="sxs-lookup"><span data-stu-id="6bde9-133">During a restore operation, if backup checksums are present on the backup media, by default, both the RESTORE and RESTORE VERIFYONLY statements verify the backup checksums and page checksums.</span></span> <span data-ttu-id="6bde9-134">En l'absence de somme de contrôle de sauvegarde, les deux opérations de restauration se poursuivent sans vérification ; en effet, sans somme de contrôle de sauvegarde, la restauration ne peut pas vérifier les sommes de contrôle de page de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="6bde9-134">If there is no backup checksum, either restore operation proceeds without any verification; this is because without a backup checksum, restore cannot reliably verify page checksums.</span></span>  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a><span data-ttu-id="6bde9-135">Réponse aux erreurs de somme de contrôle de page pendant une opération de sauvegarde ou de restauration</span><span class="sxs-lookup"><span data-stu-id="6bde9-135">Response to Page Checksum Errors During a Backup or Restore Operation</span></span>  
 <span data-ttu-id="6bde9-136">Par défaut, après la rencontre d'une erreur de somme de contrôle de page, une opération de sauvegarde BACKUP ou de restauration RESTORE échoue et une opération RESTORE VERIFYONLY se poursuit.</span><span class="sxs-lookup"><span data-stu-id="6bde9-136">By default, after encountering a page checksum error, a BACKUP or RESTORE operation fails and a RESTORE VERIFYONLY operation continues.</span></span> <span data-ttu-id="6bde9-137">Toutefois, vous pouvez contrôler si une opération donnée échoue en présence d'une erreur ou continue du mieux possible.</span><span class="sxs-lookup"><span data-stu-id="6bde9-137">However, you can control whether a given operation fails on encountering an error or continues as best it can.</span></span>  
  
 <span data-ttu-id="6bde9-138">Si une opération BACKUP continue après la survenue d'erreurs, l'opération effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bde9-138">If a BACKUP operation continues after encountering errors, the operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="6bde9-139">Marque le jeu de sauvegarde sur le support de sauvegarde comme contenant des erreurs et trace la page dans la table **suspect_pages** de la base de données **msdb** .</span><span class="sxs-lookup"><span data-stu-id="6bde9-139">Flags the backup set on the backup media as containing errors and tracks the page in the **suspect_pages** table in the **msdb** database.</span></span> <span data-ttu-id="6bde9-140">Pour plus d’informations, consultez [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6bde9-140">For more information, see [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span></span>  
  
2.  <span data-ttu-id="6bde9-141">Consigne l'erreur dans le journal des erreurs SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6bde9-141">Logs the error in the SQL Server error log.</span></span>  
  
3.  <span data-ttu-id="6bde9-142">Marque le jeu de sauvegarde comme contenant ce type d’erreur (dans la colonne **is_damaged** de **msdb.backupset**).</span><span class="sxs-lookup"><span data-stu-id="6bde9-142">Marks the backup set as containing this type of error (in the **is_damaged** column of **msdb.backupset)**.</span></span> <span data-ttu-id="6bde9-143">Pour plus d’informations, consultez [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6bde9-143">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
4.  <span data-ttu-id="6bde9-144">Émet un message indiquant que la sauvegarde a été correctement générée, mais qu'elle contient des erreurs de page.</span><span class="sxs-lookup"><span data-stu-id="6bde9-144">Issues a message that the backup was successfully generated, but contains page errors.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6bde9-145">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="6bde9-145">Related Tasks</span></span>  
 <span data-ttu-id="6bde9-146">**Pour activer ou désactiver les sommes de contrôle de sauvegarde**</span><span class="sxs-lookup"><span data-stu-id="6bde9-146">**To enable or disable backup checksums**</span></span>  
  
-   [<span data-ttu-id="6bde9-147">Activer ou désactiver des sommes de contrôle de sauvegarde au cours d’opérations de sauvegarde ou de restauration &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6bde9-147">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 <span data-ttu-id="6bde9-148">**Pour contrôler la réponse à une erreur lors d'une opération de sauvegarde**</span><span class="sxs-lookup"><span data-stu-id="6bde9-148">**To control the response to a error during a backup operation**</span></span>  
  
-   [<span data-ttu-id="6bde9-149">Spécifier si une opération de sauvegarde ou de restauration continue ou s’arrête après la survenue d’une erreur &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6bde9-149">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a><span data-ttu-id="6bde9-150"> Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bde9-150">See Also</span></span>  
 <span data-ttu-id="6bde9-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bde9-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="6bde9-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bde9-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6bde9-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bde9-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="6bde9-154">[Jeux de supports de sauvegarde en miroir &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bde9-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 <span data-ttu-id="6bde9-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bde9-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="6bde9-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6bde9-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  