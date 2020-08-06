---
title: Fonctionnalités de Master Data Services abandonnées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 595b8bf9829ee57ff0d3bee1a82e527876ecc4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615173"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="0b4d4-102">Fonctionnalités Master Data Services supprimées dans SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="0b4d4-102">Discontinued Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="0b4d4-103">Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4d4-103">This topic describes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are no longer available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="0b4d4-104">supprimées</span><span class="sxs-lookup"><span data-stu-id="0b4d4-104">Discontinued Features</span></span>  
 <span data-ttu-id="0b4d4-105">Il n'y a pas de fonctionnalités supprimées dans cette version.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-105">There are no discontinued features in this release.</span></span>  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="0b4d4-106">supprimées</span><span class="sxs-lookup"><span data-stu-id="0b4d4-106">Discontinued Features</span></span>  
  
### <a name="security"></a><span data-ttu-id="0b4d4-107">Sécurité</span><span class="sxs-lookup"><span data-stu-id="0b4d4-107">Security</span></span>  
 <span data-ttu-id="0b4d4-108">Pour faciliter la sécurité d'attribution, vous ne pouvez plus affecter des autorisations d'objet de modèle aux objets de hiérarchie dérivée, de hiérarchie explicite et de groupe d'attributs.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-108">To make assigning security easier, you can no longer assign model object permissions to the Derived Hierarchy, Explicit Hierarchy, and Attribute Group objects.</span></span>  
  
-   <span data-ttu-id="0b4d4-109">Les autorisations de hiérarchie dérivée sont désormais basées sur le modèle.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-109">Derived hierarchy permissions are now based on the model.</span></span> <span data-ttu-id="0b4d4-110">Par exemple, si vous souhaitez qu’un utilisateur dispose d’une autorisation sur une hiérarchie dérivée, vous devez affecter la **mise à jour** à l’objet de modèle.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-110">For example, if you want a user to have permission to a derived hierarchy, you must assign **Update** to the model object.</span></span> <span data-ttu-id="0b4d4-111">Vous pouvez ensuite affecter **refuser** l’accès à toutes les entités auxquelles vous ne voulez pas que l’utilisateur ait accès.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-111">Then you can assign **Deny** access to any entities you don't want the user to have access to.</span></span>  
  
-   <span data-ttu-id="0b4d4-112">Les autorisations de hiérarchie explicite sont maintenant basées sur l'entité.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-112">Explicit hierarchy permissions are now based on the entity.</span></span> <span data-ttu-id="0b4d4-113">Par exemple, si l’utilisateur dispose d’autorisations de **mise à jour** sur une entité de compte, toutes les hiérarchies explicites de l’entité pourront être mises à jour.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-113">For example, if the user has **Update** permissions to an Account entity, then all explicit hierarchies for the entity will be updateable.</span></span>  
  
-   <span data-ttu-id="0b4d4-114">Les autorisations de groupe d’attributs ne peuvent plus être affectées dans la zone fonctionnelle **autorisations d’accès** .</span><span class="sxs-lookup"><span data-stu-id="0b4d4-114">Attribute group permissions can no longer be assigned in the **User and Group Permissions** functional area.</span></span> <span data-ttu-id="0b4d4-115">Au lieu de cela, dans la zone fonctionnelle **administration de système** où les groupes d’attributs sont créés, les utilisateurs et les groupes peuvent disposer de l’autorisation **mettre à jour** sur les groupes d’attributs.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-115">Instead, in the **System Administration** functional area where attribute groups are created, users and groups can be given **Update** permission to attribute groups.</span></span> <span data-ttu-id="0b4d4-116">L’autorisation **en lecture seule sur les** groupes d’attributs n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-116">**Read-only** permission to attribute groups is no longer available.</span></span>  
  
### <a name="staging-process"></a><span data-ttu-id="0b4d4-117">Processus de site</span><span class="sxs-lookup"><span data-stu-id="0b4d4-117">Staging Process</span></span>  
 <span data-ttu-id="0b4d4-118">Vous ne pouvez pas utiliser le nouveau processus de site pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b4d4-118">You cannot use the new staging process to:</span></span>  
  
-   <span data-ttu-id="0b4d4-119">créer ou supprimer des collections ;</span><span class="sxs-lookup"><span data-stu-id="0b4d4-119">Create or delete collections.</span></span>  
  
-   <span data-ttu-id="0b4d4-120">ajouter des membres à des collections ou en supprimer ;</span><span class="sxs-lookup"><span data-stu-id="0b4d4-120">Add members to or remove members from collections.</span></span>  
  
-   <span data-ttu-id="0b4d4-121">réactiver des membres et des collections.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-121">Reactivate members and collections.</span></span>  
  
 <span data-ttu-id="0b4d4-122">Vous pouvez vous servir du processus de site [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] pour utiliser des collections.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-122">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process to work with collections.</span></span>  
  
