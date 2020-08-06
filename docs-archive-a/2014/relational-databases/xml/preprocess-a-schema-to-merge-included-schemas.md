---
title: Prétraiter un schéma pour fusionner des schémas inclus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- testing preprocessor tool
- xsd:include
- XML schema collections [SQL Server], preprocessor tool
- include element
- XML schemas [SQL Server], preprocessing
- schema collections [SQL Server], preprocessor tool
- preprocessor tool [XML schemas]
- XML schemas [SQL Server]
ms.assetid: cde1de5f-077a-4a6d-8a81-1ecb6e10d549
author: rothja
ms.author: jroth
ms.openlocfilehash: 1bd7ef3893a1e7fd51ca904caa0e76c64d2ae19c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706284"
---
# <a name="preprocess-a-schema-to-merge-included-schemas"></a><span data-ttu-id="22b49-102">Prétraiter un schéma pour fusionner des schémas inclus</span><span class="sxs-lookup"><span data-stu-id="22b49-102">Preprocess a Schema to Merge Included Schemas</span></span>
  <span data-ttu-id="22b49-103">L’élément W3C XSD **include** assure la prise en charge de la modularité des schémas, selon laquelle un schéma XML peut être partitionné en plusieurs fichiers physiques.</span><span class="sxs-lookup"><span data-stu-id="22b49-103">The W3C XSD **include** element provides support for schema modularity in which an XML schema can be partitioned into more than one physical file.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="22b49-104">ne prend pas en charge cet élément.</span><span class="sxs-lookup"><span data-stu-id="22b49-104">currently does not support this element.</span></span> <span data-ttu-id="22b49-105">Les schémas XML incluant cet élément seront rejetés par le serveur.</span><span class="sxs-lookup"><span data-stu-id="22b49-105">XML schemas that include this element will be rejected by the server.</span></span>  
  
 <span data-ttu-id="22b49-106">En guise de solution, les schémas XML comportant la directive \<xsd:include> peuvent être prétraités de façon à copier et à fusionner le contenu des schémas inclus en un seul schéma à charger sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="22b49-106">As a solution, XML schemas that include the \<xsd:include> directive can be preprocessed to copy and merge the contents of any included schemas into a single schema for uploading to the server.</span></span> <span data-ttu-id="22b49-107">Vous pouvez utiliser le code C# suivant pour le prétraitement.</span><span class="sxs-lookup"><span data-stu-id="22b49-107">The following C# code can be used for the preprocessing.</span></span> <span data-ttu-id="22b49-108">Les commentaires dans la première partie du code fournissent des informations sur son utilisation.</span><span class="sxs-lookup"><span data-stu-id="22b49-108">The comments in the early part of the code provide information about how to use it.</span></span>  
  
