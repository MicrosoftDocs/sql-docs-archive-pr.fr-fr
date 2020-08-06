---
title: Accorder des autorisations de cube ou de modèle (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.cubes.f1
helpviewer_keywords:
- user access rights [Analysis Services], cubes
- cubes [Analysis Services], security
- read/write permissions
- permissions [Analysis Services], cubes
ms.assetid: 55b1456e-2f6b-4101-b316-c926f40304e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 23e0c5d6c6e70a4ee563ec47562629dd58b0f146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694795"
---
# <a name="grant-cube-or-model-permissions-analysis-services"></a><span data-ttu-id="44dc4-102">Octroyer des autorisations de cube ou de modèle (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="44dc4-102">Grant cube or model permissions (Analysis Services)</span></span>
  <span data-ttu-id="44dc4-103">Un cube ou modèle tabulaire est le principal objet de requête dans un modèle de données Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="44dc4-103">A cube or tabular model is the primary query object in an Analysis Services data model.</span></span> <span data-ttu-id="44dc4-104">Lors de la connexion à des données tabulaires ou multidimensionnelles à partir d'Excel pour l'exploration de données ad hoc, les utilisateurs commencent en général par sélectionner un cube ou modèle tabulaire spécifique comme structure de données derrière l'objet de rapport de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="44dc4-104">When connecting to multidimensional or tabular data from Excel for ad hoc data exploration, users typically start by selecting a specific cube or tabular model as the data structure behind the Pivot report object.</span></span> <span data-ttu-id="44dc4-105">Cette rubrique explique comment accorder les autorisations nécessaires pour l'accès aux données tabulaires ou de cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-105">This topic explains how to grant the necessary permissions for cube or tabular data access.</span></span>  
  
 <span data-ttu-id="44dc4-106">Par défaut, seul un Administrateur de serveur ou Administrateur de base de données est autorisé à interroger des cubes dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-106">By default, no one except a Server Administrator or Database Administrator has permission to query cubes in a database.</span></span> <span data-ttu-id="44dc4-107">L'accès à un cube par un non-administrateur requiert l'appartenance à un rôle créé pour la base de données contenant le cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-107">Cube access by a non-administrator requires membership in a role created for the database containing the cube.</span></span> <span data-ttu-id="44dc4-108">L'appartenance est prise en charge pour les comptes d'utilisateurs ou de groupes Windows définis dans Active Directory ou sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="44dc4-108">Membership is supported for Windows user or group accounts, defined in either Active Directory or on the local computer.</span></span> <span data-ttu-id="44dc4-109">Avant de commencer, identifiez les comptes qui appartiendront aux rôles que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="44dc4-109">Before you start, identify which accounts will be assigned membership in the roles you are about to create.</span></span>  
  
 <span data-ttu-id="44dc4-110">Le fait de disposer d'un accès `Read` à un cube fournit également des autorisations d'accès aux dimensions, groupes de mesures et perspectives de ce cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-110">Having `Read` access to a cube also conveys permissions on the dimensions, measure groups, and perspectives within it.</span></span> <span data-ttu-id="44dc4-111">La plupart des administrateurs accordent des autorisations au niveau du cube, puis limitent les autorisations sur des objets spécifiques, des données associées ou selon l'identité de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44dc4-111">Most administrators will grant read permissions at the cube level and then restrict permissions on specific objects, on associated data, or by user identity.</span></span>  
  
 <span data-ttu-id="44dc4-112">Pour conserver les définitions des rôles d'un déploiement de solution au suivant, une meilleure pratique consiste à définir des rôles dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] comme partie intégrante du modèle, puis à faire en sorte qu'un administrateur de base de données assigne des appartenances aux rôles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] une fois la base de données publiée.</span><span class="sxs-lookup"><span data-stu-id="44dc4-112">To preserve role definitions over successive solution deployments, a best practice is to define roles in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] as an integral part of the model, and then have a database administrator assign role memberships in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after the database is published.</span></span> <span data-ttu-id="44dc4-113">Vous pouvez cependant utiliser l'un ou l'autre outil pour ces deux tâches.</span><span class="sxs-lookup"><span data-stu-id="44dc4-113">But you can use either tool for both tasks.</span></span> <span data-ttu-id="44dc4-114">Pour simplifier l'exercice, nous allons utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour la définition et l'appartenance aux rôles.</span><span class="sxs-lookup"><span data-stu-id="44dc4-114">To simplify the exercise, we'll use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] for both role definition and membership.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44dc4-115">Seuls les administrateurs de serveur, ou les administrateurs de base de données ayant des autorisations Contrôle total, peuvent déployer un cube à partir de fichiers sources vers un serveur ou créer des rôles et assigner des membres.</span><span class="sxs-lookup"><span data-stu-id="44dc4-115">Only server administrators, or database administrators having Full Control permissions, can deploy a cube from source files to a server, or create roles and assign members.</span></span> <span data-ttu-id="44dc4-116">Pour plus d’informations sur ces niveaux d’autorisation, consultez [accorder des autorisations d’administrateur de serveur &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) et [accorder des autorisations de base de données &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) .</span><span class="sxs-lookup"><span data-stu-id="44dc4-116">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) and [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for details about these permission levels.</span></span>  
  
