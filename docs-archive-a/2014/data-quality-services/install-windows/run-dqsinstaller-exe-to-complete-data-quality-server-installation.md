---
title: Exécuter DQSInstaller.exe pour effectuer l’installation du serveur DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7a8c96e0-1328-4f35-97fc-b6d9cb808bae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9acbf96728fad51711c364d801ab4ce1f3599f57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701981"
---
# <a name="run-dqsinstallerexe-to-complete-data-quality-server-installation"></a><span data-ttu-id="d02b1-102">Exécuter DQSInstaller.exe pour terminer l'installation du serveur DQS</span><span class="sxs-lookup"><span data-stu-id="d02b1-102">Run DQSInstaller.exe to Complete Data Quality Server Installation</span></span>
  <span data-ttu-id="d02b1-103">Pour terminer l'installation du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , vous devez exécuter le fichier DQSInstaller.exe après avoir installé [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d02b1-103">To complete the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation, you must run the DQSInstaller.exe file after installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d02b1-104">Cette rubrique décrit comment exécuter DQSInstaller.exe à partir de l'écran **Démarrer** , du menu **Démarrer** , de l'Explorateur Windows ou d'une invite de commandes ; vous pouvez choisir l'une des manières suivantes pour exécuter le fichier DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-104">This topic describes how to run the DQSInstaller.exe from the **Start** screen, **Start** menu, Windows Explorer, or Command Prompt; you can choose any of the ways to run the DQSInstaller.exe file.</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d02b1-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d02b1-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="d02b1-106">Vous devez avoir sélectionné **Data Quality Services** sous **Services Moteur de base de données** sur la page de sélection de fonctionnalités du programme d'installation de SQL Server lors de l'installation de SQL Server, et terminé l'installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d02b1-106">You must have selected **Data Quality Services** under **Database Engine Services** on the Feature Selection page in the SQL Server setup while installing SQL Server, and must have completed the SQL Server installation.</span></span> <span data-ttu-id="d02b1-107">Pour plus d’informations, consultez [Installer Data Quality Services](install-data-quality-services.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-107">For more information, see [Install Data Quality Services](install-data-quality-services.md).</span></span>  
  
-   <span data-ttu-id="d02b1-108">Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance du moteur de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d02b1-108">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server database engine instance.</span></span>  
  
-   <span data-ttu-id="d02b1-109">Vous devez être connecté en tant que membre du groupe Administrateurs sur l'ordinateur où vous exécutez DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-109">You must be logged on as a member of the Administrators group on the computer where you are running DQSInstaller.exe.</span></span>  
  
##  <a name="run-dqsinstallerexe-from-start-screen-start-menu-or-windows-explorer"></a><a name="WindowsExplorer"></a><span data-ttu-id="d02b1-110">Exécuter DQSInstaller.exe à partir de l’écran d’accueil, du menu Démarrer ou de l’Explorateur Windows</span><span class="sxs-lookup"><span data-stu-id="d02b1-110">Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer</span></span>  
  
1.  <span data-ttu-id="d02b1-111">Sur l'ordinateur sur lequel vous avez choisi d'installer le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], exécutez le fichier DQSInstaller.exe d'une des manières suivantes, selon le cas :</span><span class="sxs-lookup"><span data-stu-id="d02b1-111">On the computer where you chose to install [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], run the DQSInstaller.exe file using any of the following as applicable:</span></span>  
  
    -   <span data-ttu-id="d02b1-112">Écran**Démarrer**: dans l'écran **Démarrer** , cliquez sur **Data Quality Server Installer**.</span><span class="sxs-lookup"><span data-stu-id="d02b1-112">**Start screen**: On the **Start** screen, click **Data Quality Server Installer.**</span></span>  
  
    -   <span data-ttu-id="d02b1-113">**Menu Démarrer**: dans la barre des tâches, cliquez sur **Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Microsoft SQL Server 2014**.</span><span class="sxs-lookup"><span data-stu-id="d02b1-113">**Start menu**: On the taskbar, click **Start**, point to **All Programs**, click **Microsoft SQL Server 2014**.</span></span> <span data-ttu-id="d02b1-114">Sous **Microsoft SQL Server 2014**, cliquez sur **Data Quality Services**, puis sur **Data Quality Server installer.**</span><span class="sxs-lookup"><span data-stu-id="d02b1-114">Under **Microsoft SQL Server 2014**, click **Data Quality Services**, and then click **Data Quality Server Installer.**</span></span>  
  
    -   <span data-ttu-id="d02b1-115">**Explorateur Windows**: recherchez le fichier DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-115">**Windows Explorer**: Locate the DQSInstaller.exe file.</span></span> <span data-ttu-id="d02b1-116">Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe sera copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn.</span><span class="sxs-lookup"><span data-stu-id="d02b1-116">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn.</span></span> <span data-ttu-id="d02b1-117">Double-cliquez sur le fichier DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-117">Double-click the DQSInstaller.exe file.</span></span>  
  
