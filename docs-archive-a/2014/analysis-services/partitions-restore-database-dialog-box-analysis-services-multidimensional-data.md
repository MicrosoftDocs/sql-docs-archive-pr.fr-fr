---
title: Partitions (boîte de dialogue restaurer la base de données) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613179"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="dfa3b-102">Partitions (boîte de dialogue Restaurer la base de données) (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="dfa3b-102">Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="dfa3b-103">Utilisez la page **Partitions** de la boîte de dialogue **Restaurer la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] afin de spécifier l’emplacement de restauration des partitions locales et les fichiers de sauvegarde à distance à utiliser lors de la restauration des partitions distantes, et pour indiquer si les partitions distantes doivent, ou non, être restaurées.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-103">Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dfa3b-104">Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="dfa3b-105">Pour restaurer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dfa3b-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="dfa3b-106">Pour remplacer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfa3b-107">Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="dfa3b-108">Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="dfa3b-109">**Pour afficher la page partitions dans la boîte de dialogue restaurer la base de données**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-109">**To display the Partitions page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="dfa3b-110">Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit soit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou sur une base de données dans **l’Explorateur d’objets**, cliquez sur **Restaurer**, puis sous **Sélectionner une page**, cliquez sur **Partitions**.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dfa3b-111">Options</span><span class="sxs-lookup"><span data-stu-id="dfa3b-111">Options</span></span>  
 <span data-ttu-id="dfa3b-112">**Script**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-112">**Script**</span></span>  
 <span data-ttu-id="dfa3b-113">Crée un script de restauration basé sur les options sélectionnées dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="dfa3b-114">Le script de restauration est écrit en langage de script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (ASSL).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="dfa3b-115">Par défaut, lorsque vous cliquez sur l'icône **Script** , le script de restauration est envoyé dans une nouvelle fenêtre de requête.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="dfa3b-116">Un menu s'affiche lorsque vous cliquez sur la flèche **Script** . Il vous permet de choisir où envoyer le script de restauration :</span><span class="sxs-lookup"><span data-stu-id="dfa3b-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="dfa3b-117">Vers une nouvelle fenêtre de requête (par défaut).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="dfa3b-118">Vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-118">To a file.</span></span>  
  
-   <span data-ttu-id="dfa3b-119">Vers le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="dfa3b-120">Vers un travail.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-120">To a job.</span></span>  
  
 <span data-ttu-id="dfa3b-121">**Restaurer les emplacements d'origine**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-121">**Restore to original locations**</span></span>  
 <span data-ttu-id="dfa3b-122">Sélectionnez cette option afin de restaurer les partitions locales contenues dans le fichier de sauvegarde vers leurs emplacements d'origine.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-122">Select to restore local partitions contained in the backup file to their original locations.</span></span>  
  
 <span data-ttu-id="dfa3b-123">**Sélectionnez différents emplacements**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-123">**Select different locations**</span></span>  
 <span data-ttu-id="dfa3b-124">Choisissez cette option pour indiquer les différents emplacements vers lesquels les partitions locales seront restaurées.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-124">Select to specify different locations in which to restore local partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfa3b-125">Vous pouvez uniquement modifier le dossier de restauration d'une partition locale si l'emplacement spécifié pour cette partition dans le cube n'était pas celui par défaut.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-125">You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.</span></span>  
  
 <span data-ttu-id="dfa3b-126">La grille suivante, active lorsque cette option est sélectionnée, permet de spécifier un dossier de restauration pour chaque partition locale :</span><span class="sxs-lookup"><span data-stu-id="dfa3b-126">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="dfa3b-127">Colonne</span><span class="sxs-lookup"><span data-stu-id="dfa3b-127">Column</span></span>|<span data-ttu-id="dfa3b-128">Description</span><span class="sxs-lookup"><span data-stu-id="dfa3b-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dfa3b-129">**Dernier**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-129">**Cube**</span></span>|<span data-ttu-id="dfa3b-130">Affiche le nom du cube qui contient la partition locale.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-130">Displays the name of the cube that contains the local partition.</span></span>|  