#### <a name="step-1-create-the-role"></a><span data-ttu-id="44dc4-117">Étape 1 : Créer le rôle</span><span class="sxs-lookup"><span data-stu-id="44dc4-117">Step 1: Create the role</span></span>  
  
1.  <span data-ttu-id="44dc4-118">Dans SSMS, connectez-vous à Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="44dc4-118">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="44dc4-119">Si vous avez besoin d’aide sur cette étape, consultez [Connexion à partir d’applications clientes &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-119">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with this step.</span></span>  
  
2.  <span data-ttu-id="44dc4-120">Ouvrez le dossier **Bases de données** dans l’Explorateur d’objets et sélectionnez une base de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-120">Open the **Databases** folder in Object Explorer, and select a database.</span></span>  
  
3.  <span data-ttu-id="44dc4-121">Cliquez avec le bouton droit sur le dossier **Rôles** et choisissez **Nouveau rôle**.</span><span class="sxs-lookup"><span data-stu-id="44dc4-121">Right-click **Roles** and choose **New Role**.</span></span> <span data-ttu-id="44dc4-122">Notez que les rôles sont créés au niveau de la base de données et s'appliquent aux objets de cette base de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-122">Notice that roles are created at the database level and apply to objects within it.</span></span> <span data-ttu-id="44dc4-123">Vous ne pouvez pas partager de rôles entre des bases de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-123">You cannot share roles across databases.</span></span>  
  
4.  <span data-ttu-id="44dc4-124">Dans le volet **Général** , entrez un nom et éventuellement une description.</span><span class="sxs-lookup"><span data-stu-id="44dc4-124">In the **General** pane, enter a name, and optionally, a description.</span></span> <span data-ttu-id="44dc4-125">Ce volet contient également plusieurs autorisations de base de données, telles que Contrôle total, Traiter la base de données et Lire la définition.</span><span class="sxs-lookup"><span data-stu-id="44dc4-125">This pane also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="44dc4-126">Aucune de ces autorisations n'est nécessaire pour interroger un cube ou modèle tabulaire.</span><span class="sxs-lookup"><span data-stu-id="44dc4-126">None of these permissions are needed for querying a cube or tabular model.</span></span> <span data-ttu-id="44dc4-127">Pour plus d'informations sur ces autorisations, consultez [Octroyer des autorisations de base de données &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-127">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about these permissions.</span></span>  
  
5.  <span data-ttu-id="44dc4-128">Continuez à l'étape suivante après avoir entré un nom et une description facultative.</span><span class="sxs-lookup"><span data-stu-id="44dc4-128">Continue to the next step after entering a name and optional description.</span></span>  
  
#### <a name="step-2-assign-membership"></a><span data-ttu-id="44dc4-129">Étape 2 : Assigner l’appartenance</span><span class="sxs-lookup"><span data-stu-id="44dc4-129">Step 2: Assign Membership</span></span>  
  
1.  <span data-ttu-id="44dc4-130">Dans le volet **Appartenance** , cliquez sur **Ajouter** pour entrer les comptes d’utilisateurs ou de groupes Windows qui accéderont au cube à l’aide de ce rôle.</span><span class="sxs-lookup"><span data-stu-id="44dc4-130">In the **Membership** pane, click **Add** to enter the Windows user or group accounts that will be accessing the cube using this role.</span></span> <span data-ttu-id="44dc4-131">Analysis Services prend uniquement en charge les identités de sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="44dc4-131">Analysis Services only supports Windows security identities.</span></span> <span data-ttu-id="44dc4-132">Notez que vous ne créez pas de connexions de base de données lors de cette étape.</span><span class="sxs-lookup"><span data-stu-id="44dc4-132">Notice that you are not creating database logins in this step.</span></span> <span data-ttu-id="44dc4-133">Dans Analysis Services, les utilisateurs se connectent par l'intermédiaire de comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="44dc4-133">In Analysis Services, users connect through Windows accounts.</span></span>  
  
2.  <span data-ttu-id="44dc4-134">Continuez à l'étape suivante, la définition des autorisations de cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-134">Continue to the next step, setting cube permissions.</span></span>  
  
     <span data-ttu-id="44dc4-135">Notez que nous ignorons le volet Source de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-135">Notice that we are skipping the Data Source pane.</span></span> <span data-ttu-id="44dc4-136">La plupart des consommateurs ordinaires de données Analysis Services n'ont pas besoin d'autorisations sur l'objet source de données.</span><span class="sxs-lookup"><span data-stu-id="44dc4-136">Most regular consumers of Analysis Services data do not need permissions on the data source object.</span></span> <span data-ttu-id="44dc4-137">Pour obtenir des informations sur ces niveaux d’autorisation, consultez [Octroyer des autorisations sur un objet de source de données &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) .</span><span class="sxs-lookup"><span data-stu-id="44dc4-137">See [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) for details on when you might set this permission.</span></span>  
  
#### <a name="step-3-set-cube-permissions"></a><span data-ttu-id="44dc4-138">Étape 3 : Définir les autorisations du cube</span><span class="sxs-lookup"><span data-stu-id="44dc4-138">Step 3: Set Cube Permissions</span></span>  
  
1.  <span data-ttu-id="44dc4-139">Dans le volet **cubes** , sélectionnez un cube, puis cliquez sur `Read` ou sur accès **en lecture/écriture** .</span><span class="sxs-lookup"><span data-stu-id="44dc4-139">In the **Cubes** pane, select a cube, and then click `Read` or **Read/Write** access.</span></span>  
  
     <span data-ttu-id="44dc4-140">`Read`l’accès suffit pour la plupart des opérations.</span><span class="sxs-lookup"><span data-stu-id="44dc4-140">`Read` access is sufficient for most operations.</span></span> <span data-ttu-id="44dc4-141">**Lecture/Écriture** sert uniquement à l’écriture différée, et non au traitement.</span><span class="sxs-lookup"><span data-stu-id="44dc4-141">**Read/Write** is used only for writeback, not processing.</span></span> <span data-ttu-id="44dc4-142">Pour plus d’informations sur cette fonctionnalité, consultez [Définir l’écriture différée de partition](set-partition-writeback.md) .</span><span class="sxs-lookup"><span data-stu-id="44dc4-142">See [Set Partition Writeback](set-partition-writeback.md) for more information about this capability.</span></span>  
  
     <span data-ttu-id="44dc4-143">Notez que vous pouvez sélectionner plusieurs cubes, ainsi que d'autres objets disponibles dans la boîte de dialogue Créer un rôle.</span><span class="sxs-lookup"><span data-stu-id="44dc4-143">Notice that you can select multiple cubes, as well as other objects available in the Create Role dialog box.</span></span> <span data-ttu-id="44dc4-144">L'accord d'autorisations d'accès à un cube permet également d'accéder aux dimensions et aux perspectives associées au cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-144">Granting permissions to a cube authorizes access to the dimensions and perspectives associated with the cube.</span></span> <span data-ttu-id="44dc4-145">Il n'est pas nécessaire d'ajouter manuellement des objets déjà représentés dans le cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-145">It's not necessary to manually add objects already represented in the cube.</span></span>  
  
     <span data-ttu-id="44dc4-146">Si vous devez varier l'autorisation selon l'objet ou l'utilisateur, par exemple pour rendre certaines mesures indisponibles, vous pouvez autoriser ou refuser l'accès de manière atomique sur des objets spécifiques, et même sur des cellules.</span><span class="sxs-lookup"><span data-stu-id="44dc4-146">If you need to vary authorization by objects or user, for example to make certain measures unavailable, you can allow or deny access atomically on specific objects, even on cells.</span></span> <span data-ttu-id="44dc4-147">Pour plus d’informations, consultez [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) et [Octroyer un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-147">See [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) and [Grant custom access to cell data &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md) for details.</span></span>  
  
2.  <span data-ttu-id="44dc4-148">À ce stade, une fois que vous avez cliqué sur **OK**, tous les membres de ce rôle ont accès aux cubes, aux niveaux d'autorisation que vous avez spécifiés.</span><span class="sxs-lookup"><span data-stu-id="44dc4-148">At this point, after you click **OK**, all members of this role have access to the cubes, at the permission levels you specified.</span></span>  
  
     <span data-ttu-id="44dc4-149">Notez que dans le volet **Cubes** , vous pouvez accorder aux utilisateurs l’autorisation de créer des cubes locaux à partir d’un cube serveur via **Extraction et cube local**ou autoriser uniquement l’extraction via l'autorisation **Extraction** .</span><span class="sxs-lookup"><span data-stu-id="44dc4-149">Notice that on the **Cubes** pane, you can grant users permission to create local cubes from a server cube via **Drillthrough and Local Cube**, or allow drillthrough only, via the **Drillthrough** permission.</span></span>  
  
     <span data-ttu-id="44dc4-150">Pour finir, ce volet vous permet d’accorder des droits **Traiter la base de données** sur le cube pour permettre à tous les membres de ce rôle de traiter des données pour ce cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-150">Finally, this pane lets you grant **Process Database** rights on the cube to give all members of this role the ability to process data for this cube.</span></span> <span data-ttu-id="44dc4-151">Le traitement étant généralement une opération restreinte, nous vous recommandons de laisser cette tâche aux administrateurs ou de définir des rôles spécifiquement pour cette tâche.</span><span class="sxs-lookup"><span data-stu-id="44dc4-151">Because processing is typically a restricted operation, we recommend that you leave that task to the administrators, or define separate roles specifically for that task.</span></span> <span data-ttu-id="44dc4-152">Pour plus d’informations sur les bonnes pratiques concernant les autorisations de traitement, consultez [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-152">See [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) for more information about processing permission best practices.</span></span>  
  
#### <a name="step-4-test"></a><span data-ttu-id="44dc4-153">Étape 4 : Tester</span><span class="sxs-lookup"><span data-stu-id="44dc4-153">Step 4: Test</span></span>  
  
1.  <span data-ttu-id="44dc4-154">Utilisez Excel pour tester les autorisations d'accès au cube.</span><span class="sxs-lookup"><span data-stu-id="44dc4-154">Use Excel to test cube access permissions.</span></span> <span data-ttu-id="44dc4-155">Vous pouvez également utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], en suivant la même technique que celle décrite ci-dessous (exécution de l’application comme utilisateur non-administrateur).</span><span class="sxs-lookup"><span data-stu-id="44dc4-155">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], following the same technique described next ─ running the application as a non-administrator user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44dc4-156">Si vous êtes administrateur Analysis Services, les autorisations administrateur seront combinées avec des rôles ayant des autorisations moindres, ce qui rend difficile le test des autorisations de rôle de manière isolée.</span><span class="sxs-lookup"><span data-stu-id="44dc4-156">If you are an Analysis Services administrator, administrator permissions will be combined with roles having lesser permissions, making it difficult to test role permissions in isolation.</span></span> <span data-ttu-id="44dc4-157">Pour simplifier les tests, nous vous suggérons d'ouvrir une seconde instance de SSMS, à l'aide du compte assigné au rôle que vous testez.</span><span class="sxs-lookup"><span data-stu-id="44dc4-157">To simplify testing, we suggest that you open a second instance of SSMS, using the account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="44dc4-158">Maintenez la touche Maj enfoncée et cliquez avec le bouton droit sur le raccourci **Excel** pour accéder à l’option **Exécuter en tant qu’autre utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="44dc4-158">Hold-down the Shift key and right-click the **Excel** shortcut to access the **Run as different user** option.</span></span> <span data-ttu-id="44dc4-159">Entrez l'un des comptes d'utilisateurs ou de groupes Windows ayant une appartenance à ce rôle.</span><span class="sxs-lookup"><span data-stu-id="44dc4-159">Enter one of the Windows user or group accounts having membership in this role.</span></span>  
  
3.  <span data-ttu-id="44dc4-160">Une fois Excel ouvert, utilisez l'onglet Données pour vous connecter à Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="44dc4-160">When Excel opens, use the Data tab to connect to Analysis Services.</span></span> <span data-ttu-id="44dc4-161">Comme vous exécutez Excel en tant qu’autre utilisateur Windows, l’option **Utiliser l’authentification Windows** est le type d’informations d’identification correct à utiliser lors du test des rôles.</span><span class="sxs-lookup"><span data-stu-id="44dc4-161">Because you are running Excel as a different Windows user, the **Use Windows Authentication** option is the right credential type to use when testing roles.</span></span> <span data-ttu-id="44dc4-162">Si vous avez besoin d’aide sur cette étape, consultez [Connexion à partir d’applications clientes &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-162">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with this step.</span></span>  
  
     <span data-ttu-id="44dc4-163">Si vous recevez des erreurs lors de la connexion, vérifiez la configuration des ports pour Analysis Services et vérifiez que le serveur accepte les connexions à distance.</span><span class="sxs-lookup"><span data-stu-id="44dc4-163">If you get errors on the connection, check the port configuration for Analysis Services and verify that the server accepts remote connections.</span></span> <span data-ttu-id="44dc4-164">Pour la configuration des ports, consultez [Configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .</span><span class="sxs-lookup"><span data-stu-id="44dc4-164">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for port configuration.</span></span>  
  
#### <a name="step-5-script-role-definition-and-assignments"></a><span data-ttu-id="44dc4-165">Étape 5 : Écrire un script de définition et d’assignation des rôles</span><span class="sxs-lookup"><span data-stu-id="44dc4-165">Step 5: Script role definition and assignments</span></span>  
  
1.  <span data-ttu-id="44dc4-166">En guise d'étape finale, vous devez générer un script qui capture la définition de rôle que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="44dc4-166">As a final step, you should generate a script that captures the role definition you just created.</span></span>  
  
     <span data-ttu-id="44dc4-167">Le redéploiement d’un projet à partir de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] remplace tous les rôles ou appartenances aux rôles qui ne sont pas définis dans le projet.</span><span class="sxs-lookup"><span data-stu-id="44dc4-167">Redeploying a project from [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite any roles or role memberships that are not defined inside the project.</span></span> <span data-ttu-id="44dc4-168">Le moyen le plus rapide de recréer des rôles et des appartenances aux rôles après un redéploiement consiste à recourir à un script.</span><span class="sxs-lookup"><span data-stu-id="44dc4-168">The quickest way to rebuild roles and role membership after redeployment is through script.</span></span>  
  
2.  <span data-ttu-id="44dc4-169">Dans SSMS, accédez au dossier **Rôles** et cliquez avec le bouton droit sur un rôle existant.</span><span class="sxs-lookup"><span data-stu-id="44dc4-169">In SSMS, navigate to the **Roles** folder and right-click an existing role.</span></span>  
  
3.  <span data-ttu-id="44dc4-170">Sélectionnez le **rôle de script**  |  **créer dans**un  |  **fichier**.</span><span class="sxs-lookup"><span data-stu-id="44dc4-170">Select **Script Role as** | **CREATE TO** | **file**.</span></span>  
  
4.  <span data-ttu-id="44dc4-171">Enregistrez le fichier avec une extension .xmla.</span><span class="sxs-lookup"><span data-stu-id="44dc4-171">Save the file with an .xmla file extension.</span></span> <span data-ttu-id="44dc4-172">Pour tester le script, supprimez le rôle actif, ouvrez le fichier dans SSMS, puis appuyez sur la touche F5 pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="44dc4-172">To test the script, delete the current role, open the file in SSMS, and press F5 to execute the script.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="44dc4-173">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="44dc4-173">Next step</span></span>  
 <span data-ttu-id="44dc4-174">Vous pouvez affiner les autorisations de cube de façon à limiter l'accès à des données de dimension ou de cellule.</span><span class="sxs-lookup"><span data-stu-id="44dc4-174">You can refine cube permissions to restrict access to cell or dimension data.</span></span> <span data-ttu-id="44dc4-175">Pour plus d’informations, consultez [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) et [Octroyer un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dc4-175">See [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) and [Grant custom access to cell data &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44dc4-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44dc4-176">See Also</span></span>  
 <span data-ttu-id="44dc4-177">[Méthodologies d’authentification prises en charge par Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="44dc4-177">[Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="44dc4-178">[Accordez des autorisations sur les modèles et les structures d’exploration de données &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="44dc4-178">[Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span></span>  
 [<span data-ttu-id="44dc4-179">Octroyer des autorisations sur un objet de source de données &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="44dc4-179">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  