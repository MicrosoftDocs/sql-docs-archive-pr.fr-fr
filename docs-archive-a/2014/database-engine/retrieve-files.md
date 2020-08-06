---
title: Récupérer les fichiers | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebced9ea69f304344893289140687cd6d511e923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613112"
---
# <a name="retrieve-files"></a><span data-ttu-id="3cf89-102">Récupérer des fichiers</span><span class="sxs-lookup"><span data-stu-id="3cf89-102">Retrieve Files</span></span>
  <span data-ttu-id="3cf89-103">Une fois un projet sous contrôle de code source ouvert, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour récupérer des copies locales des fichiers projet dans le magasin du contrôle de code source et les placer dans le dossier local dans lequel réside le projet.</span><span class="sxs-lookup"><span data-stu-id="3cf89-103">After you have opened a source-controlled project, you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to retrieve local copies of project files from the source control store to the local directory in which the project resides.</span></span>  
  
 <span data-ttu-id="3cf89-104">Vous pouvez utiliser le contrôle de code source intégré pour récupérer des fichiers à l'aide des deux commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3cf89-104">You can use integrated source control to retrieve files in the following ways:</span></span>  
  
-   <span data-ttu-id="3cf89-105">Commande d' **extraction de la dernière version (récursif)**</span><span class="sxs-lookup"><span data-stu-id="3cf89-105">**Get Latest Version (Recursive)** command</span></span>  
  
     <span data-ttu-id="3cf89-106">Récupère la toute dernière version archivée des fichiers sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="3cf89-106">Retrieves the latest checked in version of the selected files.</span></span> <span data-ttu-id="3cf89-107">Si une solution ou un projet est sélectionné, cette commande récupère la dernière version de tous les fichiers de la solution et du projet.</span><span class="sxs-lookup"><span data-stu-id="3cf89-107">If a solution or project is selected, this command retrieves the latest version of all solution and project files.</span></span>  
  
-   <span data-ttu-id="3cf89-108">Commande d' **extraction**</span><span class="sxs-lookup"><span data-stu-id="3cf89-108">**Get** command</span></span>  
  
     <span data-ttu-id="3cf89-109">Affiche la boîte de dialogue **obtenir** , que vous pouvez utiliser pour récupérer la version la plus récente d’un fichier sélectionné, ou pour récupérer un sous-ensemble des fichiers dans la solution ou le projet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="3cf89-109">Displays the **Get** dialog box, which you can use to retrieve the latest version of a selected file, or to retrieve a subset of the files in the selected solution or project.</span></span>  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a><span data-ttu-id="3cf89-110">Pour récupérer la dernière version de tous les fichiers d'un projet</span><span class="sxs-lookup"><span data-stu-id="3cf89-110">To retrieve the latest version of all the files in a project</span></span>  
  
1.  <span data-ttu-id="3cf89-111">Dans l’Explorateur de solutions, sélectionnez le projet.</span><span class="sxs-lookup"><span data-stu-id="3cf89-111">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="3cf89-112">Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Télécharger la dernière version (récursif)**.</span><span class="sxs-lookup"><span data-stu-id="3cf89-112">On the **File** menu, point to **Source Control**, and then click **Get Latest Version (Recursive)**.</span></span>  
  
 <span data-ttu-id="3cf89-113">Les versions les plus récentes des fichiers du projet sont récupérées et placées à l'emplacement du projet sur votre disque local.</span><span class="sxs-lookup"><span data-stu-id="3cf89-113">The most recent versions of the files in the project are retrieved to the project location on your local disk.</span></span>  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a><span data-ttu-id="3cf89-114">Pour récupérer uniquement certains fichiers d'un projet</span><span class="sxs-lookup"><span data-stu-id="3cf89-114">To retrieve only certain files in a project</span></span>  
  
1.  <span data-ttu-id="3cf89-115">Dans l'Explorateur de solutions, sélectionnez l'élément à récupérer.</span><span class="sxs-lookup"><span data-stu-id="3cf89-115">In Solution Explorer, select the item you want to retrieve.</span></span>  
  
2.  <span data-ttu-id="3cf89-116">Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **récupérer**.</span><span class="sxs-lookup"><span data-stu-id="3cf89-116">On the **File** menu, point to **Source Control**, and then click **Get**.</span></span>  
  
3.  <span data-ttu-id="3cf89-117">Dans la boîte de dialogue **récupérer** , cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3cf89-117">In the **Get** dialog box, click **OK**.</span></span> <span data-ttu-id="3cf89-118">Si vous avez sélectionné une solution ou un projet dans l'Explorateur de solutions, désactivez les cases à cocher qui apparaissent en regard des éléments que vous ne souhaitez pas récupérer.</span><span class="sxs-lookup"><span data-stu-id="3cf89-118">Alternatively, if you selected a solution or project in Solution Explorer, clear the check boxes that appear next to the items you do not want to retrieve.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf89-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cf89-119">See Also</span></span>  
 <span data-ttu-id="3cf89-120">[Boîte de dialogue récupérer &#40;contrôle de code source&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="3cf89-120">[Get Dialog Box &#40;Source Control&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span></span>  
 <span data-ttu-id="3cf89-121">[Définir et récupérer les informations de version](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="3cf89-121">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="3cf89-122">[Afficher l’historique du projet](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="3cf89-122">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 [<span data-ttu-id="3cf89-123">Afficher l'état d'un fichier</span><span class="sxs-lookup"><span data-stu-id="3cf89-123">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
  