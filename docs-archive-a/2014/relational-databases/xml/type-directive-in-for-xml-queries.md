---
title: Directive TYPE dans les requêtes FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
author: rothja
ms.author: jroth
ms.openlocfilehash: cddce90718ef5edfcf161ddc6cc52b617825a2e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614405"
---
# <a name="type-directive-in-for-xml-queries"></a>Directive TYPE dans les requêtes FOR XML
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la prise en charge du [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql) vous permet éventuellement de demander que le résultat d’une requête for XML soit retourné en tant que `xml` type de données en spécifiant la directive type. Cela vous permet de traiter le résultat d'une requête FOR XML sur le serveur. Par exemple, vous pouvez spécifier une requête XQuery par rapport à celle-ci, assigner le résultat à une `xml` variable de type ou écrire [des requêtes for XML imbriquées](use-nested-for-xml-queries.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie des données d'instance de type de données XML au client comme résultat de différentes constructions de serveur telles que des requêtes FOR XML qui utilisent la directive TYPE ou dans lesquelles le type de données `xml` permet de renvoyer des valeurs de données d'instance XML à partir de paramètres de sortie et de colonnes de table SQL. Dans le code de l'application cliente, le fournisseur ADO.NET demande à ce que ces informations de type de données XML soient envoyées dans un encodage binaire à partir du serveur. Toutefois, si vous utilisez FOR XML sans la directive TYPE, les données XML reviennent en tant que type chaîne. Dans tous les cas, le fournisseur client est toujours en mesure de gérer toute forme XML. Notez qu'une clause FOR XML de premier niveau sans directive TYPE ne peut pas être utilisée avec les curseurs.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent l'utilisation de la directive TYPE avec des requêtes FOR XML.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>Extraction des résultats de la requête FOR XML en tant que type xml  
 La requête suivante extrait des informations de contact client de la table `Contacts` . Étant donné que la directive `TYPE` est spécifiée sous la forme `FOR XML`, le résultat est renvoyé en tant que type `xml`.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 Voici le résultat partiel :  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>Affectation des résultats de la requête FOR XML à une variable de type xml  
 Dans l'exemple suivant, un résultat FOR XML est affecté à une variable de type `xml`, `@x`. La requête récupère les informations de contact, telles que `BusinessEntityID` , `FirstName` , `LastName` et des numéros de téléphone supplémentaires, à partir de la `AdditionalContactInfo` colonne de `xml``TYPE` . Étant donné que la clause `FOR XML` spécifie la directive `TYPE`, le document XML est renvoyé en tant que type `xml` et affecté à une variable.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>Interrogation des résultats d'une requête FOR XML  
 Les requêtes FOR XML renvoient des données XML. Par conséquent, vous pouvez appliquer des méthodes de type `xml`, telles que `query()` et `value()`, au résultat XML renvoyé par des requêtes FOR XML.  
  
 Dans la requête suivante, la méthode `query()` du type de données `xml` permet d'interroger le résultat de la requête `FOR XML`. Pour plus d’informations, consultez [Méthode query&#40;&#41; &#40;type de données xml&#41;](/sql/t-sql/xml/query-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 La requête `SELECT ... FOR XML` interne retourne un résultat de type `xml` auquel la clause `SELECT` externe applique la méthode `query()` au type `xml`. Notez la directive `TYPE` spécifiée.  
  
 Voici le résultat obtenu :  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 Dans la requête suivante, la méthode `value()` du type de données `xml` permet d'extraire une valeur du résultat XML renvoyé par la requête `SELECT...FOR XML`. Pour plus d’informations, consultez [Méthode value&#40;&#41; &#40;type de données xml&#41;](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 L'expression de chemin d'accès XQuery dans la méthode `value()` extrait le premier numéro de téléphone d'un contact client dont `BusinessEntityID` a pour valeur `1`.  
  
> [!NOTE]  
>  Si la directive TYPE n'est pas spécifiée, le résultat de la requête FOR XML est renvoyé en tant que type `nvarchar(max)`.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>Utilisation des résultats de la requête FOR XML dans INSERT, UPDATE et DELETE (Transact-SQL DML)  
 L'exemple suivant montre comment des requêtes FOR XML peuvent être utilisées dans des instructions DML (Data Manipulation Language, langage de manipulation de données). Dans l'exemple, la requête `FOR XML` renvoie une instance de type `xml`. L'instruction `INSERT` insère ce document XML dans une table.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
