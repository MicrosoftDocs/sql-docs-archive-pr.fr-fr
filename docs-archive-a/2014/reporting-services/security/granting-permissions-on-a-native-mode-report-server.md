---
title: Octroi d’autorisations sur un serveur de rapports en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 22967a7c9c6b8cc3e14ecffed117d1ab821788f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613820"
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a><span data-ttu-id="86ad8-102">Octroi d'autorisations sur un serveur de rapports en mode natif</span><span class="sxs-lookup"><span data-stu-id="86ad8-102">Granting Permissions on a Native Mode Report Server</span></span>
  <span data-ttu-id="86ad8-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise l'autorisation basée sur les rôles et un sous-système d'authentification pour déterminer qui est habilité à effectuer des opérations et à accéder aux éléments d'un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses role-based authorization and an authentication subsystem to determine who can perform operations and access items on a report server.</span></span> <span data-ttu-id="86ad8-104">L'autorisation basée sur les rôles catégorise en rôles l'ensemble des actions qu'un utilisateur ou groupe peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="86ad8-104">Role-based authorization categorizes into roles the set of actions that a user or group can perform.</span></span> <span data-ttu-id="86ad8-105">L'authentification repose sur l'authentification Windows intégrée ou sur un module d'authentification personnalisé que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="86ad8-105">Authentication is based on built-in Windows Authentication or a custom authentication module that you provide.</span></span> <span data-ttu-id="86ad8-106">Vous pouvez utiliser des rôles prédéfinis ou personnalisés avec chacun de ces types d'authentifications.</span><span class="sxs-lookup"><span data-stu-id="86ad8-106">You can use predefined or custom roles with either authentication type.</span></span>  
  
## <a name="using-roles-to-grant-report-server-access"></a><span data-ttu-id="86ad8-107">Utilisation de rôles pour octroyer l'accès au serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="86ad8-107">Using Roles to Grant Report Server Access</span></span>  
 <span data-ttu-id="86ad8-108">Tous les utilisateurs interagissent avec un serveur de rapports dans le contexte d'un rôle qui définit un niveau spécifique d'accès.</span><span class="sxs-lookup"><span data-stu-id="86ad8-108">All users interact with a report server within the context of a role that defines a specific level of access.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="86ad8-109">inclut des rôles prédéfinis que vous pouvez affecter aux utilisateurs et aux groupes pour fournir l’accès immédiat à un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-109">includes predefined roles that you can assign to users and groups to provide immediate access to a report server.</span></span> <span data-ttu-id="86ad8-110">**Gestionnaire de contenu**, **Serveur de publication**et **Navigateur** sont des exemples de rôles prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="86ad8-110">**ContentManager**, **Publisher**, and **Browser** are examples of predefined roles.</span></span> <span data-ttu-id="86ad8-111">Chaque rôle définit un ensemble de tâches associées.</span><span class="sxs-lookup"><span data-stu-id="86ad8-111">Each role defines a collection of related tasks.</span></span> <span data-ttu-id="86ad8-112">Par exemple, un **serveur de publication** est autorisé à ajouter des rapports et à créer des dossiers pour stocker ces mêmes rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-112">For example, a **Publisher** has permission to add reports and create folders for storing those reports.</span></span>  
  
 <span data-ttu-id="86ad8-113">Les attributions de rôles sont généralement héritées d'un nœud parent, mais vous pouvez rompre l'héritage d'autorisation en créant une attribution de rôles pour un élément particulier.</span><span class="sxs-lookup"><span data-stu-id="86ad8-113">Role assignments are typically inherited from a parent node, but you can break permission inheritance by creating a new role assignment for a particular item.</span></span> <span data-ttu-id="86ad8-114">Un utilisateur membre du rôle **Gestionnaire de contenu** pour un rapport peut être membre du rôle **Lecteur** pour un autre rapport.</span><span class="sxs-lookup"><span data-stu-id="86ad8-114">A user who is a member of the **Content Manager** role for one report may be a member of the **Browser** role for another report.</span></span>  
  
 <span data-ttu-id="86ad8-115">Pour accorder l'accès aux éléments et aux opérations du serveur de rapports, suivez les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="86ad8-115">To grant access to report server items and operations, follow these guidelines:</span></span>  
  
