---
title: Vue d’ensemble de Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, overview
- Master Data Services
ms.assetid: 8a4c28b1-6061-4850-80b6-132438b8c156
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8ee1d9205eeff0fd407cb8c2766d8fbceed47bf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610711"
---
# <a name="master-data-services-overview"></a><span data-ttu-id="981b0-102">Vue d'ensemble de Master Data Services</span><span class="sxs-lookup"><span data-stu-id="981b0-102">Master Data Services Overview</span></span>
  <span data-ttu-id="981b0-103">Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], le modèle est le conteneur de niveau le plus élevé dans la structure de vos données de référence.</span><span class="sxs-lookup"><span data-stu-id="981b0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], the model is the highest level container in the structure of your master data.</span></span> <span data-ttu-id="981b0-104">Vous créez un modèle pour gérer des groupes de données semblables, par exemple pour gérer des données de produits en ligne.</span><span class="sxs-lookup"><span data-stu-id="981b0-104">You create a model to manage groups of similar data, for example to manage online product data.</span></span> <span data-ttu-id="981b0-105">Un modèle contient une ou plusieurs entités, et les entités contiennent des membres qui sont des enregistrements de données.</span><span class="sxs-lookup"><span data-stu-id="981b0-105">A model contains one or more entities, and entities contain members that are the data records.</span></span>

