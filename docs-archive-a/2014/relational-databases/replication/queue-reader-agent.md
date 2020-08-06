---
title: Agent de lecture de la file d’attente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.queuereaderagent.f1
helpviewer_keywords:
- Queue Reader Agent dialog box
ms.assetid: f02d24b6-dcb5-4126-b56e-fab41cfe4337
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9649223b35562da97744d79f9506615b97274870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613430"
---
# <a name="queue-reader-agent"></a><span data-ttu-id="82d66-102">Agent de lecture de la file d'attente</span><span class="sxs-lookup"><span data-stu-id="82d66-102">Queue Reader Agent</span></span>
  <span data-ttu-id="82d66-103">La boîte de dialogue **Agent de lecture de la file d'attente** affiche des informations détaillées sur l'Agent de lecture de la file d'attente, y compris l'état, l'historique, des messages d'information et d'éventuels messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="82d66-103">The **Queue Reader Agent** dialog box displays detailed information on the Queue Reader Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82d66-104">Options</span><span class="sxs-lookup"><span data-stu-id="82d66-104">Options</span></span>  
 <span data-ttu-id="82d66-105">Dans le menu **Affichage** , sélectionnez les sessions de l'Agent de lecture de la file d'attente à afficher. Sélectionnez ensuite une session particulière dans la grille étiquetée **Sessions de l'Agent de lecture de la file d'attente**.</span><span class="sxs-lookup"><span data-stu-id="82d66-105">Select which Queue Reader Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Queue Reader Agent**.</span></span> <span data-ttu-id="82d66-106">Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**.</span><span class="sxs-lookup"><span data-stu-id="82d66-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="82d66-107">Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.</span><span class="sxs-lookup"><span data-stu-id="82d66-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="82d66-108">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="82d66-108">**View**</span></span>  
 <span data-ttu-id="82d66-109">Sélectionnez les sessions de l'Agent de lecture de la file d'attente à afficher.</span><span class="sxs-lookup"><span data-stu-id="82d66-109">Select which Queue Reader Agent sessions to view.</span></span> <span data-ttu-id="82d66-110">L'Agent de lecture de la file d'attente s'exécute généralement en permanence : il se peut donc qu'il n'y ait qu'une session à afficher.</span><span class="sxs-lookup"><span data-stu-id="82d66-110">The Queue Reader Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="82d66-111">**État**</span><span class="sxs-lookup"><span data-stu-id="82d66-111">**Status**</span></span>  
 <span data-ttu-id="82d66-112">État de l'Agent de lecture de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="82d66-112">The status of the Queue Reader Agent.</span></span> <span data-ttu-id="82d66-113">La liste ci-dessous indique les valeurs d'état possibles :</span><span class="sxs-lookup"><span data-stu-id="82d66-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="82d66-114">Error</span><span class="sxs-lookup"><span data-stu-id="82d66-114">Error</span></span>  
  
-   <span data-ttu-id="82d66-115">Nouvelle tentative de la commande qui a échoué</span><span class="sxs-lookup"><span data-stu-id="82d66-115">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="82d66-116">Non exécuté</span><span class="sxs-lookup"><span data-stu-id="82d66-116">Not running</span></span>  
  
-   <span data-ttu-id="82d66-117">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="82d66-117">Running</span></span>  
  
 <span data-ttu-id="82d66-118">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="82d66-118">**Start Time**</span></span>  
 <span data-ttu-id="82d66-119">Heure d'ouverture de la session.</span><span class="sxs-lookup"><span data-stu-id="82d66-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="82d66-120">**Heure de fin**</span><span class="sxs-lookup"><span data-stu-id="82d66-120">**End Time**</span></span>  
 <span data-ttu-id="82d66-121">Heure de fin de la session.</span><span class="sxs-lookup"><span data-stu-id="82d66-121">The end time of the session.</span></span> <span data-ttu-id="82d66-122">Si l'agent ne s'est pas arrêté, ce champ est vide.</span><span class="sxs-lookup"><span data-stu-id="82d66-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="82d66-123">**Durée**</span><span class="sxs-lookup"><span data-stu-id="82d66-123">**Duration**</span></span>  
 <span data-ttu-id="82d66-124">Durée d'exécution de l'Agent de lecture de la file d'attente dans cette session.</span><span class="sxs-lookup"><span data-stu-id="82d66-124">The amount of time the Queue Reader Agent has run in this session.</span></span> <span data-ttu-id="82d66-125">Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="82d66-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="82d66-126">**Message d’erreur**</span><span class="sxs-lookup"><span data-stu-id="82d66-126">**Error Message**</span></span>  
 <span data-ttu-id="82d66-127">Si une session s'est terminée sur une erreur, ce champ affiche le dernier message d'erreur enregistré par l'Agent de lecture de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="82d66-127">If a session ended in an error, this field displays the last error message logged by the Queue Reader Agent.</span></span> <span data-ttu-id="82d66-128">Dans le cas contraire, ce champ est vide.</span><span class="sxs-lookup"><span data-stu-id="82d66-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="82d66-129">**Message d'action**</span><span class="sxs-lookup"><span data-stu-id="82d66-129">**Action Message**</span></span>  
 <span data-ttu-id="82d66-130">Tous les messages d'information ou d'erreur que l'Agent de lecture de la file d'attente a enregistrés pendant la session sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="82d66-130">All informational messages and error messages that the Queue Reader Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="82d66-131">**Heure de l'action**</span><span class="sxs-lookup"><span data-stu-id="82d66-131">**Action Time**</span></span>  
 <span data-ttu-id="82d66-132">Heure à laquelle l'action décrite dans la colonne **Message d'action** s'est déroulée.</span><span class="sxs-lookup"><span data-stu-id="82d66-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="82d66-133">**Détails de l'erreur ou message de la session sélectionnée**</span><span class="sxs-lookup"><span data-stu-id="82d66-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="82d66-134">S'affiche uniquement si la session sélectionnée affiche une valeur **Erreur** dans la colonne **État** .</span><span class="sxs-lookup"><span data-stu-id="82d66-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="82d66-135">La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="82d66-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="82d66-136">Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="82d66-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d66-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d66-137">See Also</span></span>  
 <span data-ttu-id="82d66-138">[Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="82d66-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="82d66-139">[Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="82d66-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="82d66-140">[Surveillance de la réplication](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="82d66-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="82d66-141">Présentation des Agents de réplication</span><span class="sxs-lookup"><span data-stu-id="82d66-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  