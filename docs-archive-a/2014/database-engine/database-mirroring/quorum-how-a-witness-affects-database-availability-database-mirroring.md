---
title: "Quorum : effets d'un témoin sur la disponibilité de la base de données (mise en miroir de bases de données) | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- quorum [SQL Server], database mirroring
- running exposed in database mirroring [SQL Server]
- witness-to-partner quorum [SQL Server]
- partners [SQL Server], partner-to-partner quorum
- witness [SQL Server], quorum
- have quorum [SQL Server]
- quorum [SQL Server]
- mirror database [SQL Server]
- full quorum [SQL Server]
- high-availability mode [SQL Server]
ms.assetid: a62d9dd7-3667-4751-a294-a61fc9caae7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ada152f280a4ac75543f09e5f5afa7c72c0cbef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701820"
---
# <a name="quorum-how-a-witness-affects-database-availability-database-mirroring"></a><span data-ttu-id="2369f-102">Quorum : effets d'un témoin sur la disponibilité de la base de données (mise en miroir de bases de données)</span><span class="sxs-lookup"><span data-stu-id="2369f-102">Quorum: How a Witness Affects Database Availability (Database Mirroring)</span></span>
  <span data-ttu-id="2369f-103">Chaque fois qu’un témoin est défini pour une session de mise en miroir de base de données, un *quorum* est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2369f-103">Whenever a witness is set for a database mirroring session, *quorum* is required.</span></span> <span data-ttu-id="2369f-104">Le quorum désigne une relation où deux ou plusieurs instances de serveur dans une session de mise en miroir de base de données sont connectées.</span><span class="sxs-lookup"><span data-stu-id="2369f-104">Quorum is a relationship that exists when two or more server instances in a database mirroring session are connected to each other.</span></span> <span data-ttu-id="2369f-105">En règle générale, le quorum implique trois instances de serveurs interconnectées.</span><span class="sxs-lookup"><span data-stu-id="2369f-105">Typically, quorum involves three interconnected server instances.</span></span> <span data-ttu-id="2369f-106">Lorsqu'un témoin est défini, un quorum est requis pour rendre la base de données disponible.</span><span class="sxs-lookup"><span data-stu-id="2369f-106">When a witness is set, quorum is required to make the database available.</span></span> <span data-ttu-id="2369f-107">Conçu pour les sessions en mode haute sécurité avec basculement automatique, un quorum garantit qu'une base de données appartient à un seul partenaire à la fois.</span><span class="sxs-lookup"><span data-stu-id="2369f-107">Designed for high-safety mode with automatic failover, quorum makes sure that a database is owned by only one partner at a time.</span></span>  
  
 <span data-ttu-id="2369f-108">Si une instance de serveur spécifique est déconnectée d'une session de mise en miroir, l'instance perd le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-108">If a particular server instance becomes disconnected from a mirroring session, that instance loses quorum.</span></span> <span data-ttu-id="2369f-109">Si aucune instance de serveur n'est connectée, la session perd le quorum et la base de données n'est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="2369f-109">If no server instances are connected, the session loses quorum and the database becomes unavailable.</span></span> <span data-ttu-id="2369f-110">Trois types de quorum sont possibles :</span><span class="sxs-lookup"><span data-stu-id="2369f-110">Three types of quorum are possible:</span></span>  
  
-   <span data-ttu-id="2369f-111">Un *quorum complet* inclut les deux partenaires et le témoin.</span><span class="sxs-lookup"><span data-stu-id="2369f-111">A *full quorum* includes both partners and the witness.</span></span>  
  
-   <span data-ttu-id="2369f-112">Un *quorum de témoin à partenaire* est composé du témoin et de l’un des partenaires.</span><span class="sxs-lookup"><span data-stu-id="2369f-112">A *witness-to-partner quorum* consists of the witness and either partner.</span></span>  
  