|||
|-|-|
|<span data-ttu-id="981b0-106">![Machine virtuelle Azure](../../2014/master-data-services/media/azure-virtual-machine.png "Machine virtuelle Azure")</span><span class="sxs-lookup"><span data-stu-id="981b0-106">![Azure Virtual Machine](../../2014/master-data-services/media/azure-virtual-machine.png "Azure Virtual Machine")</span></span>|<span data-ttu-id="981b0-107">Voulez-vous essayer SQL Server 2016 ?</span><span class="sxs-lookup"><span data-stu-id="981b0-107">Do you want to try out SQL Server 2016?</span></span> <span data-ttu-id="981b0-108">Inscrivez-vous à Microsoft Azure, puis cliquez **[ici](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftsqlserver.sql2017-ws2019?tab=Overview)** pour lancer une machine virtuelle avec SQL Server 2016 déjà installé.</span><span class="sxs-lookup"><span data-stu-id="981b0-108">Sign up for Microsoft Azure, and then go **[Here](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftsqlserver.sql2017-ws2019?tab=Overview)** to spin up a Virtual Machine with SQL Server 2016  already installed.</span></span> <span data-ttu-id="981b0-109">Vous pouvez supprimer la machine virtuelle une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="981b0-109">You can delete the Virtual Machine when you're finished.</span></span>|

 <span data-ttu-id="981b0-110">Par exemple, votre modèle de produit en ligne peut contenir des entités telles qu’un produit, une couleur et un style.</span><span class="sxs-lookup"><span data-stu-id="981b0-110">For example, your online product model may contain entities such as product, color, and style.</span></span> <span data-ttu-id="981b0-111">L’entité de couleur peut contenir des membres pour les couleurs rouge, argent et noir.</span><span class="sxs-lookup"><span data-stu-id="981b0-111">The  color entity may contain  members for the colors red, silver, and black.</span></span>

 <span data-ttu-id="981b0-112">![Modèle de produit avec l’entité de couleur](../../2014/master-data-services/media/mds-colorentity-productmodel.png "Modèle de produit avec l’entité de couleur")</span><span class="sxs-lookup"><span data-stu-id="981b0-112">![Product Model with Color Entity](../../2014/master-data-services/media/mds-colorentity-productmodel.png "Product Model with Color Entity")</span></span>

 <span data-ttu-id="981b0-113">Les modèles contiennent également les attributs qui sont définis dans des entités.</span><span class="sxs-lookup"><span data-stu-id="981b0-113">Models also contain attributes that are defined within entities.</span></span> <span data-ttu-id="981b0-114">Un attribut contient des valeurs qui décrivent les membres d’entité.</span><span class="sxs-lookup"><span data-stu-id="981b0-114">An attribute contains values that help describe the entity members.</span></span> <span data-ttu-id="981b0-115">Il existe des attributs de forme libre et des attributs basés sur un domaine.</span><span class="sxs-lookup"><span data-stu-id="981b0-115">There are free-form attributes and domain-based attributes.</span></span>  <span data-ttu-id="981b0-116">Un attribut basé sur un domaine contient des valeurs qui sont remplies par les membres d’une entité et peuvent être utilisés en tant que valeurs d’attribut pour d’autres entités.</span><span class="sxs-lookup"><span data-stu-id="981b0-116">A domain-based attribute contains values that are populated by members from an entity and can be used as attribute values for other entities.</span></span>

 <span data-ttu-id="981b0-117">Par exemple, une entité de produit peut avoir des attributs de forme libre pour le coût et le poids.</span><span class="sxs-lookup"><span data-stu-id="981b0-117">For example, the product entity might have free-form attributes for cost and weight.</span></span> <span data-ttu-id="981b0-118">De plus, il existe un attribut basé sur un domaine pour la couleur qui contient des valeurs remplies par les membres d’entité de couleur.</span><span class="sxs-lookup"><span data-stu-id="981b0-118">And, there is a domain-based attribute for color that contains values that are populated by the color entity members.</span></span> <span data-ttu-id="981b0-119">Cette liste principale de couleurs est utilisée comme valeurs d’attribut pour l’entité Product.</span><span class="sxs-lookup"><span data-stu-id="981b0-119">This  master list of colors is used as attribute values for the Product entity.</span></span>

 <span data-ttu-id="981b0-120">![Entité de produit avec l’attribut basé sur un domaine de couleur](../../2014/master-data-services/media/mds-productentity-colorattribute.png "Entité de produit avec l’attribut basé sur un domaine de couleur")</span><span class="sxs-lookup"><span data-stu-id="981b0-120">![Product Entity with Color Domain-based Attribute](../../2014/master-data-services/media/mds-productentity-colorattribute.png "Product Entity with Color Domain-based Attribute")</span></span>

 <span data-ttu-id="981b0-121">Les hiérarchies dérivées proviennent des relations entre les entités d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="981b0-121">Derived hierarchies come from the relationships between entities in a model.</span></span> <span data-ttu-id="981b0-122">Il s’agit de relations d’attributs basés sur un domaine.</span><span class="sxs-lookup"><span data-stu-id="981b0-122">These are domain-based attribute relationships.</span></span> <span data-ttu-id="981b0-123">Dans le modèle de produit, par exemple, vous pouvez avoir une hiérarchie dérivée de couleurs provenant de la relation entre les entités de couleur et de produit.</span><span class="sxs-lookup"><span data-stu-id="981b0-123">In the product model for example, you can have a color derived hierarchy that comes from the relationship between the color and product entities.</span></span>

 ![](../../2014/master-data-services/media/mds-derivedhierarchy.png)

 <span data-ttu-id="981b0-124">Une fois que vous avez défini une structure de base pour vos données, vous pouvez commencer à ajouter des enregistrements de données (membres) à l’aide de la fonctionnalité d’importation.</span><span class="sxs-lookup"><span data-stu-id="981b0-124">Once you've defined  a basic structure for your data, you can start adding data records (members) by using the import feature.</span></span> <span data-ttu-id="981b0-125">Vous chargez les données dans des tables de mise en lots, vous validez les données à l’aide de règles d’entreprise, puis vous chargez les données dans des tables MDS.</span><span class="sxs-lookup"><span data-stu-id="981b0-125">You load data into staging tables,  validate the data using business rules, and load the data into  MDS tables.</span></span>  <span data-ttu-id="981b0-126">Vous pouvez également utiliser des règles d’entreprise pour définir des valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="981b0-126">You can also use business rules to set attribute values.</span></span>

 <span data-ttu-id="981b0-127">Le tableau suivant présente les principales tâches [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="981b0-127">The following table outlines the key [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tasks.</span></span> <span data-ttu-id="981b0-128">Sauf indication contraire, pour effectuer l'ensemble des procédures qui suivent, vous devez être un administrateur de modèle.</span><span class="sxs-lookup"><span data-stu-id="981b0-128">Unless otherwise noted, all of the following procedures require you to be a model administrator.</span></span> <span data-ttu-id="981b0-129">Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="981b0-129">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="981b0-130">Vous pouvez compléter les tâches suivantes dans un environnement de test et utiliser les exemples de données fournis lorsque vous installez [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="981b0-130">You might want to complete the following tasks in a test environment and use the sample data provided when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="981b0-131">Pour plus d’informations, consultez [Déploiement de modèles &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="981b0-131">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).</span></span>

|<span data-ttu-id="981b0-132">Action</span><span class="sxs-lookup"><span data-stu-id="981b0-132">Action</span></span>|<span data-ttu-id="981b0-133">Détails</span><span class="sxs-lookup"><span data-stu-id="981b0-133">Details</span></span>|<span data-ttu-id="981b0-134">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="981b0-134">Related Topics</span></span>|
|------------|-------------|--------------------|
|<span data-ttu-id="981b0-135">Créer un modèle</span><span class="sxs-lookup"><span data-stu-id="981b0-135">Create a model</span></span>|<span data-ttu-id="981b0-136">Lorsque vous créez un modèle, il est considéré comme étant la VERSION_1.</span><span class="sxs-lookup"><span data-stu-id="981b0-136">When you create a model, it is considered VERSION_1.</span></span>|[<span data-ttu-id="981b0-137">Modèles &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-137">Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/models-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-138">Créer un modèle &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-138">Create a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-master-data-services.md)|
|<span data-ttu-id="981b0-139">Créer des entités</span><span class="sxs-lookup"><span data-stu-id="981b0-139">Create entities</span></span>|<span data-ttu-id="981b0-140">Créez autant d'entités que nécessaire pour contenir vos membres.</span><span class="sxs-lookup"><span data-stu-id="981b0-140">Create as many entities as you need to contain your members.</span></span>|[<span data-ttu-id="981b0-141">Entités &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-141">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-142">Créer une entité &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-142">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|
|<span data-ttu-id="981b0-143">Créer des entités à utiliser comme attributs basés sur un domaine</span><span class="sxs-lookup"><span data-stu-id="981b0-143">Create entities to use as domain-based attributes</span></span>|<span data-ttu-id="981b0-144">Pour créer un attribut basé sur un domaine, commencez par créer l'entité pour remplir la liste des valeurs d'attribut.</span><span class="sxs-lookup"><span data-stu-id="981b0-144">To create a domain-based attribute, first create the entity to populate the attribute value list.</span></span>|[<span data-ttu-id="981b0-145">Attributs basés sur un domaine &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-145">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-146">Créer un attribut basé sur un domaine &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-146">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|<span data-ttu-id="981b0-147">Créer des attributs pour vos entités</span><span class="sxs-lookup"><span data-stu-id="981b0-147">Create attributes for your entities</span></span>|<span data-ttu-id="981b0-148">Créez des attributs pour décrire des membres.</span><span class="sxs-lookup"><span data-stu-id="981b0-148">Create attributes to describe members.</span></span> <span data-ttu-id="981b0-149">Les attributs de nom et de code sont inclus automatiquement dans chaque entité et ne peuvent pas être supprimés.</span><span class="sxs-lookup"><span data-stu-id="981b0-149">A Name and Code attribute are automatically included in each entity and cannot be removed.</span></span> <span data-ttu-id="981b0-150">Vous pouvez créer d'autres attributs de forme libre pour contenir du texte, des dates, des nombres ou des fichiers.</span><span class="sxs-lookup"><span data-stu-id="981b0-150">You might want to create other free-form attributes to contain text, dates, numbers, or files.</span></span>|[<span data-ttu-id="981b0-151">Attributs &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-151">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-152">Créer un attribut de texte &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-152">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-153">Créer un attribut numérique &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-153">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-154">Créer un attribut de date &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-154">Create a Date Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-date-attribute-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-155">Créer un attribut de lien &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-155">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-156">Créer un attribut de fichier &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|
|<span data-ttu-id="981b0-157">Créer des groupes d'attributs</span><span class="sxs-lookup"><span data-stu-id="981b0-157">Create attribute groups</span></span>|<span data-ttu-id="981b0-158">Si vous avez plus de quatre ou cinq attributs pour une entité, vous pouvez créer des groupes d'attributs.</span><span class="sxs-lookup"><span data-stu-id="981b0-158">If you have more than four or five attributes for an entity, you might want to create attribute groups.</span></span> <span data-ttu-id="981b0-159">Ces groupes correspondent aux onglets affichés au-dessus de la grille dans l' **Explorateur** et permettent de faciliter la navigation en regroupant les attributs.</span><span class="sxs-lookup"><span data-stu-id="981b0-159">These groups are the tabs that are displayed above the grid in **Explorer** and they help ease navigation by grouping attributes together on individual tabs.</span></span> \<INSERT IMAGE>|[<span data-ttu-id="981b0-160">Groupes d’attributs &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-160">Attribute Groups &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attribute-groups-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-161">Créer un groupe d’attributs &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-161">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|
|<span data-ttu-id="981b0-162">Importer des enregistrements de données (membres) pour prendre en charge des entités</span><span class="sxs-lookup"><span data-stu-id="981b0-162">Import data records (members)  for supporting entities</span></span>|<span data-ttu-id="981b0-163">Importez les données de vos entités de prise en charge à l’aide du processus de mise en lots.</span><span class="sxs-lookup"><span data-stu-id="981b0-163">Import the data for your supporting entities by using the staging process.</span></span><br /><br /> <span data-ttu-id="981b0-164">Pour le modèle Product, cela peut signifier l'importation des couleurs ou des tailles.</span><span class="sxs-lookup"><span data-stu-id="981b0-164">For the Product model, this might mean importing colors or sizes.</span></span><br /><br /> <span data-ttu-id="981b0-165">Vous pouvez également créer les membres manuellement.</span><span class="sxs-lookup"><span data-stu-id="981b0-165">You can also create members manually.</span></span><br /><br /> <span data-ttu-id="981b0-166">Remarque : les utilisateurs peuvent créer des membres dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] s’ils ont au minimum l’autorisation **Mise à jour** sur un objet modèle feuille d’une entité et accès à la zone fonctionnelle de l’ **Explorateur** .</span><span class="sxs-lookup"><span data-stu-id="981b0-166">Note: Users can create members in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] if they have a minimum of **Update** permission to an entity's leaf model object and access to the **Explorer** functional area.</span></span>|[<span data-ttu-id="981b0-167">&#40;d’importation de données Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-167">Data Import &#40;Master Data Services&#41;</span></span>](overview-importing-data-from-tables-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-168">Charger ou mettre à jour des membres dans Master Data Services à l'aide du processus de site</span><span class="sxs-lookup"><span data-stu-id="981b0-168">Load or Update Members in Master Data Services by Using the Staging Process</span></span>](../../2014/master-data-services/add-update-and-delete-data-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-169">Créer un membre feuille &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-169">Create a Leaf Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|
|<span data-ttu-id="981b0-170">Créer des règles d'entreprise pour vérifier la qualité des données</span><span class="sxs-lookup"><span data-stu-id="981b0-170">Create business rules to ensure data quality</span></span>|<span data-ttu-id="981b0-171">Créez et publiez des règles d'entreprise pour garantir l'exactitude de vos données.</span><span class="sxs-lookup"><span data-stu-id="981b0-171">Create and publish business rules to ensure the accuracy of your data.</span></span> <span data-ttu-id="981b0-172">Vous pouvez utiliser des règles d'entreprise pour :</span><span class="sxs-lookup"><span data-stu-id="981b0-172">You can use business rules to:</span></span><br /><br /> <span data-ttu-id="981b0-173">Définir les valeurs d'attribut par défaut.</span><span class="sxs-lookup"><span data-stu-id="981b0-173">Set default attribute values.</span></span><br /><br /> <span data-ttu-id="981b0-174">Modifier les valeurs d'attribut.</span><span class="sxs-lookup"><span data-stu-id="981b0-174">Change attribute values.</span></span><br /><br /> <span data-ttu-id="981b0-175">Envoyer des notifications par courrier électronique lorsque les données ne sont pas validées par une règle d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="981b0-175">Send email notifications when data doesn't pass business rule validation.</span></span>|[<span data-ttu-id="981b0-176">Règles d’entreprise &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-176">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-177">Créer et publier une règle d’entreprise &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-177">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-178">Notifications &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-178">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-179">Configurer des notifications par courrier électronique &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-179">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-180">Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-180">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|
|<span data-ttu-id="981b0-181">Importez des enregistrements de données (membres) pour vos entités principales.</span><span class="sxs-lookup"><span data-stu-id="981b0-181">Import data records (members) for your primary entities.</span></span> <span data-ttu-id="981b0-182">Appliquer les règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="981b0-182">Apply business rules</span></span>|<span data-ttu-id="981b0-183">Importez les données de vos entités principales à l’aide du processus de mise en lots.</span><span class="sxs-lookup"><span data-stu-id="981b0-183">Import the data for your primary entities by using the staging process.</span></span> <span data-ttu-id="981b0-184">Quand vous avez terminé, validez la version.</span><span class="sxs-lookup"><span data-stu-id="981b0-184">When done, validate the version.</span></span> <span data-ttu-id="981b0-185">Les règles d’entreprise sont appliquées à tous les membres dans la version de modèle.</span><span class="sxs-lookup"><span data-stu-id="981b0-185">This applies business rules to all members in the model version.</span></span><br /><br /> <span data-ttu-id="981b0-186">Vous pouvez ensuite corriger tous les problèmes de la validation de la règle d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="981b0-186">You can then work to correct any business rule validation issues.</span></span>|[<span data-ttu-id="981b0-187">Validation &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-187">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-188">Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-188">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-189">Procédure stockée de validation &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-189">Validation Stored Procedure &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)|
|<span data-ttu-id="981b0-190">Créer des hiérarchies dérivées</span><span class="sxs-lookup"><span data-stu-id="981b0-190">Create derived hierarchies</span></span>|<span data-ttu-id="981b0-191">Les hiérarchies dérivées peuvent être mises à jour en fonction de l’évolution des besoins de l’entreprise et garantissent que tous les membres sont pris en compte pour le niveau approprié.</span><span class="sxs-lookup"><span data-stu-id="981b0-191">Derived hierarchies can be updated as your business needs change and ensure that all members are accounted for at the appropriate level.</span></span>|[<span data-ttu-id="981b0-192">Hiérarchies dérivées &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-192">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-193">Créer une hiérarchie dérivée &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-193">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="981b0-194">Si nécessaire, créez des hiérarchies explicites</span><span class="sxs-lookup"><span data-stu-id="981b0-194">If needed, create explicit hierarchies</span></span>|<span data-ttu-id="981b0-195">Si vous souhaitez créer des hiérarchies non basées sur le niveau et qui incluent des membres d'une entité unique, vous pouvez créer des hiérarchies explicites.</span><span class="sxs-lookup"><span data-stu-id="981b0-195">If you want to create hierarchies that are not level-based and that include members from a single entity, you can create explicit hierarchies.</span></span>|[<span data-ttu-id="981b0-196">Hiérarchies explicites &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-196">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-197">Créer une hiérarchie explicite &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-197">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="981b0-198">Si nécessaire, créez des collections</span><span class="sxs-lookup"><span data-stu-id="981b0-198">If needed, create collections</span></span>|<span data-ttu-id="981b0-199">Créez une collection si vous souhaitez afficher des regroupements différents de vos membres pour la création de rapports ou l'analyse, et si vous n'avez pas besoin d'une hiérarchie complète.</span><span class="sxs-lookup"><span data-stu-id="981b0-199">If you want to view different groupings of members for reporting or analysis and do not need a complete hierarchy, create a collection.</span></span><br /><br /> <span data-ttu-id="981b0-200">Remarque : les utilisateurs peuvent créer des collections dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] s’ils ont au minimum l’autorisation **Mise à jour** sur l’objet modèle collection et accès à la zone fonctionnelle de l’ **Explorateur** .</span><span class="sxs-lookup"><span data-stu-id="981b0-200">Note: Users can create collections in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] if they have a minimum of **Update** permission to the collection model object and access to the **Explorer** functional area.</span></span>|[<span data-ttu-id="981b0-201">Collections &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-201">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-202">Créer une collection &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-202">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)|
|<span data-ttu-id="981b0-203">Créer des métadonnées définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="981b0-203">Create user-defined metadata</span></span>|<span data-ttu-id="981b0-204">Pour décrire vos objets modèle, ajoutez des métadonnées définies par l'utilisateur à votre modèle.</span><span class="sxs-lookup"><span data-stu-id="981b0-204">To describe your model objects, add user-defined metadata to your model.</span></span> <span data-ttu-id="981b0-205">Les métadonnées peuvent inclure le propriétaire d'un objet ou la source des données.</span><span class="sxs-lookup"><span data-stu-id="981b0-205">The metadata might include the owner of an object or the source the data comes from.</span></span>|[<span data-ttu-id="981b0-206">Métadonnées &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-206">Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/metadata-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-207">Ajouter des métadonnées &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-207">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)|
|<span data-ttu-id="981b0-208">Verrouiller une version de votre modèle et affecter un indicateur de version</span><span class="sxs-lookup"><span data-stu-id="981b0-208">Lock a version of your model and assign a version flag</span></span>|<span data-ttu-id="981b0-209">Verrouillez une version de votre modèle pour empêcher la modification des membres, sauf par les administrateurs.</span><span class="sxs-lookup"><span data-stu-id="981b0-209">Lock a version of your model to prevent changes to the members, except by administrators.</span></span> <span data-ttu-id="981b0-210">Une fois que les données de la version ont été validées par les règles d'entreprise, vous pouvez valider la version et empêcher ainsi à tous les utilisateurs de modifier les membres.</span><span class="sxs-lookup"><span data-stu-id="981b0-210">When the version's data has validated successfully against business rules, you can commit the version, which prevents changes to members by all users.</span></span><br /><br /> <span data-ttu-id="981b0-211">Créez et affectez un indicateur de version au modèle.</span><span class="sxs-lookup"><span data-stu-id="981b0-211">Create and assign a version flag to the model.</span></span> <span data-ttu-id="981b0-212">Les indicateurs aident les utilisateurs et systèmes d'abonnement à identifier la version d'un modèle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="981b0-212">Flags help users and subscribing systems identify which version of a model to use.</span></span>|[<span data-ttu-id="981b0-213">Versions &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-213">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-214">Verrouiller une version &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-214">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-215">Créer un indicateur de version &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-215">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|
|<span data-ttu-id="981b0-216">Créer des vues d'abonnement</span><span class="sxs-lookup"><span data-stu-id="981b0-216">Create subscription views</span></span>|<span data-ttu-id="981b0-217">Pour que vos systèmes d'abonnement consomment vos données de référence, créez des vues d'abonnement qui créent des vues standard dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="981b0-217">For your subscribing systems to consume your master data, create subscription views, which create standard views in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="981b0-218">Exportation de données &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-218">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-219">Créer une vue d’abonnement &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-219">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)|
|<span data-ttu-id="981b0-220">Configurer les autorisations d'accès</span><span class="sxs-lookup"><span data-stu-id="981b0-220">Configure user and group permissions</span></span>|<span data-ttu-id="981b0-221">Vous ne pouvez pas copier les autorisations d'accès d'un environnement test vers un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="981b0-221">You cannot copy user and group permissions from a test to a production environment.</span></span> <span data-ttu-id="981b0-222">Toutefois, vous pouvez utiliser votre environnement de test pour déterminer la sécurité que vous souhaitez utiliser en production.</span><span class="sxs-lookup"><span data-stu-id="981b0-222">However, you can use your test environment to determine the security you want to use eventually in production.</span></span>|[<span data-ttu-id="981b0-223">Sécurité &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-223">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-224">Ajouter un groupe &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-224">Add a Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-a-group-master-data-services.md)<br /><br /> [<span data-ttu-id="981b0-225">Ajouter un utilisateur &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="981b0-225">Add a User &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-a-user-master-data-services.md)|

 <span data-ttu-id="981b0-226">Lorsque vous serez prêt, vous pourrez déployer votre modèle, avec ou sans ses données, dans votre environnement de production.</span><span class="sxs-lookup"><span data-stu-id="981b0-226">When ready, you can deploy your model, with or without its data, to your production environment.</span></span> <span data-ttu-id="981b0-227">Pour plus d’informations, consultez [Déploiement de modèles &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="981b0-227">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).</span></span>

