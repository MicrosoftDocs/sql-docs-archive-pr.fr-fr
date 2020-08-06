---
title: Accorder à un utilisateur l’accès à un serveur de rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697444"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a><span data-ttu-id="9dcf4-102">Accorder à un utilisateur l'accès à un serveur de rapports (Gestionnaire de rapports)</span><span class="sxs-lookup"><span data-stu-id="9dcf4-102">Grant User Access to a Report Server (Report Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9dcf4-103">utilise la sécurité basée sur les rôles pour permettre à un utilisateur d’accéder à un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-103">uses role-based security to grant user access to a report server.</span></span> <span data-ttu-id="9dcf4-104">Dans une nouvelle installation du serveur de rapports, seuls les utilisateurs membres du groupe Administrateurs local disposent d'autorisations relatives au contenu et au fonctionnement du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-104">On a new report server installation, only users who are members of the local Administrators group have permissions to report server content and operations.</span></span> <span data-ttu-id="9dcf4-105">Pour rendre le serveur de rapports accessible à d’autres utilisateurs, vous devez créer des attributions de rôles qui mappent des comptes d’utilisateurs ou de groupes à un rôle prédéfini spécifiant une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-105">To make the report server available to other users, you must create role assignments that map  user or group accounts to a predefined role that specifies a collection of tasks.</span></span>  
  
 <span data-ttu-id="9dcf4-106">**Serveurs de rapports en mode SharePoint :** pour un serveur de rapports configuré en mode intégré SharePoint, vous configurez l’accès à partir d’un site SharePoint à l’aide d’autorisations SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-106">**SharePoint mode report servers:** For a report server that is configured for SharePoint integrated mode, you configure access from a SharePoint site using SharePoint permissions.</span></span> <span data-ttu-id="9dcf4-107">Les niveaux d'autorisation du site SharePoint déterminent l'accès au contenu du serveur de rapports et son bon fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-107">Permission levels on the SharePoint site determine access to report server content and operations.</span></span> <span data-ttu-id="9dcf4-108">Vous devez être un administrateur de site pour pouvoir accorder des autorisations sur un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-108">You must be a site administrator to grant permissions on a SharePoint site.</span></span> <span data-ttu-id="9dcf4-109">Pour plus d’informations, consultez [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span><span class="sxs-lookup"><span data-stu-id="9dcf4-109">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="9dcf4-110">**Serveurs de rapports en mode natif :** cette rubrique traite d’un serveur de rapports configuré pour le mode natif et de l’utilisation du Gestionnaire de rapports pour affecter des utilisateurs à un rôle.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-110">**Native mode report servers:** This topic is focused on a report server that is configured for native mode and the use of Report Manager to assign users to a role.</span></span> <span data-ttu-id="9dcf4-111">Il existe deux types de rôles :</span><span class="sxs-lookup"><span data-stu-id="9dcf4-111">There are two types of roles:</span></span>  
  
-   <span data-ttu-id="9dcf4-112">Les rôles au niveau élément permettent d'afficher, d'ajouter et de gérer le contenu du serveur de rapports, les abonnements, le traitement des rapports et l'historique de rapport.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-112">Item-level roles are used to view, add, and manage report server content, subscriptions, report processing, and report history.</span></span> <span data-ttu-id="9dcf4-113">Les attributions de rôles au niveau élément sont définies sur le nœud racine (dossier de base) mais aussi sur des dossiers ou des éléments spécifiques situés plus bas dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-113">Item-level role assignments are defined on the root node (the Home folder) or on specific folders or items farther down the hierarchy.</span></span>  
  
