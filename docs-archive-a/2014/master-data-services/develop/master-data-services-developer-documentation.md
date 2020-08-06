---
title: Guide des&#39;pour les développeurs (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 067b1f69-84eb-4a13-b220-120cd63704b4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8ff7cf98959c2b1ca5aef035963c9a9484cd82db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615174"
---
# <a name="developer39s-guide-master-data-services"></a><span data-ttu-id="fde8f-102">Guide des&#39;pour les développeurs (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="fde8f-102">Developer&#39;s Guide (Master Data Services)</span></span>
  <span data-ttu-id="fde8f-103">Recherchez des informations sur l'écriture du code pour personnaliser la façon dont vous et les utilisateurs interagissez avec [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fde8f-103">Find information about how to write code to customize the way you and your users interact with [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="fde8f-104">Découvrez comment :</span><span class="sxs-lookup"><span data-stu-id="fde8f-104">Learn how to:</span></span>  
  
-   <span data-ttu-id="fde8f-105">Ecrire un programme qui accède au service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-105">Write a program that accesses the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service.</span></span> <span data-ttu-id="fde8f-106">Le service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est un service Windows Communication Foundation (WCF) utilisé par les développeurs pour contrôler les fonctionnalités de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] via du code.</span><span class="sxs-lookup"><span data-stu-id="fde8f-106">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service is a Windows Communication Foundation (WCF) service that developers use to control [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] features through code.</span></span>  
  
-   <span data-ttu-id="fde8f-107">Incorporer les fonctionnalités [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] dans des applications existantes.</span><span class="sxs-lookup"><span data-stu-id="fde8f-107">Incorporate [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] features into existing applications.</span></span>  
  
-   <span data-ttu-id="fde8f-108">Entrer du code pour traiter des actions répétitives ou complexes qu'il est impossible ou difficile d'effectuer avec l'interface utilisateur [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-108">Write code to perform repetitive or complex actions that are difficult or impossible to do with the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] UI.</span></span>  
  
-   <span data-ttu-id="fde8f-109">Créer un flux de travail personnalisé qui s'exécute en réponse à une règle d'entreprise que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="fde8f-109">Create a custom workflow that executes in response to a business rule you specify.</span></span> <span data-ttu-id="fde8f-110">Un flux de travail personnalisé appelle du code que vous écrivez et qui peut exécuter n'importe quelle action requise pour traiter le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fde8f-110">A custom workflow calls code that you write, which can take whatever action you require to process the workflow.</span></span>  
  
## <a name="master-data-manager-web-service"></a><span data-ttu-id="fde8f-111">Service Web Master Data Manager</span><span class="sxs-lookup"><span data-stu-id="fde8f-111">Master Data Manager Web Service</span></span>  
 <span data-ttu-id="fde8f-112">Le service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] vous permet de programmer les fonctionnalités de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] à partir de n'importe quel ordinateur pouvant accéder à votre site Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-112">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service lets you make programmatic use of the features of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from any computer that can access your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site.</span></span> <span data-ttu-id="fde8f-113">Avant de démarrer l'écriture du code pour accéder au service Web, vous devez générer les classes proxy, contenues dans un espace de noms que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="fde8f-113">Before you can start writing code to access the web service, you must generate proxy classes, which are contained in a namespace that you specify.</span></span> <span data-ttu-id="fde8f-114">Cette documentation utilise <xref:Microsoft.MasterDataServices> comme espace de noms de proxy.</span><span class="sxs-lookup"><span data-stu-id="fde8f-114">This documentation uses <xref:Microsoft.MasterDataServices> as the proxy namespace.</span></span> <span data-ttu-id="fde8f-115">La classe proxy principale que vous utilisez pour effectuer des opérations de service Web est la classe <xref:Microsoft.MasterDataServices.ServiceClient>, qui implémente l'interface <xref:Microsoft.MasterDataServices.IService>.</span><span class="sxs-lookup"><span data-stu-id="fde8f-115">The main proxy class you use to perform web service operations is the <xref:Microsoft.MasterDataServices.ServiceClient> class, which implements the <xref:Microsoft.MasterDataServices.IService> interface.</span></span> <span data-ttu-id="fde8f-116">Depuis votre code, appelez les méthodes de la classe <xref:Microsoft.MasterDataServices.ServiceClient> pour accéder au service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fde8f-116">From your code, call methods of the <xref:Microsoft.MasterDataServices.ServiceClient> class to access the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service.</span></span> <span data-ttu-id="fde8f-117">Le reste des classes dans l'espace de noms sont utilisées par les opérations de service Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-117">The remainder of the classes in the namespace are used by the web service operations.</span></span>  
  