### <a name="model-deployment-wizard"></a><span data-ttu-id="0b4d4-123">Assistant Déploiement de modèle</span><span class="sxs-lookup"><span data-stu-id="0b4d4-123">Model Deployment Wizard</span></span>  
 <span data-ttu-id="0b4d4-124">Les packages qui contiennent des données ne peuvent plus être créés et déployés à l'aide de l'Assistant dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4d4-124">Packages that contain data can no longer be created and deployed by using the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="0b4d4-125">Un nouvel utilitaire de ligne de commande peut être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-125">A new command line utility can be used instead.</span></span> <span data-ttu-id="0b4d4-126">Pour plus d’informations, consultez [Déploiement de modèles &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-126">For more information, see [Deploying Models &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span></span>  
  
 <span data-ttu-id="0b4d4-127">L'Assistant peut toujours être utilisé pour créer et déployer des packages qui ne contiennent pas de données.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-127">The wizard can still be used to create and deploy packages that do not contain data.</span></span>  
  
 <span data-ttu-id="0b4d4-128">En outre, les packages peuvent être déployés uniquement dans l'édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-128">In addition, packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="0b4d4-129">Cela signifie que les packages créés dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ne peuvent pas être déployés sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4d4-129">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="0b4d4-130">Vous devez déployer le package dans un environnement [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] puis mettre à niveau la base de données vers [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4d4-130">You must deploy the package to a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] environment and then upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="code-generation-business-rules"></a><span data-ttu-id="0b4d4-131">Règles d'entreprise de génération de code</span><span class="sxs-lookup"><span data-stu-id="0b4d4-131">Code Generation Business Rules</span></span>  
 <span data-ttu-id="0b4d4-132">Les règles d'entreprise qui génèrent automatiquement des valeurs pour l'attribut Code sont maintenant administrées différemment.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-132">Business rules that automatically generate values for the Code attribute are now administered differently.</span></span> <span data-ttu-id="0b4d4-133">Auparavant, pour générer des valeurs pour l’attribut code, vous avez utilisé l' **attribut default à une action valeur générée** dans la zone fonctionnelle **administration de système** sous **règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-133">Previously, to generate values for the Code attribute, you used the **Default attribute to a generated value** action in the **System Administration** functional area under **Business Rules**.</span></span> <span data-ttu-id="0b4d4-134">Désormais, dans **administration de système**, vous devez modifier l’entité pour activer les valeurs de code générées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-134">Now, in **System Administration**, you must edit the entity to enable automatically-generated Code values.</span></span> <span data-ttu-id="0b4d4-135">Pour plus d’informations, consultez [création automatique de Code &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-135">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span></span>  
  
 <span data-ttu-id="0b4d4-136">Si vous possédez un package de déploiement de modèle [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] qui contient une règle de ce type, lorsque vous mettez à niveau la base de données vers [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], la règle d'entreprise est exclue.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-136">If you have a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] model deployment package that contains a rule of this type, when you upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the business rule will be excluded.</span></span>  
  
### <a name="bulk-updates-and-exporting"></a><span data-ttu-id="0b4d4-137">Mises à jour et exporations en bloc</span><span class="sxs-lookup"><span data-stu-id="0b4d4-137">Bulk Updates and Exporting</span></span>  
 <span data-ttu-id="0b4d4-138">Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus mettre à jour les valeurs d'attribut de plusieurs membres en bloc.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-138">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer update attribute values for multiple members in bulk.</span></span> <span data-ttu-id="0b4d4-139">Pour effectuer des mises à jour en bloc, utilisez le processus de site ou [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b4d4-139">To do bulk updates, use the staging process or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="0b4d4-140">Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus exporter des membres vers Excel.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-140">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer export members to Excel.</span></span> <span data-ttu-id="0b4d4-141">Pour travailler avec des membres dans Excel, utilisez le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b4d4-141">To work with members in Excel, use the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="0b4d4-142">Transactions</span><span class="sxs-lookup"><span data-stu-id="0b4d4-142">Transactions</span></span>  
 <span data-ttu-id="0b4d4-143">Dans la zone fonctionnelle **Explorateur** , les utilisateurs ne peuvent plus restaurer leurs propres transactions.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-143">In the **Explorer** functional area, users can no longer revert their own transactions.</span></span> <span data-ttu-id="0b4d4-144">Auparavant, les utilisateurs pouvaient annuler les modifications apportées aux données dans l' **Explorateur**.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-144">Previously, users could revert changes they made to data in **Explorer**.</span></span> <span data-ttu-id="0b4d4-145">Les administrateurs peuvent toujours rétablir des transactions pour tous les utilisateurs dans la zone fonctionnelle **gestion des versions** .</span><span class="sxs-lookup"><span data-stu-id="0b4d4-145">Administrators can still revert transactions for all users in the **Version Management** functional area.</span></span>  
  
 <span data-ttu-id="0b4d4-146">Les annotations sont maintenant permanentes et ne peuvent pas être supprimées.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-146">Annotations are now permanent and cannot be deleted.</span></span> <span data-ttu-id="0b4d4-147">Précédemment, les annotations étaient considérées comme des transactions et pouvaient être supprimées en inversant la transaction.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-147">Previously, annotations were considered transactions and could be deleted by reverting the transaction.</span></span>  
  
### <a name="web-service"></a><span data-ttu-id="0b4d4-148">Service Web</span><span class="sxs-lookup"><span data-stu-id="0b4d4-148">Web Service</span></span>  
 <span data-ttu-id="0b4d4-149">Le service Web de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est maintenant activé automatiquement, conformément aux exigences de Silverlight.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-149">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] web service is now enabled automatically, as required by Silverlight.</span></span> <span data-ttu-id="0b4d4-150">Précédemment, le service Web devait être activé manuellement.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-150">Previously, the web service had to be enabled manually.</span></span>  
  
### <a name="powershell-cmdlets"></a><span data-ttu-id="0b4d4-151">Applets de commande Powershell</span><span class="sxs-lookup"><span data-stu-id="0b4d4-151">PowerShell Cmdlets</span></span>  
 <span data-ttu-id="0b4d4-152">MDS n'inclut plus les applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-152">MDS no longer includes PowerShell cmdlets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b4d4-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b4d4-153">See Also</span></span>  
 [<span data-ttu-id="0b4d4-154">Fonctionnalités Master Data Services déconseillées dans SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="0b4d4-154">Deprecated Master Data Services Features in SQL Server 2014</span></span>](deprecated-master-data-services-features.md)  
  
  