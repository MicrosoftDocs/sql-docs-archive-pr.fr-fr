---
title: Modifier des colonnes (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610985"
---
# <a name="modify-columns-database-engine"></a>Modifier des colonnes (moteur de base de données)
  Vous pouvez modifier le type de données d'une colonne dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  La modification du type de données d'une colonne qui contient déjà des données peut entraîner la perte définitive des données lors de leur conversion en ce nouveau type. De plus, le code et les applications qui dépendent de la colonne modifiée peuvent échouer. Il peut s'agir de requêtes, de vues, de procédures stockées, de fonctions définies par l'utilisateur et d'applications clientes. Notez que ces défaillances se produisent en cascade. Par exemple, une procédure stockée qui appelle une fonction définie par l'utilisateur dépendant de la colonne modifiée peut échouer. Prenez toutes les précautions nécessaires avant de modifier une colonne.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier le type de données d'une colonne à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>Pour modifier le type de données d'une colonne  
  
1.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table contenant les colonnes dont vous souhaitez modifier l’échelle et cliquez sur **Conception**.  
  
2.  Sélectionnez la colonne pour laquelle vous souhaitez modifier le type de données.  
  
3.  Sous l’onglet **Propriétés des colonnes** , cliquez sur la cellule de grille correspondant à la propriété **Type de données** et choisissez un nouveau type de données dans la liste déroulante.  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer**_nom de la table_.  
  
> [!NOTE]  
>  Lorsque vous modifiez le type de données d'une colonne, le Concepteur de tables applique la longueur par défaut du type de données que vous avez sélectionné, même si vous en avez déjà spécifié une autre. Affectez toujours la valeur souhaitée comme longueur de type de données après avoir spécifié le type de données.  
  
> [!WARNING]  
>  Si vous tentez de modifier le type de données d'une colonne associée à d'autres tables, le Concepteur de tables vous demande de confirmer que la modification concerne également les colonnes d'autres tables.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>Pour modifier le type de données d'une colonne  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
  