1.  <span data-ttu-id="86ad8-116">Examinez les rôles prédéfinis pour déterminer si vous pouvez les utiliser en l'état.</span><span class="sxs-lookup"><span data-stu-id="86ad8-116">Review the predefined roles to determine whether you can use them as is.</span></span> <span data-ttu-id="86ad8-117">Si vous devez ajuster les tâches ou définir des rôles supplémentaires, vous devez le faire avant de commencer à assigner des utilisateurs à des rôles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="86ad8-117">If you need to adjust the tasks or define additional roles, you should do this before you begin assigning users to specific roles.</span></span> <span data-ttu-id="86ad8-118">Pour plus d’informations sur chaque rôle, consultez [Rôles prédéfinis](role-definitions-predefined-roles.md).</span><span class="sxs-lookup"><span data-stu-id="86ad8-118">For more information about each role, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
2.  <span data-ttu-id="86ad8-119">Identifiez les utilisateurs et les groupes qui doivent accéder au serveur de rapports, et à quel niveau.</span><span class="sxs-lookup"><span data-stu-id="86ad8-119">Identify which users and groups require access to the report server, and at what level.</span></span> <span data-ttu-id="86ad8-120">Le rôle **Lecteur** ou le rôle **Générateur de rapports** doit être attribué à la plupart des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="86ad8-120">Most users should be assigned to the **Browser** role or the **Report Builder** role.</span></span> <span data-ttu-id="86ad8-121">Le rôle **Serveur de publication** doit être attribué à un nombre restreint d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="86ad8-121">A smaller number of users should be assigned to the **Publisher** role.</span></span> <span data-ttu-id="86ad8-122">Le rôle **Gestionnaire de contenu**ne doit être attribué qu'à un nombre très limité d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="86ad8-122">Very few users should be assigned to **Content Manager**.</span></span>  
  
3.  <span data-ttu-id="86ad8-123">Utilisez le Gestionnaire de rapports pour assigner des rôles sur le dossier de base (il s'agit du dossier à la racine de l'arborescence des dossiers du serveur de rapports) à chaque utilisateur ou groupe qui requiert l'accès.</span><span class="sxs-lookup"><span data-stu-id="86ad8-123">Use Report Manager to assign roles on the Home folder (this is the top-level folder of the report server folder hierarchy) for each user or group who requires access.</span></span>  
  
4.  <span data-ttu-id="86ad8-124">Au niveau du site, dans la page Paramètres du site du Gestionnaire de rapports, créez une attribution de rôles au niveau système pour chaque utilisateur ou groupe en utilisant les rôles prédéfinis **Utilisateur système** et **Administrateur système**.</span><span class="sxs-lookup"><span data-stu-id="86ad8-124">At the site level, on the Site Settings page in Report Manager, create a system-level role assignment for each user and group using the predefined roles **System User** and **System Administrator**.</span></span>  
  
5.  <span data-ttu-id="86ad8-125">Créez autant d'attributions de rôles supplémentaires que nécessaire pour des dossiers, des rapports et d'autres éléments spécifiques.</span><span class="sxs-lookup"><span data-stu-id="86ad8-125">Create additional role assignments as needed for specific folders, reports, and other items.</span></span> <span data-ttu-id="86ad8-126">Évitez de créer un grand nombre d'attributions de rôles.</span><span class="sxs-lookup"><span data-stu-id="86ad8-126">Avoid creating a large number of role assignments.</span></span> <span data-ttu-id="86ad8-127">Si vous en créez trop, il sera difficile de gérer les différents niveaux d'autorisation pour chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86ad8-127">If you create too many, it will be difficult to keep track of the different permission levels for each user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86ad8-128">Si vous avez configuré un serveur de rapports de telle sorte qu'il s'exécute en mode intégré SharePoint, vous devez définir des autorisations sur le site SharePoint de manière à accorder l'accès aux éléments du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-128">If you configured a report server to run in SharePoint integrated mode, you must set permissions on the SharePoint site to grant access to report server items.</span></span> <span data-ttu-id="86ad8-129">Pour plus d’informations, consultez [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span><span class="sxs-lookup"><span data-stu-id="86ad8-129">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
## <a name="who-sets-permissions"></a><span data-ttu-id="86ad8-130">Qui définit les autorisations ?</span><span class="sxs-lookup"><span data-stu-id="86ad8-130">Who Sets Permissions</span></span>  
 <span data-ttu-id="86ad8-131">Initialement, seuls les utilisateurs qui sont membres du groupe des administrateurs locaux peuvent accéder au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-131">Initially, only users who are members of the local administrators group can access a report server.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="86ad8-132">est installé avec deux attributions de rôles par défaut qui accordent un accès au niveau élément et au niveau système aux membres du groupe des administrateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="86ad8-132">is installed with two default role assignments that grant item-level and system-level access to members of the local administrators group.</span></span> <span data-ttu-id="86ad8-133">Les administrateurs locaux peuvent utiliser ces attributions de rôles intégrées pour accorder l’accès du serveur de rapports à d’autres utilisateurs et gérer les éléments du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-133">Local Administrators can use these built-in role assignments to grant report server access to other users and manage report server items.</span></span> <span data-ttu-id="86ad8-134">Les attributions de rôles intégrées ne peuvent pas être supprimées.</span><span class="sxs-lookup"><span data-stu-id="86ad8-134">The built-in role assignments cannot be deleted.</span></span> <span data-ttu-id="86ad8-135">Un administrateur local a toujours l'autorisation de gérer entièrement une instance de serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-135">A local administrator always has permission to fully manage a report server instance.</span></span>  
 
 <span data-ttu-id="86ad8-136">Une configuration supplémentaire est requise avant que vous puissiez administrer une instance du serveur de rapports sur un ordinateur local qui exécute Windows Vista ou Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="86ad8-136">Additional configuration is required before you can administer a report server instance on a local computer that runs Windows Vista or Windows Server 2008.</span></span> <span data-ttu-id="86ad8-137">Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="86ad8-137">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="how-permissions-are-stored"></a><span data-ttu-id="86ad8-138">Stockage des autorisations</span><span class="sxs-lookup"><span data-stu-id="86ad8-138">How Permissions are Stored</span></span>  
 <span data-ttu-id="86ad8-139">Les attributions et les définitions de rôles sont stockées dans la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="86ad8-139">Role assignments and definitions are stored in the report server database.</span></span> <span data-ttu-id="86ad8-140">Si vous utilisez de nombreux outils clients ou interfaces de programmation, tout accès est soumis aux autorisations définies pour l'instance du serveur de rapports dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="86ad8-140">If you are using variety of client tools or programmatic interfaces, all access is subject to the permissions that are defined for the report server instance as a whole.</span></span> <span data-ttu-id="86ad8-141">Si vous configurez plusieurs serveurs de rapports au sein d'un déploiement évolutif, les attributions de rôles que vous définissez sur une instance sont stockées dans une base de données partagée et utilisées par toutes les autres instances du même déploiement évolutif.</span><span class="sxs-lookup"><span data-stu-id="86ad8-141">If you are configuring multiple report servers in a scale-out-deployment, the role assignments that you define on one instance are stored in a shared database and used by all the other instances in the same scale-out deployment.</span></span> <span data-ttu-id="86ad8-142">Dans la mesure où les attributions de rôles sont stockées avec les éléments qu'elles sécurisent, vous pouvez déplacer la base de données vers une autre instance du serveur de rapports sans perdre les autorisations définies.</span><span class="sxs-lookup"><span data-stu-id="86ad8-142">Because role assignments are stored with the items they secure, you can move the database to another report server instance without losing the permissions you defined.</span></span>  
  
