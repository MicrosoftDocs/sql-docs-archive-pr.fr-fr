---
title: Supprimer ou désactiver des déclencheurs DML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 39b345ade1258987df06938791ac0024e8612365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613888"
---
# <a name="delete-or-disable-dml-triggers"></a>Supprimer ou désactiver les déclencheurs DML
  Cette rubrique explique comment supprimer ou désactiver un déclencheur DML dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer ou désactiver un déclencheur DML à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   La suppression d'un déclencheur entraîne sa suppression définitive de la base de données actuelle. La table et les données sur lesquelles il est basé ne sont pas affectées. La suppression d'une table supprime automatiquement les déclencheurs qui lui sont associés.  
  
-   Un déclencheur est activé par défaut lors de sa création.  
  
-   La désactivation d'un déclencheur ne le supprime pas. Le déclencheur existe toujours en tant qu'objet dans la base de données actuelle. Il ne s'activera toutefois pas lors de l'exécution d'une instruction INSERT, UPDATE ou DELETE pour laquelle il avait été programmé. Tout déclencheur désactivé peut être à nouveau réactivé. Un déclencheur n'est pas recréé par son activation. Le déclencheur est activé de la même manière que lorsqu'il a été initialement créé.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 La suppression d'un déclencheur DML nécessite une autorisation ALTER sur la table ou la vue sur laquelle le déclencheur est défini.  
  
 Pour désactiver ou activer un déclencheur DML, un utilisateur doit avoir au minimum l'autorisation ALTER pour la table ou la vue sur laquelle le déclencheur a été créé.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-dml-trigger"></a>Pour supprimer un déclencheur DML  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez la base de données choisie, développez **Tables**, puis développez la table qui contient le déclencheur que vous souhaitez supprimer.  
  
3.  Développez **Déclencheurs**, cliquez avec le bouton droit sur le déclencheur à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que le déclencheur correct est spécifié et cliquez sur **OK**.  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Pour désactiver et activer un déclencheur DML  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez la base de données choisie, développez **Tables**, puis développez la table qui contient le déclencheur que vous souhaitez désactiver.  
  
3.  Développez **Déclencheurs**, cliquez avec le bouton droit sur le déclencheur à désactiver, puis cliquez sur **Désactiver**.  
  
4.  Pour activer le déclencheur, cliquez sur **Activer**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-dml-trigger"></a>Pour supprimer un déclencheur DML  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête. Exécutez l'instruction [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) pour créer le déclencheur `Sales.bonus_reminder` . Pour supprimer le déclencheur, exécutez l'instruction [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) .  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Pour désactiver et activer un déclencheur DML  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête. Exécutez l'instruction [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) pour créer le déclencheur `Sales.bonus_reminder` . Pour désactiver et activer le déclencheur, exécutez les instructions [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) et [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) , respectivement.  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)   
 [Obtenir des informations sur les déclencheurs DML](dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql)   
 [sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql)   
 [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)   
 [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)   
 [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
