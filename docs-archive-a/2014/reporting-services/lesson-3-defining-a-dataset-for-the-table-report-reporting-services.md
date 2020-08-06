---
title: 'Leçon 3 : définition d’un dataset destiné à un rapport de table (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603306"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Leçon 3 : définition d'un dataset destiné à un rapport de table (Reporting Services)
  Après avoir défini une source de données, vous devez spécifier un dataset. Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les données utilisées par les rapports sont contenues dans des *datasets*. Les datasets contiennent un pointeur qui renvoient à la source des données, la requête que doit utiliser le rapport ainsi que des champs et variables calculées.  
  
 Le Concepteur de requêtes du Concepteur de rapports permet de définir des requêtes. Pour ce didacticiel, vous allez créer une requête qui extrait les informations sur les commandes à partir de la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de données **2008** .  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>Pour définir une requête Transact-SQL pour les données du rapport  
  
1.  Dans le volet **données du rapport** , cliquez sur **nouveau**, puis sur **DataSet...**. La boîte de dialogue **Propriétés du DataSet** s’ouvre.  
  
2.  Dans la zone **Nom** , tapez **AdventureWorksDataset**.  
  
3.  Cliquez sur **Utiliser un dataset incorporé dans mon rapport**.  
  
4.  Assurez-vous que le nom de votre source de données, AdventureWorks2012, se trouve dans la zone de texte **source de données** , et que le **type de requête** est **texte**.  
  
5.  Tapez ou copiez et collez la requête Transact-SQL ci-après dans la zone **Requête** .  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  (Facultatif) Cliquez sur le bouton **Concepteur de requêtes** . La requête est affichée dans le Concepteur de requêtes textuel. Vous pouvez utiliser le concepteur de requêtes graphique en cliquant sur l’option **Modifier en tant que texte**. Affichez les résultats de la requête en cliquant sur le bouton exécuter **( !)** dans la barre d’outils du concepteur de requêtes.  
  
     Vous pouvez consulter les données contenues dans six champs à partir de quatre tables différentes de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . La requête utilise des fonctionnalités Transact-SQL telles que des alias. Par exemple, la table SalesOrderHeader est intitulée soh.  
  
     Cliquez sur **OK** pour quitter le Concepteur de requêtes.  
  
7.  Cliquez sur **OK** pour quitter la boîte de dialogue **Propriétés du dataset** .  
  
     Les champs et votre dataset **AdventureWorksDataset** s’affichent dans le volet des données de rapport.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de spécifier une requête qui permet d'extraire les données pour votre rapport. Vous allez ensuite créer la disposition du rapport. Consultez [Leçon 4 : ajout d’une table au rapport &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de conception de requête dans Concepteur de rapports SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [Type de connexion SQL Server &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [Tutoriel : Écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
