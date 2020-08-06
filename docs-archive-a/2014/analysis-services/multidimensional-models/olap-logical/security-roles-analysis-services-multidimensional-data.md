---
title: Rôles de sécurité (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62abaab5a8f74dfee7d51962f2fb243dc6eb20a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705560"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a><span data-ttu-id="fbea6-102">Rôles de sécurité (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="fbea6-102">Security Roles  (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fbea6-103">Les rôles sont utilisés dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour gérer la sécurité des [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objets et des données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-103">Roles are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] to manage security for [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects and data.</span></span> <span data-ttu-id="fbea6-104">En clair, un rôle associe les identificateurs de sécurité (SID) des utilisateurs et des groupes de Microsoft Windows qui disposent de droits et d'autorisations d'accès spécifiques, définis pour des objets gérés par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbea6-104">In basic terms, a role associates the security identifiers (SIDs) of Microsoft Windows users and groups that have specific access rights and permissions defined for objects managed by an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fbea6-105">Deux types de rôles sont fournis dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="fbea6-105">Two types of roles are provided in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="fbea6-106">le rôle du serveur, un rôle fixe qui fournit un accès administrateur à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)];</span><span class="sxs-lookup"><span data-stu-id="fbea6-106">The server role, a fixed role that provides administrator access to an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fbea6-107">les rôles de base de données, des rôles définis par les administrateurs pour contrôler l'accès des utilisateurs qui ne sont pas administrateurs aux objets et aux données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-107">Database roles, roles defined by administrators to control access to objects and data for non-administrator users.</span></span>  
  
 <span data-ttu-id="fbea6-108">La sécurité dans la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sécurité est gérée à l’aide de rôles et d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="fbea6-108">Security in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] security is managed by using roles and permissions.</span></span> <span data-ttu-id="fbea6-109">Les rôles sont des groupes d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbea6-109">Roles are groups of users.</span></span> <span data-ttu-id="fbea6-110">Les utilisateurs, également appelés membres, peuvent être ajoutés ou supprimés des rôles.</span><span class="sxs-lookup"><span data-stu-id="fbea6-110">Users, also called members, can be added or removed from roles.</span></span> <span data-ttu-id="fbea6-111">Les autorisations pour les objets sont spécifiées par les rôles et tous les membres dans un rôle peuvent utiliser les objets pour lesquels le rôle a des autorisations.</span><span class="sxs-lookup"><span data-stu-id="fbea6-111">Permissions for objects are specified by roles, and all members in a role can use the objects for which the role has permissions.</span></span> <span data-ttu-id="fbea6-112">Tous les membres dans un rôle ont des autorisations aux objets égales.</span><span class="sxs-lookup"><span data-stu-id="fbea6-112">All members in a role have equal permissions to the objects.</span></span> <span data-ttu-id="fbea6-113">Les autorisations sont particulières aux objets.</span><span class="sxs-lookup"><span data-stu-id="fbea6-113">Permissions are particular to objects.</span></span> <span data-ttu-id="fbea6-114">Chaque objet a une collection d'autorisations incluant les autorisations accordées pour cet objet, différents jeux d'autorisations peuvent être accordés sur un objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-114">Each object has a permissions collection with the permissions granted on that object, different sets of permissions can be granted on an object.</span></span> <span data-ttu-id="fbea6-115">Chaque autorisation de la collection d'autorisations de l'objet se voit attribuer un rôle unique.</span><span class="sxs-lookup"><span data-stu-id="fbea6-115">Each permission, from the permissions collection of the object, has a single role assigned to it.</span></span>  
  
## <a name="role-and-role-member-objects"></a><span data-ttu-id="fbea6-116">Rôle et objets membres du rôle</span><span class="sxs-lookup"><span data-stu-id="fbea6-116">Role and Role Member Objects</span></span>  
 <span data-ttu-id="fbea6-117">Un rôle est un objet conteneur d'une collection d'utilisateurs (membres).</span><span class="sxs-lookup"><span data-stu-id="fbea6-117">A role is a containing object for a collection of users (members).</span></span> <span data-ttu-id="fbea6-118">La définition du rôle établit l'appartenance des utilisateurs dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbea6-118">A Role definition establishes the membership of the users in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fbea6-119">Parce que les autorisations sont assignées par rôle, un utilisateur doit être le membre d'un rôle avant d'avoir accès à tout objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-119">Because permissions are assigned by role, a user must be a member of a role before the user has access to any object.</span></span>  
  
 <span data-ttu-id="fbea6-120">Un objet <xref:Microsoft.AnalysisServices.Role> est composé des paramètres Name, Id et Members.</span><span class="sxs-lookup"><span data-stu-id="fbea6-120">A <xref:Microsoft.AnalysisServices.Role> object is composed of the parameters Name, Id, and Members.</span></span> <span data-ttu-id="fbea6-121">Le paramètre Members est une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="fbea6-121">Members is a collection of strings.</span></span> <span data-ttu-id="fbea6-122">Chaque membre contient le nom d'utilisateur sous la forme « domaine\nom d'utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="fbea6-122">Each member contains the user name in the form of "domain\username".</span></span> <span data-ttu-id="fbea6-123">Le nom est une chaîne qui contient le nom du rôle.</span><span class="sxs-lookup"><span data-stu-id="fbea6-123">Name is a string that contains the name of the role.</span></span> <span data-ttu-id="fbea6-124">L'ID est une chaîne qui contient l'identificateur unique du rôle.</span><span class="sxs-lookup"><span data-stu-id="fbea6-124">ID is a string that contains the unique identifier of the role.</span></span>  
  
### <a name="server-role"></a><span data-ttu-id="fbea6-125">Rôle serveur</span><span class="sxs-lookup"><span data-stu-id="fbea6-125">Server Role</span></span>  
 <span data-ttu-id="fbea6-126">Le rôle de serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] définit l'accès d'administrateur des utilisateurs et des groupes Windows à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbea6-126">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server role defines administrative access of Windows users and groups to an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fbea6-127">Les membres de ce rôle ont accès à toutes les bases de données et tous les objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sur une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]et ils peuvent effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fbea6-127">Members of this role have access to all [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] databases and objects on an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="fbea6-128">effectuer des fonctions d'administration de niveau serveur à l'aide de SQL Server Management Studio ou de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], notamment créer des bases de données et définir des propriétés de niveau serveur ;</span><span class="sxs-lookup"><span data-stu-id="fbea6-128">Perform server-level administrative functions using SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], including creating databases and setting server-level properties.</span></span>  
  
