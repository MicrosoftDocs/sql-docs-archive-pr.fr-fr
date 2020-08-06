---
title: 'Création de sections CDATA à l’aide de SQL : use-cdata (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
ms.openlocfilehash: c0ba0787efbda400590a75f0f3529e3df8819e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613389"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>Création de sections CDATA à l'aide de sql:use-cdata (SQLXML 4.0)
  En XML, les sections CDATA sont utilisées pour l'échappement des blocs de texte qui contiennent des caractères qui seraient reconnus comme caractères de balisage dans un autre contexte.  
  
 Une base de données dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut parfois contenir des caractères qui sont traités comme des caractères de balisage par l’analyseur XML. par exemple, les crochets pointus ( \< and > ), le symbole « inférieur à » ou « égal à » (<=) et les esperluette (&) sont traités comme des caractères de balisage. Toutefois, vous pouvez encapsuler ce type de caractères spéciaux dans une section CDATA afin de les empêcher d'être traités comme des caractères de balisage. Le texte dans la section CDATA est traité par l'analyseur XML comme du texte brut.  
  
 L'annotation `sql:use-cdata` est utilisée pour spécifier que les données retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être encapsulées dans une section CDATA (autrement dit, elle indique si la valeur d'une colonne spécifiée par `sql:field` doit être placée dans une section CDATA). L'annotation `sql:use-cdata` peut être spécifiée uniquement sur des éléments qui mappent à une colonne de base de données.  
  
 L'annotation `sql:use-cdata` prend une valeur booléenne (0 = faux, 1 = vrai). Les valeurs acceptables sont 0, 1, true et false.  
  
 Cette annotation ne peut pas être utilisée avec `sql:url-encode`, ni sur les types d'attributs ID, IDREF, IDREFS, NMTOKEN et NMTOKENS.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>R. Spécification de sql:use-cdata sur un élément  
 Dans le schéma suivant, `sql:use-cdata` a la valeur 1 (true) pour le **\<AddressLine1>** au sein de l' **\<Address>** élément. En conséquence, les données sont retournées dans une section CDATA.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom UseCData.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom UseCDataT.xml dans le répertoire où vous avez enregistré le fichier UseCData.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (UseCData.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
