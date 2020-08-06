---
title: Tâches et autorisations | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01cbf00850c5dd57e7ca1575a1a0cb826c009714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707007"
---
# <a name="tasks-and-permissions"></a><span data-ttu-id="e511a-102">Tâches et autorisations</span><span class="sxs-lookup"><span data-stu-id="e511a-102">Tasks and Permissions</span></span>
  <span data-ttu-id="e511a-103">Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les *tâches* correspondent aux actions qu’un utilisateur ou un administrateur peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="e511a-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], *tasks* are actions that a user or administrator can perform.</span></span> <span data-ttu-id="e511a-104">Les tâches sont prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="e511a-104">Tasks are predefined.</span></span> <span data-ttu-id="e511a-105">Vous ne pouvez pas créer de tâches personnalisées ou modifier celles qui sont fournies, par programme ou à l'aide d'un outil.</span><span class="sxs-lookup"><span data-stu-id="e511a-105">You cannot create custom tasks or modify the ones provided either programmatically or through a tool.</span></span> <span data-ttu-id="e511a-106">Il en existe vingt cinq en tout.</span><span class="sxs-lookup"><span data-stu-id="e511a-106">There are twenty-five tasks in all.</span></span> <span data-ttu-id="e511a-107">Ces tâches comprennent l'ensemble des opérations disponibles dans la sécurité basée sur l'attribution de rôles.</span><span class="sxs-lookup"><span data-stu-id="e511a-107">These tasks comprise the entire set of operations that are available in role-based security.</span></span> <span data-ttu-id="e511a-108">Parmi ces tâches, citons par exemple « Afficher les rapports », « Gérer les rapports » et « Gérer les propriétés du serveur de rapports ».</span><span class="sxs-lookup"><span data-stu-id="e511a-108">Some examples of tasks include "View reports," "Manage reports," and "Manage report server properties."</span></span>  
  
 <span data-ttu-id="e511a-109">Chaque tâche se compose d'un ensemble d'autorisations, qui sont également prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="e511a-109">Each task consists of a set of permissions, which are also predefined.</span></span> <span data-ttu-id="e511a-110">Par exemple, la tâche « Gérer les dossiers » contient les autorisations de création et de suppression des dossiers, et d'affichage et de mise à jour des propriétés des dossiers.</span><span class="sxs-lookup"><span data-stu-id="e511a-110">For example, the "Manage folders" task contains permissions to create and delete folders and view and update folder properties.</span></span> <span data-ttu-id="e511a-111">Les autorisations pour chaque tâche sont documentées pour fournir une description plus exacte de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="e511a-111">Permissions for each task are documented to provide a more exact description of each task.</span></span> <span data-ttu-id="e511a-112">Les utilisateurs n'interagissent pas directement avec les autorisations, ils ne les spécifient pas dans les attributions de rôle.</span><span class="sxs-lookup"><span data-stu-id="e511a-112">It is not possible to interact with permissions directly or to specify them in role assignments.</span></span> <span data-ttu-id="e511a-113">Ils se voient accorder des autorisations indirectement par le biais des tâches qui sont incluses dans les définitions de rôles.</span><span class="sxs-lookup"><span data-stu-id="e511a-113">Users are granted permissions indirectly through the tasks that are included in role definitions.</span></span>  
  
 <span data-ttu-id="e511a-114">Ils peuvent effectuer les tâches uniquement si elles font partie d'un rôle et que celui-ci est compris dans une attribution.</span><span class="sxs-lookup"><span data-stu-id="e511a-114">Tasks can be performed only if they are part of a role and that role is included in a role assignment.</span></span> <span data-ttu-id="e511a-115">Ainsi, si la tâche « Consulter des modèles » n'est pas comprise dans un rôle, ou si le rôle ne fait pas partie d'une attribution, les utilisateurs ne peuvent pas consulter les modèles de rapports.</span><span class="sxs-lookup"><span data-stu-id="e511a-115">Thus, if the View Models task is not included in a role, or that role is not included in a role assignment, users cannot view report models.</span></span> <span data-ttu-id="e511a-116">Le diagramme suivant illustre comment les autorisations sont combinées en tâches, et comment les tâches sont combinées en rôles pouvant être utilisés dans des attributions de rôles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e511a-116">The following diagram shows how permissions are combined into tasks, and how tasks are combined into roles that can be used for specific role assignments.</span></span>  
  
 <span data-ttu-id="e511a-117">![Diagramme Autorisations et tâches](../media/report-securityobjects.gif "Diagramme Autorisations et tâches")</span><span class="sxs-lookup"><span data-stu-id="e511a-117">![Permissions and task diagram](../media/report-securityobjects.gif "Permissions and task diagram")</span></span>  