-   <span data-ttu-id="fbea6-129">effectuer des fonctions d'administration par programme avec AMO (Analysis Management Objects) ;</span><span class="sxs-lookup"><span data-stu-id="fbea6-129">Perform administrative functions programmatically with Analysis Management Objects (AMO).</span></span>  
  
-   <span data-ttu-id="fbea6-130">maintenir les rôles de base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="fbea6-130">Maintain [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database roles.</span></span>  
  
-   <span data-ttu-id="fbea6-131">démarrer des traces (à des fins autres que le traitement des événements, qui peut être effectué par un rôle de base de données ayant accès aux processus).</span><span class="sxs-lookup"><span data-stu-id="fbea6-131">Start traces (other than for processing events, which can be performed by a database role with Process access).</span></span>  
  
 <span data-ttu-id="fbea6-132">Chaque instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] a un rôle de serveur qui définit les utilisateurs pouvant l'administrer.</span><span class="sxs-lookup"><span data-stu-id="fbea6-132">Every instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] has a server role that defines which users can administer that instance.</span></span> <span data-ttu-id="fbea6-133">Le nom et ID de ce rôle est Administrateurs et contrairement aux rôles de base de données, le rôle du serveur ne peut pas être supprimé et des autorisations ne peuvent pas être ajoutées ou supprimées.</span><span class="sxs-lookup"><span data-stu-id="fbea6-133">The name and ID of this role is Administrators, and unlike database roles, the server role cannot be deleted, nor can permissions be added or removed.</span></span> <span data-ttu-id="fbea6-134">En d'autres termes, un utilisateur est ou n'est pas administrateur pour une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], selon qu'il ou elle est inclus dans le rôle de serveur de cette instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbea6-134">In other words, a user either is or is not an administrator for an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], depending on whether he or she is included in the server role for that instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="database-roles"></a><span data-ttu-id="fbea6-135">Rôles de base de données</span><span class="sxs-lookup"><span data-stu-id="fbea6-135">Database Roles</span></span>  
 <span data-ttu-id="fbea6-136">Un rôle de base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] définit l'accès utilisateur aux objets et données d'une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fbea6-136">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database role defines user access to objects and data in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fbea6-137">Un rôle de base de données est créé comme un objet distinct dans une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et s'applique uniquement à la base de données dans laquelle il est créé.</span><span class="sxs-lookup"><span data-stu-id="fbea6-137">A database role is created as a separate object in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database, and applies only to the database in which that role is created.</span></span> <span data-ttu-id="fbea6-138">Les utilisateurs et les groupes Windows sont inclus dans le rôle par un administrateur, qui définit également les autorisations à l'intérieur du rôle.</span><span class="sxs-lookup"><span data-stu-id="fbea6-138">Windows users and groups are included in the role by an administrator, who also defines permissions within the role.</span></span>  
  
 <span data-ttu-id="fbea6-139">Les autorisations d'un rôle peuvent permettre aux membres d'accéder à la base de données et de l'administrer, y compris les objets et les données qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="fbea6-139">The permissions of a role may allow members to access and administer the database, in addition to the objects and data within the database.</span></span> <span data-ttu-id="fbea6-140">Chaque autorisation a un ou plusieurs droits d'accès qui lui sont associés, ce qui permet d'affiner le contrôle relatif à l'accès à un objet particulier de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-140">Each permission has one or more access rights associated with it, which in turn give the permission finer control over access to a particular object in the database.</span></span>  
  
