---
title: Prise en main avec l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 43c97e411a4d74aa48b88f2edbbe420ae17f3534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600078"
---
# <a name="getting-started-with-clr-integration"></a>Mise en route avec l'intégration du CLR
  Cette rubrique fournit une vue d’ensemble des espaces de noms et des bibliothèques requis pour compiler des objets de base de données à l’aide de l' [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] intégration avec l' .NET Framework Common Language Runtime (CLR). La rubrique vous indique également comment écrire, compiler et exécuter une procédure stockée CLR simple écrite dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
## <a name="required-namespaces"></a>Espaces de noms requis  
 À partir de [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] . Les fonctionnalités d'intégration du CLR sont exposées dans un assembly appelé system.data.dll, qui fait partie du .NET Framework. Cet assembly se trouve dans le Global Assembly Cache (GAC), ainsi que dans le répertoire .NET Framework. Une référence à cet assembly est ajoutée en général automatiquement par les outils en ligne de commande et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, afin qu'il ne soit pas nécessaire de l'ajouter manuellement.  
  
 L'assembly system.data.dll contient les espaces de noms suivants, qui sont requis pour compiler les objets de base de données CLR :  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a>Écriture d'une procédure stockée "Hello World" simple  
 Copiez et collez le code Visual C# ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic suivant dans un éditeur de texte et enregistrez-le dans un fichier nommé "helloworld.cs" ou "helloworld.vb".  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 Ce programme simple contient une méthode statique unique sur une classe publique. Cette méthode utilise deux nouvelles classes, `SqlContext` et `SqlPipe`, pour créer des objets de base de données managés afin d'obtenir un message textuel simple. La méthode assigne également la chaîne « Hello World ! » comme valeur d’un paramètre de sortie. Cette méthode peut être déclarée en tant que procédure stockée dans une [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] procédure stockée.  
  
 Nous allons maintenant compiler ce programme sous la forme d'une bibliothèque, le charger dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et l'exécuter en tant que procédure stockée.  
  
## <a name="compiling-the-hello-world-stored-procedure"></a>Compilation de la procédure stockée "Hello World"  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)].NET Framework les fichiers de redistribution par défaut. Ces fichiers incluent csc.exe et vbc.exe, les compilateurs de ligne de commande pour les programmes Visual C# et Visual Basic. Pour compiler notre exemple, vous devez modifier votre variable de chemin d'accès pour pointer sur le répertoire qui contient csc.exe ou vbc.exe. Le chemin d'installation par défaut du .NET Framework est le suivant :  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 La version contient le numéro de version du programme redistribuable .NET Framework installé. Par exemple :  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 Une fois que vous avez ajouté le répertoire .NET Framework à votre chemin d'accès, vous pouvez compiler l'exemple de procédure stockée en assembly à l'aide de la commande ci-dessous. L'option `/target` vous permet de le compiler en assembly.  
  
 Pour les fichiers sources Visual C# :  
  
```  
csc /target:library helloworld.cs   
```  
  
 Pour les fichiers sources Visual Basic :  
  
```  
vbc /target:library helloworld.vb  
```  
  
 Ces commandes lancent le compilateur Visual C# ou Visual Basic en utilisant l'option /target pour spécifier la génération d'une DLL de bibliothèque.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Chargement et exécution de la procédure stockée "Hello World" dans SQL Server  
 Une fois que l’exemple de procédure a été compilé avec succès, vous pouvez le tester dans [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] et créer une nouvelle requête, en vous connectant à une base de données de test appropriée (par exemple, l’exemple de base de données AdventureWorks).  
  
 La fonctionnalité d'exécution du code CLR est désactivée par défaut dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code CLR peut être activé à l’aide de la procédure stockée système **sp_configure** . Pour plus d’informations, consultez [Activation de l’intégration du CLR](../clr-integration-enabling.md).  
  
 Il est nécessaire de créer l'assembly afin de pouvoir accéder à la procédure stockée. Pour cet exemple, nous supposerons que vous avez créé l'assembly helloworld.dll dans le répertoire C:\. Ajoutez l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante à votre requête.  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 Une fois l'assembly créé, il est possible d'accéder à la méthode HelloWorld en utilisant l'instruction CREATE PROCEDURE. Nous appellerons la procédure stockée "hello" :  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 Une fois la procédure créée, elle peut être exécutée tout comme une procédure stockée normale écrite dans [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Exécutez la commande suivante :  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 Cela doit générer la sortie ci-dessous dans la fenêtre des messages [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a>Suppression de l'exemple de procédure stockée "Hello World"  
 Lorsque vous avez terminé d'exécuter l'exemple de procédure stockée, vous pouvez supprimer la procédure et l'assembly de votre base de données de test.  
  
 En premier lieu, supprimez la procédure à l'aide de la commande drop procedure.  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 Une fois la procédure supprimée, vous pouvez supprimer l'assembly qui contient votre exemple de code.  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [SQL Server des extensions spécifiques in-process à ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)   
 [Débogage d’objets de base de données CLR](../debugging-clr-database-objects.md)   
 [Sécurité de l'intégration du CLR](../security/clr-integration-security.md)  
  
  
