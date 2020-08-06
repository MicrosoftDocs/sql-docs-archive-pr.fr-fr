---
title: Démarrage de l’utilitaire en ligne de commande dta et paramétrage d’une charge de travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b2b1755a2ce8299556ab7d0ae14c89d3b2c8554
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695007"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a><span data-ttu-id="40ff2-102">Démarrage de l'utilitaire de ligne de commande dta et paramétrage d'une charge de travail</span><span class="sxs-lookup"><span data-stu-id="40ff2-102">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>
  <span data-ttu-id="40ff2-103">Au cours de cette tâche, vous allez démarrer l’utilitaire **dta** et afficher son aide, puis vous allez l’utiliser afin de paramétrer une charge de travail à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="40ff2-103">This task guides you through starting the **dta** utility, viewing its Help, and then using it to tune a workload from the command prompt.</span></span> <span data-ttu-id="40ff2-104">Elle utilise la charge de travail, MyScript. SQL, que vous avez créée pour l’Assistant Paramétrage du moteur de base de données la pratique de l’interface utilisateur graphique (GUI) de [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md).</span><span class="sxs-lookup"><span data-stu-id="40ff2-104">It uses the workload, MyScript.sql, which you created for the Database Engine Tuning Advisor graphical user interface (GUI) practice [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
 <span data-ttu-id="40ff2-105">Le didacticiel utilise l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="40ff2-105">The tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="40ff2-106">Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.</span><span class="sxs-lookup"><span data-stu-id="40ff2-106">For security reasons, the sample databases are not installed by default.</span></span> <span data-ttu-id="40ff2-107">Pour installer les exemples de bases de données, consultez [Installation des exemples SQL Server et des exemples de bases de données](http://sqlserversamples.codeplex.com).</span><span class="sxs-lookup"><span data-stu-id="40ff2-107">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
 <span data-ttu-id="40ff2-108">Les tâches suivantes sont destinées à vous guider pour ouvrir une invite de commandes, démarrer l’utilitaire en ligne de commande **dta** , afficher son aide sur la syntaxe et paramétrer la charge de travail simple, MyScript.sql, que vous avez créée dans le cadre de l’exercice : [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md).</span><span class="sxs-lookup"><span data-stu-id="40ff2-108">The following tasks guide you through opening a command prompt, starting the **dta** command prompt utility, viewing its syntax Help, and tuning a simple workload, MyScript.sql, which you created in [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a><span data-ttu-id="40ff2-109">Pour démarrer l'utilitaire de ligne de commande dta et afficher l'aide</span><span class="sxs-lookup"><span data-stu-id="40ff2-109">To start the dta command prompt utility and view Help</span></span>  
  
1.  <span data-ttu-id="40ff2-110">Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur **Accessoires**, puis cliquez sur **Invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="40ff2-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="40ff2-111">À l’invite de commandes, tapez ce qui suit, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="40ff2-111">At the command prompt, type the following, and press ENTER:</span></span>  
  
    ```  
    dta -? | more  
    ```  
  
     <span data-ttu-id="40ff2-112">La section `| more` de cette commande est facultative.</span><span class="sxs-lookup"><span data-stu-id="40ff2-112">The `| more` part of this command is optional.</span></span> <span data-ttu-id="40ff2-113">Sachez cependant que son utilisation permet de parcourir l'aide sur la syntaxe de l'utilitaire.</span><span class="sxs-lookup"><span data-stu-id="40ff2-113">However, using it enables you to page through the syntax help for the utility.</span></span> <span data-ttu-id="40ff2-114">Appuyez sur Entrée pour faire défiler le texte de l'aide ligne par ligne ou sur Espace pour le faire défiler page par page.</span><span class="sxs-lookup"><span data-stu-id="40ff2-114">Press ENTER to advance the help text by the line, or press the SPACEBAR to advance it by the page.</span></span>  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a><span data-ttu-id="40ff2-115">Pour paramétrer une charge de travail simple à l'aide de l'utilitaire de ligne de commande dta</span><span class="sxs-lookup"><span data-stu-id="40ff2-115">To tune a simple workload by using the dta command prompt utility</span></span>  
  
1.  <span data-ttu-id="40ff2-116">À l'invite de commandes, indiquez le chemin du répertoire dans lequel vous avez stocké le fichier MyScript.sql.</span><span class="sxs-lookup"><span data-stu-id="40ff2-116">At the command prompt, navigate to the directory where you have stored the MyScript.sql file.</span></span>  
  
2.  <span data-ttu-id="40ff2-117">À l'invite de commandes, tapez la commande suivante et appuyez sur Entrée pour l'exécuter et démarrer la session de paramétrage (notez que l'utilitaire respecte la distinction entre les majuscules et les minuscules lorsqu'il analyse les commandes) :</span><span class="sxs-lookup"><span data-stu-id="40ff2-117">At the command prompt, type the following, and press ENTER to run the command and start the tuning session (note that the utility is case-sensitive when it parses commands):</span></span>  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     <span data-ttu-id="40ff2-118">où `-S` spécifie le nom de votre serveur et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est installée.</span><span class="sxs-lookup"><span data-stu-id="40ff2-118">where `-S` specifies the name of your server and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is installed.</span></span> <span data-ttu-id="40ff2-119">Le paramètre `-E` spécifie que vous souhaitez utiliser une connexion approuvée à l'instance, ce qui est approprié si vous utilisez un compte de domaine Windows pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="40ff2-119">The setting `-E` specifies that you want to use a trusted connection to the instance, which is appropriate if you are connecting with a Windows domain account.</span></span> <span data-ttu-id="40ff2-120">Le paramètre `-D` spécifie la base de données à paramétrer, `-if` le fichier de la charge de travail, `-s` le nom de la session, `-of` le fichier dans lequel l'outil doit enregistrer le script [!INCLUDE[tsql](../../includes/tsql-md.md)] de recommandations et enfin, le paramètre `-ox` indique le fichier dans lequel l'outil doit enregistrer les recommandations au format XML.</span><span class="sxs-lookup"><span data-stu-id="40ff2-120">The setting `-D` specifies the database that you want to tune, `-if` specifies the workload file, `-s` specifies the session name, `-of` specifies the file to which you want the tool to write the [!INCLUDE[tsql](../../includes/tsql-md.md)] recommendations script, and `-ox` specifies the file to which you want the tool to write the recommendations in XML format.</span></span> <span data-ttu-id="40ff2-121">Les trois derniers commutateurs spécifient les options de paramétrage comme suit : `-fa IDX_IV` spécifie que l'Assistant Paramétrage du moteur de base de données doit considérer uniquement l'ajout des index (cluster et non cluster) et des vues indexées ; `-fp NONE` spécifie qu'aucune stratégie de partition ne doit être prise en compte au cours de l'analyse et `-fk NONE` indique qu'aucune structure de création physique existante dans la base de données ne doit être conservée lorsque l'Assistant Paramétrage du moteur de base de données effectue ses recommandations.</span><span class="sxs-lookup"><span data-stu-id="40ff2-121">The last three switches specify tuning options as follows: `-fa IDX_IV` specifies that Database Engine Tuning Advisor should only consider adding indexes (both clustered and nonclustered) and indexed views; `-fp NONE` specifies that no partition strategy should be considered during analysis; and `-fk NONE` specifies that no existing physical design structures in the database must be kept when Database Engine Tuning Advisor makes its recommendations.</span></span>  
  
3.  <span data-ttu-id="40ff2-122">Lorsque l'Assistant Paramétrage du moteur de base de données a terminé de paramétrer la charge de travail, il affiche un message signalant que votre session de paramétrage s'est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="40ff2-122">After Database Engine Tuning Advisor finishes tuning the workload, it displays a message indicating that your tuning session completed successfully.</span></span> <span data-ttu-id="40ff2-123">Vous pouvez afficher les résultats du paramétrage. Pour cela, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour ouvrir les fichiers MySession2OutputScript.sql et RMySession2Output.xml.</span><span class="sxs-lookup"><span data-stu-id="40ff2-123">You can view the tuning results, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open the files MySession2OutputScript.sql and MySession2Output.xml.</span></span> <span data-ttu-id="40ff2-124">Une autre méthode consiste à ouvrir la session de paramétrage MySession2 dans l’interface de l’Assistant Paramétrage du moteur de base de données et à afficher les recommandations et les rapports en procédant comme aux exercices [Affichage des recommandations pour le paramétrage](lesson-1-2-viewing-tuning-recommendations.md) et [Affichage des rapports de paramétrage](lesson-1-3-viewing-tuning-reports.md).</span><span class="sxs-lookup"><span data-stu-id="40ff2-124">Alternatively, you can also open the MySession2 tuning session in the Database Engine Tuning Advisor GUI and view its recommendations and reports in the same way that you did in [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) and [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="40ff2-125">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="40ff2-125">Summary</span></span>  
 <span data-ttu-id="40ff2-126">Vous avez correctement paramétré une charge de travail simple à partir de l’invite de commandes en utilisant l’utilitaire **dta** .</span><span class="sxs-lookup"><span data-stu-id="40ff2-126">You have completed tuning a simple workload from the command prompt by using the **dta** utility.</span></span> <span data-ttu-id="40ff2-127">Cet outil fournit de nombreuses autres options de paramétrage.</span><span class="sxs-lookup"><span data-stu-id="40ff2-127">This tool provides many other tuning options.</span></span> <span data-ttu-id="40ff2-128">Pour plus d’informations, consultez l’aide de cet outil (**dta -?**) et la rubrique [Utilitaire dta](dta-utility.md) .</span><span class="sxs-lookup"><span data-stu-id="40ff2-128">Refer to the tool Help (**dta -?**) and the reference topic [dta Utility](dta-utility.md) for more information.</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="40ff2-129">Fin du didacticiel</span><span class="sxs-lookup"><span data-stu-id="40ff2-129">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="40ff2-130">Une fois les leçons du didacticiel terminées, reportez-vous aux rubriques suivantes pour plus d'informations sur l'Assistant Paramétrage du moteur de base de données :</span><span class="sxs-lookup"><span data-stu-id="40ff2-130">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="40ff2-131">[Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md) : cette rubrique propose des descriptions de la façon d’effectuer des tâches avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="40ff2-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="40ff2-132">[Utilitaire dta](dta-utility.md) : cette rubrique propose des documents de référence sur l’utilitaire en ligne de commande et le fichier XML facultatif que vous pouvez utiliser pour contrôler le fonctionnement de l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="40ff2-132">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
 <span data-ttu-id="40ff2-133">Pour revenir au début de ce didacticiel, consultez [Didacticiel : Assistant Paramétrage du moteur de base de données](tutorial-database-engine-tuning-advisor.md).</span><span class="sxs-lookup"><span data-stu-id="40ff2-133">To return to the start of the tutorial, see [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ff2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ff2-134">See Also</span></span>  
 [<span data-ttu-id="40ff2-135">Didacticiels sur le moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="40ff2-135">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  