```  
// XSD Schema Include Normalizer  
// To compile:   
// csc filename.cs  
//  
// How to use:  
//  
// Arguments: [-q] input.xsd [output.xsd]  
//  
// input.xsd       - file to normalize  
// output.xsd      - file to output, default is console  
// -q              - quiet  
//   
// Example:  
//   
// filename.exe schema.xsd  
//   
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.IO;  
using System.Collections;  
public class XsdSchemaNormalizer  
{  
    private static bool NormalizeXmlSchema( String url, TextWriter writer )  
    {  
   try {  
       XmlTextReader txtRead = new XmlTextReader( url );  
       XmlSchema sch = XmlSchema.Read( txtRead, null );  
  
       // Compiling Schema  
       sch.Compile(null);  
  
       XmlSchema outSch =   
      XmlSchemaIncludeNormalizer.BuildIncludeFreeXmlSchema( sch);  
  
       outSch.Write( writer );  
   } catch ( Exception e ) {  
       Console.WriteLine(e.ToString());  
       return false;  
   }  
   return true;  
    }  
    public static void usage()  
    {  
   Console.WriteLine("Arguments: [-q] [-v] input.xsd [output.xsd]\n");  
   Console.WriteLine("input.xsd       - file to normalize");  
   Console.WriteLine("output.xsd      - file to output, default is console");  
   Console.WriteLine("-q              - quiet");  
    }  
    public static void Main(String []args)  
    {  
   if( args.GetLength(0) < 1 ) {  
       usage();  
       return;  
   }  
   int argi = 0;  
   bool quiet = false;  
   if( args[argi] == "-q" ) {  
       quiet = true;  
            argi++;  
   }  
  
   if( argi == args.GetLength(0) )  
   {  
       usage();  
       return;  
   }  
  
   String url = args[argi];  
  
   if( !quiet )  
       Console.WriteLine("Loading Schema: " + url);  
  
   if( argi < ( args.GetLength(0) - 1 ) )  
   {  
       if( !quiet )  
      Console.WriteLine("Outputing to file: " + args[argi+1]);  
  
       StreamWriter output =   
      new StreamWriter( new FileStream(args[argi+1], FileMode.Create ));  
  
       NormalizeXmlSchema( url, output);  
   }  
   else   
   {  
       NormalizeXmlSchema( url, Console.Out);  
   }  
  
    }  
}  
  
// A class to remove all <include> from a Xml Schema  
//  
public class XmlSchemaIncludeNormalizer  
{  
    // Takes as input a XmlSchema which has includes in it   
    // and the schema location uri of that XmlSchema  
    //   
    // Returns a "preprocessed" form of XmlSchema without any   
    // includes. It still retains imports though. Also, it does  
    // not propagate unhandled attributes  
    //  
    // It can throw any exception  
    public static XmlSchema BuildIncludeFreeXmlSchema( XmlSchema inSch )  
    {  
   XmlSchema outSch = new XmlSchema();  
  
   AddSchema( outSch, inSch );  
  
   return outSch;  
    }  
  
    // Adds everything in the second schema minus includes to   
    // the first schema  
    //  
    private static void AddSchema( XmlSchema outSch, XmlSchema add)  
    {  
   outSch.AttributeFormDefault = add.AttributeFormDefault;  
   outSch.BlockDefault = add.BlockDefault;  
   outSch.ElementFormDefault = add.ElementFormDefault;  
   outSch.FinalDefault = add.FinalDefault;  
   outSch.Id = add.Id;  
   outSch.TargetNamespace = add.TargetNamespace;  
   outSch.Version = add.Version;  
  
   AddTableToSchema( outSch, add.AttributeGroups );  
   AddTableToSchema( outSch, add.Attributes );  
   AddTableToSchema( outSch, add.Elements );  
   AddTableToSchema( outSch, add.Groups );  
   AddTableToSchema( outSch, add.Notations );  
   AddTableToSchema( outSch, add.SchemaTypes );  
  
   // Handle includes as a special case  
   for( int i = 0; i < add.Includes.Count; i++ )  
   {  
       if( ! ( add.Includes[i] is XmlSchemaInclude) )  
      outSch.Includes.Add( add.Includes[i] );  
   }  
    }  
  
    // Adds all items in the XmlSchemaObjectTable to the specified XmlSchema  
    //  
    private static void AddTableToSchema( XmlSchema outSch,   
                 XmlSchemaObjectTable table )  
    {  
   IDictionaryEnumerator e = table.GetEnumerator();  
  
   while( e.MoveNext() )  
   {  
       outSch.Items.Add( (XmlSchemaObject)e.Value );  
   }  
    }  
}  
```  
  
## <a name="testing-the-preprocessor-tool"></a><span data-ttu-id="22b49-109">Test de l'outil du préprocesseur</span><span class="sxs-lookup"><span data-stu-id="22b49-109">Testing the Preprocessor Tool</span></span>  
 <span data-ttu-id="22b49-110">Vous pouvez utiliser les schémas XSD suivants pour tester l'outil du préprocesseur :</span><span class="sxs-lookup"><span data-stu-id="22b49-110">You can use the following XSD schemas to test the preprocessor tool:</span></span>  
  
### <a name="books_commonxsd"></a><span data-ttu-id="22b49-111">books_common.xsd</span><span class="sxs-lookup"><span data-stu-id="22b49-111">books_common.xsd</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="bookstore-schema"  
     elementFormDefault="qualified" >  
  <xsd:element name="publisher" type="xsd:string"/>  
</xsd:schema>  
```  
  
### <a name="booksxsd"></a><span data-ttu-id="22b49-112">books.xsd</span><span class="sxs-lookup"><span data-stu-id="22b49-112">books.xsd</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="bookstore-schema"  
     elementFormDefault="qualified"  
     targetNamespace="bookstore-schema">  
  <xsd:include id="books_common" schemaLocation="books_common.xsd"/>  
  <xsd:element name="bookstore" type="xsd:string" />  
</xsd:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22b49-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22b49-113">See Also</span></span>  
 [<span data-ttu-id="22b49-114">Collections de schémas XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="22b49-114">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  