|<span data-ttu-id="dfa3b-131">**MeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-131">**MeasureGroup**</span></span>|<span data-ttu-id="dfa3b-132">Affiche le nom du groupe de mesures qui contient la partition locale.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-132">Displays the name of the measure group that contains the local partition.</span></span>|  
|<span data-ttu-id="dfa3b-133">**Partition**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-133">**Partition**</span></span>|<span data-ttu-id="dfa3b-134">Affiche le nom de la partition locale.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-134">Displays the name of the local partition.</span></span>|  
|<span data-ttu-id="dfa3b-135">**Taille (Mo)**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-135">**Size (MB)**</span></span>|<span data-ttu-id="dfa3b-136">Affiche la taille (en mégaoctets) de la partition locale.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-136">Displays the size, in megabytes, of the local partition.</span></span>|  
|<span data-ttu-id="dfa3b-137">**Dossier original**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-137">**Original Folder**</span></span>|<span data-ttu-id="dfa3b-138">Affiche le nom du dossier original dans lequel la partition locale était stockée.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-138">Displays the name of the original folder in which the local partition was stored.</span></span>|  
|<span data-ttu-id="dfa3b-139">**Dossier de restauration**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-139">**Restoration Folder**</span></span>|<span data-ttu-id="dfa3b-140">Tapez le nom du dossier de restauration de la partition locale ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher un dossier distant** et sélectionner le chemin du dossier à utiliser.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-140">Type the name of the restoration folder for the local partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="dfa3b-141">Pour plus d'informations sur la boîte de dialogue **Rechercher un dossier distant**, consultez [Boîte de dialogue Rechercher un dossier distant &#40;Analysis Services - Données multidimensionnelles&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-141">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
 <span data-ttu-id="dfa3b-142">**Restaurer les partitions distantes**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-142">**Restore remote partitions**</span></span>  
 <span data-ttu-id="dfa3b-143">Sélectionnez cette option pour restaurer les partitions distantes stockées dans les fichiers de sauvegarde à distance.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-143">Select to restore remote partitions stored in remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfa3b-144">Cette option est uniquement active si le fichier de sauvegarde contient des références à des partitions distantes.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-144">This option is enabled only if the backup file contains references to remote partitions.</span></span>  
  
 <span data-ttu-id="dfa3b-145">La grille suivante, active lorsque cette option est sélectionnée, permet de spécifier un dossier de restauration pour chaque partition locale :</span><span class="sxs-lookup"><span data-stu-id="dfa3b-145">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="dfa3b-146">Colonne</span><span class="sxs-lookup"><span data-stu-id="dfa3b-146">Column</span></span>|<span data-ttu-id="dfa3b-147">Description</span><span class="sxs-lookup"><span data-stu-id="dfa3b-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dfa3b-148">**Serveur**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-148">**Server**</span></span>|<span data-ttu-id="dfa3b-149">Affiche le nom de l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère la partition distante.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-149">Displays the name of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partition.</span></span>|  
|<span data-ttu-id="dfa3b-150">**Source de données**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-150">**Data Source**</span></span>|<span data-ttu-id="dfa3b-151">Affiche le nom de la source de données dans le fichier de sauvegarde qui correspond à la base de données contenant la partition distante.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-151">Displays the name of the data source in the backup file that represents the database that contains the remote partition.</span></span>|  
|<span data-ttu-id="dfa3b-152">**Fichier de sauvegarde**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-152">**Backup File**</span></span>|<span data-ttu-id="dfa3b-153">Tapez le chemin complet et le nom du fichier de sauvegarde à distance à utiliser ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher les fichiers de base de données** et sélectionner le chemin et le nom du fichier en question.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="dfa3b-154">Pour plus d’informations sur la boîte de dialogue **Rechercher les fichiers de base de données**, consultez [Boîte de dialogue Rechercher les fichiers de base de données &#40;Analysis Services - Données multidimensionnelles&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-154">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="dfa3b-155">**...**</span><span class="sxs-lookup"><span data-stu-id="dfa3b-155">**...**</span></span>|<span data-ttu-id="dfa3b-156">Cliquez sur ce bouton pour afficher la boîte de dialogue **Partitions distantes - Paramètres avancés** et modifier les options avancées liées à la restauration de la partition distante, telles que la chaîne de connexion de la source de données.</span><span class="sxs-lookup"><span data-stu-id="dfa3b-156">Click to display the **Remote Partitions - Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition.</span></span> <span data-ttu-id="dfa3b-157">Pour plus d’informations sur la boîte de dialogue **Partitions distantes - Paramètres avancés**, consultez [Boîte de dialogue Partitions distantes - Paramètres avancés &#40;Analysis Services - Données multidimensionnelles&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfa3b-157">For more information about the **Remote Partitions - Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfa3b-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfa3b-158">See Also</span></span>  
 <span data-ttu-id="dfa3b-159">[Boîte de dialogue restaurer la base de données &#40;Analysis Services-données multidimensionnelles&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dfa3b-159">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dfa3b-160">[Boîte de dialogue &#40;de restauration de base de données général&#41; &#40;Analysis Services-données multidimensionnelles&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dfa3b-160">[General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="dfa3b-161">Sauvegarde et restauration de bases de données Analysis Services</span><span class="sxs-lookup"><span data-stu-id="dfa3b-161">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  