-   <span data-ttu-id="2369f-113">Un *quorum de partenaire à partenaire* est composé des deux partenaires.</span><span class="sxs-lookup"><span data-stu-id="2369f-113">A *partner-to-partner quorum* consists of the two partners.</span></span>  
  
 <span data-ttu-id="2369f-114">La figure suivante illustre ces types de quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-114">The following figure shows these types of quorum.</span></span>  
  
 <span data-ttu-id="2369f-115">![Quorums : complet ; témoin et serveur partenaire ; deux serveurs partenaires](../media/dbm-failovautoquorum.gif "Quorums : complet ; témoin et serveur partenaire ; deux serveurs partenaires")</span><span class="sxs-lookup"><span data-stu-id="2369f-115">![Quorums: full; witness and partner; both partners](../media/dbm-failovautoquorum.gif "Quorums: full; witness and partner; both partners")</span></span>  
  
 <span data-ttu-id="2369f-116">Tant que le serveur principal actuel possède un quorum, ce serveur détient le rôle principal et continue de servir la base de données, sauf si le propriétaire de la base de données effectue un basculement manuel.</span><span class="sxs-lookup"><span data-stu-id="2369f-116">As long as the current principal server has quorum, this server owns the role of principal and continues to serve the database, unless the database owner performs a manual failover.</span></span> <span data-ttu-id="2369f-117">Si le serveur principal perd le quorum, il ne sert plus la base de données.</span><span class="sxs-lookup"><span data-stu-id="2369f-117">If the principal server loses quorum, it stops serving the database.</span></span> <span data-ttu-id="2369f-118">Un basculement automatique peut se produire seulement si la base de données principale a perdu le quorum, ce qui garantit qu'elle ne sert plus la base de données.</span><span class="sxs-lookup"><span data-stu-id="2369f-118">Automatic failover can occur only if the principal database has lost quorum, which guarantees that it is no longer serving the database.</span></span>  
  
 <span data-ttu-id="2369f-119">Une instance de serveur déconnectée enregistre son rôle le plus récent dans la session.</span><span class="sxs-lookup"><span data-stu-id="2369f-119">A disconnected server instance saves its most recent role in the session.</span></span> <span data-ttu-id="2369f-120">En principe, une instance de serveur déconnectée se reconnecte à la session lors de son redémarrage et obtient de nouveau le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-120">Typically, a disconnected server instance reconnects to the session when it restarts and regains quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2369f-121">Le témoin ne doit être défini que si vous avez l'intention d'utiliser le mode haute sécurité avec basculement automatique.</span><span class="sxs-lookup"><span data-stu-id="2369f-121">The witness should be set only when you intend to use high-safety mode with automatic failover.</span></span> <span data-ttu-id="2369f-122">En mode hautes performances, qui ne requiert jamais de témoin, nous vous conseillons vivement d'attribuer la valeur OFF à la propriété WITNESS.</span><span class="sxs-lookup"><span data-stu-id="2369f-122">In high-performance mode, for which a witness is never required, we strongly recommend setting the WITNESS property to OFF.</span></span> <span data-ttu-id="2369f-123">Pour plus d’informations sur l’incidence d’un témoin sur le mode hautes performances, consultez [Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring-operating-modes.md).</span><span class="sxs-lookup"><span data-stu-id="2369f-123">For information about the impact of a witness on high-performance mode, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="quorum-in-high-safety-mode-sessions"></a><span data-ttu-id="2369f-124">Quorum dans les sessions en mode haute sécurité</span><span class="sxs-lookup"><span data-stu-id="2369f-124">Quorum in High-Safety Mode Sessions</span></span>  
 <span data-ttu-id="2369f-125">En mode haute sécurité, un quorum permet le basculement automatique en fournissant un contexte dans lequel les instances de serveur avec quorum décident quel partenaire détient le rôle de principal.</span><span class="sxs-lookup"><span data-stu-id="2369f-125">In high-safety mode, quorum allows automatic failover by providing a context in which the server instances with quorum arbitrate which partner owns the role of principal.</span></span> <span data-ttu-id="2369f-126">Le serveur principal sert la base de données s'il dispose d'un quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-126">The principal server serves the database if it has quorum.</span></span> <span data-ttu-id="2369f-127">Si le serveur principal perd le quorum lorsque le serveur miroir synchronisé et le témoin conservent le quorum, le basculement automatique se produit.</span><span class="sxs-lookup"><span data-stu-id="2369f-127">If the principal server loses quorum when the synchronized mirror server and witness retain quorum, automatic failover occurs.</span></span>  
  
 <span data-ttu-id="2369f-128">Les scénarios de quorum en mode haute sécurité sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="2369f-128">The quorum scenarios for high-safety mode are as follows:</span></span>  
  