2.  <span data-ttu-id="d02b1-118">Une fenêtre d'invite de commandes s'affiche qui indique l'état de l'installation.</span><span class="sxs-lookup"><span data-stu-id="d02b1-118">A command prompt window appears that shows the status of the installation.</span></span> <span data-ttu-id="d02b1-119">Vous remarquerez les trois événements suivants :</span><span class="sxs-lookup"><span data-stu-id="d02b1-119">You will notice the following three things:</span></span>  
  
    1.  <span data-ttu-id="d02b1-120">Le programme d'installation crée un fichier journal d'installation, DQS_install.log, qui contient des informations sur les actions effectuées lors de l'exécution du fichier DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-120">The installer creates an installation log file, DQS_install.log, which contains information about the actions performed on running the DQSInstaller.exe file.</span></span> <span data-ttu-id="d02b1-121">Si vous avez installé l'instance par défaut de SQL Server, le fichier DQS_install.log sera copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span><span class="sxs-lookup"><span data-stu-id="d02b1-121">If you installed the default instance of SQL Server, the DQS_install.log file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span></span>  
  
    2.  <span data-ttu-id="d02b1-122">Le programme d'installation utilise le classement par défaut du serveur, SQL_Latin1_General_CP1_CI_AS, pour installer le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d02b1-122">The installer uses the default server collation, SQL_Latin1_General_CP1_CI_AS, for installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="d02b1-123">Vous pouvez fournir une valeur différente de classement du serveur pour installer le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] uniquement si vous exécutez DQSInstaller.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d02b1-123">You can provide a different server collation value for installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] only if you are running DQSInstaller.exe from command prompt.</span></span> <span data-ttu-id="d02b1-124">Pour plus d'informations, consultez la section [Exécuter DQSInstaller.exe à partir d'une invite de commandes](#CommandPrompt) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d02b1-124">For more information, see [Run DQSInstaller.exe from Command Prompt](#CommandPrompt) later in this topic.</span></span>  
  
    3.  <span data-ttu-id="d02b1-125">Le programme d'installation vérifie tous les redémarrages en attente sur votre ordinateur dus à toutes les mises à jour qui ont été récemment installées sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d02b1-125">The installer checks for any pending restarts on your computer owing to any updates that have been recently installed on your computer.</span></span> <span data-ttu-id="d02b1-126">Si des redémarrages en attente sont trouvés, un message apparaît vous en informant, et vous pouvez choisir de poursuivre ou d'interrompre l'installation en appuyant sur O ou N respectivement.</span><span class="sxs-lookup"><span data-stu-id="d02b1-126">If any pending restarts are found, a message appears to notify you about the same, and you can choose to continue or abort the installation by pressing Y or N respectively.</span></span> <span data-ttu-id="d02b1-127">S'il existe des redémarrages en attente, nous vous recommandons d'abandonner l'installation, de redémarrer votre ordinateur, puis d'exécuter à nouveau DQSInstaller.exe.</span><span class="sxs-lookup"><span data-stu-id="d02b1-127">We recommend that if there are any pending restarts, you must abort the installation, restart your computer, and then run the DQSInstaller.exe again.</span></span>  
  
3.  <span data-ttu-id="d02b1-128">Vous êtes invité à taper un mot de passe pour la clé principale de base de données.</span><span class="sxs-lookup"><span data-stu-id="d02b1-128">You are prompted to type a password for the database master key.</span></span> <span data-ttu-id="d02b1-129">La clé principale de base de données est requise pour chiffrer les clés du fournisseur de services de données de référence qui seront stockées dans la base de données DQS_MAIN lorsque vous installerez des fournisseurs de données de référence dans [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d02b1-129">The database master key is required to encrypt the reference data service provider keys that will be stored in the DQS_MAIN database when you set up reference data providers in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) later.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d02b1-130">Le mot de passe doit comporter au moins 8 caractères et doit contenir des caractères provenant de trois des quatre catégories suivantes : lettre majuscule anglaise (A, B, C,... Z), lettre minuscule anglaise (a, b, c,... z), chiffre (0, 1, 2,... 9) et les caractères non alphanumériques ou spéciaux (~ ! @ # $% ^& \* () _-+ = | \\ {} []:;"' <>,. ? /).</span><span class="sxs-lookup"><span data-stu-id="d02b1-130">The password must be at least 8 characters long, and must contain characters from three of the following four categories: English upper case letter (A, B, C,... Z), English lowercase letter (a, b, c,... z), Numeral (0, 1, 2,... 9), and nonalphanumeric or special character (~!@#$%^&\*()_-+=|\\{}[]:;"'<>,.?/).</span></span> <span data-ttu-id="d02b1-131">Par exemple : P@ssword.</span><span class="sxs-lookup"><span data-stu-id="d02b1-131">For example: P@ssword.</span></span> <span data-ttu-id="d02b1-132">Le programme d'installation vous invite à entrer un autre mot de passe si le mot de passe actuel ne correspond pas aux conditions.</span><span class="sxs-lookup"><span data-stu-id="d02b1-132">The installer will prompt you to enter another password if the current password does not match the requirement.</span></span>  
  
4.  <span data-ttu-id="d02b1-133">Fournissez un mot de passe, confirmez le mot de passe, puis appuyez sur ENTRÉE pour continuer l'installation.</span><span class="sxs-lookup"><span data-stu-id="d02b1-133">Provide a password, confirm the password, and then press ENTER to continue with the installation.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d02b1-134">Vous devez conserver le mot de passe spécifié pour la clé principale de base de données parce que vous en aurez besoin plus tard pour restaurer les sauvegardes des bases de données DQS, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d02b1-134">You must retain the password specified for the database master key because you will require it while restoring the DQS databases from a backup in future, if you choose to do so.</span></span> <span data-ttu-id="d02b1-135">Pour plus d'informations sur la restauration d'une base de données DQS, consultez [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-135">For more information about restoring DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
5.  <span data-ttu-id="d02b1-136">Si une base de données Master Data Services est présente dans la même instance SQL Server que le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], le programme d'installation crée un utilisateur mappé dans la connexion Master Data Services, et lui affecte le rôle dqs_administrator sur la base de données DQS_MAIN.</span><span class="sxs-lookup"><span data-stu-id="d02b1-136">If a Master Data Services database is present in the same SQL Server instance as [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], the installer creates a user mapped to the Master Data Services login, and grants it the dqs_administrator role on the DQS_MAIN database.</span></span> <span data-ttu-id="d02b1-137">Pour plus d'informations sur l'installation de Master Data Services et la création d'une base de données Master Data Services, consultez [Install Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-137">For information about installing Master Data Services and creating a Master Data Services database, see [Install Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).</span></span>  
  
6.  <span data-ttu-id="d02b1-138">Un message d'achèvement s'affiche une fois l'installation terminée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-138">A completion message is displayed after the installation has completed successfully.</span></span> <span data-ttu-id="d02b1-139">Appuyez sur n'importe quelle touche pour fermer la fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d02b1-139">Press any key to close the command prompt window.</span></span>  
  
##  <a name="run-dqsinstallerexe-from-command-prompt"></a><a name="CommandPrompt"></a><span data-ttu-id="d02b1-140">Exécuter DQSInstaller.exe à partir de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="d02b1-140">Run DQSInstaller.exe from Command Prompt</span></span>  
 <span data-ttu-id="d02b1-141">Vous pouvez exécuter DQSInstaller.exe depuis une invite de commandes à l'aide des paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="d02b1-141">You can run DQSInstaller.exe from command prompt using the following command-line parameters:</span></span>  
  
|<span data-ttu-id="d02b1-142">Paramètre DQSInstaller.exe</span><span class="sxs-lookup"><span data-stu-id="d02b1-142">DQSInstaller.exe Parameter</span></span>|<span data-ttu-id="d02b1-143">Description</span><span class="sxs-lookup"><span data-stu-id="d02b1-143">Description</span></span>|<span data-ttu-id="d02b1-144">Exemple de syntaxe</span><span class="sxs-lookup"><span data-stu-id="d02b1-144">Sample Syntax</span></span>|  
|--------------------------------|-----------------|-------------------|  
|<span data-ttu-id="d02b1-145">-collation</span><span class="sxs-lookup"><span data-stu-id="d02b1-145">-collation</span></span>|<span data-ttu-id="d02b1-146">Le classement du serveur à utiliser pour installer le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d02b1-146">The server collation to be used for installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span><br /><br /> <span data-ttu-id="d02b1-147">DQS prend seulement en charge le classement qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="d02b1-147">DQS supports only case-insensitive collation.</span></span> <span data-ttu-id="d02b1-148">Si vous spécifiez un classement qui respecte la casse, le programme d'installation essaie d'utiliser la version qui ne respecte pas la casse du classement spécifié.</span><span class="sxs-lookup"><span data-stu-id="d02b1-148">If you specify a case-sensitive collation, the installer attempts to use the case-insensitive version of the specified collation.</span></span> <span data-ttu-id="d02b1-149">S'il n'existe aucune version ne respectant pas la casse, ou si le classement n'est pas pris en charge par SQL, l'installation du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] échoue.</span><span class="sxs-lookup"><span data-stu-id="d02b1-149">If there is no case-insensitive version, or if the collation is unsupported by SQL, the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation fails.</span></span><br /><br /> <span data-ttu-id="d02b1-150">Si un classement du serveur n'est pas spécifié, le classement par défaut, SQL_Latin1_General_CP1_CI_AS, est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d02b1-150">If a server collation is not specified, the default collation, SQL_Latin1_General_CP1_CI_AS, is used.</span></span>|`dqsinstaller.exe -collation <collation_name>`|  
|<span data-ttu-id="d02b1-151">-upgradedlls</span><span class="sxs-lookup"><span data-stu-id="d02b1-151">-upgradedlls</span></span>|<span data-ttu-id="d02b1-152">Ignore la nouvelle création des bases de données DQS (DQS_MAIN, DQS_PROJECTS et DQS_STAGING_DATA) et met à jour uniquement des assemblys du Common Language Runtime de SQL (SQLCLR) utilisés par DQS dans la base de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d02b1-152">Skips recreating the DQS databases (DQS_MAIN, DQS_PROJECTS, and DQS_STAGING_DATA), and only updates the SQL Common Language Runtime (SQLCLR) assemblies used by DQS in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database.</span></span><br /><br /> <span data-ttu-id="d02b1-153">Pour plus d’informations, consultez [Mettre à niveau des assemblys SQLCLR après une mise à jour de .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-153">For more information, see [Upgrade SQLCLR Assemblies After .NET Framework Update](upgrade-sqlclr-assemblies-after-net-framework-update.md)</span></span>|`dqsinstaller.exe -upgradedlls`|  
|<span data-ttu-id="d02b1-154">-exportkbs</span><span class="sxs-lookup"><span data-stu-id="d02b1-154">-exportkbs</span></span>|<span data-ttu-id="d02b1-155">Exportez toutes les bases de connaissances vers un fichier de sauvegarde DQS (.dqsb).</span><span class="sxs-lookup"><span data-stu-id="d02b1-155">Export all the knowledge bases to a DQS backup file (.dqsb).</span></span> <span data-ttu-id="d02b1-156">Vous devez également spécifier le chemin d'accès complet et le nom du fichier où vous voulez exporter toutes les bases de connaissances.</span><span class="sxs-lookup"><span data-stu-id="d02b1-156">You must also specify the full path and file name where you want to export all the knowledge bases.</span></span><br /><br /> <span data-ttu-id="d02b1-157">Pour plus d'informations, consultez [Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-157">For more information, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span></span>|`dqsinstaller.exe -exportkbs <path><filename>`<br /><br /> <span data-ttu-id="d02b1-158">Par exemple : `dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb`</span><span class="sxs-lookup"><span data-stu-id="d02b1-158">For example, `dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb`</span></span>|  
|<span data-ttu-id="d02b1-159">-importkbs</span><span class="sxs-lookup"><span data-stu-id="d02b1-159">-importkbs</span></span>|<span data-ttu-id="d02b1-160">Importez toutes les bases de connaissances à partir d'un fichier de sauvegarde DQS (.dqsb) après l'installation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d02b1-160">Import all the knowledge bases from a DQS backup file (.dqsb) after completing the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation.</span></span> <span data-ttu-id="d02b1-161">Vous devez également spécifier le chemin d'accès complet et le nom du fichier à partir duquel vous voulez importer toutes les bases de connaissances.</span><span class="sxs-lookup"><span data-stu-id="d02b1-161">You must also specify the full path and file name from where you want to import all the knowledge bases.</span></span><br /><br /> <span data-ttu-id="d02b1-162">Pour plus d'informations, consultez [Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-162">For more information, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span></span>|`dqsinstaller.exe -importkbs <path><filename>`<br /><br /> <span data-ttu-id="d02b1-163">Par exemple : `dqsinstaller.exe -importkbs c:\DQSBackup.dqsb`</span><span class="sxs-lookup"><span data-stu-id="d02b1-163">For example, `dqsinstaller.exe -importkbs c:\DQSBackup.dqsb`</span></span>|  
|<span data-ttu-id="d02b1-164">-upgrade</span><span class="sxs-lookup"><span data-stu-id="d02b1-164">-upgrade</span></span>|<span data-ttu-id="d02b1-165">Met à niveau le schéma des bases de données DQS.</span><span class="sxs-lookup"><span data-stu-id="d02b1-165">Upgrades DQS databases schema.</span></span> <span data-ttu-id="d02b1-166">Vous devez utiliser ce paramètre après avoir installé une mise à jour de SQL Server sur une instance DQS précédemment configurée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-166">You must use this parameter after you have installed a SQL Server update on a previously configured DQS instance.</span></span> <span data-ttu-id="d02b1-167">Pour plus d'informations, consultez [Upgrade DQS Databases Schema After Installing SQL Server Update](upgrade-dqs-databases-schema-after-installing-sql-server-update.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-167">For more information, see [Upgrade DQS Databases Schema After Installing SQL Server Update](upgrade-dqs-databases-schema-after-installing-sql-server-update.md).</span></span>|`dqsinstaller.exe -upgrade`|  
|<span data-ttu-id="d02b1-168">-uninstall</span><span class="sxs-lookup"><span data-stu-id="d02b1-168">-uninstall</span></span>|<span data-ttu-id="d02b1-169">Désinstalle le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] de l'instance actuelle de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d02b1-169">Uninstalls [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from the current SQL Server instance.</span></span><br /><br /> <span data-ttu-id="d02b1-170">Vous pouvez également exporter toutes les bases de connaissances de l'installation existante du serveur DQS vers un fichier de sauvegarde DQS (.dqsb), avant de désinstaller le serveur DQS.</span><span class="sxs-lookup"><span data-stu-id="d02b1-170">You can also export all the knowledge bases in the existing Data Quality Server installation to a DQS backup file (.dqsb), and then uninstall Data Quality Server.</span></span> <span data-ttu-id="d02b1-171">Pour plus d'informations, consultez [Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-171">For more information, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).</span></span><br /><br /> <span data-ttu-id="d02b1-172">Important si vous désinstallez à partir d’une instance SQL Server à l’aide du paramètre de ligne de \*\* \* commande, tous les \* objets DQS sont supprimés dans le cadre du processus de désinstallation. \* \* \*\* [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] `-uninstall`</span><span class="sxs-lookup"><span data-stu-id="d02b1-172">**\*\* Important \*\*** If you uninstall [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from a SQL server instance using the `-uninstall` command line parameter, all the DQS objects are deleted as part of the uninstall process.</span></span> <span data-ttu-id="d02b1-173">Vous n’êtes pas obligé de les supprimer manuellement après la désinstallation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] comme indiqué dans [Supprimer les objets serveur DQS](../../sql-server/install/remove-data-quality-server-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-173">You do not have to delete them manually after uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] as mentioned in [Remove Data Quality Server Objects](../../sql-server/install/remove-data-quality-server-objects.md).</span></span>|<span data-ttu-id="d02b1-174">**Pour désinstaller uniquement le serveur DQS :**</span><span class="sxs-lookup"><span data-stu-id="d02b1-174">**To just uninstall Data Quality Server:**</span></span> <br /> `dqsinstaller.exe -uninstall`<br /><br /> <span data-ttu-id="d02b1-175">**Pour exporter toutes les bases de connaissances vers un fichier, puis désinstaller le serveur DQS :**</span><span class="sxs-lookup"><span data-stu-id="d02b1-175">**To export all the knowledge bases to a file, and then uninstall Data Quality Server:**</span></span> <br /> `dqsinstaller.exe -uninstall <path><filename>` <br /><span data-ttu-id="d02b1-176">Par exemple : `dqsinstaller.exe -uninstall c:\DQSBackup.dqsb`</span><span class="sxs-lookup"><span data-stu-id="d02b1-176">For example, `dqsinstaller.exe -uninstall c:\DQSBackup.dqsb`</span></span>|  
  
 <span data-ttu-id="d02b1-177">**Pour exécuter DQSInstaller.exe à partir d'une invite de commandes :**</span><span class="sxs-lookup"><span data-stu-id="d02b1-177">**To run DQSInstaller.exe from Command Prompt:**</span></span>  
  
1.  <span data-ttu-id="d02b1-178">Démarrez l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d02b1-178">Start Command Prompt.</span></span>  
  
2.  <span data-ttu-id="d02b1-179">À l'invite de commandes, remplacez votre répertoire à l'emplacement où DQSInstaller.exe est disponible.</span><span class="sxs-lookup"><span data-stu-id="d02b1-179">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="d02b1-180">Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe sera copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn :</span><span class="sxs-lookup"><span data-stu-id="d02b1-180">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  <span data-ttu-id="d02b1-181">À l'invite de commandes, exécutez DQSInstaller.exe avec ou sans paramètres de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="d02b1-181">At the command prompt, run DQSInstaller.exe with or without command-line parameters:</span></span>  
  
    -   <span data-ttu-id="d02b1-182">**Sans paramètre de ligne de commande**: tapez `dqsinstaller.exe`, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-182">**Without Command-Line Parameter**: Type `dqsinstaller.exe`, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="d02b1-183">**Avec paramètre de ligne de commande**: tapez la commande requise comme indiqué dans le tableau ci-dessus, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-183">**With Command-Line Parameter**: Type the required command as mentioned in the table above, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="d02b1-184">Les actions requises sont exécutées selon la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-184">The required actions are performed based on the specified command.</span></span> <span data-ttu-id="d02b1-185">Si vous choisissez d’installer uniquement [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] sans aucun paramètre de ligne de commande, le reste des étapes est identique, comme décrit dans les étapes 2 à 6 dans la section précédente, [Exécuter DQSInstaller.exe à partir de l’écran Démarrer, du menu Démarrer ou de l’Explorateur Windows](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer).</span><span class="sxs-lookup"><span data-stu-id="d02b1-185">If you just chose to install [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] without any command-line parameters, rest of the steps are same as described in steps 2-6 in the previous section, [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d02b1-186">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d02b1-186">Next Steps</span></span>  
  
-   <span data-ttu-id="d02b1-187">Attribuez les rôles DQS appropriés aux utilisateurs selon leur profil de travail.</span><span class="sxs-lookup"><span data-stu-id="d02b1-187">Grant appropriate DQS roles to users based on their work profile.</span></span> <span data-ttu-id="d02b1-188">Consultez [Affecter des rôles DQS aux utilisateurs](grant-dqs-roles-to-users.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-188">See [Grant DQS Roles to Users](grant-dqs-roles-to-users.md).</span></span>  
  
-   <span data-ttu-id="d02b1-189">Si le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] est accessible à distance à partir d'un [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)], activez le protocole TCP/IP à l'aide du gestionnaire de configuration SQL Server sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d02b1-189">If [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] will be accessed remotely from [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)], enable the TCP/IP protocol using SQL Server Configuration Manager on this computer.</span></span>  
  
-   <span data-ttu-id="d02b1-190">Assurez-vous que vous avez accès à vos données sources pour les opérations DQS et que vous pouvez exporter les données traitées vers une table dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="d02b1-190">Make sure that you can access your source data for the DQS operations, and can export the processed data to a table in a database.</span></span> <span data-ttu-id="d02b1-191">Consultez [Accéder aux données pour les opérations DQS](access-data-for-the-dqs-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d02b1-191">See [Access Data for the DQS Operations](access-data-for-the-dqs-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02b1-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d02b1-192">See Also</span></span>  
 <span data-ttu-id="d02b1-193">[Installer Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="d02b1-193">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 <span data-ttu-id="d02b1-194">[Mettre à niveau les assemblys SQLCLR après la mise à jour .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md) </span><span class="sxs-lookup"><span data-stu-id="d02b1-194">[Upgrade SQLCLR Assemblies After .NET Framework Update](upgrade-sqlclr-assemblies-after-net-framework-update.md) </span></span>  
 [<span data-ttu-id="d02b1-195">Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe</span><span class="sxs-lookup"><span data-stu-id="d02b1-195">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span></span>](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)  
  
  