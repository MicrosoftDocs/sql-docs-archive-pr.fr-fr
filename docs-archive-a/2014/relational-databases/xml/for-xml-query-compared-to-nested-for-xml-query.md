---
title: Comparaison de la requête FOR XML et de la requête FOR XML imbriquée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], comparing query types
ms.assetid: 19225b4a-ee3f-47cf-8bcc-52699eeda32c
author: rothja
ms.author: jroth
ms.openlocfilehash: ca10060702d0c7e50f2be79310c55e177dca358d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710460"
---
# <a name="for-xml-query-compared-to-nested-for-xml-query"></a>Comparaison de la requête FOR XML et de la requête FOR XML imbriquée
  Cette rubrique compare une requête FOR XML d'un seul niveau à une requête FOR XML imbriquée. L'un des avantages liés à l'utilisation des requêtes FOR XML imbriquées est que vous pouvez spécifier une combinaison de données XML centrées sur l'attribut et centrées sur l'élément pour les résultats de requête. L'exemple suivant en offre une illustration.  
  
## <a name="example"></a>Exemple  
 La requête `SELECT` suivante extrait de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] des informations sur les catégories et les sous-catégories de produits. La requête ne contient aucune clause FOR XML imbriquée.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductCategory.ProductCategoryID,   
         ProductCategory.Name as CategoryName,  
         ProductSubCategory.ProductSubCategoryID,   
         ProductSubCategory.Name  
FROM     Production.ProductCategory, Production.ProductSubCategory  
WHERE    ProductCategory.ProductCategoryID = ProductSubCategory.ProductCategoryID  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
GO  
```  
  
 Voici le résultat partiel :  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory ProductSubCategoryID="1" Name="Mountain Bike"/>  
  <ProductSubCategory ProductSubCategoryID="2" Name="Road Bike"/>  
  <ProductSubCategory ProductSubCategoryID="3" Name="Touring Bike"/>  
</ProductCategory>  
...  
```  
  
 Si vous spécifiez la directive `ELEMENTS` dans la requête, vous recevez un résultat centré sur l'élément, comme le montre le fragment de résultat suivant :  
  
```  
<ProductCategory>  
  <ProductCategoryID>1</ProductCategoryID>  
  <CategoryName>Bike</CategoryName>  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <Name>Mountain Bike</Name>  
  </ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  </ProductSubCategory>  
</ProductCategory>  
```  
  
 Ensuite, supposons que vous souhaitez générer une hiérarchie XML qui combine des données XML centrées sur l'attribut et centrées sur l'élément, comme le montre le fragment suivant :  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 Dans le fragment précédent, les informations relatives aux catégories de produits, telles que l'ID de catégorie et le nom de catégorie, sont des attributs. Toutefois, les informations sur les sous-catégories sont centrées sur l'élément. Pour construire l'élément <`ProductCategory`>, vous pouvez écrire une requête `FOR XML`, comme l'illustre le code suivant :  
  
```  
SELECT ProductCategoryID, Name as CategoryName  
FROM Production.ProductCategory ProdCat  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 Voici le résultat obtenu :  
  
```  
< ProdCat ProductCategoryID="1" CategoryName="Bikes" />  
< ProdCat ProductCategoryID="2" CategoryName="Components" />  
< ProdCat ProductCategoryID="3" CategoryName="Clothing" />  
< ProdCat ProductCategoryID="4" CategoryName="Accessories" />  
```  
  
 Ensuite, pour construire les éléments <`ProductSubCategory`> imbriqués dans le document XML de votre choix, vous ajoutez une requête `FOR XML` imbriquée, comme le montre le code suivant :  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName  
        FROM   Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 Notez les points suivants par rapport à la requête ci-dessus :  
  
-   La requête `FOR XML` interne extrait des informations sur les sous-catégories de produits. La directive `ELEMENTS` est ajoutée à la requête `FOR XML` interne pour générer des données XML centrées sur l'élément, qui sont ajoutées aux données XML créées par la requête externe. Par défaut, la requête externe génère des données XML centrées sur l'attribut.  
  
-   Dans la requête interne, la directive `TYPE` est spécifiée de manière que le résultat soit de type **xml** . Si la directive `TYPE` n'est pas spécifiée, le résultat est de type `nvarchar(max)` et les données XML sont renvoyées sous la forme d'entités.  
  
-   La requête externe spécifie également la directive `TYPE` . Ainsi, le résultat de cette requête retourné au client est de type **xml** .  
  
 Voici le résultat partiel :  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 La requête suivante est simplement une extension de la requête précédente. Elle montre la hiérarchie complète des produits stockés dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Notamment :  
  
-   Les catégories de produits  
  
-   Les sous-catégories de produits dans chaque catégorie  
  
-   Les modèles de produits dans chaque sous-catégorie  
  
-   Les produits dans chaque modèle  
  
 La requête suivante peut s'avérer utile pour comprendre la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName,  
               (SELECT ProductModel.ProductModelID,   
                       ProductModel.Name as ModelName,  
                       (SELECT ProductID, Name as ProductName, Color  
                        FROM   Production.Product  
                        WHERE  Product.ProductModelID =   
                               ProductModel.ProductModelID  
                        FOR XML AUTO, TYPE)  
                FROM   (SELECT distinct ProductModel.ProductModelID,   
                               ProductModel.Name  
                        FROM   Production.ProductModel,   
                               Production.Product  
                        WHERE  ProductModel.ProductModelID =   
                               Product.ProductModelID  
                        AND    Product.ProductSubCategoryID =   
                               ProductSubCategory.ProductSubCategoryID)   
                                  ProductModel  
                FOR XML AUTO, type  
               )  
        FROM Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 Voici le résultat partiel :  
  
```  
<Production.ProductCategory ProductCategoryID="1" CategoryName="Bikes">  
  <Production.ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bikes</SubCategoryName>  
    <ProductModel ProductModelID="19" ModelName="Mountain-100">  
      <Production.Product ProductID="771"   
                ProductName="Mountain-100 Silver, 38" Color="Silver" />  
      <Production.Product ProductID="772"   
                ProductName="Mountain-100 Silver, 42" Color="Silver" />  
      <Production.Product ProductID="773"   
                ProductName="Mountain-100 Silver, 44" Color="Silver" />  
        ...  
    </ProductModel>  
     ...  
```  
  
 Si vous supprimez la directive `ELEMENTS` de la requête `FOR XML` imbriquée qui génère les sous-catégories de produits, la totalité du résultat est centrée sur l'attribut. Vous pouvez ensuite écrire cette requête sans imbrication. L'ajout de la directive `ELEMENTS` aboutit à un document XML en partie centré sur l'attribut et en partie centré sur l'élément. Ce résultat ne peut pas être généré par une requête FOR XML d'un seul niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des requêtes FOR XML imbriquées](use-nested-for-xml-queries.md)  
  
  
