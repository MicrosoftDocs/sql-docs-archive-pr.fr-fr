---
title: Étude de la structure actuelle de la table Employee | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7f63773ebc1f28fb24f8f1000c3f87ee4d50544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599848"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a>Étude de la structure actuelle de la table Employee
   L’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] contient une table **Employee** dans le schéma **HumanResources**. Afin d'éviter de modifier la table d'origine, cette étape effectue une copie de la table **Employee** , nommée **EmployeeDemo**. Pour simplifier l'exemple, vous ne copiez que cinq colonnes de la table d'origine. Ensuite, vous interrogez la table **HumanResources. EmployeeDemo** pour vérifier comment les données sont structurées dans une table sans utiliser le `hierarchyid` type de données.  
  
### <a name="to-copy-the-employee-table"></a>Pour copier la table Employee  
  
1.  Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour copier la structure et les données de la table **Employee** dans une nouvelle table nommée **EmployeeDemo**.  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>Pour examiner la structure et les données de la table EmployeeDemo  
  
-   Cette nouvelle table **EmployeeDemo** représente une table classique dans une base de données existante que vous pouvez souhaiter migrer vers une nouvelle structure. Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour voir comment la table utilise une jointure réflexive pour afficher les relations employé/responsable :  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     Les résultats se poursuivent pour un total de 290 lignes.  
  
 Notez que le résultat de la clause `ORDER BY` a provoqué le regroupement des subordonnés directs de chaque niveau de gestion. Par exemple, les sept subordonnés directs de **MgrID** 3 (roberto0) sont regroupés les uns à côté des autres. Il est beaucoup plus difficile, bien que pas impossible, de regrouper tous ceux dont **MgrID** 3 est le supérieur final.  
  
 Dans la tâche suivante, nous créerons une table avec un type de données `hierarchyid` et déplacerons les données dans la nouvelle table.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Remplissage d'une table avec des données hiérarchiques existantes](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