-   <span data-ttu-id="2369f-129">Un *quorum complet* composé des deux partenaires et du témoin.</span><span class="sxs-lookup"><span data-stu-id="2369f-129">A *full quorum* that consists of both partners and the witness.</span></span>  
  
     <span data-ttu-id="2369f-130">Normalement, les trois instances de serveur participent à un quorum à trois voies, appelé *quorum complet*.</span><span class="sxs-lookup"><span data-stu-id="2369f-130">Ordinarily, all three server instances participate in a three-way quorum, called a *full quorum*.</span></span> <span data-ttu-id="2369f-131">Avec un quorum complet, le serveur principal et le serveur miroir continuent d'assumer leur rôle respectif (sauf si un basculement manuel intervient).</span><span class="sxs-lookup"><span data-stu-id="2369f-131">With a full quorum, the principal and mirror servers continue to perform their respective roles (unless manual failover occurs).</span></span>  
  
-   <span data-ttu-id="2369f-132">Un *quorum de témoin à partenaire* composé du témoin et de l’un des partenaires.</span><span class="sxs-lookup"><span data-stu-id="2369f-132">A *witness-to-partner quorum* that consists of the witness and either partner.</span></span>  
  
     <span data-ttu-id="2369f-133">Si la connexion réseau entre les partenaires est perdue car l'un des partenaires a été perdu, les cas suivants sont possibles :</span><span class="sxs-lookup"><span data-stu-id="2369f-133">If the network connection between the partners is lost because one of the partners has been lost, the following cases are possible:</span></span>  
  
    -   <span data-ttu-id="2369f-134">Le serveur miroir est perdu et le serveur principal et le témoin conservent le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-134">The mirror server is lost, and the principal server and witness retain quorum.</span></span>  
  
         <span data-ttu-id="2369f-135">Dans ce cas, le principal définit sa base de données sur DISCONNECTED, et la mise en miroir est en état SUSPENDED.</span><span class="sxs-lookup"><span data-stu-id="2369f-135">In this case, the principal sets its database to DISCONNECTED and runs with mirroring in a SUSPENDED state.</span></span> <span data-ttu-id="2369f-136">(Cette opération est appelée *exécution exposée*, car la base de données ne fait pas l’objet d’une mise en miroir). Lorsque le serveur miroir réintègre la session, il acquiert de nouveau le quorum en tant que miroir et commence à resynchroniser sa copie de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2369f-136">(This is referred to as *running exposed*, because the database is currently not being mirrored.) When the mirror server rejoins the session, the server regains quorum as mirror and starts resynchronizing its copy of the database.</span></span>  
  
    -   <span data-ttu-id="2369f-137">Le serveur principal est perdu et le serveur témoin et le serveur miroir conservent le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-137">The principal server is lost, and the witness and the mirror server retain quorum.</span></span>  
  
         <span data-ttu-id="2369f-138">Dans ce cas, le basculement automatique intervient.</span><span class="sxs-lookup"><span data-stu-id="2369f-138">In this case, automatic failover occurs.</span></span> <span data-ttu-id="2369f-139">Pour plus d'informations, voir [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span><span class="sxs-lookup"><span data-stu-id="2369f-139">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    -   <span data-ttu-id="2369f-140">Toutes les instances de serveur perdent le quorum, mais le miroir et le témoin se reconnectent par la suite.</span><span class="sxs-lookup"><span data-stu-id="2369f-140">All the server instances lose quorum, but subsequently the mirror and witness reconnect.</span></span> <span data-ttu-id="2369f-141">La base de données ne sera pas utilisée dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="2369f-141">The database will not be served in this case.</span></span>  
  
     <span data-ttu-id="2369f-142">À de rares occasions, la connexion réseau entre les partenaires de basculement est perdue alors que les deux partenaires restent connectés au témoin.</span><span class="sxs-lookup"><span data-stu-id="2369f-142">Rarely, the network connection between failover partners is lost while both partners remain connected to the witness.</span></span> <span data-ttu-id="2369f-143">Dans ce cas, il existe deux quorums distincts de témoin à partenaire, avec le témoin comme liaison.</span><span class="sxs-lookup"><span data-stu-id="2369f-143">In this event, two, separate witness-to-partner quorums exist, with the witness as a liaison.</span></span> <span data-ttu-id="2369f-144">Le témoin informe le serveur miroir que le serveur principal est toujours connecté.</span><span class="sxs-lookup"><span data-stu-id="2369f-144">The witness informs the mirror server that the principal server is still connected.</span></span> <span data-ttu-id="2369f-145">De ce fait, le basculement automatique n'intervient pas.</span><span class="sxs-lookup"><span data-stu-id="2369f-145">Therefore, automatic failover does not occur.</span></span> <span data-ttu-id="2369f-146">À la place, le serveur miroir conserve le rôle de miroir et attend de se reconnecter au principal.</span><span class="sxs-lookup"><span data-stu-id="2369f-146">Instead, the mirror server retains the mirror role and waits to reconnect to the principal.</span></span> <span data-ttu-id="2369f-147">Si la file d'attente de restauration par progression contient des enregistrements de journaux à ce stade, le serveur miroir continue de restaurer par progression la base de données miroir.</span><span class="sxs-lookup"><span data-stu-id="2369f-147">If the redo queue contains log records at this point, the mirror server continues to roll forward the mirror database.</span></span> <span data-ttu-id="2369f-148">Lors de la reconnexion, le serveur miroir resynchronisera la base de données miroir.</span><span class="sxs-lookup"><span data-stu-id="2369f-148">On reconnecting, the mirror server will resynchronize the mirror database.</span></span>  
  
