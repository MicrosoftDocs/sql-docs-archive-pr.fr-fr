---
title: Mappage par défaut d’éléments et d’attributs XSD à des tables et des colonnes (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bccec2413e8a0a6e13283a0f3e5f63ab61e934b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605350"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a>Mappage par défaut d'éléments et d'attributs XSD à des tables et des colonnes (SQLXML 4.0)
  Par défaut, un élément de type complexe dans un schéma annoté XSD est mappé à la table (vue) du même nom dans la base de données spécifiée ; par ailleurs, un élément ou attribut de type simple est mappé à la colonne du même nom dans la table.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-default-mapping"></a>R. Spécification du mappage par défaut  
 Dans cet exemple, aucune annotation n'est spécifiée dans le schéma XSD. L' **\<Person.Contact>** élément est de type complexe et, par conséquent, est mappé par défaut à la table Person. contact de la base de données AdventureWorks. Tous les attributs (ContactID, FirstName, LastName) de l' **\<Person.Contact>** élément sont de type simple et sont mappés par défaut aux colonnes portant le même nom dans la table Person. contact.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchema.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchemaT.xml dans le même répertoire que celui où vous avez enregistré MySchema.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (MySchema.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a>B. Mappage d'un élément XML à une colonne de base de données  
 Dans cet exemple, le mappage par défaut a lieu également, car aucune annotation n'est utilisée. L' **\<Person.Contact>** élément est de type complexe et est mappé à la table portant le même nom dans la base de données. Les éléments **\<FirstName>** et **\<LastName>** et l’attribut **EmployeeID** sont de type simple et, par conséquent, sont mappés aux colonnes portant le même nom. La seule différence entre ceci et l'exemple précédent réside dans le fait que les éléments sont utilisés pour le mappage des champs FirstName et LastName.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchemaElements.xml.  
  
2.  Créez le modèle suivant (MySchemaElementsT.xml) et enregistrez-le dans le même répertoire que celui utilisé à l'étape précédente.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a>C. Mappage d'un élément XML à une colonne de type de données XML  
 Dans cet exemple, le mappage par défaut a lieu également, car aucune annotation n'est utilisée. L' **\<Production.ProductModel>** élément est de type complexe et est mappé à la table portant le même nom dans la base de données. L’attribut **ProductModelID** est de type simple et, par conséquent, est mappé aux colonnes portant le même nom. La seule différence entre cet exemple et les exemples précédents est que l' **\<Instructions>** élément est mappé à une colonne qui utilise le `xml` type de données à l’aide du `xsd:anyType` type.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Le type de données `xml` a été introduit dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchemaXmlAnyElements.xml.  
  
2.  Créez le modèle suivant (MySchemaXmlAnyElementsT.xml) et enregistrez-le dans le même répertoire que celui utilisé à l'étape précédente.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité des schémas annotés &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Données XML &#40;SQL Server&#41;](../xml/xml-data-sql-server.md)   
 [Prise en charge du type de données xml dans SQLXML 4.0](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