-   <span data-ttu-id="9dcf4-114">Les rôles de niveau système accordent l'accès aux opérations à l'échelle du site qui ne sont pas liées à un élément spécifique.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-114">System-level roles grant access to site-wide operations that are not bound to any specific item.</span></span> <span data-ttu-id="9dcf4-115">Cela inclut par exemple l'utilisation du Générateur de rapports et des planifications partagées.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-115">Examples include using Report Builder and using shared schedules.</span></span>  
  
     <span data-ttu-id="9dcf4-116">Les deux types de rôles sont complémentaires et doivent être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-116">The two types of roles complement each other and should be used together.</span></span> <span data-ttu-id="9dcf4-117">Par conséquent, l'ajout d'un utilisateur à un serveur de rapports est une opération en deux parties.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-117">For this reason, adding a user to a report server is a two-part operation.</span></span> <span data-ttu-id="9dcf4-118">Si vous attribuez un rôle au niveau élément à un utilisateur, vous devez également lui attribuer un rôle de niveau système.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-118">If you assign a user to an item-level role, you should also assign them to a system-level role.</span></span> <span data-ttu-id="9dcf4-119">Lorsque vous attribuez un rôle à un utilisateur, vous devez sélectionner un rôle déjà défini.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-119">When assigning a user to a role, you must select a role that is already defined.</span></span> <span data-ttu-id="9dcf4-120">Pour créer, modifier ou supprimer des rôles, utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9dcf4-120">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="9dcf4-121">Pour plus d’informations, consultez [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span><span class="sxs-lookup"><span data-stu-id="9dcf4-121">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="before-you-start"></a><span data-ttu-id="9dcf4-122">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="9dcf4-122">Before you start</span></span>  
 <span data-ttu-id="9dcf4-123">Examinez la liste suivante avant d'ajouter des utilisateurs à un serveur de rapports en mode natif.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-123">Review the following list before adding users to a native mode report server.</span></span>  
  
-   <span data-ttu-id="9dcf4-124">Vous devez être membre du groupe Administrateurs local sur le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-124">You must be a member of the local Administrators group on the report server computer.</span></span> <span data-ttu-id="9dcf4-125">Si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ou Windows Server 2008, vous devez effectuer une configuration supplémentaire pour pouvoir administrer un serveur de rapports localement.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-125">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] or Windows Server 2008, additional configuration is required before you can administer a report server locally.</span></span> <span data-ttu-id="9dcf4-126">Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="9dcf4-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
-   <span data-ttu-id="9dcf4-127">Pour déléguer cette tâche à d'autres utilisateurs, créez des attributions de rôles qui mappent des comptes d'utilisateurs aux rôles Gestionnaire de contenu et Administrateur système.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-127">To delegate this task to other users, create role assignments that map user accounts to Content Manager and System Administrator roles.</span></span> <span data-ttu-id="9dcf4-128">Les utilisateurs qui disposent d'autorisations liées aux rôles Gestionnaire de contenu et Administrateur système peuvent ajouter des utilisateurs à un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-128">Users who have Content Manager and System Administrator permissions can add users to a report server.</span></span>  
  
-   <span data-ttu-id="9dcf4-129">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], passez en revue les rôles prédéfinis pour les rôles système et les rôles d’utilisateurs pour vous familiariser avec les types de tâches de chaque rôle.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], view the predefined roles for System Roles and User Roles so that you are familiar with the kinds of tasks in each role.</span></span> <span data-ttu-id="9dcf4-130">Les descriptions des tâches ne sont pas visibles dans le Gestionnaire de rapports ; par conséquent, familiarisez-vous avec les rôles avant de commencer à ajouter des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-130">Task descriptions are not visible in Report Manager, so you will want to be familiar with the roles before you begin adding users.</span></span>  
  
-   <span data-ttu-id="9dcf4-131">Vous pouvez éventuellement personnaliser les rôles ou définir des rôles supplémentaires pour inclure la collection de tâches dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-131">Optionally, customize the roles or define additional roles to include the collection of tasks that you require.</span></span> <span data-ttu-id="9dcf4-132">Par exemple, si vous envisagez d'utiliser des paramètres de sécurité personnalisés pour des éléments individuels, vous pouvez créer une définition de rôle qui permet d'afficher les dossiers.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-132">For example, if you plan to use custom security settings for individual items, you might want to create a new role definition that grants view-access to folders.</span></span>  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a><span data-ttu-id="9dcf4-133">Pour ajouter un utilisateur ou un groupe à un rôle système</span><span class="sxs-lookup"><span data-stu-id="9dcf4-133">To add a user or group to a system role</span></span>  
  
