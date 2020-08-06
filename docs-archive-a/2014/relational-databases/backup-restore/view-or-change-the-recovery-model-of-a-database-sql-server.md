---
title: Afficher ou modifier le mode de récupération d’une base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889080301109938f0514bd6b81265c100237ab60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703012"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a>Afficher ou modifier le mode de récupération d'une base de données (SQL Server)
  Cette rubrique explique comment afficher ou modifier le mode de récupération d'une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un *mode de récupération* est une propriété de base de données qui contrôle la façon dont les transactions sont journalisées, précise si le journal des transactions nécessite (et permet) une sauvegarde et spécifie les types d’opérations de restauration disponibles. Il existe trois modes de récupération : simple, complète et utilisant les journaux de transactions. En règle générale, une base de données utilise le mode de restauration complète ou le mode de récupération simple. Il est possible de modifier le mode de récupération d'une base de données à tout moment. La base de données **model** définit le mode de récupération par défaut des nouvelles bases de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou modifier le mode de récupération d'une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Recommandations de suivi :**  [Après avoir modifié le mode de récupération](#FollowUp)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Avant de passer en mode de récupération complète ou en mode de récupération utilisant les journaux de transactions, sauvegardez le journal des transactions.  
  
-   La récupération jusqu'à une date et heure n'est pas possible dans le mode de récupération utilisant les journaux de transactions. Par conséquent, si vous exécutez des transactions en mode de récupération utilisant les journaux de transactions, pouvant nécessiter une restauration du journal des transactions, ces transactions peuvent être exposées à des pertes de données. Pour optimiser la possibilité de récupérer les données dans un scénario de récupération après sinistre, nous vous recommandons de passer au mode de récupération utilisant les journaux de transactions dans les conditions suivantes :  
  
    -   Les utilisateurs ne sont pas actuellement autorisés dans la base de données.  
  
    -   Toutes modifications effectuées au cours du traitement en bloc sont récupérables sans une restauration du journal en réexécutant, par exemple, les processus en bloc.  
  
     Si ces deux conditions sont satisfaites, vous ne serez pas exposé à des pertes de données lors d'une restauration du journal des transactions sauvegardé en mode de récupération utilisant les journaux de transactions.  
  
> [!NOTE]  
>  Si vous adoptez le mode de récupération complète pendant une opération en bloc, la journalisation des opérations en bloc passe de la journalisation minimale à la journalisation complète, et inversement.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-recovery-model"></a>Pour afficher ou modifier le mode de récupération  
  
1.  Après vous être connecté à l'instance appropriée du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit de la souris sur la base de données, puis cliquez sur **Propriétés**pour ouvrir la boîte de dialogue **Propriétés de la base de données** .  
  
4.  Dans le volet **Sélectionner une page** , cliquez sur **Options**.  
  
5.  Le mode de récupération actuel s'affiche dans la zone de liste **Mode de récupération** .  
  
6.  Au besoin, pour modifier le mode de récupération, sélectionnez un autre mode dans la liste. Les choix sont **Complet**, **Journalisé en bloc**ou **Simple**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-the-recovery-model"></a>Pour afficher le mode de récupération  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment interroger l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) pour connaître le mode de récupération de la base de données **model** .  
  
```sql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a>Pour modifier le mode de récupération  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment modifier le mode de récupération de la base de données `model` en `FULL` à l'aide de l'option `SET RECOVERY` de l'instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) .  
  
```sql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="follow-up-recommendations-after-you-change-the-recovery-model"></a><a name="FollowUp"></a>Recommandations de suivi : après avoir modifié le mode de récupération  
  
-   **Après un changement de mode de récupération complète ou de mode de récupération utilisant les journaux de transactions**  
  
    -   Repassez immédiatement en mode de récupération complète après avoir effectué les opérations en bloc.  
  
    -   Après être passé du mode de récupération utilisant les journaux de transactions au mode de récupération complète, sauvegardez le journal.  
  
        > [!NOTE]  
        >  Votre stratégie de sauvegarde ne change pas : continuez à effectuer régulièrement des sauvegardes des bases de données, des sauvegardes des journaux et des sauvegardes différentielles.  
  
-   **Après basculement à partir du mode de récupération simple**  
  
    -   Aussitôt après être passé en mode de restauration complète ou en mode de récupération utilisant les journaux de transactions, procédez à une sauvegarde de base de données complète ou différentielle pour lancer la séquence de journaux.  
  
        > [!NOTE]  
        >  Le passage au mode de restauration complète ou mode de récupération utilisant les journaux de transactions n'est effectif qu'après la première sauvegarde de base de données.  
  
    -   Planifiez des sauvegardes de journaux régulières et mettez à jour votre plan de restauration en conséquence.  
  
        > [!IMPORTANT]  
        >  Si vous ne sauvegardez pas assez souvent le journal, il est susceptible de s'étendre jusqu'à manquer de l'espace disque nécessaire.  
  
-   **Après basculement en mode de récupération simple**  
  
    -   Mettez fin à tous les travaux planifiés afin de sauvegarder le journal des transactions.  
  
    -   Assurez-vous que des sauvegardes des bases de données régulières sont planifiées. La sauvegarde de votre base de données est essentielle pour protéger vos données et tronquer la partie inactive du journal des transactions.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Créer un travail](../../ssms/agent/create-a-job.md)  
  
-   [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   [Plans de maintenance de base de données](../maintenance-plans/maintenance-plans.md) (dans la documentation en ligne de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] )  
  
## <a name="see-also"></a> Voir aussi  
 [Modes de récupération &#40;SQL Server&#41;](recovery-models-sql-server.md)   
 [Journal des transactions &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [Modes de récupération &#40;SQL Server&#41;](recovery-models-sql-server.md)  
  
  
