---
title: Créer des clés primaires | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
ms.openlocfilehash: c515ef8f978b41225ff45e87646b0aa7a9706a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615093"
---
# <a name="create-primary-keys"></a>Créer des clés primaires
  Vous pouvez définir une clé primaire dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. La création d'une clé primaire crée automatiquement un correspondant unique, index cluster ou non-cluster.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une clé primaire à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Une table ne peut contenir qu'une seule contrainte PRIMARY KEY.  
  
-   Toutes les colonnes définies dans une contrainte PRIMARY KEY doivent avoir la valeur NOT NULL. Si vous ne spécifiez pas la possibilité ou non de valeurs NULL, toutes les colonnes participant à une contrainte PRIMARY KEY sont définies à NOT NULL.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 La création d'une nouvelle table avec une clé primaire nécessite une autorisation CREATE TABLE dans la base de données et une autorisation ALTER pour le schéma dans lequel la table a été créée.  
  
 La création d'une clé primaire dans une table existante nécessite l'autorisation ALTER sur la table.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-primary-key"></a>Pour créer une clé primaire  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table à laquelle vous souhaitez ajouter une contrainte unique, puis cliquez sur **conception**.  
  
2.  Dans le **Concepteur de tables**, cliquez sur le sélecteur de ligne correspondant à la colonne de base de données que vous voulez définir comme clé primaire. Si vous voulez sélectionner plusieurs colonnes, appuyez sur la touche CTRL et, tout en la maintenant enfoncée, cliquez sur les sélecteurs de ligne des autres colonnes.  
  
3.  Cliquez avec le bouton droit sur le sélecteur de ligne de la colonne et cliquez sur **Définir la clé primaire**.  
  
> [!CAUTION]  
>  Si vous voulez redéfinir la clé primaire, vous devez supprimer toutes les relations avec la clé primaire existante avant de pouvoir créer la nouvelle clé primaire. Un message vous avertira que les relations existantes seront automatiquement supprimées dans le cadre de ce processus.  
  
 Une colonne clé primaire est identifiée par un symbole de clé primaire dans son sélecteur de ligne.  
  
 Si une clé primaire comporte plusieurs colonnes, les doublons sont autorisés dans une colonne, mais chaque combinaison de valeurs provenant de toutes les colonnes de la clé primaire doit être unique.  
  
 Si vous définissez une clé composée, l'ordre des colonnes dans la clé primaire correspond à l'ordre des colonnes de la table. Vous pouvez cependant modifier l'ordre des colonnes après la création de la clé primaire. Pour plus d’informations, consultez [Modifier des clés primaires](modify-primary-keys.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a>Pour créer une clé primaire dans une table existante  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une clé primaire sur la colonne `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a>Pour créer une clé primaire dans une nouvelle table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une table et affecte une clé primaire sur la colonne `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) et [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
###  <a name="TsqlExample"></a>  
