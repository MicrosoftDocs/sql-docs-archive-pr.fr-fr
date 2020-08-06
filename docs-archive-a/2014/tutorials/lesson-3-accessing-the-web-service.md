---
title: 'Leçon 3 : accès au service Web | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c69e0dbe9eef987a764686bdf84e68bd8c530628
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702204"
---
# <a name="lesson-3-accessing-the-web-service"></a>Leçon 3 : Accès au service web
  Après avoir ajouté une référence au service Web Report Server à votre projet, l'étape suivante consiste à créer une instance de la classe proxy du service Web. Vous pouvez alors accéder aux méthodes de ce service Web en les appelant dans la classe proxy. Lorsque votre application appelle ces méthodes, le code de la classe proxy générée par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gère les communications entre votre application et le service Web.  
  
 Vous allez tout d'abord créer une instance de la classe proxy du service Web <xref:ReportService2010.ReportingService2010>. Vous allez ensuite appeler la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> du service Web en utilisant la classe proxy. Vous utiliserez cet appel pour extraire le nom et la description de l'un des exemples de rapports appelé Company Sales.  
  
> [!NOTE]  
>  Lors de l'accès à un service Web s'exécutant sous [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, vous devez ajouter "$SQLExpress" au chemin d'accès "ReportServer". Par exemple :  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a>Pour accéder au service Web  
  
1.  Vous devez tout d'abord ajouter l'espace de noms au fichier Program.cs (Module1.vb dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) en ajoutant une directive `using` (`Imports` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) dans le fichier de code. Si vous utilisez cette directive, il n'est pas nécessaire de qualifier complètement les types dans l'espace de noms.  
  
2.  Pour ce faire, ajoutez le code suivant au début de votre fichier de code :  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  Après avoir entré la directive d'espace de noms dans votre fichier de code, entrez le code suivant dans la méthode Main de votre application console. Pensez à modifier le nom de votre serveur au moment de définir la propriété **Url** de l'instance du service Web :  
  
    ```vb  
    Sub Main()  
       Dim rs As New ReportingService2010  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx"  
  
       Dim name As New [Property]  
       name.Name = "Name"  
  
       Dim description As New [Property]  
       description.Name = "Description"  
  
       Dim properties(1) As [Property]  
       properties(0) = name  
       properties(1) = description  
  
       Try  
          Dim returnProperties As [Property]() = rs.GetProperties( _  
             "/AdventureWorks 2012 Sample Reports/Company Sales 2012", properties)  
  
          Dim p As [Property]  
          For Each p In returnProperties  
              Console.WriteLine((p.Name + ": " + p.Value))  
          Next p  
  
       Catch e As Exception  
          Console.WriteLine(e.Message)  
       End Try  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
       ReportingService2010 rs = new ReportingService2010();  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx";  
  
       Property name = new Property();  
       name.Name = "Name";  
  
       Property description = new Property();  
       description.Name = "Description";  
  
       Property[] properties = new Property[2];  
       properties[0] = name;  
       properties[1] = description;  
  
       try  
       {  
          Property[] returnProperties = rs.GetProperties(  
          "/AdventureWorks 2012 Sample Reports/Company Sales 2012",properties);  
  
          foreach (Property p in returnProperties)  
          {  
             Console.WriteLine(p.Name + ": " + p.Value);  
          }  
       }  
  
       catch (Exception e)  
       {  
          Console.WriteLine(e.Message);  
       }  
    }  
    ```  
  
4.  Enregistrez la solution.  
  
 L'exemple de code de cette procédure pas à pas utilise la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> du service Web pour récupérer les propriétés de l'exemple de rapport intitulé Company Sales 2012. La <xref:ReportService2010.ReportingService2010.GetProperties%2A> méthode accepte deux arguments : le nom du rapport pour lequel vous souhaitez récupérer les informations de propriété et un tableau d’objets **Property []** qui contient les noms des propriétés dont vous souhaitez récupérer les valeurs. Cette méthode renvoie également un tableau d'objets **Property[]** qui contient les noms et les valeurs des propriétés spécifiées dans l'argument des propriétés.  
  
> [!NOTE]  
>  Si vous fournissez un tableau **Property[]** vide pour l'argument des propriétés, toutes les propriétés disponibles sont renvoyées.  
  
 Dans l'exemple précédent, le code utilise la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> pour renvoyer le nom et la description de l'exemple de rapport intitulé Company Sales 2012. Il utilise ensuite une boucle `foreach` pour écrire les propriétés et les valeurs dans la console.  
  
 Pour plus d'informations sur la création et l'utilisation d'une classe proxy pour le service Web Report Server, consultez [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Leçon 4 : exécution de l’application &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Accès au service Web Report Server à l’aide de Visual Basic ou du didacticiel Visual C&#35; &#40;SSRS&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
