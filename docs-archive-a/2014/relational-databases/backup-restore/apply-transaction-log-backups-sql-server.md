---
title: Appliquer les sauvegardes du journal de transactions (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c91106f8ca6f15539b4103220860143882c3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604591"
---
# <a name="apply-transaction-log-backups-sql-server"></a>Appliquer les sauvegardes du journal de transactions (SQL Server)
  Cette rubrique concerne uniquement le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions.  
  
 Cette rubrique décrit l'application de sauvegardes du journal des transaction dans le cadre de la restauration d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Dans cette rubrique :**  
  
-   [Conditions requises pour la restauration des sauvegardes du journal des transactions](#Requirements)  
  
-   [Récupération et journaux des transactions](#RecoveryAndTlogs)  
  
-   [Utilisation des sauvegardes du journal des transactions pour effectuer une restauration jusqu'au point d'échec](#PITrestore)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a>Conditions requises pour la restauration des sauvegardes du journal des transactions  
 Pour appliquer une sauvegarde du journal des transactions, les conditions suivantes doivent être remplies :  
  
-   **Sauvegardes de journal en nombre suffisant pour une séquence de restauration :** Vous devez disposer de suffisamment d'enregistrements de journal sauvegardés pour exécuter une séquence de restauration. Les sauvegardes de journal nécessaires, notamment la [sauvegarde de la fin du journal](tail-log-backups-sql-server.md) le cas échéant, doivent être disponibles avant le début de la séquence de restauration.  
  
-   **Ordre de restauration correct :**  La sauvegarde différentielle ou la sauvegarde complète de base de données effectuée juste avant doit d'abord être restaurée. Puis, tous les journaux de transactions créés après cette sauvegarde complète ou différentielle de base de données doivent être restaurés dans l'ordre chronologique. Si une sauvegarde du journal des transactions dans cette séquence de journaux de transactions consécutifs est perdue ou endommagée, vous ne pouvez restaurer que les journaux des transactions antérieurs au journal des transactions manquant.  
  
-   **Base de données pas encore récupérée :**  La base de données ne peut pas être récupérée tant que le dernier journal des transactions n'a pas été appliqué. Si vous récupérez la base de données après avoir restauré l'une des sauvegardes du journal des transactions intermédiaires, c'est-à-dire avant la fin de la séquence de journaux de transactions consécutifs, vous ne pouvez pas restaurer la base de données au-delà de ce point sans redémarrer toute la séquence de restauration, en commençant par la sauvegarde complète de base de données.  
  
    > [!TIP]  
    >  Il est recommandé de restaurer toutes les sauvegardes des journaux (RESTORE LOG *nom_base_de_données* WITH NORECOVERY). Ensuite, après la restauration de la dernière sauvegarde du journal, récupérez la base de données dans une opération séparée (RESTORE DATABASE *nom_base_de_données* WITH RECOVERY).  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a>Récupération et journaux des transactions  
 Lorsque vous terminez l'opération de restauration et récupérez la base de données, la récupération annule toutes les transactions incomplètes. Cette phase se nomme *phase de restauration*. Cette opération est nécessaire pour restaurer l'intégrité de la base de données. Après la restauration, la base de données passe en ligne, et aucune autre sauvegarde du journal des transactions ne peut être appliquée à la base de données.  
  
 Par exemple, une série de sauvegardes du journal des transactions contient une transaction longue. Le démarrage de la transaction est enregistré dans la première sauvegarde du journal des transactions, mais la fin de la transaction est enregistrée dans la seconde sauvegarde du journal des transactions. Il n’y a pas d'enregistrement d’une opération de validation ou de restauration dans la première sauvegarde du journal des transactions. Si une opération de récupération est exécutée lors de l'application de la première sauvegarde du journal des transactions, la longue transaction est traitée comme incomplète, et les modifications de données enregistrées dans la première sauvegarde du journal des transactions pour la transaction sont restaurées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas l'application de la deuxième sauvegarde du journal des transactions après ce stade.  
  
> [!NOTE]  
>  Dans certains cas, vous pouvez ajouter un fichier de façon explicite pendant la restauration du journal.  
  
##  <a name="using-log-backups-to-restore-to-the-point-of-failure"></a><a name="PITrestore"></a>Utilisation des sauvegardes de journaux pour restaurer jusqu’au point de défaillance  
 Supposons la séquence d'événements suivante.  
  
|Temps|Événement|  
|----------|-----------|  
|8h00|Sauvegardez la base de données pour créer une sauvegarde complète de base de données.|  
|Midi|Sauvegarde du journal des transactions.|  
|16h00|Sauvegarde du journal des transactions.|  
|18h00|Sauvegardez la base de données pour créer une sauvegarde complète de base de données.|  
|20h00|Sauvegarde du journal des transactions.|  
|21h45|Une défaillance se produit.|  
  
> [!NOTE]  
>  Pour une explication de cet exemple de cette séquence de sauvegardes, consultez [Sauvegardes des journaux de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).  
  
 Pour restaurer la base de données à son état à 21:45 (point d'échec), les autres procédures suivantes peuvent être utilisées :  
  
 **Solution 1 : restaurer la base de données en utilisant la sauvegarde complète de base de données la plus récente**  
  
1.  Créez une sauvegarde de la fin du journal du journal des transactions actuellement actif comme point d'échec.  
  
2.  Ne restaurez pas la sauvegarde complète de base de données de 18h00. Restaurez plutôt la sauvegarde complète de base de données la plus récente de 18h00, puis appliquez la sauvegarde du journal de 20h00 et la sauvegarde de la fin du journal.  
  
 **Solution 2 : restaurer la base de données en utilisant une sauvegarde complète de base de données antérieure**  
  
> [!NOTE]  
>  Cette autre solution est utile si un problème vous empêche d'utiliser la sauvegarde complète de base de données de 18h00. Ce processus prend plus de temps que la restauration de la sauvegarde complète de base de données de 18h00.  
  
1.  Créez une sauvegarde de la fin du journal du journal des transactions actuellement actif comme point d'échec.  
  
2.  Restaurez la sauvegarde complète de base de données de 8h00, puis restaurez dans l'ordre les quatre sauvegardes du journal des transactions. Cette procédure restaure par progression toutes les transactions achevées jusqu'à 21h45.  
  
     Cette solution souligne la sécurité redondante offerte par le maintien d'une séquence de sauvegardes de journaux de transactions dans une série de sauvegardes complètes de base de données.  
  
> [!NOTE]  
>  Dans certains cas, vous pouvez utiliser des journaux de transactions pour restaurer une base de données à un point spécifique dans le temps. Pour plus d’informations, consultez [Restaurer une base de données SQL Server jusqu’à une limite dans le temps &#40;mode de récupération complète&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour appliquer une sauvegarde du journal des transactions**  
  
-   [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
 **Pour effectuer une restauration au point de récupération**  
  
-   [Restaurer une base de données jusqu’au point d’échec en mode de récupération complète &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Restaurer une base de données SQL Server jusqu’à une limite dans le temps &#40;mode de récupération complète&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)  
  
-   [Récupération de bases de données associées contenant une transaction marquée](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [Récupérer un numéro séquentiel dans le journal &#40;SQL Server&#41;](recover-to-a-log-sequence-number-sql-server.md)  
  
 **Pour récupérer une base de données après la restauration de sauvegardes à l'aide de WITH NORECOVERY**  
  
-   [Récupérer une base de données sans restaurer les données &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des transactions &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)  
  
  