## <a name="tasks-and-tools-for-managing-permissions"></a><span data-ttu-id="86ad8-143">Tâches et outils de gestion des autorisations</span><span class="sxs-lookup"><span data-stu-id="86ad8-143">Tasks and tools for Managing Permissions</span></span>  
 <span data-ttu-id="86ad8-144">Utilisez les outils suivants pour gérer les définitions et les attributions de rôles.</span><span class="sxs-lookup"><span data-stu-id="86ad8-144">Use the following tools to manage role definitions and assignments.</span></span>  
  
|<span data-ttu-id="86ad8-145">Outil</span><span class="sxs-lookup"><span data-stu-id="86ad8-145">Tool</span></span>|<span data-ttu-id="86ad8-146">Tâches</span><span class="sxs-lookup"><span data-stu-id="86ad8-146">Tasks</span></span>|  
|----------|-----------|  
|<span data-ttu-id="86ad8-147">Management Studio – Permet d'afficher, modifier, créer et supprimer des définitions de rôles.</span><span class="sxs-lookup"><span data-stu-id="86ad8-147">Management Studio - Used to view, modify, create, and delete role definitions.</span></span>|[<span data-ttu-id="86ad8-148">Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="86ad8-148">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](role-definitions-create-delete-or-modify.md)|  
|<span data-ttu-id="86ad8-149">Gestionnaire de rapports – Permet d'assigner des utilisateurs et des groupes aux rôles.</span><span class="sxs-lookup"><span data-stu-id="86ad8-149">Report Manager - Used to assign users and groups to roles.</span></span>|[<span data-ttu-id="86ad8-150">Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;</span><span class="sxs-lookup"><span data-stu-id="86ad8-150">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](grant-user-access-to-a-report-server.md)<br /><br /> [<span data-ttu-id="86ad8-151">Modifier ou supprimer une affectation de rôle &#40;Gestionnaire de rapports&#41;</span><span class="sxs-lookup"><span data-stu-id="86ad8-151">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a><span data-ttu-id="86ad8-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86ad8-152">See Also</span></span>  
 <span data-ttu-id="86ad8-153">[Rôles prédéfinis](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="86ad8-153">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="86ad8-154">[Octroi d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="86ad8-154">[Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="86ad8-155">[Authentification avec le serveur de rapports](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="86ad8-155">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="86ad8-156">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="86ad8-156">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="86ad8-157">[Sécurité et protection Reporting Services](reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="86ad8-157">[Reporting Services Security and Protection](reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="86ad8-158">Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;</span><span class="sxs-lookup"><span data-stu-id="86ad8-158">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  