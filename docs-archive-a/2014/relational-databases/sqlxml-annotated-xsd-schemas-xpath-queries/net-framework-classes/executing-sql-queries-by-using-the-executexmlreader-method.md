---
title: Exécution de requêtes SQL à l’aide de la méthode ExecuteXMLReader | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: rothja
ms.author: jroth
ms.openlocfilehash: 1570e877ae84a813e5a053df34c35d5fe840969c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610528"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a>Exécution de requêtes SQL à l'aide de la méthode ExecuteXMLReader
  Au lieu d’utiliser la méthode ExecuteToStream, vous pouvez utiliser la méthode ExecuteXmlReader de l’objet SqlXmlCommand pour exécuter des commandes. Cette méthode retourne un objet XmlReader qui peut être utilisé pour le traitement supplémentaire du résultat (qui, dans cet exemple, imprime les noms d’éléments ou d’attributs et les valeurs).  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Assurez-vous que le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework est installé sur votre ordinateur.  
  
2.  Enregistrez le code C# (DocSample.cs) fourni dans cette rubrique dans un dossier.  
  
3.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
4.  À l'invite de commandes, exécutez DocSample.exe.  
  
  