-   <span data-ttu-id="2369f-149">Un *quorum de partenaire à partenaire* composé des deux partenaires.</span><span class="sxs-lookup"><span data-stu-id="2369f-149">A *partner-to-partner quorum* that consists of the two partners.</span></span>  
  
     <span data-ttu-id="2369f-150">Dans la mesure où les partenaires conservent le quorum, la base de données continue dans un état SYNCHRONIZED et un basculement manuel reste possible.</span><span class="sxs-lookup"><span data-stu-id="2369f-150">As long as the partners retain quorum, the database continues in a SYNCHRONIZED state, and manual failover remains possible.</span></span> <span data-ttu-id="2369f-151">Sans le témoin, le basculement automatique n'est pas possible, mais si le témoins acquiert de nouveau le quorum, la session reprend les opérations normales et le basculement automatique est à nouveau pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2369f-151">Without the witness, automatic failover is not possible; but when the witness regains quorum, the session resumes regular operation, and automatic failover is supported again.</span></span>  
  
-   <span data-ttu-id="2369f-152">La session perd le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-152">The session loses quorum.</span></span>  
  
     <span data-ttu-id="2369f-153">Si toutes les instances de serveur se déconnectent les unes des autres, on dit que la session a *perdu le quorum*.</span><span class="sxs-lookup"><span data-stu-id="2369f-153">If all the server instances become disconnected from each other, the session is said to have *lost quorum*.</span></span> <span data-ttu-id="2369f-154">Lorsque les instances de serveur se reconnectent entre elles, elles acquièrent de nouveau le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-154">As server instances reconnect to each other, they regain quorum with each other.</span></span>  
  
    -   <span data-ttu-id="2369f-155">Si le serveur principal se reconnecte à l'une ou l'autre des instances du serveur, la base de données est disponible.</span><span class="sxs-lookup"><span data-stu-id="2369f-155">If the principal server reconnects with either of the other server instances, the database becomes available.</span></span>  
  
    -   <span data-ttu-id="2369f-156">Si le serveur principal reste déconnecté, mais que le miroir et le témoin se reconnectent, le basculement automatique ne peut pas se produire en raison du risque de perte des données.</span><span class="sxs-lookup"><span data-stu-id="2369f-156">If the principal server remains disconnected, but the mirror and witness reconnect to each other, automatic failover cannot occur because data loss might occur.</span></span> <span data-ttu-id="2369f-157">C'est pourquoi la base de données reste indisponible tant que le serveur principal n'a pas réintégré la session.</span><span class="sxs-lookup"><span data-stu-id="2369f-157">Therefore, the database remains unavailable, until the principal server rejoins the session.</span></span>  
  
    -   <span data-ttu-id="2369f-158">Lorsque les trois instances du serveur se sont reconnectées, le quorum complet est de nouveau acquis et la session reprend ses opérations normales.</span><span class="sxs-lookup"><span data-stu-id="2369f-158">When all three server instances have reconnected, full quorum is regained, and the session resumes its regular operation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2369f-159">Lorsqu'une session possède un quorum partenaire à partenaire, si l'un des partenaires perd le quorum, la session perd le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-159">When a session has a partner-to-partner quorum, if either partner loses quorum, the session loses quorum.</span></span> <span data-ttu-id="2369f-160">Cependant, si vous pensez que le témoin va rester longtemps déconnecté, nous vous recommandons de supprimer temporairement le témoin de la session.</span><span class="sxs-lookup"><span data-stu-id="2369f-160">Therefore, if you expect the witness to remain disconnected for lots of time, we recommend that you temporarily remove the witness from the session.</span></span> <span data-ttu-id="2369f-161">La suppression du témoin supprime la nécessité d'avoir un quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-161">Removing the witness removes the requirement for quorum.</span></span> <span data-ttu-id="2369f-162">Enfin, si le serveur miroir perd la connexion, le serveur principal peut continuer de servir la base de données.</span><span class="sxs-lookup"><span data-stu-id="2369f-162">Then, if the mirror server becomes disconnected, the principal server can continue to serve the database.</span></span> <span data-ttu-id="2369f-163">Pour plus d’informations sur l’ajout ou la suppression d’un témoin, consultez [Témoin de mise en miroir de base de données](database-mirroring-witness.md).</span><span class="sxs-lookup"><span data-stu-id="2369f-163">For information about how to add or remove a witness, see [Database Mirroring Witness](database-mirroring-witness.md).</span></span>  
  
