---
title: Lancement de l’Assistant Paramétrage du moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server]
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: 4abc0e10-96fd-4e46-93d6-d7ee03eec844
author: stevestein
ms.author: sstein
ms.openlocfilehash: ad8a594873e581d116acd50a336652f27002112d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703620"
---
# <a name="launching-database-engine-tuning-advisor"></a><span data-ttu-id="6b45c-102">Lancement de l'Assistant Paramétrage du moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="6b45c-102">Launching Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="6b45c-103">Pour commencer, ouvrez l'interface utilisateur graphique de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="6b45c-103">To begin, open the Database Engine Tuning Advisor graphical user interface (GUI).</span></span> <span data-ttu-id="6b45c-104">Pour la première utilisation, un membre du rôle serveur fixe **sysadmin** doit lancer l’Assistant Paramétrage du moteur de base de données pour initialiser l’application.</span><span class="sxs-lookup"><span data-stu-id="6b45c-104">On first use, a member of the **sysadmin** fixed server role must launch Database Engine Tuning Advisor to initialize the application.</span></span> <span data-ttu-id="6b45c-105">Après l’initialisation, les membres du rôle de base de données fixe **db_owner** peuvent utiliser l’Assistant Paramétrage du moteur de base de données pour paramétrer les bases de données dont ils sont propriétaires.</span><span class="sxs-lookup"><span data-stu-id="6b45c-105">After initialization, members of the **db_owner** fixed database role can use Database Engine Tuning Advisor to tune databases that they own.</span></span> <span data-ttu-id="6b45c-106">Pour plus d’informations sur l’initialisation de l’Assistant Paramétrage du moteur de base de données, consultez [Démarrer et utiliser l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md).</span><span class="sxs-lookup"><span data-stu-id="6b45c-106">For more information about initializing Database Engine Tuning Advisor, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
### <a name="open-the-database-engine-tuning-advisor-gui"></a><span data-ttu-id="6b45c-107">Ouverture de l'interface utilisateur graphique de l'Assistant Paramétrage du moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="6b45c-107">Open the Database Engine Tuning Advisor GUI</span></span>  
  