## <a name="permission-objects"></a><span data-ttu-id="fbea6-141">Objets Permission</span><span class="sxs-lookup"><span data-stu-id="fbea6-141">Permission Objects</span></span>  
 <span data-ttu-id="fbea6-142">Les autorisations sont associées à un objet (cube, dimension et autres) pour un rôle particulier.</span><span class="sxs-lookup"><span data-stu-id="fbea6-142">Permissions are associated with an object (cube, dimension, others) for a particular role.</span></span> <span data-ttu-id="fbea6-143">Les autorisations spécifient les opérations que le membre d'un rôle peut effectuer sur un objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-143">Permissions specify what operations the member of that role can perform on that object.</span></span>  
  
 <span data-ttu-id="fbea6-144">La classe <xref:Microsoft.AnalysisServices.Permission> est une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="fbea6-144">The <xref:Microsoft.AnalysisServices.Permission> class is an abstract class.</span></span> <span data-ttu-id="fbea6-145">Par conséquent, vous devez utiliser les classes dérivées pour définir des autorisations sur les objets correspondants.</span><span class="sxs-lookup"><span data-stu-id="fbea6-145">Therefore, you must use the derived classes to define permissions on the corresponding objects.</span></span> <span data-ttu-id="fbea6-146">Pour chaque objet, une classe d'autorisation dérivée est définie.</span><span class="sxs-lookup"><span data-stu-id="fbea6-146">For each object, a permission derived class is defined.</span></span>  
  
