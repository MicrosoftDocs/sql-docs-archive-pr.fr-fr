---
title: SQL Server, objet General Statistics | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a982796230304f85545fa8812ad1c3b2558365ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602088"
---
# <a name="sql-server-general-statistics-object"></a><span data-ttu-id="56b79-102">SQL Server, objet General Statistics</span><span class="sxs-lookup"><span data-stu-id="56b79-102">SQL Server, General Statistics Object</span></span>
  <span data-ttu-id="56b79-103">L’objet **SQLServer:General Statistics** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs pour surveiller l’activité générale du serveur, comme le nombre de connexions actives et le nombre d’utilisateurs se connectant et se déconnectant à la seconde d’ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b79-103">The **SQLServer:General Statistics** object in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor general server-wide activity, such as the number of current connections and the number of users connecting and disconnecting per second from computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="56b79-104">Cela s'avère utile lorsque vous travaillez sur des systèmes OLTP importants sur lesquels de nombreux clients se connectent et se déconnectent d'ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b79-104">This can be useful when you are working on large online transaction processing (OLTP) type systems where there are many clients connecting and disconnecting from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="56b79-105">Ce tableau décrit les compteurs **Statistiques générales** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b79-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **General Statistics** counters.</span></span>  
  
|<span data-ttu-id="56b79-106">Compteurs statistiques générales de SQL Server</span><span class="sxs-lookup"><span data-stu-id="56b79-106">SQL Server General Statistics counters</span></span>|<span data-ttu-id="56b79-107">Description</span><span class="sxs-lookup"><span data-stu-id="56b79-107">Description</span></span>|  
|--------------------------------------------|-----------------|  
|<span data-ttu-id="56b79-108">**Tables temporaires actives**</span><span class="sxs-lookup"><span data-stu-id="56b79-108">**Active Temp Tables**</span></span>|<span data-ttu-id="56b79-109">Nombre de tables temporaires/variables de table en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="56b79-109">Number of temporary tables/table variables in use.</span></span>|  
|<span data-ttu-id="56b79-110">**Réinitialisation de la connexion/s**</span><span class="sxs-lookup"><span data-stu-id="56b79-110">**Connection resets/sec**</span></span>|<span data-ttu-id="56b79-111">Nombre total de connexions établies à partir du groupement de connexions.</span><span class="sxs-lookup"><span data-stu-id="56b79-111">Total number of logins started from the connection pool.</span></span>|  
|<span data-ttu-id="56b79-112">**Suppression différée des notifications d'événements**</span><span class="sxs-lookup"><span data-stu-id="56b79-112">**Event Notifications Delayed Drop**</span></span>|<span data-ttu-id="56b79-113">Nombre de notifications d'événements en attente de suppression par un thread système</span><span class="sxs-lookup"><span data-stu-id="56b79-113">Number of event notifications waiting to be dropped by a system thread.</span></span>|  
|<span data-ttu-id="56b79-114">**Requêtes HTTP authentifiées**</span><span class="sxs-lookup"><span data-stu-id="56b79-114">**HTTP Authenticated Requests**</span></span>|<span data-ttu-id="56b79-115">Nombre de requêtes HTTP authentifiées démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-115">Number of authenticated HTTP requests started per second.</span></span>|  
|<span data-ttu-id="56b79-116">**Connexions logiques**</span><span class="sxs-lookup"><span data-stu-id="56b79-116">**Logical Connections**</span></span>|<span data-ttu-id="56b79-117">Nombre de connexions logiques au système.</span><span class="sxs-lookup"><span data-stu-id="56b79-117">Number of logical connections to the system.</span></span><br /><br /> <span data-ttu-id="56b79-118">La finalité principale des connexions logiques est de traiter les requêtes MARS (multiple active result sets).</span><span class="sxs-lookup"><span data-stu-id="56b79-118">The main purpose of logical connections is to service multiple active result sets (MARS) requests.</span></span> <span data-ttu-id="56b79-119">Dans le cas des requêtes MARS, chaque fois qu'une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il peut y avoir plusieurs connexions logiques associées à une connexion physique.</span><span class="sxs-lookup"><span data-stu-id="56b79-119">For MARS requests, every time that an application makes a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], there may be more than one logical connection that corresponds to a physical connection.</span></span><br /><br /> <span data-ttu-id="56b79-120">Lorsque vous n'utilisez pas MARS, le ratio entre les connexions physiques et logiques et de 1:1.</span><span class="sxs-lookup"><span data-stu-id="56b79-120">When MARS is not used, the ratio between physical and logical connections is 1:1.</span></span> <span data-ttu-id="56b79-121">Chaque fois qu'une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les connexions logiques augmentent donc de 1.</span><span class="sxs-lookup"><span data-stu-id="56b79-121">Therefore, every time that an application makes a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], logical connections will increase by 1.</span></span>|  
|<span data-ttu-id="56b79-122">**Connexions/s**</span><span class="sxs-lookup"><span data-stu-id="56b79-122">**Logins/sec**</span></span>|<span data-ttu-id="56b79-123">Nombre total de connexions démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-123">Total number of logins started per second.</span></span> <span data-ttu-id="56b79-124">N'inclut pas les connexions regroupées.</span><span class="sxs-lookup"><span data-stu-id="56b79-124">This does not include pooled connections.</span></span>|  
|<span data-ttu-id="56b79-125">**Déconnexions/s**</span><span class="sxs-lookup"><span data-stu-id="56b79-125">**Logouts/sec**</span></span>|<span data-ttu-id="56b79-126">Nombre total de déconnexions effectuées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-126">Total number of logout operations started per second.</span></span>|  
|<span data-ttu-id="56b79-127">**Blocages MARS**</span><span class="sxs-lookup"><span data-stu-id="56b79-127">**Mars Deadlocks**</span></span>|<span data-ttu-id="56b79-128">Nombre de blocages MARS détectés.</span><span class="sxs-lookup"><span data-stu-id="56b79-128">Number of MARS deadlocks detected.</span></span>|  
|<span data-ttu-id="56b79-129">**Taux de rendement non atomique**</span><span class="sxs-lookup"><span data-stu-id="56b79-129">**Non-atomic yield rate**</span></span>|<span data-ttu-id="56b79-130">Nombre de rendements non atomiques par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-130">Number of non-atomic yields per second.</span></span>|  
|<span data-ttu-id="56b79-131">**Processus bloqués**</span><span class="sxs-lookup"><span data-stu-id="56b79-131">**Processes blocked**</span></span>|<span data-ttu-id="56b79-132">Nombre de processus actuellement bloqués.</span><span class="sxs-lookup"><span data-stu-id="56b79-132">Number of currently blocked processes.</span></span>|  
|<span data-ttu-id="56b79-133">**Requêtes SOAP vides**</span><span class="sxs-lookup"><span data-stu-id="56b79-133">**SOAP Empty Requests**</span></span>|<span data-ttu-id="56b79-134">Nombre de requêtes SOAP vides démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-134">Number of empty SOAP requests started per second.</span></span>|  
|<span data-ttu-id="56b79-135">**Appels de méthode SOAP**</span><span class="sxs-lookup"><span data-stu-id="56b79-135">**SOAP Method Invocations**</span></span>|<span data-ttu-id="56b79-136">Nombre d'appels de méthode SOAP démarrés par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-136">Number of SOAP method invocations started per second.</span></span>|  
|<span data-ttu-id="56b79-137">**Requêtes d'ouverture de session SOAP**</span><span class="sxs-lookup"><span data-stu-id="56b79-137">**SOAP Session Initiate Requests**</span></span>|<span data-ttu-id="56b79-138">Nombre de requêtes d'ouverture de session SOAP démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-138">Number of SOAP Session initiate requests started per second.</span></span>|  
|<span data-ttu-id="56b79-139">**Requêtes de fermeture de session SOAP**</span><span class="sxs-lookup"><span data-stu-id="56b79-139">**SOAP Session Terminate Requests**</span></span>|<span data-ttu-id="56b79-140">Nombre de requêtes de fermeture de session SOAP démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-140">Number of SOAP Session terminate requests started per second.</span></span>|  
|<span data-ttu-id="56b79-141">**Requêtes SQL SOAP**</span><span class="sxs-lookup"><span data-stu-id="56b79-141">**SOAP SQL Requests**</span></span>|<span data-ttu-id="56b79-142">Nombre de requêtes SQL SOAP démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-142">Number of SOAP SQL requests started per second.</span></span>|  
|<span data-ttu-id="56b79-143">**Requêtes WSDL SOAP**</span><span class="sxs-lookup"><span data-stu-id="56b79-143">**SOAP WSDL Requests**</span></span>|<span data-ttu-id="56b79-144">Nombre de requêtes WSDL SOAP démarrées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-144">Number of SOAP Web Service Description Language requests started per second.</span></span>|  
|<span data-ttu-id="56b79-145">**Taux de création de tables temporaires**</span><span class="sxs-lookup"><span data-stu-id="56b79-145">**Temp Tables Creation Rate**</span></span>|<span data-ttu-id="56b79-146">Nombre de tables temporaires/variables de table créées par seconde.</span><span class="sxs-lookup"><span data-stu-id="56b79-146">Number of temporary tables/table variables created per second.</span></span>|  
|<span data-ttu-id="56b79-147">**Tables temporaires en attente de destruction**</span><span class="sxs-lookup"><span data-stu-id="56b79-147">**Temp Tables For Destruction**</span></span>|<span data-ttu-id="56b79-148">Nombre de tables temporaires/variables de table qui attendent d'être détruites par le thread système de nettoyage</span><span class="sxs-lookup"><span data-stu-id="56b79-148">Number of temporary tables/table variables waiting to be destroyed by the cleanup system thread.</span></span>|  
|<span data-ttu-id="56b79-149">**File d'attente des notifications d'événements de trace**</span><span class="sxs-lookup"><span data-stu-id="56b79-149">**Trace Event Notifications Queue**</span></span>|<span data-ttu-id="56b79-150">Nombre d'instances de notifications d'événements de trace qui attendent dans la file d'attente interne d'être envoyées via Service Broker</span><span class="sxs-lookup"><span data-stu-id="56b79-150">Number of trace event notification instances waiting in the internal queue to be sent through Service Broker.</span></span>|  
|<span data-ttu-id="56b79-151">**Transactions**</span><span class="sxs-lookup"><span data-stu-id="56b79-151">**Transactions**</span></span>|<span data-ttu-id="56b79-152">Nombre d'inscriptions de transactions (locales, du DTC et lie´es).</span><span class="sxs-lookup"><span data-stu-id="56b79-152">Number of transaction enlistments (local, DTC, bound all combined).</span></span>|  
|<span data-ttu-id="56b79-153">**Connexions utilisateur**</span><span class="sxs-lookup"><span data-stu-id="56b79-153">**User Connections**</span></span>|<span data-ttu-id="56b79-154">Compte le nombre d'utilisateurs actuellement connectés à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56b79-154">Counts the number of users currently connected to SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56b79-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56b79-155">See Also</span></span>  
 [<span data-ttu-id="56b79-156">Analyser l’utilisation des ressources &#40;Moniteur système&#41;</span><span class="sxs-lookup"><span data-stu-id="56b79-156">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  