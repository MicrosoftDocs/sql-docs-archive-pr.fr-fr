---
title: Supprimer une base de données secondaire dans une configuration de la copie des journaux de transaction (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 119f2762d41d0787b6b3279507e9671e89fddfca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611271"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a>Supprimer une base de données secondaire dans une configuration de copie des journaux de transaction (SQL Server)
  Cette rubrique explique comment supprimer la base de données secondaire de copie des journaux de transaction dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une base de données secondaire de copie des journaux de transaction, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les procédures stockées de copie des journaux de transaction nécessitent l’appartenance au rôle serveur fixe **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a>Pour supprimer une base de données secondaire pour la copie des journaux de transaction  
  
1.  Connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est actuellement le serveur principal de copie des journaux de transaction et développez-la.  
  
2.  Développez **Bases de données**, cliquez avec le bouton droit sur la base de données primaire de copie des journaux de transaction, puis cliquez sur **Propriétés**.  
  
3.  Sous **Sélectionner une page**, cliquez sur **Envoi de journaux de transaction**.  
  
4.  Sous **Instances de serveurs et bases de données secondaires**, cliquez sur la base de données à supprimer.  
  
5.  Cliquez sur **Supprimer**.  
  
6.  Cliquez sur **OK** pour mettre à jour la configuration.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-remove-a-secondary-database"></a>Pour supprimer une base de données secondaire  
  
1.  Sur le serveur principal, exécutez [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) pour supprimer du serveur principal les informations relatives à la base de données secondaire.  
  
2.  Sur le serveur secondaire, exécutez [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) pour supprimer la base de données secondaire.  
  
    > [!NOTE]  
    >  Si aucune autre base de données secondaire portant le même ID secondaire n’existe, **sp_delete_log_shipping_secondary_primary** est appelé par **sp_delete_log_shipping_secondary_database** et supprime l’entrée de l’ID secondaire, ainsi que les travaux de copie et de restauration.  
  
3.  Sur le serveur secondaire, désactivez les travaux de copie et de restauration. Pour plus d’informations, consultez [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Mise à niveau de la copie des journaux de transaction vers SQL Server 2014 &#40;Transact-SQL&#41;](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Configurer la copie des journaux de transaction &#40;Transact-SQL&#41;](configure-log-shipping-sql-server.md)  
  
-   [Ajouter une base de données secondaire dans une configuration de copie des journaux de transaction &#40;SQL Server&#41;](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [Supprimer la copie des journaux de transaction &#40;SQL Server&#41;](remove-log-shipping-sql-server.md)  
  
-   [Afficher le rapport de la copie des journaux de transaction &#40;SQL Server Management Studio&#41;](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Surveiller la copie des journaux de transaction &#40;Transact-SQL&#41;](monitor-log-shipping-transact-sql.md)  
  
-   [Basculer vers un serveur secondaire d’envoi de journaux &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [Tables et procédures stockées liées à la copie des journaux de transaction](log-shipping-tables-and-stored-procedures.md)  
  
  
