---
title: Création, modification et suppression des valeurs par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 747f7ff60122c5265cd68060063946a3e22d0301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707339"
---
# <a name="creating-altering-and-removing-defaults"></a>Création, modification et suppression des valeurs par défaut
  Dans SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), la contrainte par défaut est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Default>.  
  
 La propriété <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Default> est utilisée pour définir la valeur à insérer. Il peut s'agir d'une constante ou d'une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] qui retourne une valeur constante, telle que GETDATE(). La propriété <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> ne peut pas être modifiée en utilisant la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. L'objet <xref:Microsoft.SqlServer.Management.Smo.Default> doit d'abord être supprimé, puis recréé.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un projet Visual C&#35; Smo dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>Création, modification et suppression d'une valeur par défaut en Visual Basic  
 Cet exemple de code montre comment créer une valeur par défaut qui est du texte simple et une autre valeur par défaut qui est une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] . La valeur par défaut doit être attachée à la colonne à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>, puis détachée à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>Création, modification et suppression d'une valeur par défaut en Visual C#  
 Cet exemple de code montre comment créer une valeur par défaut qui est du texte simple et une autre valeur par défaut qui est une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] . La valeur par défaut doit être attachée à la colonne à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>, puis détachée à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```csharp
{
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>Création, modification et suppression d'une valeur par défaut dans PowerShell  
 Cet exemple de code montre comment créer une valeur par défaut qui est du texte simple et une autre valeur par défaut qui est une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] . La valeur par défaut doit être attachée à la colonne à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>, puis détachée à l'aide de la méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
