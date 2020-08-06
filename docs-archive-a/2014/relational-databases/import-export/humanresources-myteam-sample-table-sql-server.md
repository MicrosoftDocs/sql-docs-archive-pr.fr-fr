---
title: Exemple de table HumanResources.myTeam (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612337"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>Exemple de table HumanResources.myTeam (SQL Server)
  Les exemples de code fournis au chapitre [Importation et exportation de données en bloc](bulk-import-and-export-of-data-sql-server.md) font généralement appel à une table de test spéciale nommée **myTeam**. Pour pouvoir mettre à exécution les exemples, vous devez d’abord créer la table **myTeam** dans le schéma **HumanResources** de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est l’un des exemples de bases de données fournis dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 La table **myTeam** contient les colonnes suivantes.  
  
|Colonne|Type de données|Possibilité de valeurs nulles|Description|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|`smallint`|Non Null|Clé primaire des lignes. EmployeeID d'un membre de l'équipe.|  
|**Nom**|`nvarchar(50)`|Non Null|Name est un membre de l'équipe.|  
|**Titre**|`nvarchar(50)`|Nullable|Fonction occupée par l'employé au sein de l'équipe.|  
|**Contexte**|`nvarchar(50)`|Non Null|Date et heure de dernière mise à jour de la ligne (Par défaut)|  
  
 **Pour créer HumanResources.myTeam**  
  
-   Utilisez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes :  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 **Pour remplir HumanResources.myTeam**  
  
-   Exécutez les instructions `INSERT` suivantes pour remplir la table de deux lignes :  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  Ces instructions ignorent la quatrième colonne, `Background`. Celle-ci a une valeur par défaut. En l'ignorant, l'instruction `INSERT` laisse cette colonne vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)  
  
  
