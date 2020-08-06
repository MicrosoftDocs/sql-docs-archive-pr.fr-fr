---
title: Désinstaller une instance existante de SQL Server (programme d’installation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51d426a12a2f7f1b7bedbfb7770c4d9cb369f12b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604889"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a><span data-ttu-id="0a877-102">Désinstaller une instance existante de SQL Server (programme d'installation)</span><span class="sxs-lookup"><span data-stu-id="0a877-102">Uninstall an Existing Instance of SQL Server (Setup)</span></span>
  <span data-ttu-id="0a877-103">Cet article explique comment désinstaller une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a877-103">This article describes how to uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a877-104">En suivant les étapes de cette rubrique, vous préparez également le système afin de pouvoir réinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a877-104">By following the steps in this topic, you also prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a877-105">Pour désinstaller une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez être administrateur local et disposer des autorisations requises pour vous connecter en tant que service.</span><span class="sxs-lookup"><span data-stu-id="0a877-105">To uninstall an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be a local administrator with permission to log on as a service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a877-106">Pour désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez la fonctionnalité Supprimer un nœud fournie par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour supprimer chaque nœud individuellement.</span><span class="sxs-lookup"><span data-stu-id="0a877-106">To uninstall a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="0a877-107">Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="0a877-107">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="0a877-108">Prenez en compte les points importants indiqués ci-après avant de désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0a877-108">Consider the following important information before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="0a877-109">Avant de supprimer les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'un ordinateur disposant de la quantité minimale de mémoire physique requise, vous devez vous assurer que la taille du fichier d'échange est suffisante.</span><span class="sxs-lookup"><span data-stu-id="0a877-109">Before you remove [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components from a computer that has the minimum required amount of physical memory, make sure that the page file size is sufficient.</span></span> <span data-ttu-id="0a877-110">La taille du fichier d'échange doit être égale à deux fois la quantité de mémoire physique.</span><span class="sxs-lookup"><span data-stu-id="0a877-110">The page file size must be equal to two times the amount of physical memory.</span></span> <span data-ttu-id="0a877-111">Une mémoire virtuelle insuffisante peut entraîner la suppression incomplète de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a877-111">Insufficient virtual memory can cause an incomplete removal of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0a877-112">Si vous avez plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est automatiquement désinstallé lorsque la dernière instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est elle-même désinstallée.</span><span class="sxs-lookup"><span data-stu-id="0a877-112">If you have multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser uninstalls automatically when the last instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is uninstalled.</span></span>  
  
     <span data-ttu-id="0a877-113">Si vous souhaitez désinstaller tous les composants de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez désinstaller manuellement le composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser en utilisant **Programmes et fonctionnalités** dans le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="0a877-113">If you want to uninstall all components of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must uninstall the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser component manually from **Programs and Features** in **Control Panel**.</span></span>  
  
### <a name="before-you-uninstall"></a><span data-ttu-id="0a877-114">Avant la désinstallation</span><span class="sxs-lookup"><span data-stu-id="0a877-114">Before You Uninstall</span></span>  
  
1.  <span data-ttu-id="0a877-115">**Sauvegardez vos données.**</span><span class="sxs-lookup"><span data-stu-id="0a877-115">**Back up your data.**</span></span> <span data-ttu-id="0a877-116">Bien que ce ne soit pas une étape obligatoire, vous pouvez enregistrer des bases de données dans leur état actuel.</span><span class="sxs-lookup"><span data-stu-id="0a877-116">Although this is not a required step, you might have databases that you want to save in their present state.</span></span> <span data-ttu-id="0a877-117">Peut-être souhaitez-vous également enregistrer les modifications qui ont été apportées aux bases de données système.</span><span class="sxs-lookup"><span data-stu-id="0a877-117">You might also want to save changes that were made to the system databases.</span></span> <span data-ttu-id="0a877-118">Dans l'une de ces situations, veillez à sauvegarder les données avant de désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a877-118">If either situation is true, make sure that back up the data before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a877-119">Vous avez aussi la possibilité d'enregistrer une copie de tous les fichiers journaux et de données dans un dossier autre que le dossier MSSQL.</span><span class="sxs-lookup"><span data-stu-id="0a877-119">Alternatively, save a copy of all the data and log files in a folder other than the MSSQL folder.</span></span> <span data-ttu-id="0a877-120">Le dossier MSSQL est supprimé durant la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="0a877-120">The MSSQL folder is deleted during uninstallation.</span></span>  
  
     <span data-ttu-id="0a877-121">Les fichiers que vous devez enregistrer incluent les fichiers de base de données suivants :</span><span class="sxs-lookup"><span data-stu-id="0a877-121">The files that you must save include the following database files:</span></span>  
  
    -   <span data-ttu-id="0a877-122">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="0a877-122">Master.mdf</span></span>  
  
    -   <span data-ttu-id="0a877-123">mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="0a877-123">Mastlog.ldf</span></span>  
  
    -   <span data-ttu-id="0a877-124">Model.mdf</span><span class="sxs-lookup"><span data-stu-id="0a877-124">Model.mdf</span></span>  
  
    -   <span data-ttu-id="0a877-125">Modellog.ldf</span><span class="sxs-lookup"><span data-stu-id="0a877-125">Modellog.ldf</span></span>  
  
    -   <span data-ttu-id="0a877-126">Msdbdata.mdf</span><span class="sxs-lookup"><span data-stu-id="0a877-126">Msdbdata.mdf</span></span>  
  
    -   <span data-ttu-id="0a877-127">Msdblog.ldf</span><span class="sxs-lookup"><span data-stu-id="0a877-127">Msdblog.ldf</span></span>  
  
    -   <span data-ttu-id="0a877-128">Mssqlsystemresource.mdf</span><span class="sxs-lookup"><span data-stu-id="0a877-128">Mssqlsystemresource.mdf</span></span>  
  
    -   <span data-ttu-id="0a877-129">Mssqlsustemresource.ldf</span><span class="sxs-lookup"><span data-stu-id="0a877-129">Mssqlsustemresource.ldf</span></span>  
  
    -   <span data-ttu-id="0a877-130">Tempdb.mdf</span><span class="sxs-lookup"><span data-stu-id="0a877-130">Tempdb.mdf</span></span>  
  
    -   <span data-ttu-id="0a877-131">Templog.ldf</span><span class="sxs-lookup"><span data-stu-id="0a877-131">Templog.ldf</span></span>  
  
    -   <span data-ttu-id="0a877-132">`ReportServer[$InstanceName]`(Il s’agit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la base de données par défaut.)</span><span class="sxs-lookup"><span data-stu-id="0a877-132">`ReportServer[$InstanceName]` (Thisis the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default database.)</span></span>  
  
    -   <span data-ttu-id="0a877-133">ReportServer[$InstanceName]TempDB (Il s'agit de la base de données temporaire par défaut de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .)</span><span class="sxs-lookup"><span data-stu-id="0a877-133">ReportServer[$InstanceName]TempDB (This is the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default temporary database.)</span></span>  
  
2.  <span data-ttu-id="0a877-134">**Supprimez les groupes de sécurité locaux.**</span><span class="sxs-lookup"><span data-stu-id="0a877-134">**Delete the local security groups.**</span></span> <span data-ttu-id="0a877-135">Avant de désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], supprimez les groupes de sécurité locaux des composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a877-135">Before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], delete the local security groups for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
3.  <span data-ttu-id="0a877-136">\*\*Arrêtez tous les \*\*  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services**.</span><span class="sxs-lookup"><span data-stu-id="0a877-136">**Stop all**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services.**</span></span> <span data-ttu-id="0a877-137">Nous vous recommandons d'arrêter tous les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de désinstaller les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a877-137">We recommend that you stop all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="0a877-138">La désinstallation peut échouer s'il existe des connexions actives.</span><span class="sxs-lookup"><span data-stu-id="0a877-138">Active connections can prevent successful uninstallation.</span></span>  
  
4.  <span data-ttu-id="0a877-139">**Utiliser un compte bénéficiant des autorisations appropriées**</span><span class="sxs-lookup"><span data-stu-id="0a877-139">**Use an account that has the appropriate permissions.**</span></span> <span data-ttu-id="0a877-140">Connectez-vous au serveur à l'aide du compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à l'aide d'un compte doté d'autorisations équivalentes.</span><span class="sxs-lookup"><span data-stu-id="0a877-140">Log on to the server by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account or by using an account that has equivalent permissions.</span></span> <span data-ttu-id="0a877-141">Par exemple, vous pouvez vous connecter au serveur à l'aide d'un compte qui est membre du groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="0a877-141">For example, you can log on to the server by using an account that is a member of the local Administrators group.</span></span>  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a><span data-ttu-id="0a877-142">Pour désinstaller une instance SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a877-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="0a877-143">Pour commencer le processus de désinstallation, cliquez sur **Panneau de configuration** , puis accédez à **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="0a877-143">To begin the uninstall process, go to **Control Panel** and then **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="0a877-144">Cliquez avec le bouton droit **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** et sélectionnez **désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="0a877-144">Right click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** and select **Uninstall**.</span></span> <span data-ttu-id="0a877-145">Cliquez ensuite sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="0a877-145">Then click **Remove**.</span></span> <span data-ttu-id="0a877-146">Ainsi, vous démarrez l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a877-146">This starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
     <span data-ttu-id="0a877-147">Les règles de support du programme d'installation s'exécutent pour vérifier la configuration de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0a877-147">Setup Support Rules runs to verify your computer configuration.</span></span> <span data-ttu-id="0a877-148">Pour continuer, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0a877-148">To continue, click **Next**.</span></span>  
  
3.  <span data-ttu-id="0a877-149">Dans la page Sélectionner une instance, utilisez la zone de liste déroulante pour spécifier une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à supprimer ou l'option pour supprimer uniquement les fonctionnalités partagées et outils d'administration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a877-149">On the Select Instance page, use the drop-down box to specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to remove, or specify the option to remove only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared features and management tools.</span></span> <span data-ttu-id="0a877-150">Pour continuer, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0a877-150">To continue, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0a877-151">Dans la page Sélectionner les composants, spécifiez les fonctionnalités à supprimer de l'instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a877-151">On the Select Features page, specify the features to remove from the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="0a877-152">Les règles de suppression s'exécutent pour vérifier que l'opération peut s'effectuer correctement.</span><span class="sxs-lookup"><span data-stu-id="0a877-152">Removal rules runs to verify that the operation can complete successfully.</span></span>  
  
5.  <span data-ttu-id="0a877-153">Dans la page **Prêt pour la suppression** , consultez la liste des composants et des fonctionnalités à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="0a877-153">On the **Ready to Remove** page, review the list of components and features that will be uninstalled.</span></span> <span data-ttu-id="0a877-154">Cliquez sur **Supprimer** pour commencer la désinstallation</span><span class="sxs-lookup"><span data-stu-id="0a877-154">Click **Remove** to begin uninstalling</span></span>  
  
6.  <span data-ttu-id="0a877-155">Immédiatement après avoir désinstallé la dernière instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les autres programmes associés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont toujours visibles dans la liste des programmes de **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="0a877-155">Immediately after you uninstall the last [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, the other programs associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will still be visible in the list of programs in **Programs and Features**.</span></span> <span data-ttu-id="0a877-156">Toutefois, si vous fermez **Programmes et fonctionnalités**, la prochaine fois que vous ouvrirez **Programmes et fonctionnalités**, la liste des programmes sera actualisée afin de ne montrer que ceux qui sont toujours installés.</span><span class="sxs-lookup"><span data-stu-id="0a877-156">However, if you close **Programs and Features**, the next time you open **Programs and Features**, it will refresh the list of programs, to show only the ones that are actually still installed.</span></span>  
  
### <a name="if-the-uninstallation-fails"></a><span data-ttu-id="0a877-157">En cas d'échec de la désinstallation</span><span class="sxs-lookup"><span data-stu-id="0a877-157">If the Uninstallation Fails</span></span>  
  
1.  <span data-ttu-id="0a877-158">Si le processus de désinstallation ne se termine pas correctement, essayez de résoudre le problème à l'origine de cet échec.</span><span class="sxs-lookup"><span data-stu-id="0a877-158">If the uninstallation process does not complete successfully, attempt to fix the problem that caused the uninstallation to fail.</span></span> <span data-ttu-id="0a877-159">Les articles suivants peuvent vous aider à comprendre la cause de l'échec de la désinstallation :</span><span class="sxs-lookup"><span data-stu-id="0a877-159">The following articles can help you understand the cause of the failed uninstallation:</span></span>  
  
    -   [<span data-ttu-id="0a877-160">Procédure pour identifier les problèmes d'installation de SQL Server 2008 dans les fichiers journaux d'installation</span><span class="sxs-lookup"><span data-stu-id="0a877-160">How to identify SQL Server 2008 setup issues in the setup log files</span></span>](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [<span data-ttu-id="0a877-161">Afficher et lire les fichiers journaux d'installation de SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a877-161">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  <span data-ttu-id="0a877-162">Si vous ne parvenez pas à remédier à la cause de l'échec de désinstallation, vous pouvez contacter le support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a877-162">If you are unable to fix the cause of the uninstallation failure, you can contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support.</span></span> <span data-ttu-id="0a877-163">Dans certains cas, comme la suppression involontaire de fichiers importants, la réinstallation du système d'exploitation peut être requise avant de réinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0a877-163">In some cases, such as unintentional deletion of important files, reinstalling the operating system may be required before reinstalling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a877-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a877-164">See Also</span></span>  
 [<span data-ttu-id="0a877-165">Afficher et lire les fichiers journaux d'installation de SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a877-165">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  