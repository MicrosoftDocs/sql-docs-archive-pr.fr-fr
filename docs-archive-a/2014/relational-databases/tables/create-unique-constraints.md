---
title: Créer des contraintes uniques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 252de63f965f98734a6d62d94bfff9dc5774cab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706355"
---
# <a name="create-unique-constraints"></a>Créer des contraintes uniques
  Vous pouvez créer une contrainte unique dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)] pour interdire l'entrée de doublons dans des colonnes spécifiques qui ne participent pas à une clé primaire. La création d'une contrainte unique crée automatiquement un index unique correspondant.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer une contrainte unique à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-unique-constraint"></a>Pour créer une contrainte unique  
  
1.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table à laquelle vous souhaitez ajouter une contrainte unique et cliquez sur **Conception**.  
  
2.  Dans le menu **Concepteur de tables** , cliquez sur **index/clés**.  
  
3.  Dans la boîte de dialogue **Index/Clés** , cliquez sur **Ajouter**.  
  
4.  Dans la grille sous **Général**, cliquez sur **Type** et choisissez **Clé unique** dans la zone de liste déroulante située à droite de la propriété.  
  
5.  Dans le menu **Fichier**, cliquez sur **Enregistrer**_nom de la table_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-unique-constraint"></a>Pour créer une contrainte unique  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée la table `TransactionHistoryArchive4` et une contrainte unique sur la colonne `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a>Pour créer une contrainte unique sur une table existante  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une contrainte unique sur les colonnes `PasswordHash` et `PasswordSalt` dans la table `Person.Password`.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a>Pour créer une contrainte unique sur une nouvelle table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une table et définit une contrainte unique sur la colonne `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) et [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
###  <a name="TsqlExample"></a>  
