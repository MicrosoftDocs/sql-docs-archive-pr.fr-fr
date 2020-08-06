---
title: Attributs (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613004"
---
# <a name="attributes-master-data-services"></a><span data-ttu-id="8ebb7-102">Attributs (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8ebb7-102">Attributes (Master Data Services)</span></span>
  <span data-ttu-id="8ebb7-103">Les attributs sont des objets contenus dans des entités [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8ebb7-103">Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] entities.</span></span> <span data-ttu-id="8ebb7-104">Les valeurs d'attribut décrivent les membres de l'entité.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-104">Attribute values describe the members of the entity.</span></span> <span data-ttu-id="8ebb7-105">Un attribut peut être utilisé pour décrire un membre feuille, un membre consolidé ou une collection.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-105">An attribute can be used to describe a leaf member, a consolidated member, or a collection.</span></span>  
  
## <a name="how-attributes-relate-to-other-model-objects"></a><span data-ttu-id="8ebb7-106">Relations entre les attributs et les autres objets de modèle</span><span class="sxs-lookup"><span data-stu-id="8ebb7-106">How Attributes Relate to Other Model Objects</span></span>  
 <span data-ttu-id="8ebb7-107">Vous pouvez considérer un attribut comme une colonne dans une table d'entités.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-107">You can think of an attribute as a column in an entity table.</span></span> <span data-ttu-id="8ebb7-108">Une valeur d'attribut est la valeur utilisée pour décrire un membre spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-108">An attribute value is the value used to describe a specific member.</span></span>  
  
 <span data-ttu-id="8ebb7-109">![Entité Master Data Services représentée en tant que table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Entité Master Data Services représentée en tant que table")</span><span class="sxs-lookup"><span data-stu-id="8ebb7-109">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="8ebb7-110">Lorsque vous créez une entité qui contient de nombreux attributs, vous pouvez les organiser en groupes d'attributs.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-110">When you create an entity that contains many attributes, you can organize the attributes into attribute groups.</span></span> <span data-ttu-id="8ebb7-111">Pour plus d’informations, consultez [Groupes d’attributs &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb7-111">For more information, see [Attribute Groups &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span></span>  
  
## <a name="required-attributes"></a><span data-ttu-id="8ebb7-112">Attributs requis</span><span class="sxs-lookup"><span data-stu-id="8ebb7-112">Required Attributes</span></span>  
 <span data-ttu-id="8ebb7-113">Lorsque vous créez une entité, les attributs Name et Code sont créés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-113">When you create an entity, the Name and Code attributes are automatically created.</span></span> <span data-ttu-id="8ebb7-114">L'attribut Code requiert une valeur et doit être unique dans l'entité.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-114">Code requires a value and must be unique within the entity.</span></span> <span data-ttu-id="8ebb7-115">Vous ne pouvez pas supprimer les attributs Name et Code.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-115">You cannot remove the Name and Code attributes.</span></span>  
  
## <a name="attribute-types"></a><span data-ttu-id="8ebb7-116">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="8ebb7-116">Attribute Types</span></span>  
 <span data-ttu-id="8ebb7-117">Il existe trois types d'attributs :</span><span class="sxs-lookup"><span data-stu-id="8ebb7-117">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="8ebb7-118">Les attributs de forme libre qui acceptent comme entrées de forme libre du texte, des nombres, des dates et des liens.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-118">Free-form attributes, which allow free-form input for text, numbers, dates, or links.</span></span>  
  
-   <span data-ttu-id="8ebb7-119">Les attributs basés sur un domaine, remplis par les entités.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-119">Domain-based attributes, which are populated by entities.</span></span> <span data-ttu-id="8ebb7-120">Pour plus d’informations, consultez [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb7-120">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8ebb7-121">Les attributs de fichier qui permettent de stocker des fichiers, des documents ou des images.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-121">File attributes, which are used to store files, documents, or images.</span></span> <span data-ttu-id="8ebb7-122">Les attributs de fichier qui contribuent à la cohérence de vos données en requérant que les fichiers aient une extension spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-122">File attributes are intended to help with the consistency of your data by requiring files to have a specific extension.</span></span> <span data-ttu-id="8ebb7-123">Les attributs de fichier ne peuvent pas empêcher un utilisateur malveillant de télécharger un fichier d'un type différent.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-123">File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.</span></span>  
  
### <a name="numeric-free-form-attributes"></a><span data-ttu-id="8ebb7-124">Attributs numériques de forme libre</span><span class="sxs-lookup"><span data-stu-id="8ebb7-124">Numeric Free-Form Attributes</span></span>  
 <span data-ttu-id="8ebb7-125">Les attributs numériques de forme libre nécessitent une gestion spéciale, car leurs valeurs sont limitées au type **SqlDouble** .</span><span class="sxs-lookup"><span data-stu-id="8ebb7-125">Numeric free-form attributes require special handling, because numeric free-form attribute values are limited to the **SqlDouble** value type.</span></span>  
  
 <span data-ttu-id="8ebb7-126">Par défaut, une valeur décimale **SqlDouble** est caractérisée par une précision à 15 chiffres, bien qu’un maximum de 17 chiffres soit maintenu en interne.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-126">By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally.</span></span> <span data-ttu-id="8ebb7-127">La précision d'un nombre à virgule flottante a plusieurs conséquences :</span><span class="sxs-lookup"><span data-stu-id="8ebb7-127">The precision of a floating-point number has several consequences:</span></span>  
  
-   <span data-ttu-id="8ebb7-128">Deux nombres à virgule flottante qui apparaissent égaux pour une précision particulière peuvent ne pas l'être parce que leurs chiffres de droite sont différents.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-128">Two floating-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.</span></span>  
  
-   <span data-ttu-id="8ebb7-129">Une opération mathématique ou de comparaison qui utilise un nombre à virgule flottante peut ne pas donner le même résultat si un nombre décimal est utilisé parce que le nombre à virgule flottante peut ne pas se rapprocher exactement du nombre décimal.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-129">A mathematical or comparison operation that uses a floating-point number might not yield the same result if a decimal number is used because the floating-point number might not exactly approximate the decimal number.</span></span>  
  
-   <span data-ttu-id="8ebb7-130">Il peut arriver qu’une valeur n’effectue pas *d’aller-retour* si un nombre à virgule flottante est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-130">A value might not *roundtrip* if a floating-point number is involved.</span></span> <span data-ttu-id="8ebb7-131">Une valeur est dite d'aller-retour lorsqu'une opération convertit un nombre à virgule flottante d'origine sous une autre forme, lorsque l'opération inverse retransforme la forme convertie en un nombre à virgule flottante et lorsque le dernier chiffre du nombre à virgule flottante est égal au chiffre du nombre à virgule flottante d'origine.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-131">A value is said to roundtrip if an operation converts an original floating-point number to another form, an inverse operation transforms the converted form back to a floating-point number, and the final floating-point number is equal to the original floating-point number.</span></span> <span data-ttu-id="8ebb7-132">L'aller-retour peut échouer parce qu'un ou plusieurs chiffres de droite sont perdus ou ont changé au cours d'une conversion.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-132">The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.</span></span>  
  
## <a name="attribute-examples"></a><span data-ttu-id="8ebb7-133">Exemples d'attributs</span><span class="sxs-lookup"><span data-stu-id="8ebb7-133">Attribute Examples</span></span>  
 <span data-ttu-id="8ebb7-134">Dans l'exemple suivant, l'entité comporte les attributs suivants : Name, Code, Subcategory, StandardCost, ListPrice et FilePhoto.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-134">In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="8ebb7-135">Ces attributs décrivent les membres.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-135">These attributes describe the members.</span></span> <span data-ttu-id="8ebb7-136">Chaque membre est représenté par une ligne unique de valeurs d'attribut.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-136">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="8ebb7-137">![Table de l'entité Bike Product](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Table de l'entité Bike Product")</span><span class="sxs-lookup"><span data-stu-id="8ebb7-137">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="8ebb7-138">Dans l'exemple suivant, l'entité Product contient :</span><span class="sxs-lookup"><span data-stu-id="8ebb7-138">In the following example, the Product entity contains:</span></span>  
  
-   <span data-ttu-id="8ebb7-139">Les attributs de forme libre Name, Code, StandardCost et ListPrice.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-139">The free-form attributes of Name, Code, StandardCost and ListPrice.</span></span>  
  
-   <span data-ttu-id="8ebb7-140">L'attribut basé sur un domaine Subcategory.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-140">The domain-based attribute of Subcategory.</span></span>  
  
-   <span data-ttu-id="8ebb7-141">L'attribut de fichier FilePhoto.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-141">The file attribute of FilePhoto.</span></span>  
  
 <span data-ttu-id="8ebb7-142">Subcategory est une entité utilisée comme un attribut basé sur un domaine de Product.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-142">Subcategory is an entity that is used as a domain-based attribute of Product.</span></span> <span data-ttu-id="8ebb7-143">Category est une entité utilisée comme un attribut basé sur un domaine de Subcategory.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-143">Category is an entity that is used as a domain-based attribute of Subcategory.</span></span> <span data-ttu-id="8ebb7-144">Comme l'entité Product, les entités Category et Subcategory contiennent chacune les attributs par défaut Name et Code.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-144">Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.</span></span>  
  
 <span data-ttu-id="8ebb7-145">![Arborescence de l'entité Product](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Arborescence de l'entité Product")</span><span class="sxs-lookup"><span data-stu-id="8ebb7-145">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8ebb7-146">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="8ebb7-146">Related Tasks</span></span>  
  
|<span data-ttu-id="8ebb7-147">Description de la tâche</span><span class="sxs-lookup"><span data-stu-id="8ebb7-147">Task Description</span></span>|<span data-ttu-id="8ebb7-148">Rubrique</span><span class="sxs-lookup"><span data-stu-id="8ebb7-148">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8ebb7-149">Créer un attribut de texte de forme libre.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-149">Create a new free-form text attribute.</span></span>|[<span data-ttu-id="8ebb7-150">Créer un attribut de texte &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-150">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-151">Créer un attribut numérique de forme libre.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-151">Create a new free-form numeric attribute.</span></span>|[<span data-ttu-id="8ebb7-152">Créer un attribut numérique &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-152">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-153">Créer un attribut de lien de forme libre.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-153">Create a new free-form link attribute.</span></span>|[<span data-ttu-id="8ebb7-154">Créer un attribut de lien &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-154">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-155">Créer un attribut de fichier.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-155">Create a new file attribute.</span></span>|[<span data-ttu-id="8ebb7-156">Créer un attribut de fichier &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-157">Créer un attribut basé sur un domaine.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-157">Create a new domain-based attribute.</span></span>|[<span data-ttu-id="8ebb7-158">Créer un attribut basé sur un domaine &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-158">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-159">Modifier le nom d'un attribut existant.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-159">Change the name of an existing attribute.</span></span>|[<span data-ttu-id="8ebb7-160">Modifier le nom d’un attribut &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-160">Change an Attribute Name &#40;Master Data Services&#41;</span></span>](change-an-attribute-name-and-data-type-master-data-services.md)|  
|<span data-ttu-id="8ebb7-161">Ajouter des attributs existants à un groupe de suivi des modifications.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-161">Add existing attributes to a change tracking group.</span></span>|[<span data-ttu-id="8ebb7-162">Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-162">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="8ebb7-163">Supprimer un attribut existant.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-163">Delete an existing attribute.</span></span>|[<span data-ttu-id="8ebb7-164">Supprimer un attribut &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-164">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|<span data-ttu-id="8ebb7-165">Modifier l'ordre des attributs.</span><span class="sxs-lookup"><span data-stu-id="8ebb7-165">Change the order of attributes.</span></span>|[<span data-ttu-id="8ebb7-166">Changer l'ordre des attributs</span><span class="sxs-lookup"><span data-stu-id="8ebb7-166">Change the Order of Attributes</span></span>](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a><span data-ttu-id="8ebb7-167">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="8ebb7-167">Related Content</span></span>  
  
-   [<span data-ttu-id="8ebb7-168">Attributs basés sur un domaine &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-168">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="8ebb7-169">Groupes d’attributs &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-169">Attribute Groups &#40;Master Data Services&#41;</span></span>](attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="8ebb7-170">Membres &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-170">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="8ebb7-171">Autorisations de feuille &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-171">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [<span data-ttu-id="8ebb7-172">Autorisations consolidées &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebb7-172">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  