1.  <span data-ttu-id="9dcf4-134">Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="9dcf4-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="9dcf4-135">Cliquez sur **Paramètres du site**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-135">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="9dcf4-136">Cliquez sur **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-136">Click **Security**.</span></span>  
  
4.  <span data-ttu-id="9dcf4-137">Cliquez sur **Nouvelle attribution de rôle**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-137">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="9dcf4-138">Dans **nom d’utilisateur ou de groupe**, entrez un compte d’utilisateur ou de groupe de domaine Windows au format suivant : \<domain> \\<compte \> .</span><span class="sxs-lookup"><span data-stu-id="9dcf4-138">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="9dcf4-139">Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-139">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="9dcf4-140">Sélectionnez un rôle système, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-140">Select a system role, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9dcf4-141">Les rôles sont cumulatifs ; par conséquent, si vous sélectionnez à la fois le rôle Administrateur système et le rôle Utilisateur système, un utilisateur ou un groupe pourra effectuer les tâches incluses dans les deux rôles.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-141">Roles are cumulative, so if you select both System Administrator and System User, a user or group will be able to perform the tasks in both roles.</span></span>  
  
7.  <span data-ttu-id="9dcf4-142">Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-142">Repeat to create assignments for additional users or groups.</span></span>  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a><span data-ttu-id="9dcf4-143">Pour ajouter un utilisateur ou un groupe à un rôle au niveau élément</span><span class="sxs-lookup"><span data-stu-id="9dcf4-143">To add a user or group to an item role</span></span>  
  
1.  <span data-ttu-id="9dcf4-144">Démarrez le **Gestionnaire de rapports** , puis recherchez l’élément de rapport pour lequel vous souhaitez ajouter un utilisateur ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-144">Start **Report Manager** and locate the report item for which you want to add a user or group.</span></span>  
  
2.  <span data-ttu-id="9dcf4-145">Pointez sur l'élément et cliquez sur la flèche déroulante.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-145">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="9dcf4-146">Dans le menu déroulant, cliquez sur **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-146">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="9dcf4-147">Cliquez sur **Nouvelle attribution de rôle**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-147">Click **New Role Assignment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9dcf4-148">Si un élément hérite actuellement de la sécurité de l’un de ses parents, cliquez sur **Modifier la sécurité de l’élément** dans la barre d’outils pour changer les paramètres de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-148">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span> <span data-ttu-id="9dcf4-149">Puis cliquez sur **Nouvelle attribution de rôle**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-149">Then click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="9dcf4-150">Dans **nom d’utilisateur ou de groupe**, entrez un compte d’utilisateur ou de groupe de domaine Windows au format suivant : \<domain> \\<compte \> .</span><span class="sxs-lookup"><span data-stu-id="9dcf4-150">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="9dcf4-151">Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-151">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="9dcf4-152">Sélectionnez une ou plusieurs définitions de rôles décrivant la façon dont l’utilisateur ou le groupe doit accéder à l’élément, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-152">Select one or more role definitions that describe how the user or group should access the item, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="9dcf4-153">Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9dcf4-153">Repeat to create assignments for additional users or groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dcf4-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dcf4-154">See Also</span></span>  
 <span data-ttu-id="9dcf4-155">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="9dcf4-155">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="9dcf4-156">[Page nouvelle attribution de rôle : modifier l’attribution de rôle &#40;Gestionnaire de rapports&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="9dcf4-156">[New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span></span>  
 <span data-ttu-id="9dcf4-157">[Page Propriétés de sécurité, éléments &#40;Gestionnaire de rapports&#41;](../security-properties-page-items-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="9dcf4-157">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md) </span></span>  
 <span data-ttu-id="9dcf4-158">[Attributions de rôles](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="9dcf4-158">[Role Assignments](role-assignments.md) </span></span>  
 [<span data-ttu-id="9dcf4-159">Définitions de rôles</span><span class="sxs-lookup"><span data-stu-id="9dcf4-159">Role Definitions</span></span>](role-definitions.md)  
  
  