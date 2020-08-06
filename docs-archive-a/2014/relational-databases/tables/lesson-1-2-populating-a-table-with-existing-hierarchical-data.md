---
title: Remplissage d’une table avec des données hiérarchiques existantes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966548b11ad4697abc06de5c5c239a511f80b7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696704"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a>Remplissage d'une table avec des données hiérarchiques existantes
   Cette tâche crée une table et la remplit avec les données de la table **EmployeeDemo**. Les étapes de cette tâche sont les suivantes :  
  
-   Créez une nouvelle table qui contient une colonne `hierarchyid`. Cette colonne pourrait remplacer les colonnes **EmployeeID** et **ManagerID** existantes. Toutefois, vous conserverez ces colonnes. Cela s'explique par le fait que les applications existantes peuvent faire référence à ces colonnes. De même, cela peut vous aider à comprendre les données après le transfert. La définition de table spécifie que **OrgNode** est la clé primaire, ce qui exige que la colonne contienne des valeurs uniques. L’index cluster sur la colonne **OrgNode** stockera la date dans la séquence **OrgNode** .  
  
-   Créez une table temporaire utilisée pour effectuer le suivi du nombre d'employés dont chaque responsable est le supérieur direct.  
  
-   Remplissez la nouvelle table en utilisant les données de la table **EmployeeDemo** .  
  
### <a name="to-create-a-new-table-named-neworg"></a>Pour créer une table nommée NewOrg  
  
-   Dans une fenêtre de l’Éditeur de requête, exécutez le code suivant pour créer une table nommée **HumanResources.NewOrg**:  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a>Pour créer une table temporaire nommée #Children  
  
1.  Créez une table temporaire nommée **#Children** avec une colonne nommée **Num** qui contiendra le nombre d’enfants pour chaque nœud :  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Ajoutez un index qui accélérera considérablement la requête qui remplit la table **NewOrg** :  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a>Pour remplir la table NewOrg  
  
1.  Les requêtes récursives interdisent les sous-requêtes avec agrégats. À la place, remplissez la table **#Children** avec le code suivant, qui utilise la méthode [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) pour remplir la colonne **Num** :  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  Examinez la table **#Children** . Notez la façon dont la colonne **Num** contient des numéros séquentiels pour chaque responsable.  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  Remplissez la table **NewOrg** . Utilisez les méthodes GetRoot et ToString pour concaténer les valeurs **num** au `hierarchyid` format, puis mettez à jour la colonne **OrgNode** avec les valeurs hiérarchiques résultantes :  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  Une colonne `hierarchyid` est plus compréhensible lorsque vous la convertissez au format caractère. Vérifiez les données de la table **NewOrg** en exécutant le code suivant, qui contient deux représentations de la colonne **OrgNode** :  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     La colonne **LogicalNode** convertit la `hierarchyid` colonne en un format de texte plus lisible qui représente la hiérarchie. Dans les tâches restantes, vous utiliserez la méthode `ToString()` pour afficher le format logique des colonnes `hierarchyid`.  
  
5.  Supprimez la table temporaire, qui n'est plus nécessaire :  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 La tâche suivante créera des index pour prendre en charge la structure hiérarchique.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Optimisation de la table NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