### <a name="how-quorum-affects-database-availability"></a><span data-ttu-id="2369f-164">Effets du quorum sur la disponibilité de la base de données</span><span class="sxs-lookup"><span data-stu-id="2369f-164">How Quorum Affects Database Availability</span></span>  
 <span data-ttu-id="2369f-165">L'illustration suivante montre la façon dont le témoin et les partenaires coopèrent pour garantir que, à un moment donné, un seul partenaire possède le rôle principal, et que seul le serveur principal actif peut mettre sa base de données en ligne.</span><span class="sxs-lookup"><span data-stu-id="2369f-165">The following illustration shows how the witness and the partners cooperate to make sure that, at given time, only one partner owns the role of principal and only the current principal server can bring its database online.</span></span> <span data-ttu-id="2369f-166">Les deux scénarios commencent avec un quorum complet, avec **Partner_A** dans le rôle de principal et **Partner_B** dans le rôle de miroir.</span><span class="sxs-lookup"><span data-stu-id="2369f-166">Both scenarios start with full quorum, and **Partner_A** in the principal role and **Partner_B** in the mirror role.</span></span>  
  
 <span data-ttu-id="2369f-167">![Coopération entre témoin et serveurs partenaires](../media/dbm-quorum-scenarios.gif "Coopération entre témoin et serveurs partenaires")</span><span class="sxs-lookup"><span data-stu-id="2369f-167">![How the witness and partners cooperate](../media/dbm-quorum-scenarios.gif "How the witness and partners cooperate")</span></span>  
  
 <span data-ttu-id="2369f-168">Le scénario 1 montre comment, après que le serveur principal d’origine (**Partner_A**) a subi une défaillance, le témoin et le miroir s’accordent à considérer le principal, **Partner_A**, comme n’étant plus disponible et forment un quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-168">Scenario 1 shows how after the original principal server (**Partner_A**) fails, the witness and mirror agree that the principal, **Partner_A**, is not available any longer and form quorum.</span></span> <span data-ttu-id="2369f-169">Le miroir, **Partner_B** , assume alors le rôle de principal.</span><span class="sxs-lookup"><span data-stu-id="2369f-169">The mirror, **Partner_B** then assumes the principal role.</span></span> <span data-ttu-id="2369f-170">Le basculement automatique intervient et **Partner_B**met sa copie de la base de données en ligne.</span><span class="sxs-lookup"><span data-stu-id="2369f-170">Automatic failover occurs, and **Partner_B**, brings its copy of the database online.</span></span> <span data-ttu-id="2369f-171">Ensuite, **Partner_B** tombe en panne et la base de données bascule hors connexion.</span><span class="sxs-lookup"><span data-stu-id="2369f-171">Then **Partner_B** goes down, and the database goes offline.</span></span> <span data-ttu-id="2369f-172">Plus tard, l’ancien serveur principal, **Partner_A**, se reconnecte au témoin regagnant le quorum, mais, en communiquant avec le témoin, **Partner_A** apprend qu’il ne peut pas mettre sa copie de la base de données en ligne étant donné que **Partner_B** possède maintenant le rôle de principal.</span><span class="sxs-lookup"><span data-stu-id="2369f-172">Later, the former principal server, **Partner_A**, reconnects to the witness regaining quorum, but on communicating with the witness, **Partner_A** learns that it cannot bring its copy of the database online, because **Partner_B** now owns the principal role.</span></span> <span data-ttu-id="2369f-173">Quand **Partner_B** réintègre la session, il remet la base de données en ligne.</span><span class="sxs-lookup"><span data-stu-id="2369f-173">When **Partner_B** rejoins the session, it brings the database back online.</span></span>  
  
 <span data-ttu-id="2369f-174">Dans le scénario 2, le témoin perd le quorum, tandis que les partenaires, **Partner_A** et **Partner_B**, le conservent, et la base de données reste en ligne.</span><span class="sxs-lookup"><span data-stu-id="2369f-174">In Scenario 2, the witness loses quorum, while the partners, **Partner_A** and **Partner_B**, retain quorum with each other, and the database remains online.</span></span> <span data-ttu-id="2369f-175">Puis, les partenaires perdent également leur quorum et la base de données bascule hors connexion.</span><span class="sxs-lookup"><span data-stu-id="2369f-175">Then the partners lose their quorum, too, and the database goes offline.</span></span> <span data-ttu-id="2369f-176">Plus tard, le serveur principal, **Partner_A**, se reconnecte au témoin regagnant le quorum.</span><span class="sxs-lookup"><span data-stu-id="2369f-176">Later, the principal server, **Partner_A**, reconnects to the witness regaining quorum.</span></span> <span data-ttu-id="2369f-177">Le témoin confirme que **Partner_A** possède encore le rôle de principal et **Partner_A** remet la base de données en ligne.</span><span class="sxs-lookup"><span data-stu-id="2369f-177">The witness confirms that **Partner_A** still owns the principal role, and **Partner_A** brings the database back online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2369f-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2369f-178">See Also</span></span>  
 <span data-ttu-id="2369f-179">[Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="2369f-179">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="2369f-180">[Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2369f-180">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="2369f-181">[Témoin de mise en miroir de base de données](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="2369f-181">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="2369f-182">[Défaillances possibles pendant la mise en miroir de bases de données](possible-failures-during-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="2369f-182">[Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md) </span></span>  
 [<span data-ttu-id="2369f-183">États de la mise en miroir &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2369f-183">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  