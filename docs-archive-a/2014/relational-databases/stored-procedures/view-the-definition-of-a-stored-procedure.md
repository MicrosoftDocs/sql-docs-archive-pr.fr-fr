---
title: Afficher la définition d’une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4da455d38f984b08ee1f396f26cd4cc85411be92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605328"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>Afficher la définition d'une procédure stockée
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a>Vous pouvez afficher la définition d’une procédure stockée dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] à l’aide des options du menu de l’Explorateur d’objets ou dans l’éditeur de requête à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Cette rubrique décrit comment afficher la définition de la procédure dans l'Explorateur d'objets et en utilisant une procédure stockée système, une fonction système et un affichage catalogue d'objets dans l'éditeur de requête.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour afficher la définition d'une procédure, à l'aide de :**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Procédure stockée système : `sp_helptext`  
 Nécessite l'appartenance au rôle **public** . Les définitions de l'objet système sont visibles publiquement. La définition des objets utilisateur est visible par le propriétaire de l’objet ou les bénéficiaires de l’une des autorisations suivantes : ALTER, CONTROL, TAKE OWNERSHIP ou VIEW DEFINITION.  
  
 Fonction système : `OBJECT_DEFINITION`  
 Les définitions de l'objet système sont visibles publiquement. La définition des objets utilisateur est visible par le propriétaire de l’objet ou les bénéficiaires de l’une des autorisations suivantes : ALTER, CONTROL, TAKE OWNERSHIP ou VIEW DEFINITION. Ces autorisations sont implicitement possédées par des membres des rôles de base de données fixes **db_owner**, **db_ddladmin**et **db_securityadmin** .  
  
 Affichage catalogue d'objets : `sys.sql_modules`  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées. Pour plus d'informations, consultez [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> Comment afficher la définition d'une procédure stockée  
 Vous pouvez utiliser l'un des éléments suivants :  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher la définition d'une procédure dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  Développez **Procédures stockées**, cliquez avec le bouton de droite sur la procédure, puis cliquez sur **Script de procédure stockée en tant que**, puis cliquez sur l'une des options suivantes : **Créer dans**, **Modifier dans** ou **Déposer et créer dans**.  
  
4.  Sélectionnez **Nouvelle fenêtre d’éditeur de requête**. Cette action affiche la définition de la procédure.  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher la définition d'une procédure dans l'éditeur de requête**  
  
 Procédure stockée système : `sp_helptext`  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez l'instruction suivante qui utilise la procédure stockée système `sp_helptext`. Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 Fonction système : `OBJECT_DEFINITION`  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent la fonction système `OBJECT_DEFINITION`. Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Affichage catalogue d'objets : `sys.sql_modules`  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent l'affichage catalogue `sys.sql_modules`. Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une procédure stockée](create-a-stored-procedure.md)   
 [Modifier une procédure stockée](modify-a-stored-procedure.md)   
 [Supprimer une procédure stockée](delete-a-stored-procedure.md)   
 [Renommer une procédure stockée](rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)   
 [OBJECT_ID &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-id-transact-sql)  
  
  
