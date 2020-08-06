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
# <a name="lesson-3-accessing-the-web-service"></a><span data-ttu-id="316db-102">Leçon 3 : Accès au service web</span><span class="sxs-lookup"><span data-stu-id="316db-102">Lesson 3: Accessing the Web Service</span></span>
  <span data-ttu-id="316db-103">Après avoir ajouté une référence au service Web Report Server à votre projet, l'étape suivante consiste à créer une instance de la classe proxy du service Web.</span><span class="sxs-lookup"><span data-stu-id="316db-103">After you add a reference for the Report Server Web service to your project, the next step is to create an instance of the Web service's proxy class.</span></span> <span data-ttu-id="316db-104">Vous pouvez alors accéder aux méthodes de ce service Web en les appelant dans la classe proxy.</span><span class="sxs-lookup"><span data-stu-id="316db-104">You can then access the methods of the Web service by calling the methods in the proxy class.</span></span> <span data-ttu-id="316db-105">Lorsque votre application appelle ces méthodes, le code de la classe proxy générée par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gère les communications entre votre application et le service Web.</span><span class="sxs-lookup"><span data-stu-id="316db-105">When your application calls these methods, the proxy class code generated by [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] handles the communications between your application and the Web service.</span></span>  
  
 <span data-ttu-id="316db-106">Vous allez tout d'abord créer une instance de la classe proxy du service Web <xref:ReportService2010.ReportingService2010>.</span><span class="sxs-lookup"><span data-stu-id="316db-106">First, you will create an instance of the Web service's proxy class, <xref:ReportService2010.ReportingService2010>.</span></span> <span data-ttu-id="316db-107">Vous allez ensuite appeler la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> du service Web en utilisant la classe proxy.</span><span class="sxs-lookup"><span data-stu-id="316db-107">Next, you will make a call to the Web service's <xref:ReportService2010.ReportingService2010.GetProperties%2A> method using the proxy class.</span></span> <span data-ttu-id="316db-108">Vous utiliserez cet appel pour extraire le nom et la description de l'un des exemples de rapports appelé Company Sales.</span><span class="sxs-lookup"><span data-stu-id="316db-108">You will use the call to retrieve the name and description of one of the sample reports, Company Sales.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="316db-109">Lors de l'accès à un service Web s'exécutant sous [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, vous devez ajouter "$SQLExpress" au chemin d'accès "ReportServer".</span><span class="sxs-lookup"><span data-stu-id="316db-109">When accessing a Web service running on [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, you must append "$SQLExpress" to the "ReportServer" path.</span></span> <span data-ttu-id="316db-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="316db-110">For example:</span></span>  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a><span data-ttu-id="316db-111">Pour accéder au service Web</span><span class="sxs-lookup"><span data-stu-id="316db-111">To access the Web service</span></span>  
  
1.  <span data-ttu-id="316db-112">Vous devez tout d'abord ajouter l'espace de noms au fichier Program.cs (Module1.vb dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) en ajoutant une directive `using` (`Imports` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="316db-112">You must first add the namespace to the Program.cs file (Module1.vb in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) by adding a `using` (`Imports` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) directive to the code file.</span></span> <span data-ttu-id="316db-113">Si vous utilisez cette directive, il n'est pas nécessaire de qualifier complètement les types dans l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="316db-113">If you use this directive, you do not need to fully qualify the types in the namespace.</span></span>  
  
2.  <span data-ttu-id="316db-114">Pour ce faire, ajoutez le code suivant au début de votre fichier de code :</span><span class="sxs-lookup"><span data-stu-id="316db-114">To do this, add the following code to the beginning of your code file:</span></span>  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  <span data-ttu-id="316db-115">Après avoir entré la directive d'espace de noms dans votre fichier de code, entrez le code suivant dans la méthode Main de votre application console.</span><span class="sxs-lookup"><span data-stu-id="316db-115">Once you have entered the namespace directive to your code file, enter the following code in the Main method of your console application.</span></span> <span data-ttu-id="316db-116">Pensez à modifier le nom de votre serveur au moment de définir la propriété **Url** de l'instance du service Web :</span><span class="sxs-lookup"><span data-stu-id="316db-116">Make sure to change the name of your server when setting the **Url** property of the web service instance:</span></span>  
  
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
  
4.  <span data-ttu-id="316db-117">Enregistrez la solution.</span><span class="sxs-lookup"><span data-stu-id="316db-117">Save the solution.</span></span>  
  
 <span data-ttu-id="316db-118">L'exemple de code de cette procédure pas à pas utilise la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> du service Web pour récupérer les propriétés de l'exemple de rapport intitulé Company Sales 2012.</span><span class="sxs-lookup"><span data-stu-id="316db-118">The walkthrough sample code uses the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method of the Web service to retrieve properties of the sample report, Company Sales 2012.</span></span> <span data-ttu-id="316db-119">La <xref:ReportService2010.ReportingService2010.GetProperties%2A> méthode accepte deux arguments : le nom du rapport pour lequel vous souhaitez récupérer les informations de propriété et un tableau d’objets **Property []** qui contient les noms des propriétés dont vous souhaitez récupérer les valeurs.</span><span class="sxs-lookup"><span data-stu-id="316db-119">The <xref:ReportService2010.ReportingService2010.GetProperties%2A> method takes two arguments: the name of the report for which you want to retrieve property information and an array of **Property[]** objects that contains the names of properties whose values you want to retrieve.</span></span> <span data-ttu-id="316db-120">Cette méthode renvoie également un tableau d'objets **Property[]** qui contient les noms et les valeurs des propriétés spécifiées dans l'argument des propriétés.</span><span class="sxs-lookup"><span data-stu-id="316db-120">The method also returns an array of **Property[]** objects that contains the names and values of the properties specified in the properties argument.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="316db-121">Si vous fournissez un tableau **Property[]** vide pour l'argument des propriétés, toutes les propriétés disponibles sont renvoyées.</span><span class="sxs-lookup"><span data-stu-id="316db-121">If you supply an empty **Property[]** array for the properties argument, all available properties are returned.</span></span>  
  
 <span data-ttu-id="316db-122">Dans l'exemple précédent, le code utilise la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> pour renvoyer le nom et la description de l'exemple de rapport intitulé Company Sales 2012.</span><span class="sxs-lookup"><span data-stu-id="316db-122">In the previous sample, the code uses the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method to return the name and description of the sample report, Company Sales 2012.</span></span> <span data-ttu-id="316db-123">Il utilise ensuite une boucle `foreach` pour écrire les propriétés et les valeurs dans la console.</span><span class="sxs-lookup"><span data-stu-id="316db-123">The code then uses a `foreach` loop to write the properties and values to the console.</span></span>  
  
 <span data-ttu-id="316db-124">Pour plus d'informations sur la création et l'utilisation d'une classe proxy pour le service Web Report Server, consultez [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="316db-124">For more information about creating and using a proxy class for the Report Server Web service, see [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316db-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="316db-125">See Also</span></span>  
 <span data-ttu-id="316db-126">[Leçon 4 : exécution de l’application &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md) </span><span class="sxs-lookup"><span data-stu-id="316db-126">[Lesson 4: Running the Application &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md) </span></span>  
 [<span data-ttu-id="316db-127">Accès au service Web Report Server à l’aide de Visual Basic ou du didacticiel Visual C&#35; &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="316db-127">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  