1.  <span data-ttu-id="6b45c-108">Dans le menu **Démarrer** de Windows, pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de performances**, puis cliquez sur **Assistant Paramétrage du moteur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="6b45c-108">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="6b45c-109">Dans la boîte de dialogue **Se connecter à un serveur** , vérifiez les paramètres par défaut, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6b45c-109">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="6b45c-110">Par défaut, l'Assistant Paramétrage du moteur de base de données s'ouvre avec la configuration représentée dans l'illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="6b45c-110">By default, Database Engine Tuning Advisor opens to the configuration in the following illustration:</span></span>  
  
 <span data-ttu-id="6b45c-111">![Fenêtre par défaut de l'Assistant Paramétrage du moteur de base de données](media/defaultdtagui.gif "Fenêtre par défaut de l'Assistant Paramétrage du moteur de base de données")</span><span class="sxs-lookup"><span data-stu-id="6b45c-111">![Database Engine Tuning Advisor default window](media/defaultdtagui.gif "Database Engine Tuning Advisor default window")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b45c-112">La zone nom de la **session** et de l’onglet affiche le nom de votre ordinateur et l’instance à laquelle vous êtes connecté.</span><span class="sxs-lookup"><span data-stu-id="6b45c-112">The tab and **Session Name** box display the name of your computer and the instance you are connected to.</span></span> <span data-ttu-id="6b45c-113">L'onglet et la zone affichent également la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="6b45c-113">The tab and box also display the current date and time.</span></span>  
  
 <span data-ttu-id="6b45c-114">Lorsque l'Assistant Paramétrage du moteur de base de données s'ouvre pour la première fois, deux volets principaux s'affichent.</span><span class="sxs-lookup"><span data-stu-id="6b45c-114">Two main panes are displayed in the Database Engine Tuning Advisor GUI when it is first opened.</span></span>  
  
-   <span data-ttu-id="6b45c-115">Le volet gauche contient le moniteur de session, qui répertorie toutes les sessions de paramétrage qui ont été effectuées sur cette [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span><span class="sxs-lookup"><span data-stu-id="6b45c-115">The left pane contains the Session Monitor, which lists all tuning sessions that have been performed on this [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="6b45c-116">Lorsque vous ouvrez l'Assistant Paramétrage du moteur de base de données, il affiche une nouvelle session en haut du volet.</span><span class="sxs-lookup"><span data-stu-id="6b45c-116">When you open Database Engine Tuning Advisor, it displays a new session at the top of the pane.</span></span> <span data-ttu-id="6b45c-117">Vous pouvez attribuer un nom à cette session dans le volet voisin.</span><span class="sxs-lookup"><span data-stu-id="6b45c-117">You can name this session in the adjacent pane.</span></span> <span data-ttu-id="6b45c-118">Au départ, seule une session par défaut figure dans la liste.</span><span class="sxs-lookup"><span data-stu-id="6b45c-118">Initially, only a default session is listed.</span></span> <span data-ttu-id="6b45c-119">Il s'agit de la session par défaut que l'Assistant Paramétrage du moteur de base de données crée automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="6b45c-119">This is the default session that Database Engine Tuning Advisor automatically creates for you.</span></span> <span data-ttu-id="6b45c-120">Une fois les bases de données paramétrées, toutes les sessions de paramétrage réalisées pour l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous êtes connecté sont indiquées sous la nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="6b45c-120">After you have tuned databases, all tuning sessions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you are connected are listed below the new session.</span></span> <span data-ttu-id="6b45c-121">Vous pouvez cliquer avec le bouton droit sur une session de paramétrage pour la renommer, la fermer, la supprimer ou la dupliquer.</span><span class="sxs-lookup"><span data-stu-id="6b45c-121">You can right-click a tuning session to rename it, close it, delete it, or clone it.</span></span> <span data-ttu-id="6b45c-122">Si vous cliquez avec le bouton droit dans la liste, vous pouvez trier les sessions sur le nom, l'état, l'heure de création ou créer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="6b45c-122">If you right-click in the list you can sort the sessions by name, status, or creation time, or create a new session.</span></span> <span data-ttu-id="6b45c-123">La section inférieure de ce volet présente des informations détaillées sur la session de paramétrage sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6b45c-123">In the bottom section of this pane, details of the selected tuning session are displayed.</span></span> <span data-ttu-id="6b45c-124">Vous pouvez choisir d’afficher ces informations par catégorie en utilisant le bouton **Par catégorie** , ou vous pouvez les afficher par ordre alphabétique au moyen du bouton **Alphabétique** .</span><span class="sxs-lookup"><span data-stu-id="6b45c-124">You can choose to display the details organized into categories with the **Categorized** button, or you can display them in an alphabetized list by using the **Alphabetical** button.</span></span> <span data-ttu-id="6b45c-125">Vous pouvez également masquer le moniteur de session en faisant glisser le bord du volet droit sur le côté gauche de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6b45c-125">You can also hide Session Monitor by dragging the right pane border to the left side of the window.</span></span> <span data-ttu-id="6b45c-126">Pour le faire réapparaître, faites glisser le bord du volet vers la droite.</span><span class="sxs-lookup"><span data-stu-id="6b45c-126">To view it again, drag the pane border back to the right.</span></span> <span data-ttu-id="6b45c-127">Le moniteur de session permet d'afficher les sessions de paramétrage précédentes ou de les utiliser pour créer de nouvelles sessions avec des définitions similaires.</span><span class="sxs-lookup"><span data-stu-id="6b45c-127">Session Monitor enables you to view previous tuning sessions, or to use them to create new sessions with similar definitions.</span></span> <span data-ttu-id="6b45c-128">Vous pouvez également utiliser le moniteur de session pour étudier les recommandations de paramétrage.</span><span class="sxs-lookup"><span data-stu-id="6b45c-128">You can also use Session Monitor to evaluate tuning recommendations.</span></span> <span data-ttu-id="6b45c-129">Pour plus d’informations, consultez [Afficher et utiliser la sortie de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md).</span><span class="sxs-lookup"><span data-stu-id="6b45c-129">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="6b45c-130">Utilisez le bouton **Précédent** de votre navigateur pour revenir au didacticiel.</span><span class="sxs-lookup"><span data-stu-id="6b45c-130">Use the **Back** button on your browser to return to this tutorial.</span></span>  
  
-   <span data-ttu-id="6b45c-131">Le volet droit contient les onglets **Général** et **Options de paramétrage** .</span><span class="sxs-lookup"><span data-stu-id="6b45c-131">The right pane contains the **General** and the **Tuning Options** tabs.</span></span> <span data-ttu-id="6b45c-132">Ces onglets permettent de définir votre session de paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="6b45c-132">This is where you can define your Database Engine Tuning session.</span></span> <span data-ttu-id="6b45c-133">Sous l’onglet **Général** , vous pouvez taper le nom de votre session de paramétrage, spécifier le fichier de charge de travail ou la table à utiliser, et sélectionner les bases de données et les tables à paramétrer au cours de cette session.</span><span class="sxs-lookup"><span data-stu-id="6b45c-133">In the **General** tab, you type the name for your tuning session, specify the workload file or table to use, and select the databases and tables you want to tune in this session.</span></span> <span data-ttu-id="6b45c-134">Une charge de travail est un ensemble d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui s'exécute sur une ou plusieurs bases de données que vous souhaitez paramétrer.</span><span class="sxs-lookup"><span data-stu-id="6b45c-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="6b45c-135">L'Assistant Paramétrage du moteur de base de données utilise des fichiers de trace et des tables de trace, des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fichiers XML comme entrée de charge de travail pour le paramétrage des bases de données.</span><span class="sxs-lookup"><span data-stu-id="6b45c-135">Database Engine Tuning Advisor uses trace files, trace tables, [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, or XML files as workload input when tuning databases.</span></span> <span data-ttu-id="6b45c-136">Sous l’onglet **Options de paramétrage** , vous pouvez sélectionner les structures de création de base de données physiques (index ou vues indexées) et la stratégie de partitionnement que l’Assistant Paramétrage du moteur de base de données doit prendre en compte au cours de son analyse.</span><span class="sxs-lookup"><span data-stu-id="6b45c-136">On the **Tuning Options** tab, you can select the physical database design structures (indexes or indexed views) and the partitioning strategy that you want Database Engine Tuning Advisor to consider during its analysis.</span></span> <span data-ttu-id="6b45c-137">Dans cet onglet, vous pouvez également spécifier la durée maximale pendant laquelle l'Assistant Paramétrage du moteur de base de données paramètre une charge de travail.</span><span class="sxs-lookup"><span data-stu-id="6b45c-137">On this tab you also can specify the maximum time that Database Engine Tuning Advisor takes to tune a workload.</span></span> <span data-ttu-id="6b45c-138">La durée par défaut est d'une heure.</span><span class="sxs-lookup"><span data-stu-id="6b45c-138">By default, Database Engine Tuning Advisor will tune a workload for one hour.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b45c-139">L’Assistant Paramétrage du moteur de base de données peut accepter les fichiers XML comme entrée quand un script [!INCLUDE[tsql](../../includes/tsql-md.md)] est importé à partir de l’Éditeur de requête [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6b45c-139">Database Engine Tuning Advisor can take XML files as input when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is imported from [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span> <span data-ttu-id="6b45c-140">Pour plus d’informations, consultez la section sur le lancement de l’Assistant Paramétrage du moteur de base de données à partir de l’Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans [Démarrer et utiliser l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md).</span><span class="sxs-lookup"><span data-stu-id="6b45c-140">For more information, see the section on launching Database Engine Tuning Advisor from the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor in [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6b45c-141">Tâche suivante de la leçon</span><span class="sxs-lookup"><span data-stu-id="6b45c-141">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6b45c-142">Définition des options du menu Outils et de la disposition</span><span class="sxs-lookup"><span data-stu-id="6b45c-142">Setting Tool Options and Layout</span></span>](lesson-1-2-setting-tool-options-and-layout.md)  
  
  