### <a name="web-service-content"></a><span data-ttu-id="fde8f-118">Contenu du service Web</span><span class="sxs-lookup"><span data-stu-id="fde8f-118">Web Service Content</span></span>  
 [<span data-ttu-id="fde8f-119">Créer des classes proxy de service Web Master Data Manager</span><span class="sxs-lookup"><span data-stu-id="fde8f-119">Create Master Data Manager Web Service Proxy Classes</span></span>](create-master-data-manager-web-service-proxy-classes.md)  
 <span data-ttu-id="fde8f-120">Décrit comment activer la publication des métadonnées à partir du site Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] et comment créer les classes proxy qui peuvent être utilisées pour accéder par programmation aux opérations du service Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-120">Describes how to enable metadata publishing from the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site and how to create proxy classes that can be used to programmatically access the web service operations.</span></span>  
  
 [<span data-ttu-id="fde8f-121">Opérations de service web par catégorie &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fde8f-121">Categorized Web Service Operations &#40;Master Data Services&#41;</span></span>](categorized-web-service-operations-master-data-services.md)  
 <span data-ttu-id="fde8f-122">Liste par catégorie des opérations de service Web de la classe <xref:Microsoft.MasterDataServices.ServiceClient>.</span><span class="sxs-lookup"><span data-stu-id="fde8f-122">A categorized list of the web service operations of the <xref:Microsoft.MasterDataServices.ServiceClient> class.</span></span>  
  
## <a name="custom-workflows"></a><span data-ttu-id="fde8f-123">Flux de travail personnalisés</span><span class="sxs-lookup"><span data-stu-id="fde8f-123">Custom Workflows</span></span>  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="fde8f-124">utilise des règles d'entreprise pour créer des solutions de flux de travail de base.</span><span class="sxs-lookup"><span data-stu-id="fde8f-124">uses business rules to create basic workflow solutions.</span></span> <span data-ttu-id="fde8f-125">Vous pouvez automatiquement mettre à jour et valider les données et recevoir des notifications par courrier électronique en fonction des conditions que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="fde8f-125">You can automatically update and validate data and have e-mail notifications sent based on conditions you specify.</span></span> <span data-ttu-id="fde8f-126">Les règles d'entreprise dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sont prévues pour gérer les scénarios de flux de travail les plus courants.</span><span class="sxs-lookup"><span data-stu-id="fde8f-126">Business rules in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] are intended to manage the most common workflow scenarios.</span></span> <span data-ttu-id="fde8f-127">Si votre flux de travail nécessite le traitement d'événements plus complexes, tels que les approbations multicouche ou les arbres décisionnels complexes, vous pouvez configurer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour envoyer des données à un assembly personnalisé que vous créez.</span><span class="sxs-lookup"><span data-stu-id="fde8f-127">If your workflow requires more complex event processing, such as multi-tiered approvals or complex decision trees, you can configure [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] to send data to a custom assembly that you create.</span></span> <span data-ttu-id="fde8f-128">Pour gérer les flux de travail personnalisés, vous devez configurer et démarrer SQL Server Service d’intégration de flux de travail MDS sur l’ordinateur de l’application Web, et créer un assembly qui implémente l’interface [Microsoft. MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) .</span><span class="sxs-lookup"><span data-stu-id="fde8f-128">To handle custom workflows, you must configure and start SQL Server MDS Workflow Integration Service on the web application computer, and create an assembly that implements the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) interface.</span></span>  
  
### <a name="custom-workflow-content"></a><span data-ttu-id="fde8f-129">Contenu personnalisé de flux de travail</span><span class="sxs-lookup"><span data-stu-id="fde8f-129">Custom Workflow Content</span></span>  
 [<span data-ttu-id="fde8f-130">Créer un flux de travail personnalisé &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fde8f-130">Create a Custom Workflow &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-master-data-services.md)  
 <span data-ttu-id="fde8f-131">Instructions sur la création d'un assembly de gestionnaire de flux de travail, sur la configuration et le démarrage du service d'intégration de flux de travail MDS SQL Server et sur la création d'une règle d'entreprise dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] qui démarre un flux de travail personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fde8f-131">Instructions on how to create a workflow handler assembly, how to configure and start SQL Server MDS Workflow Integration Service, and how to create a business rule in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] that starts a custom workflow.</span></span>  
  
## <a name="web-server-namespaces"></a><span data-ttu-id="fde8f-132">Espaces de noms de serveur Web</span><span class="sxs-lookup"><span data-stu-id="fde8f-132">Web Server Namespaces</span></span>  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="fde8f-133">installe un ensemble d'assemblys sur le serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-133">installs a set of assemblies on the web server computer.</span></span> <span data-ttu-id="fde8f-134">Ces assemblys contiennent des espaces de noms qui peuvent être utilisés pour des scénarios avancés qui personnalisent le comportement du serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-134">These assemblies contain namespaces that can be used for advanced scenarios that customize the behavior of the web server computer.</span></span> <span data-ttu-id="fde8f-135">Le tableau suivant décrit ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="fde8f-135">The following table describes these namespaces.</span></span>  
  
|<span data-ttu-id="fde8f-136">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="fde8f-136">Namespace</span></span>|<span data-ttu-id="fde8f-137">Description</span><span class="sxs-lookup"><span data-stu-id="fde8f-137">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fde8f-138">[Microsoft. MasterDataServices. Deployment](/previous-versions/sql/sql-server-2016/ff487448(v=sql.130))</span><span class="sxs-lookup"><span data-stu-id="fde8f-138">[Microsoft.MasterDataServices.Deployment](/previous-versions/sql/sql-server-2016/ff487448(v=sql.130))</span></span>|<span data-ttu-id="fde8f-139">Contient les classes qui peuvent être utilisées pour créer un package de déploiement de modèle et pour déployer un package dans une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-139">Contains classes that can be used to create a deployment package from a model and to deploy a package into a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|  
|<xref:Microsoft.MasterDataServices.Services>|<span data-ttu-id="fde8f-140">Contient une classe qui reçoit et traite des opérations de service Web effectuées sur le serveur Web par l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-140">Contains a class that receives and processes web service operations made to the web server computer through the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>|  
|<xref:Microsoft.MasterDataServices.Services.DataContracts>|<span data-ttu-id="fde8f-141">Contient les classes qui définissent la façon dont les données sont transmises à partir de l'ordinateur client par l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] au serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-141">Contains classes that define how data is passed from the client computer through the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to the web server computer.</span></span>|  
|<xref:Microsoft.MasterDataServices.Services.MessageContracts>|<span data-ttu-id="fde8f-142">Contient les classes qui définissent la façon dont les demandes et les réponses sont transmises à partir de l'ordinateur client par l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] au serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fde8f-142">Contains classes that define how requests and responses are passed from the client computer through the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to the web server computer.</span></span>|  
|<xref:Microsoft.MasterDataServices.Services.ServiceContracts>|<span data-ttu-id="fde8f-143">Contient l'interface qui définit les opérations qui peuvent être appelées par le service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fde8f-143">Contains the interface that defines the operations that can be called through the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service.</span></span>|  
  
  