|<span data-ttu-id="fbea6-147">Object</span><span class="sxs-lookup"><span data-stu-id="fbea6-147">Object</span></span>|<span data-ttu-id="fbea6-148">Classe</span><span class="sxs-lookup"><span data-stu-id="fbea6-148">Class</span></span>|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 <span data-ttu-id="fbea6-149">Les actions possibles activées par les autorisations sont répertoriées dans la liste :</span><span class="sxs-lookup"><span data-stu-id="fbea6-149">Possible actions enabled by permissions are shown in the list:</span></span>  
  
|<span data-ttu-id="fbea6-150">Action</span><span class="sxs-lookup"><span data-stu-id="fbea6-150">Action</span></span>|<span data-ttu-id="fbea6-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="fbea6-151">Values</span></span>|<span data-ttu-id="fbea6-152">Explication</span><span class="sxs-lookup"><span data-stu-id="fbea6-152">Explanation</span></span>|  
|------------|------------|-----------------|  
|<span data-ttu-id="fbea6-153">Process</span><span class="sxs-lookup"><span data-stu-id="fbea6-153">Process</span></span>|<span data-ttu-id="fbea6-154">{`true`, `false`}</span><span class="sxs-lookup"><span data-stu-id="fbea6-154">{`true`, `false`}</span></span><br /><br /> <span data-ttu-id="fbea6-155">Valeur par défaut=`false`</span><span class="sxs-lookup"><span data-stu-id="fbea6-155">Default=`false`</span></span>|<span data-ttu-id="fbea6-156">Si `true`, les membres peuvent traiter l'objet et tout objet contenu dans l'objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-156">If `true`, members can process the object and any object that is contained in the object.</span></span><br /><br /> <span data-ttu-id="fbea6-157">Les autorisations de processus ne s'appliquent pas aux modèles d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-157">Process permissions do not apply to mining models.</span></span> <span data-ttu-id="fbea6-158">Les autorisations <xref:Microsoft.AnalysisServices.MiningModel> sont toujours héritées de l'objet <xref:Microsoft.AnalysisServices.MiningStructure>.</span><span class="sxs-lookup"><span data-stu-id="fbea6-158"><xref:Microsoft.AnalysisServices.MiningModel> permissions are always inherited from <xref:Microsoft.AnalysisServices.MiningStructure>.</span></span>|  
|<span data-ttu-id="fbea6-159">ReadDefinition</span><span class="sxs-lookup"><span data-stu-id="fbea6-159">ReadDefinition</span></span>|<span data-ttu-id="fbea6-160">{`None`, `Basic`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="fbea6-160">{`None`, `Basic`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="fbea6-161">Valeur par défaut=`None`</span><span class="sxs-lookup"><span data-stu-id="fbea6-161">Default=`None`</span></span>|<span data-ttu-id="fbea6-162">Spécifie si les membres peuvent lire les définitions de données (ASSL) associées à l'objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-162">Specifies whether members can read the data definition (ASSL) associated with the object.</span></span><br /><br /> <span data-ttu-id="fbea6-163">Si `Allowed`, les membres peuvent lire les définitions ASSL associées à l'objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-163">If `Allowed`, members can read the ASSL associated with the object.</span></span><br /><br /> <span data-ttu-id="fbea6-164">`Basic` et `Allowed` sont hérités par les objets contenus dans l'objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-164">`Basic` and `Allowed` are inherited by objects that are contained in the object.</span></span> <span data-ttu-id="fbea6-165">`Allowed` remplace `Basic` et `None`.</span><span class="sxs-lookup"><span data-stu-id="fbea6-165">`Allowed` overrides `Basic` and `None`.</span></span><br /><br /> <span data-ttu-id="fbea6-166">`Allowed` est requis pour DISCOVER_XML_METADATA sur un objet.</span><span class="sxs-lookup"><span data-stu-id="fbea6-166">`Allowed` is required for DISCOVER_XML_METADATA on an object.</span></span> <span data-ttu-id="fbea6-167">`Basic` est requis pour créer des objets liés et des cubes locaux.</span><span class="sxs-lookup"><span data-stu-id="fbea6-167">`Basic` is required to create linked objects and local cubes.</span></span>|  
|<span data-ttu-id="fbea6-168">Lire</span><span class="sxs-lookup"><span data-stu-id="fbea6-168">Read</span></span>|<span data-ttu-id="fbea6-169">{`None`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="fbea6-169">{`None`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="fbea6-170">Valeur par défaut =`None` (sauf pour DimensionPermission, où la valeur par défaut est `Allowed`)</span><span class="sxs-lookup"><span data-stu-id="fbea6-170">Default=`None` (Except for DimensionPermission, where default=`Allowed`)</span></span>|<span data-ttu-id="fbea6-171">Spécifie si les membres ont l'accès en lecture aux ensembles de lignes et au contenu des données du schéma.</span><span class="sxs-lookup"><span data-stu-id="fbea6-171">Specifies whether members have read access to schema rowsets and data content.</span></span><br /><br /> <span data-ttu-id="fbea6-172">`Allowed`octroie l’accès en lecture à une base de données, ce qui vous permet de découvrir une base de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-172">`Allowed` gives read access on a database, which lets you discover a database.</span></span><br /><br /> <span data-ttu-id="fbea6-173">`Allowed` sur un cube, donne l'accès en lecture aux ensembles de lignes du schéma et l'accès au contenu du cube (sauf si contraint par <xref:Microsoft.AnalysisServices.CellPermission> et <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span><span class="sxs-lookup"><span data-stu-id="fbea6-173">`Allowed` on a cube gives read access in schema rowsets and access to cube content (unless constrained by <xref:Microsoft.AnalysisServices.CellPermission> and <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span></span><br /><br /> <span data-ttu-id="fbea6-174">`Allowed` sur une dimension, accorde une autorisation de lecture sur tous les attributs dans la dimension (sauf si contraint par <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span><span class="sxs-lookup"><span data-stu-id="fbea6-174">`Allowed` on a dimension grants that read permission on all attributes in the dimension (unless constrained by <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span></span> <span data-ttu-id="fbea6-175">L'autorisation de lecture est utilisée uniquement pour l'héritage statique à l'objet <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.</span><span class="sxs-lookup"><span data-stu-id="fbea6-175">Read permission is used for static inheritance to the <xref:Microsoft.AnalysisServices.CubeDimensionPermission> only.</span></span> <span data-ttu-id="fbea6-176">`None` sur une dimension masque la dimension et donne uniquement l'accès au membre par défaut pour les attributs pouvant faire l'objet d'une agrégation ; une erreur est levée si la dimension contient un attribut ne pouvant pas faire l'objet d'une agrégation.</span><span class="sxs-lookup"><span data-stu-id="fbea6-176">`None` on a dimension hides the dimension and gives access to the default member only for aggregatable attributes; an error is raised if the dimension contains a non-aggregatable attribute.</span></span><br /><br /> <span data-ttu-id="fbea6-177">`Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningModelPermission> accorde des autorisations pour consulter des objets dans les ensembles de lignes de schéma et effectuer des jointures de prédiction.</span><span class="sxs-lookup"><span data-stu-id="fbea6-177">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningModelPermission> grants permissions to see objects in schema rowsets and to perform predict joins.</span></span><br /><br /> <span data-ttu-id="fbea6-178">**NoteAllowed** est requis pour lire ou écrire dans n’importe quel objet de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-178">**NoteAllowed** is required to read or write to any object in the database.</span></span>|  
|<span data-ttu-id="fbea6-179">Write</span><span class="sxs-lookup"><span data-stu-id="fbea6-179">Write</span></span>|<span data-ttu-id="fbea6-180">{`None`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="fbea6-180">{`None`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="fbea6-181">Valeur par défaut=`None`</span><span class="sxs-lookup"><span data-stu-id="fbea6-181">Default=`None`</span></span>|<span data-ttu-id="fbea6-182">Spécifie si les membres ont un accès en écriture aux données de l'objet parent.</span><span class="sxs-lookup"><span data-stu-id="fbea6-182">Specifies whether members have write access to data of the parent object.</span></span><br /><br /> <span data-ttu-id="fbea6-183">L'accès s'applique aux sous-classes <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, et <xref:Microsoft.AnalysisServices.MiningModel>.</span><span class="sxs-lookup"><span data-stu-id="fbea6-183">Access applies to <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, and <xref:Microsoft.AnalysisServices.MiningModel> subclasses.</span></span> <span data-ttu-id="fbea6-184">Il ne s'applique pas aux sous-classes <xref:Microsoft.AnalysisServices.MiningStructure> de base de données, qui génèrent une erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="fbea6-184">It does not apply to database <xref:Microsoft.AnalysisServices.MiningStructure> subclasses, which generates a validation error.</span></span><br /><br /> <span data-ttu-id="fbea6-185">`Allowed` sur un objet <xref:Microsoft.AnalysisServices.Dimension> accorde une autorisation d'écriture sur tous les attributs dans une dimension.</span><span class="sxs-lookup"><span data-stu-id="fbea6-185">`Allowed` on a <xref:Microsoft.AnalysisServices.Dimension> grants write permission on all attributes in the dimension.</span></span><br /><br /> <span data-ttu-id="fbea6-186">`Allowed` sur un objet <xref:Microsoft.AnalysisServices.Cube> accorde l'autorisation d'écriture sur les cellules du cube pour les partitions définies comme Type=writeback.</span><span class="sxs-lookup"><span data-stu-id="fbea6-186">`Allowed` on a <xref:Microsoft.AnalysisServices.Cube> grants write permission on the cells of the cube for partitions defined as Type=writeback.</span></span><br /><br /> <span data-ttu-id="fbea6-187">`Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningModel> accorde l'autorisation de modifier le contenu du modèle.</span><span class="sxs-lookup"><span data-stu-id="fbea6-187">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningModel> grants permission to modify model content.</span></span><br /><br /> <span data-ttu-id="fbea6-188">`Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningStructure> n'a aucune signification spécifique dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbea6-188">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningStructure> has no specific meaning in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fbea6-189">**Remarque :**  Impossible d’affecter la valeur Write à `Allowed` , sauf si Read a également la valeur`Allowed`</span><span class="sxs-lookup"><span data-stu-id="fbea6-189">**Note:**  Write cannot be set to `Allowed` unless read is also set to `Allowed`</span></span>|  
|<span data-ttu-id="fbea6-190">Remarque de l’administration **:** uniquement dans les autorisations de base de données</span><span class="sxs-lookup"><span data-stu-id="fbea6-190">Administer **Note:**  Only in Database permissions</span></span>|<span data-ttu-id="fbea6-191">{`true`, `false`}</span><span class="sxs-lookup"><span data-stu-id="fbea6-191">{`true`, `false`}</span></span><br /><br /> <span data-ttu-id="fbea6-192">Valeur par défaut=`false`</span><span class="sxs-lookup"><span data-stu-id="fbea6-192">Default=`false`</span></span>|<span data-ttu-id="fbea6-193">Spécifie si les membres peuvent administrer une base de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-193">Specifies whether members can administer a database.</span></span><br /><br /> <span data-ttu-id="fbea6-194">`true` accorde aux membres l'accès à tous les objets dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="fbea6-194">`true` grants members access to all objects in a database.</span></span><br /><br /> <span data-ttu-id="fbea6-195">Un membre peut avoir des autorisations d'administrateur pour une base de données spécifique, mais pas pour les autres.</span><span class="sxs-lookup"><span data-stu-id="fbea6-195">A member can have Administer permissions for a specific database, but not for others.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbea6-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbea6-196">See Also</span></span>  
 [<span data-ttu-id="fbea6-197">Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fbea6-197">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  