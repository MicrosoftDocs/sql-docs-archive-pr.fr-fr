---
title: Afficher l’historique d’actualisation des données (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- data refresh history [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 4c8d8aa8-794d-4f72-ace3-78d0e688e1a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: c7a858aedcbca7aa1436ff06bdf9ebc61724f511
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706868"
---
# <a name="view-data-refresh-history-powerpivot-for-sharepoint"></a><span data-ttu-id="d4df2-102">Afficher l'historique d'actualisation des données (PowerPivot pour SharePoint)</span><span class="sxs-lookup"><span data-stu-id="d4df2-102">View Data Refresh History (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d4df2-103">L'historique d'actualisation des données est un enregistrement de toute l'activité d'actualisation de données PowerPivot dans un classeur Excel.</span><span class="sxs-lookup"><span data-stu-id="d4df2-103">Data refresh history is a record of all data refresh activity for PowerPivot data in an Excel workbook.</span></span> <span data-ttu-id="d4df2-104">Dans une batterie de serveurs SharePoint, les opérations d'actualisation des données sont effectuées sur une instance du serveur Analysis Services, selon une planification que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="d4df2-104">Data refresh operations are performed on an Analysis Services server instance in a SharePoint farm on a schedule that you provide.</span></span> <span data-ttu-id="d4df2-105">Par défaut, l'historique d'actualisation des données est conservé pendant un an.</span><span class="sxs-lookup"><span data-stu-id="d4df2-105">By default, data refresh history is retained for one year.</span></span> <span data-ttu-id="d4df2-106">Toutefois, un administrateur de batterie de serveurs peut, pour l'historique de l'utilisation et des événements, spécifier une stratégie de rétention différente qui détermine la durée de conservation des enregistrements d'actualisation des données.</span><span class="sxs-lookup"><span data-stu-id="d4df2-106">However, a farm administrator can specify a different retention policy for usage and event history that determines how long data refresh records are kept.</span></span>  
  
 <span data-ttu-id="d4df2-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="d4df2-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="d4df2-108">**Dans cette rubrique :**</span><span class="sxs-lookup"><span data-stu-id="d4df2-108">**In this topic:**</span></span>  
  
 [<span data-ttu-id="d4df2-109">Composants requis</span><span class="sxs-lookup"><span data-stu-id="d4df2-109">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="d4df2-110">Afficher l'historique d'actualisation des données d'un classeur</span><span class="sxs-lookup"><span data-stu-id="d4df2-110">View Data Refresh History for an Individual Workbook</span></span>](#viewhistory)  
  
 [<span data-ttu-id="d4df2-111">Afficher l'historique d'actualisation des données de tous les classeurs</span><span class="sxs-lookup"><span data-stu-id="d4df2-111">View Data Refresh History for All Workbooks</span></span>](#viewITOps)  
  
 [<span data-ttu-id="d4df2-112">Utiliser les informations de l'historique</span><span class="sxs-lookup"><span data-stu-id="d4df2-112">Use History Information</span></span>](#pageelements)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="d4df2-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d4df2-113">Prerequisites</span></span>  
 <span data-ttu-id="d4df2-114">Pour afficher l'historique d'actualisation des données, vous devez disposer d'autorisations Collaboration ou supérieures.</span><span class="sxs-lookup"><span data-stu-id="d4df2-114">You must have Contribute permissions or greater to view the data refresh history.</span></span>  
  
 <span data-ttu-id="d4df2-115">Vous avez avoir activé et planifié l'actualisation des données sur un classeur qui contient des données PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="d4df2-115">You must have enabled and scheduled data refresh on a workbook that contains PowerPivot data.</span></span> <span data-ttu-id="d4df2-116">Si vous n'avez pas planifié l'actualisation des données, la page de définition de la planification s'affichera au lieu des informations d'historique.</span><span class="sxs-lookup"><span data-stu-id="d4df2-116">If you have not scheduled data refresh, you will see the schedule definition page instead of history information.</span></span>  
  
##  <a name="view-data-refresh-history-for-an-individual-workbook"></a><a name="viewhistory"></a><span data-ttu-id="d4df2-117">Afficher l’historique d’actualisation des données pour un classeur individuel</span><span class="sxs-lookup"><span data-stu-id="d4df2-117">View Data Refresh History for an Individual Workbook</span></span>  
  
1.  <span data-ttu-id="d4df2-118">Sur un site SharePoint, ouvrez la bibliothèque où figure un classeur Excel qui contient des données PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="d4df2-118">On a SharePoint site, open the library that contains an Excel workbook that contains PowerPivot data.</span></span>  
  
     <span data-ttu-id="d4df2-119">Aucun indicateur visuel ne permet d'identifier les classeurs d'une bibliothèque SharePoint qui contiennent des données PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="d4df2-119">There is no visual indicator that identifies which workbooks in a SharePoint library contain PowerPivot data.</span></span> <span data-ttu-id="d4df2-120">Vous devez savoir à l'avance quel classeur contient des données PowerPivot actualisables.</span><span class="sxs-lookup"><span data-stu-id="d4df2-120">You must know in advance which workbook contains refreshable PowerPivot data.</span></span>  
  
2.  <span data-ttu-id="d4df2-121">Sélectionnez le classeur, puis cliquez sur la flèche orientée vers le bas qui s'affiche à droite.</span><span class="sxs-lookup"><span data-stu-id="d4df2-121">Select the workbook, and then click the down arrow that appears to the right.</span></span>  
  
3.  <span data-ttu-id="d4df2-122">Sélectionnez **Gérer l'actualisation des données PowerPivot**.</span><span class="sxs-lookup"><span data-stu-id="d4df2-122">Select **Manage PowerPivot Data Refresh**.</span></span>  
  
 <span data-ttu-id="d4df2-123">La page d'historique s'affiche. Elle contient des informations complètes sur l'ensemble de l'activité d'actualisation des données PowerPivot du classeur Excel actif.</span><span class="sxs-lookup"><span data-stu-id="d4df2-123">The history page appears, showing a complete record for all refresh activity for PowerPivot data in the current Excel workbook.</span></span>  
  
##  <a name="view-data-refresh-history-for-all-workbooks"></a><a name="viewITOps"></a><span data-ttu-id="d4df2-124">Afficher l’historique d’actualisation des données pour tous les classeurs</span><span class="sxs-lookup"><span data-stu-id="d4df2-124">View Data Refresh History for All Workbooks</span></span>  
 <span data-ttu-id="d4df2-125">Les administrateurs de batteries et d'applications de service peuvent, en utilisant le tableau de bord de gestion PowerPivot de l'Administration centrale, obtenir une vue complète de l'historique et de l'état d'actualisation des données de tous les classeurs PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="d4df2-125">Using the PowerPivot Management Dashboard in Central administration, farm administrators and service application administrators can get a comprehensive view of data refresh history and status for all PowerPivot workbooks.</span></span> <span data-ttu-id="d4df2-126">Pour plus d'informations, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="d4df2-126">For more information, see [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
##  <a name="use-history-information"></a><a name="pageelements"></a><span data-ttu-id="d4df2-127">Utiliser les informations d’historique</span><span class="sxs-lookup"><span data-stu-id="d4df2-127">Use History Information</span></span>  
 <span data-ttu-id="d4df2-128">La page d'historique d'actualisation des données fournit des informations détaillées sur chaque opération d'actualisation.</span><span class="sxs-lookup"><span data-stu-id="d4df2-128">The data refresh history page provides detailed information about each refresh operation.</span></span> <span data-ttu-id="d4df2-129">Vous pouvez utiliser les informations de cette page afin de vérifier si l'actualisation a eu lieu ou de déterminer la raison pour laquelle elle a échoué.</span><span class="sxs-lookup"><span data-stu-id="d4df2-129">You can use the information on this page to confirm whether refresh occurred or determine why it failed.</span></span>  
  
|<span data-ttu-id="d4df2-130">Élément</span><span class="sxs-lookup"><span data-stu-id="d4df2-130">Item</span></span>|<span data-ttu-id="d4df2-131">Description</span><span class="sxs-lookup"><span data-stu-id="d4df2-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d4df2-132">Nom</span><span class="sxs-lookup"><span data-stu-id="d4df2-132">Name</span></span>|<span data-ttu-id="d4df2-133">Spécifie le nom de fichier du classeur Excel qui contient les données PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="d4df2-133">Specifies the file name of the Excel workbook that contains PowerPivot data.</span></span>|  
|<span data-ttu-id="d4df2-134">État actuel</span><span class="sxs-lookup"><span data-stu-id="d4df2-134">Current status</span></span>|<span data-ttu-id="d4df2-135">Les valeurs possibles sont **Planifiée**, **Actualisation**, **Opération réussie**ou **Échec**.</span><span class="sxs-lookup"><span data-stu-id="d4df2-135">Values include **Scheduled**, **Refreshing**, **Succeeded**, or **Failed**.</span></span><br /><br /> <span data-ttu-id="d4df2-136">**Planifiée** apparaît la première fois que vous créez la planification.</span><span class="sxs-lookup"><span data-stu-id="d4df2-136">**Scheduled** appears when you first create the schedule.</span></span> <span data-ttu-id="d4df2-137">Une fois la première actualisation des données effectuée, ce message d'état ne s'affiche plus.</span><span class="sxs-lookup"><span data-stu-id="d4df2-137">After data refresh runs the first time, this status message no longer appears.</span></span><br /><br /> <span data-ttu-id="d4df2-138">**Actualisation** indique que l'actualisation des données est en cours.</span><span class="sxs-lookup"><span data-stu-id="d4df2-138">**Refreshing** indicates that data refresh is in progress.</span></span> <span data-ttu-id="d4df2-139">Une requête figure dans la file d'attente des processus ou s'exécute activement sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d4df2-139">A request is either in the process queue or actively running on the server.</span></span><br /><br /> <span data-ttu-id="d4df2-140">**Opération réussie** indique que la dernière opération d'actualisation des données est terminée et que le classeur mis à jour est archivé dans la bibliothèque SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d4df2-140">**Succeeded** indicates that the last data refresh operation completed and the updated workbook is checked back into the SharePoint library.</span></span><br /><br /> <span data-ttu-id="d4df2-141">**Échec** indique que la dernière opération d'actualisation des données n'a pas réussi.</span><span class="sxs-lookup"><span data-stu-id="d4df2-141">**Failed** indicates that the last data refresh operation did not succeed.</span></span> <span data-ttu-id="d4df2-142">Les données actualisées n'ont pas été enregistrées.</span><span class="sxs-lookup"><span data-stu-id="d4df2-142">The refreshed data was not saved.</span></span> <span data-ttu-id="d4df2-143">Le classeur contient les mêmes données qu'avant l'opération d'actualisation des données.</span><span class="sxs-lookup"><span data-stu-id="d4df2-143">The workbook contains the same data it had before data refresh began.</span></span>|  
|<span data-ttu-id="d4df2-144">Dernière actualisation réussie</span><span class="sxs-lookup"><span data-stu-id="d4df2-144">Last successful refresh</span></span>|<span data-ttu-id="d4df2-145">Spécifie la date de dernière exécution réussie de l'actualisation des données.</span><span class="sxs-lookup"><span data-stu-id="d4df2-145">Specifies the date on which the last data refresh completed successfully.</span></span>|  
|<span data-ttu-id="d4df2-146">Prochaine actualisation planifiée</span><span class="sxs-lookup"><span data-stu-id="d4df2-146">Next schedule refresh</span></span>|<span data-ttu-id="d4df2-147">Spécifie la date prévue pour la prochaine actualisation des données.</span><span class="sxs-lookup"><span data-stu-id="d4df2-147">Specifies the date on which the next data refresh is scheduled to occur.</span></span><br /><br /> <span data-ttu-id="d4df2-148">Le lien **Configurer la planification** vous dirige vers la page de définition de la planification.</span><span class="sxs-lookup"><span data-stu-id="d4df2-148">The **Configure schedule** link takes you to the schedule definition page.</span></span> <span data-ttu-id="d4df2-149">Si vous disposez d'autorisations Collaboration sur le classeur, vous pouvez cliquer sur ce lien pour afficher et modifier les informations de planification qui contrôlent l'actualisation sans assistance des données PowerPivot du classeur.</span><span class="sxs-lookup"><span data-stu-id="d4df2-149">If you have Contribute permissions on the workbook, you can click the link to view and modify the schedule information that controls unattended data refresh for PowerPivot data in the workbook.</span></span>|  
|<span data-ttu-id="d4df2-150">Démarré</span><span class="sxs-lookup"><span data-stu-id="d4df2-150">Started</span></span>|<span data-ttu-id="d4df2-151">Dans la section des détails de l'historique, **Démarré** indique l'heure réelle du traitement.</span><span class="sxs-lookup"><span data-stu-id="d4df2-151">Within the history details section, **Started** indicates the actual processing time.</span></span> <span data-ttu-id="d4df2-152">Celle-ci peut différer de celle que vous avez planifiée.</span><span class="sxs-lookup"><span data-stu-id="d4df2-152">The actual processing time might be different from what you scheduled.</span></span> <span data-ttu-id="d4df2-153">En effet, le traitement commence lorsque le serveur dispose de suffisamment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d4df2-153">Processing will begin when sufficient memory is available on the server.</span></span> <span data-ttu-id="d4df2-154">Si le serveur est très occupé, le traitement peut commencer plusieurs heures après l'heure de début que vous avez spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d4df2-154">If the server is very busy, the processing might begin several hours after the start time you specified.</span></span>|  
|<span data-ttu-id="d4df2-155">Completed</span><span class="sxs-lookup"><span data-stu-id="d4df2-155">Completed</span></span>|<span data-ttu-id="d4df2-156">Dans la section des détails de l'historique, **Terminé** indique quand l'opération d'actualisation de données s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="d4df2-156">Within the history details section, **Completed** indicates when the data refresh operation finished.</span></span> <span data-ttu-id="d4df2-157">Les date et heure indiquent quand le classeur a été réarchivé dans la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d4df2-157">The date and time indicates when the workbook was checked back into the library.</span></span><br /><br /> <span data-ttu-id="d4df2-158">Si l'actualisation des données échoue, un ou plusieurs messages d'erreur expliquent la cause de l'échec.</span><span class="sxs-lookup"><span data-stu-id="d4df2-158">If data refresh fails, one or more error messages explain the cause of the failure.</span></span> <span data-ttu-id="d4df2-159">Vous pouvez développer chaque enregistrement pour consulter l'état détaillé.</span><span class="sxs-lookup"><span data-stu-id="d4df2-159">You can expand each record to view detailed status.</span></span> <span data-ttu-id="d4df2-160">Chaque source de données apparaît individuellement, avec les messages de réussite ou d'échec indiquant le cas échéant la raison pour laquelle l'actualisation n'a pas été effectuée.</span><span class="sxs-lookup"><span data-stu-id="d4df2-160">Each data source is listed individually, alongside success or failure messages that explain why data refresh did not complete.</span></span>|  
|<span data-ttu-id="d4df2-161">Temps</span><span class="sxs-lookup"><span data-stu-id="d4df2-161">Time</span></span>|<span data-ttu-id="d4df2-162">Indique le temps écoulé entre l'heure de début et l'heure de fin de l'opération d'actualisation.</span><span class="sxs-lookup"><span data-stu-id="d4df2-162">Provides the cumulative time from when data refresh started to when it was completed.</span></span>|  
|<span data-ttu-id="d4df2-163">Statut</span><span class="sxs-lookup"><span data-stu-id="d4df2-163">Status</span></span>|<span data-ttu-id="d4df2-164">Fournit un enregistrement d'historique indiquant si une opération d'actualisation a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="d4df2-164">Provides a historical record of whether a refresh operation succeeded or failed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4df2-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4df2-165">See Also</span></span>  
 <span data-ttu-id="d4df2-166">[Configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="d4df2-166">[Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="d4df2-167">[Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="d4df2-167">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="d4df2-168">Actualisation des données PowerPivot</span><span class="sxs-lookup"><span data-stu-id="d4df2-168">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
  