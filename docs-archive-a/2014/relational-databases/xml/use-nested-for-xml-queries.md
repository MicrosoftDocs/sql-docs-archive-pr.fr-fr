---
title: Utiliser des requêtes FOR XML imbriquées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 60c4198697f8d19c9b2e5bc1b415e0787861d40a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706280"
---
# <a name="use-nested-for-xml-queries"></a>Utiliser des requêtes FOR XML imbriquées
  Le `xml` type de données et la [directive type dans les requêtes for XML](type-directive-in-for-xml-queries.md) permettent au XML retourné par les requêtes for XML d’être traité sur le serveur et sur le client.  
  
## <a name="processing-with-xml-type-variables"></a>Traitement avec des variables de type xml  
 Vous pouvez affecter le résultat de la requête FOR XML à une variable de type `xml` ou bien utiliser XQuery pour interroger le résultat et affecter celui-ci à une variable de type `xml` en vue d'un traitement supplémentaire.  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 Vous pouvez poursuivre le traitement du document XML renvoyé dans la variable `@x` à l'aide de l'une des méthodes de type de données `xml`. Par exemple, vous pouvez extraire la valeur de l’attribut `ProductModelID` à l’aide de la [méthode value()](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 Dans l'exemple suivant, le résultat de la requête `FOR XML` renvoyé est de type `xml` car la directive `TYPE` est spécifiée dans la clause `FOR XML`.  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 Voici le résultat obtenu :  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 Étant donné que le résultat est de type `xml`, vous pouvez spécifier l'une des méthodes de type de données `xml` directement par rapport à ce document XML, comme le montre la requête suivante. Dans la requête, la [méthode query() (type de données xml)](/sql/t-sql/xml/query-method-xml-data-type) est utilisée pour extraire le premier élément enfant <`row`> de l’élément <`myRoot`>.  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 Voici le résultat obtenu :  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a>Renvoi de résultats de requêtes FOR XML internes à des requêtes externes en tant qu'instances de type xml  
 Vous pouvez écrire des requêtes `FOR XML` imbriquées où le résultat de la requête interne est retourné en tant que type `xml` à la requête externe. Par exemple :  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le XML généré par la requête `FOR XML` interne est ajouté au XML généré par la requête `FOR XML`externe.  
  
-   La requête interne spécifie la directive `TYPE` . Par conséquent, les données XML retournées par la requête interne sont du type `xml`. Si la directive TYPE n'est pas spécifiée, le résultat de la requête `FOR XML` interne est retourné en tant que `nvarchar(max)` et les données XML sont converties en entités.  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a>Contrôle de la forme des données XML résultantes  
 Les requêtes FOR XML imbriquées vous permettent de mieux contrôler la forme des données XML résultantes. Vous pouvez utiliser des requêtes FOR XML imbriquées pour construire des données XML centrées partiellement sur l'attribut et partiellement sur l'élément.  
  
 Pour plus d’informations sur la spécification de données XML centrées sur l’attribut et sur l’élément avec des requêtes FOR XML imbriquées, consultez [Comparaison de la requête FOR XML et de la requête FOR XML imbriquée](../xml/for-xml-query-compared-to-nested-for-xml-query.md) et [Façonner des données XML avec des requêtes FOR XML imbriquées](../xml/shape-xml-with-nested-for-xml-queries.md).  
  
 Vous pouvez générer des hiérarchies XML qui incluent des frères en spécifiant des requêtes FOR XML en mode AUTO imbriquées. Pour plus d’informations, consultez [Générer des frères à l’aide d’une requête imbriquée en mode AUTO](../xml/generate-siblings-with-a-nested-auto-mode-query.md).  
  
 Quel que soit le mode utilisé, les requêtes FOR XML imbriquées procurent davantage de contrôle dans la description de la forme des données XML résultantes. Elles peuvent être utilisées à la place des requêtes en mode EXPLICIT.  
  
## <a name="examples"></a>Exemples  
 Les rubriques suivantes fournissent des exemples de requêtes FOR XML imbriquées.  
  
 [Comparaison de la requête FOR XML et de la requête FOR XML imbriquée](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 Compare une requête FOR XML d'un seul niveau à une requête FOR XML imbriquée. Cet exemple inclut une démonstration de la manière de spécifier à la fois des données XML centrées sur l'attribut et centrées sur l'élément comme résultat de requête.  
  
 [Générer des frères à l’aide d’une requête imbriquée en mode AUTO](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 Montre comment générer des frères à l'aide d'une requête imbriquée en mode AUTO  
  
 [Utiliser des requêtes FOR XML imbriquées dans ASP.NET](use-nested-for-xml-queries-in-asp-net.md)  
 Montre comment une application ASPX peut utiliser FOR XML pour retourner des données XML à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Façonner des données XML avec des requêtes FOR XML imbriquées](../xml/shape-xml-with-nested-for-xml-queries.md)  
 Montre comment utiliser des requêtes FOR XML imbriquées pour contrôler la structure d'un document XML créé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
