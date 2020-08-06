---
title: Paramétrage d’une charge de travail | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
author: stevestein
ms.author: sstein
ms.openlocfilehash: f95aab55d402ac72228dcc4326ad00ea15e7471f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703624"
---
# <a name="tuning-a-workload"></a><span data-ttu-id="83031-102">Paramétrage d'une charge de travail</span><span class="sxs-lookup"><span data-stu-id="83031-102">Tuning a Workload</span></span>
  <span data-ttu-id="83031-103">L'Assistant Paramétrage du moteur de base de données peut servir à trouver la conception de base de données physique qui permet d'obtenir les meilleures performances des requêtes sur les bases de données et les tables que vous avez sélectionnées pour le paramétrage.</span><span class="sxs-lookup"><span data-stu-id="83031-103">The Database Engine Tuning Advisor can be used to find the best physical database design for query performance on the databases and tables that you select for tuning.</span></span>  
  
 <span data-ttu-id="83031-104">Cette tâche utilise l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="83031-104">This task uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="83031-105">Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.</span><span class="sxs-lookup"><span data-stu-id="83031-105">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="83031-106">Pour installer les exemples de bases de données, consultez [Installation des exemples SQL Server et des exemples de bases de données](http://sqlserversamples.codeplex.com).</span><span class="sxs-lookup"><span data-stu-id="83031-106">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
### <a name="tune-a-workload-transact-sql-script-file"></a><span data-ttu-id="83031-107">Pour paramétrer le fichier de script Transact-SQL d'une charge de travail</span><span class="sxs-lookup"><span data-stu-id="83031-107">Tune a workload Transact-SQL script file</span></span>  
  
1.  <span data-ttu-id="83031-108">Copiez une ou plusieurs instructions SELECT exemple à partir de « A.</span><span class="sxs-lookup"><span data-stu-id="83031-108">Copy a sample SELECT statement or statements from "A.</span></span> <span data-ttu-id="83031-109">Utilisation de SELECT pour extraire des lignes et des colonnes » dans [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql), puis collez les instructions dans l’Éditeur de requête de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83031-109">Using SELECT to retrieve rows and columns" in [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql) and paste the statements into the Query Editor of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="83031-110">Enregistrez le fichier sous le nom **MyScript.sql** dans un répertoire où il est facile de le retrouver.</span><span class="sxs-lookup"><span data-stu-id="83031-110">Save the file as **MyScript.sql** in a directory where you can easily find it.</span></span>  
  
2.  <span data-ttu-id="83031-111">Démarrez l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="83031-111">Start Database Engine Tuning Advisor.</span></span> <span data-ttu-id="83031-112">Consultez [Lancement de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md).</span><span class="sxs-lookup"><span data-stu-id="83031-112">See [Launching Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="83031-113">Dans le volet droit de l’interface utilisateur graphique de l’Assistant Paramétrage du moteur de base de données, tapez **MySession** dans la zone **Nom de session**.</span><span class="sxs-lookup"><span data-stu-id="83031-113">In the right pane of the Database Engine Tuning Advisor GUI, type **MySession** in **Session name**.</span></span>  
  
4.  <span data-ttu-id="83031-114">Sélectionnez **Fichier** pour votre **Charge de travail**et cliquez sur **Rechercher un fichier de charge de travail** pour localiser le fichier **MyScript.sql** que vous avez enregistré à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="83031-114">Select **File** for your **Workload**, and click the **Browse for a workload file** button to locate the **MyScript.sql** file that you saved in Step 1.</span></span>  
  
5.  <span data-ttu-id="83031-115">Sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans la liste **Base de données pour l’analyse de la charge de travail** , sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans la grille **Sélectionnez les bases de données et tables à analyser** et laissez la case **Enregistrer le journal de paramétrage** cochée.</span><span class="sxs-lookup"><span data-stu-id="83031-115">Select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Database for workload analysis** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Select databases and tables to tune** grid, and leave **Save tuning log** selected.</span></span> <span data-ttu-id="83031-116">**Base de données pour l’analyse de la charge de travail** spécifie la première base de données à laquelle l’Assistant Paramétrage du moteur de base de données se connecte lors du paramétrage d’une charge de travail.</span><span class="sxs-lookup"><span data-stu-id="83031-116">**Database for workload analysis** specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="83031-117">Dès que le paramétrage commence, l'Assistant Paramétrage du moteur de base de données se connecte aux bases de données spécifiées par les instructions `USE DATABASE` contenues dans la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="83031-117">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
6.  <span data-ttu-id="83031-118">Cliquez sur l’onglet **options de paramétrage** . Vous ne pouvez pas définir d’options de paramétrage pour cette pratique, mais prenez un moment pour passer en revue les options de paramétrage par défaut.</span><span class="sxs-lookup"><span data-stu-id="83031-118">Click the **Tuning Options** tab. You will not set any tuning options for this practice, but take a moment to review the default tuning options.</span></span> <span data-ttu-id="83031-119">Appuyez sur F1 pour afficher l'aide de cette page à onglets.</span><span class="sxs-lookup"><span data-stu-id="83031-119">Press F1 to view the Help for this tabbed page.</span></span> <span data-ttu-id="83031-120">Cliquez sur **Options avancées** pour afficher des options de paramétrage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="83031-120">Click **Advanced Options** to view additional tuning options.</span></span> <span data-ttu-id="83031-121">Cliquez sur **Aide** dans la boîte de dialogue **Options de paramétrage avancées** pour obtenir des informations sur les options de paramétrage affichées ici.</span><span class="sxs-lookup"><span data-stu-id="83031-121">Click **Help** in the **Advanced Tuning Options** dialog box for information about the tuning options that are displayed there.</span></span> <span data-ttu-id="83031-122">Cliquez sur **Annuler** pour fermer la boîte de dialogue **Options de paramétrage avancées** sans désactiver les options sélectionnées par défaut.</span><span class="sxs-lookup"><span data-stu-id="83031-122">Click **Cancel** to close the **Advanced Tuning Options** dialog box, leaving the default options selected.</span></span>  
  
7.  <span data-ttu-id="83031-123">Dans la barre d'outils, cliquez sur le bouton **Démarrer l'analyse** .</span><span class="sxs-lookup"><span data-stu-id="83031-123">Click the **Start Analysis** button on the toolbar.</span></span> <span data-ttu-id="83031-124">Si Assistant Paramétrage du moteur de base de données analyse la charge de travail, vous pouvez surveiller son état dans l’onglet **progression** . Une fois le paramétrage terminé, l’onglet **recommandations** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="83031-124">While Database Engine Tuning Advisor is analyzing the workload, you can monitor the status on the **Progress** tab. When tuning is complete, the **Recommendations** tab is displayed.</span></span>  
  
     <span data-ttu-id="83031-125">Si vous recevez une erreur relative à la date et à l’heure d’arrêt du paramétrage, sélectionnez l’option **arrêter à** l’heure sous l’onglet **options de paramétrage** principales. Assurez-vous que l’heure et la date d' **arrêt** sont supérieures à la date et à l’heure actuelles et, si nécessaire, modifiez-les.</span><span class="sxs-lookup"><span data-stu-id="83031-125">If you receive an error about the tuning stop date and time, check the **Stop at** time on the main **Tuning Options** tab. Make sure the **Stop at** date and time are greater than the current date and time, and if necessary, change them.</span></span>  
  
8.  <span data-ttu-id="83031-126">Une fois l’analyse terminée, enregistrez votre recommandation sous la forme d’un script [!INCLUDE[tsql](../../includes/tsql-md.md)] en cliquant sur **Enregistrer les recommandations** dans le menu **Actions** .</span><span class="sxs-lookup"><span data-stu-id="83031-126">After the analysis completes, save your recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script by clicking **Save Recommendations** on the **Actions** menu.</span></span> <span data-ttu-id="83031-127">Dans la boîte de dialogue **Enregistrer sous** , accédez au répertoire dans lequel vous souhaitez enregistrer le script de recommandations et tapez le nom de fichier **MyRecommendations**.</span><span class="sxs-lookup"><span data-stu-id="83031-127">In the **Save As** dialog box, navigate to the directory where you want to save the recommendations script, and type the file name **MyRecommendations**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="83031-128">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="83031-128">Summary</span></span>  
 <span data-ttu-id="83031-129">Vous avez correctement paramétré une charge de travail d'instruction SELECT simple sur la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="83031-129">You have completed tuning a simple SELECT statement workload on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="83031-130">L'Assistant Paramétrage du moteur de base de données peut également utiliser les fichiers et les tables de trace [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] comme charges de travail de paramétrage.</span><span class="sxs-lookup"><span data-stu-id="83031-130">The Database Engine Tuning Advisor can also take [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace files and tables as tuning workloads.</span></span> <span data-ttu-id="83031-131">Au cours de la tâche suivante, vous allez afficher et interpréter les recommandations de paramétrage que vous avez reçues en résultat de l'exercice de paramétrage.</span><span class="sxs-lookup"><span data-stu-id="83031-131">The next task shows you how to view and interpret the tuning recommendations that you received as a result of the practice tuning.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="83031-132">Tâche suivante de la leçon</span><span class="sxs-lookup"><span data-stu-id="83031-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="83031-133">Affichage des recommandations pour le paramétrage</span><span class="sxs-lookup"><span data-stu-id="83031-133">Viewing Tuning Recommendations</span></span>](lesson-1-2-viewing-tuning-recommendations.md)  
  
  