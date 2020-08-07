---
title: Boîte de dialogue partitions distantes-paramètres avancés (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: e68aea7325094af7b60d4b3f0c8ca0cd9525df71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600249"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="25050-102">Boîte de dialogue Partitions distantes - Paramètres avancés (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="25050-102">Remote Partitions - Advanced Settings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="25050-103">La boîte de dialogue **Partitions distantes - Paramètres avancés** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] permet de modifier les paramètres avancés tels que la chaîne de connexion à la source de données représentant la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante qui englobe les partitions distantes, tout en restaurant ces partitions distantes à partir d’un fichier de sauvegarde distant vers une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans la boîte de dialogue **Restaurer la base de données** .</span><span class="sxs-lookup"><span data-stu-id="25050-103">Use the **Remote Partitions - Advanced Settings** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to edit advanced settings, such as the connection string of the data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database maintaining remote partitions, while restoring remote partitions from a remote backup file to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database by using the **Restore Database** dialog box.</span></span> <span data-ttu-id="25050-104">Pour accéder à cette boîte de dialogue, sélectionnez l’option **Restaurer les partitions distantes** puis cliquez sur le bouton, représenté par les points de suspension ( **...** ), correspondant à une partition distante. Dans la boîte de dialogue **Restaurer la base de données** , ouvrez la page**Partitions**où vous retrouverez ainsi la boîte de dialogue **Partitions distantes - Paramètres avancés** .</span><span class="sxs-lookup"><span data-stu-id="25050-104">You can display the **Remote Partitions - Advanced Settings** dialog box from the **Partitions** page of the **Restore Database** dialog box by clicking the ellipsis button (**...**) for a remote partition after selecting the **Restore remote partitions** option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="25050-105">Options</span><span class="sxs-lookup"><span data-stu-id="25050-105">Options</span></span>  
  
|<span data-ttu-id="25050-106">Terme</span><span class="sxs-lookup"><span data-stu-id="25050-106">Term</span></span>|<span data-ttu-id="25050-107">Définition</span><span class="sxs-lookup"><span data-stu-id="25050-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="25050-108">**Nom de la source de données**</span><span class="sxs-lookup"><span data-stu-id="25050-108">**Data source name**</span></span>|<span data-ttu-id="25050-109">Affiche le nom de la source de données représentant la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante chargée de gérer les partitions distantes répertoriées.</span><span class="sxs-lookup"><span data-stu-id="25050-109">Displays the name of the data source that represents the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that manages the listed remote partitions.</span></span>|  
|<span data-ttu-id="25050-110">**Fichier de sauvegarde**</span><span class="sxs-lookup"><span data-stu-id="25050-110">**Backup file**</span></span>|<span data-ttu-id="25050-111">Affiche le nom du fichier de sauvegarde qui contient les données à restaurer concernant les partitions distantes répertoriées.</span><span class="sxs-lookup"><span data-stu-id="25050-111">Displays the name of the remote backup file that contains the data to be restored for the listed remote partitions.</span></span><br /><br /> <span data-ttu-id="25050-112">Remarque : aucun fichier de sauvegarde n’est affiché si un fichier de sauvegarde distant a été spécifié dans la colonne **fichier de sauvegarde** de la page **partitions** de la boîte de dialogue **restaurer la base de données** .</span><span class="sxs-lookup"><span data-stu-id="25050-112">Note: No backup file is displayed if a remote backup file was specified in the **Backup file** column on the **Partitions** page of the **Restore Database** dialog box.</span></span>|  
|<span data-ttu-id="25050-113">**Chaîne de connexion**</span><span class="sxs-lookup"><span data-stu-id="25050-113">**Connection string**</span></span>|<span data-ttu-id="25050-114">Affiche la chaîne de connexion pour la source de données apparaissant dans **Nom de la source de données**.</span><span class="sxs-lookup"><span data-stu-id="25050-114">Displays the connection string for the data source displayed in **Data source name**.</span></span>|  
|<span data-ttu-id="25050-115">**Modifier**</span><span class="sxs-lookup"><span data-stu-id="25050-115">**Edit**</span></span>|<span data-ttu-id="25050-116">Permet d'afficher la boîte de dialogue **Propriétés des liaisons de données** et de modifier les propriétés contenues dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="25050-116">Click to display the **Data Link Properties** dialog box and edit the properties contained in the connection string.</span></span>|  
|<span data-ttu-id="25050-117">**Liste des partitions**</span><span class="sxs-lookup"><span data-stu-id="25050-117">**Partitions list**</span></span>|<span data-ttu-id="25050-118">Permet d'indiquer différents emplacements dans lesquels doivent être restaurées les partitions distantes.</span><span class="sxs-lookup"><span data-stu-id="25050-118">Select to specify different locations in which to restore remote partitions.</span></span> <span data-ttu-id="25050-119">Notez que vous pouvez uniquement modifier le dossier de restauration d’une partition distante si l’emplacement spécifié pour cette partition distante dans le cube n’était pas celui par défaut.</span><span class="sxs-lookup"><span data-stu-id="25050-119">Note that you can only change the restoration folder of a remote partition if a location other than the default location was specified for that remote partition in the cube.</span></span> <span data-ttu-id="25050-120">La grille suivante, activée si l'option est cochée, permet d'indiquer un dossier de restauration pour chaque partition distante :</span><span class="sxs-lookup"><span data-stu-id="25050-120">The following grid, enabled when this option is selected, is used to specify a restoration folder for each remote partition:</span></span><br /><br /> <span data-ttu-id="25050-121">**Cube**: affiche le nom du cube qui contient la partition distante.</span><span class="sxs-lookup"><span data-stu-id="25050-121">**Cube**: Displays the name of the cube that contains the remote partition.</span></span><br /><br /> <span data-ttu-id="25050-122">**MeasureGroup**: affiche le nom du groupe de mesures qui contient la partition distante.</span><span class="sxs-lookup"><span data-stu-id="25050-122">**MeasureGroup**: Displays the name of the measure group that contains the remote partition.</span></span><br /><br /> <span data-ttu-id="25050-123">**Partition**: affiche le nom de la partition distante.</span><span class="sxs-lookup"><span data-stu-id="25050-123">**Partition**: Displays the name of the remote partition.</span></span><br /><br /> <span data-ttu-id="25050-124">**Taille (Mo)**: affiche la taille, en mégaoctets, de la partition distante.</span><span class="sxs-lookup"><span data-stu-id="25050-124">**Size (MB)**: Displays the size, in megabytes, of the remote partition.</span></span><br /><br /> <span data-ttu-id="25050-125">**Dossier d’origine**: affiche le nom du dossier d’origine dans lequel la partition distante a été stockée.</span><span class="sxs-lookup"><span data-stu-id="25050-125">**Original Folder**: Displays the name of the original folder in which the remote partition was stored.</span></span><br /><br /> <span data-ttu-id="25050-126">**Dossier de restauration**: tapez le nom du dossier de restauration de la partition distante, ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher un dossier distant** et sélectionner le chemin d’accès du dossier à utiliser.</span><span class="sxs-lookup"><span data-stu-id="25050-126">**Restoration Folder**: Type the name of the restoration folder for the remote partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="25050-127">Pour plus d'informations sur la boîte de dialogue **Rechercher un dossier distant**, consultez [Boîte de dialogue Rechercher un dossier distant &#40;Analysis Services - Données multidimensionnelles&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="25050-127">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25050-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25050-128">See Also</span></span>  
 <span data-ttu-id="25050-129">[Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="25050-129">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="25050-130">[Boîte de dialogue partitions &#40;boîte de dialogue restaurer la base de données&#41; &#40;Analysis Services-données multidimensionnelles&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="25050-130">[Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="25050-131">Sauvegarde et restauration de bases de données Analysis Services</span><span class="sxs-lookup"><span data-stu-id="25050-131">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  