<span data-ttu-id="e511a-118">Diagramme Autorisations et tâches</span><span class="sxs-lookup"><span data-stu-id="e511a-118">Permissions and task diagram</span></span>  
  
## <a name="system-and-item-level-tasks"></a><span data-ttu-id="e511a-119">Tâches au niveau système et au niveau élément</span><span class="sxs-lookup"><span data-stu-id="e511a-119">System and Item Level Tasks</span></span>  
 <span data-ttu-id="e511a-120">Les tâches entrent dans deux catégories : niveau système et niveau élément.</span><span class="sxs-lookup"><span data-stu-id="e511a-120">Tasks fall into two categories: system level and item level.</span></span> <span data-ttu-id="e511a-121">Un rôle ne peut inclure de tâches que d'une seule catégorie.</span><span class="sxs-lookup"><span data-stu-id="e511a-121">A role can include tasks only from a single category.</span></span> <span data-ttu-id="e511a-122">Le tableau suivant décrit chaque catégorie de tâches.</span><span class="sxs-lookup"><span data-stu-id="e511a-122">The following table describes each category of tasks.</span></span>  
  
|<span data-ttu-id="e511a-123">Category</span><span class="sxs-lookup"><span data-stu-id="e511a-123">Category</span></span>|<span data-ttu-id="e511a-124">Description</span><span class="sxs-lookup"><span data-stu-id="e511a-124">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="e511a-125">Tâches au niveau élément</span><span class="sxs-lookup"><span data-stu-id="e511a-125">Item-Level Tasks</span></span>](tasks-and-permissions-item-level-tasks.md)|<span data-ttu-id="e511a-126">Actions qui sont effectuées sur des éléments gérés par un serveur de rapports, tels que les dossiers, les rapports, les modèles de rapports et les ressources.</span><span class="sxs-lookup"><span data-stu-id="e511a-126">Actions that are performed on items managed by a report server, such as folders, reports, report models, and resources.</span></span><br /><br /> <span data-ttu-id="e511a-127">Les tâches au niveau élément sont limitées à l'espace de noms de dossier du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="e511a-127">Item-level tasks are scoped to the report server folder namespace.</span></span> <span data-ttu-id="e511a-128">Tous les éléments auxquels vous accédez par le biais des dossiers sur un serveur de rapports ou par le biais de liens URL sont sécurisés par des attributions de rôles comprenant des tâches au niveau élément.</span><span class="sxs-lookup"><span data-stu-id="e511a-128">All items that you access through the folders on a report server or through URL access are secured by role assignments that include item-level tasks.</span></span>|  
|[<span data-ttu-id="e511a-129">Tâches au niveau système</span><span class="sxs-lookup"><span data-stu-id="e511a-129">System-Level Tasks</span></span>](tasks-and-permissions-system-level-tasks.md)|<span data-ttu-id="e511a-130">Actions qui sont effectuées au niveau du système, telles que la gestion des travaux ou des planifications partagées pouvant être utilisées avec de nombreux éléments.</span><span class="sxs-lookup"><span data-stu-id="e511a-130">Actions that are performed at the system level, such as managing jobs or shared schedules that can be used with many items.</span></span> <span data-ttu-id="e511a-131">Les tâches au niveau système sont limitées en dehors de l'espace de noms de dossier du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="e511a-131">System-level tasks are scoped outside of the report server folder namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e511a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e511a-132">See Also</span></span>  
 <span data-ttu-id="e511a-133">[Définitions de rôles](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="e511a-133">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="e511a-134">[Rôles prédéfinis](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="e511a-134">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="e511a-135">Octroi d'autorisations sur un serveur de rapports en mode natif</span><span class="sxs-lookup"><span data-stu-id="e511a-135">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  