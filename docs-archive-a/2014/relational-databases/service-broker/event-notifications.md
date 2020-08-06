---
title: Notifications d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications, about
- events [SQL Server], notifications
ms.assetid: 4da73ca1-6c06-4e96-8ab8-2ecba30b6c86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2d5d7114515179cda973b9685c57b26fa930521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613387"
---
# <a name="event-notifications"></a><span data-ttu-id="9cf84-102">Notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-102">Event Notifications</span></span>
  <span data-ttu-id="9cf84-103">Les notifications d'événements envoient des informations sur les événements à un service [!INCLUDE[ssSB](../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cf84-103">Event notifications send information about events to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] service.</span></span> <span data-ttu-id="9cf84-104">Les notifications d'événements sont exécutées en réponse à une variété d'instructions DDL (Data Definition Language) [!INCLUDE[tsql](../../includes/tsql-md.md)] et d'événements Trace SQL, par l'envoi d'informations relatives à ces événements à un service [!INCLUDE[ssSB](../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cf84-104">Event notifications execute in response to a variety of [!INCLUDE[tsql](../../includes/tsql-md.md)] data definition language (DDL) statements and SQL Trace events by sending information about these events to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] service.</span></span>  
  
 <span data-ttu-id="9cf84-105">Les notifications d'événements peuvent être utilisées pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9cf84-105">Event notifications can be used to do the following:</span></span>  
  
-   <span data-ttu-id="9cf84-106">enregistrer dans un journal et examiner les modifications ou l'activité de la base de données ;</span><span class="sxs-lookup"><span data-stu-id="9cf84-106">Log and review changes or activity occurring on the database.</span></span>  
  
-   <span data-ttu-id="9cf84-107">réaliser une action en réponse à un événement de manière asynchrone plutôt que synchrone.</span><span class="sxs-lookup"><span data-stu-id="9cf84-107">Perform an action in response to an event in an asynchronous instead of synchronous manner.</span></span>  
  
 <span data-ttu-id="9cf84-108">Les notifications d'événements peuvent constituer une alternative de programmation aux déclencheurs DDL et à Trace SQL.</span><span class="sxs-lookup"><span data-stu-id="9cf84-108">Event notifications can offer a programming alternative to DDL triggers and SQL Trace.</span></span>  
  
## <a name="event-notifications-benefits"></a><span data-ttu-id="9cf84-109">Avantages des notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-109">Event Notifications Benefits</span></span>  
 <span data-ttu-id="9cf84-110">Elles sont exécutées de manière asynchrone, en dehors de la portée d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="9cf84-110">Event notifications run asynchronously, outside the scope of a transaction.</span></span> <span data-ttu-id="9cf84-111">Ainsi, contrairement aux déclencheurs DDL, les notifications d'événements peuvent être utilisées dans une application de base de données pour répondre à des événements sans recourir aux ressources définies par la transaction immédiate.</span><span class="sxs-lookup"><span data-stu-id="9cf84-111">Therefore, unlike DDL triggers, event notifications can be used inside a database application to respond to events without using any resources defined by the immediate transaction.</span></span>  
  
 <span data-ttu-id="9cf84-112">Contrairement à Trace SQL, les notifications d'événements peuvent être utilisées pour exécuter une action dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en réponse à un événement Trace SQL.</span><span class="sxs-lookup"><span data-stu-id="9cf84-112">Unlike SQL Trace, event notifications can be used to perform an action inside an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in response to a SQL Trace event.</span></span>  
  
 <span data-ttu-id="9cf84-113">Les données des événements peuvent être utilisées par les applications exécutées avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour en suivre la progression et prendre des décisions.</span><span class="sxs-lookup"><span data-stu-id="9cf84-113">Event data can be used by applications that are running together with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to track progress and make decisions.</span></span> <span data-ttu-id="9cf84-114">Par exemple, la notification d'événement suivante envoie un avis à un certain service chaque fois qu'une instruction `ALTER TABLE` est émise dans l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cf84-114">For example, the following event notification sends a notice to a certain service every time an `ALTER TABLE` statement is issued in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE '//Adventure-Works.com/ArchiveService' ,  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
```  
  
## <a name="event-notifications-concepts"></a><span data-ttu-id="9cf84-115">Concepts de notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-115">Event Notifications Concepts</span></span>  
 <span data-ttu-id="9cf84-116">Lorsqu'une notification d'événement est créée, une ou plusieurs conversations [!INCLUDE[ssSB](../../includes/sssb-md.md)] entre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le service cible spécifié sont ouvertes.</span><span class="sxs-lookup"><span data-stu-id="9cf84-116">When an event notification is created, one or more [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversations between an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the target service you specify are opened.</span></span> <span data-ttu-id="9cf84-117">Les conversations restent en général ouvertes tant que la notification d'événement existe en tant qu'objet sur l'instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="9cf84-117">The conversations typically remain open as long as the event notification exists as an object on the server instance.</span></span> <span data-ttu-id="9cf84-118">Dans certains cas d'erreur, les conversations peuvent être interrompues avant la suppression de la notification d'événement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-118">In some error cases the conversations can close before the event notification is dropped.</span></span> <span data-ttu-id="9cf84-119">Ces conversations ne sont jamais partagées entre les notifications d'événements.</span><span class="sxs-lookup"><span data-stu-id="9cf84-119">These conversations are never shared between event notifications.</span></span> <span data-ttu-id="9cf84-120">Toutes les notifications d'événements possèdent leurs propres conversations exclusives.</span><span class="sxs-lookup"><span data-stu-id="9cf84-120">Every event notification has its own exclusive conversations.</span></span> <span data-ttu-id="9cf84-121">L'interruption d'une conversation interdit explicitement au service cible de recevoir davantage de messages ; en outre, la conversation ne rouvrira pas au déclenchement suivant de la notification d'événement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-121">Ending a conversation explicitly prevents the target service from receiving more messages, and the conversation will not reopen the next time the event notification fires.</span></span>  
  
 <span data-ttu-id="9cf84-122">Les informations sur l'événement sont livrées au service [!INCLUDE[ssSB](../../includes/sssb-md.md)] sous forme de variable de type `xml` qui fournit des informations sur l'heure à laquelle un événement se produit, l'objet de base de données concerné, l'instruction par lot [!INCLUDE[tsql](../../includes/tsql-md.md)] impliquée ainsi que d'autres informations.</span><span class="sxs-lookup"><span data-stu-id="9cf84-122">Event information is delivered to the [!INCLUDE[ssSB](../../includes/sssb-md.md)] service as a variable of type `xml` that provides information about when an event occurs, about the database object affected, the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch statement involved, and other information.</span></span> <span data-ttu-id="9cf84-123">Pour plus d’informations sur le schéma XML produit par les notifications d’événements, consultez [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="9cf84-123">For more information about the XML schema produced by event notifications, see [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).</span></span>  
  
### <a name="event-notifications-vs-triggers"></a><span data-ttu-id="9cf84-124">Notifications d'événements et Déclencheurs</span><span class="sxs-lookup"><span data-stu-id="9cf84-124">Event Notifications vs. Triggers</span></span>  
 <span data-ttu-id="9cf84-125">Le tableau suivant répertorie les similitudes et les différences entre les déclencheurs et les notifications d'événements.</span><span class="sxs-lookup"><span data-stu-id="9cf84-125">The following table compares and contrasts triggers and event notifications.</span></span>  
  
|<span data-ttu-id="9cf84-126">Déclencheurs</span><span class="sxs-lookup"><span data-stu-id="9cf84-126">Triggers</span></span>|<span data-ttu-id="9cf84-127">Notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-127">Event Notifications</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="9cf84-128">Les déclencheurs DML répondent aux événements DML (Data Manipulation Language, ou langage de manipulation de données).</span><span class="sxs-lookup"><span data-stu-id="9cf84-128">DML triggers respond to data manipulation language (DML) events.</span></span> <span data-ttu-id="9cf84-129">Les déclencheurs DDL répondent aux événements DDL (Data Definition Language, ou langage de définition de données).</span><span class="sxs-lookup"><span data-stu-id="9cf84-129">DDL triggers respond to data definition language (DDL) events.</span></span>|<span data-ttu-id="9cf84-130">Les notifications d'événements répondent aux événements DDL et à un sous-ensemble d'événements de Trace SQL.</span><span class="sxs-lookup"><span data-stu-id="9cf84-130">Event notifications respond to DDL events and a subset of SQL trace events.</span></span>|  
|<span data-ttu-id="9cf84-131">Les déclencheurs peuvent exécuter Transact-SQL ou le code managé CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9cf84-131">Triggers can run Transact-SQL or common language runtime (CLR) managed code.</span></span>|<span data-ttu-id="9cf84-132">Les notifications d'événements n'exécutent aucun code.</span><span class="sxs-lookup"><span data-stu-id="9cf84-132">Event notifications do not run code.</span></span> <span data-ttu-id="9cf84-133">Au lieu de cela, ils envoient des `xml` messages à un Service Service Broker.</span><span class="sxs-lookup"><span data-stu-id="9cf84-133">Instead, they send `xml` messages to a Service Broker service.</span></span>|  
|<span data-ttu-id="9cf84-134">Les déclencheurs sont traités de manière synchrone, dans le cadre des transactions qui provoquent leur déclenchement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-134">Triggers are processed synchronously, within the scope of the transactions that cause them to fire.</span></span>|<span data-ttu-id="9cf84-135">Les notifications d'événements peuvent être traitées de manière synchrone, et elles ne sont pas exécutées dans le cadre des transactions qui provoquent leur déclenchement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-135">Event notifications may be processed asynchronously and do not run in the scope of the transactions that cause them to fire.</span></span>|  
|<span data-ttu-id="9cf84-136">Le consommateur d'un déclencheur est étroitement lié à l'événement qui provoque son déclenchement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-136">The consumer of a trigger is tightly coupled with the event that causes it to fire.</span></span>|<span data-ttu-id="9cf84-137">Le consommateur d'une notification d'événement est dissocié de l'événement qui provoque son déclenchement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-137">The consumer of an event notification is decoupled from the event that causes it to fire.</span></span>|  
|<span data-ttu-id="9cf84-138">Les déclencheurs doivent être traités sur le serveur local.</span><span class="sxs-lookup"><span data-stu-id="9cf84-138">Triggers must be processed on the local server.</span></span>|<span data-ttu-id="9cf84-139">Les notifications d'événements peuvent être traitées sur un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="9cf84-139">Event notifications can be processed on a remote server.</span></span>|  
|<span data-ttu-id="9cf84-140">Les déclencheurs peuvent être restaurés.</span><span class="sxs-lookup"><span data-stu-id="9cf84-140">Triggers can be rolled back.</span></span>|<span data-ttu-id="9cf84-141">Les notifications d'événements ne peuvent pas être restaurées.</span><span class="sxs-lookup"><span data-stu-id="9cf84-141">Event notifications cannot be rolled back.</span></span>|  
|<span data-ttu-id="9cf84-142">Les noms de déclencheurs DML ont une portée de schéma.</span><span class="sxs-lookup"><span data-stu-id="9cf84-142">DML trigger names are schema-scoped.</span></span> <span data-ttu-id="9cf84-143">Les noms de déclencheurs DDL sont limités au niveau de la base de données ou du serveur.</span><span class="sxs-lookup"><span data-stu-id="9cf84-143">DDL trigger names are database-scoped or server-scoped.</span></span>|<span data-ttu-id="9cf84-144">Les noms de notifications d'événements sont limités par le serveur ou la base de données.</span><span class="sxs-lookup"><span data-stu-id="9cf84-144">Event notification names are scoped by the server or database.</span></span> <span data-ttu-id="9cf84-145">Les notifications d'événements sur un événement QUEUE_ACTIVATION sont limitées à une file d'attente spécifique.</span><span class="sxs-lookup"><span data-stu-id="9cf84-145">Event notifications on a QUEUE_ACTIVATION event are scoped to a specific queue.</span></span>|  
|<span data-ttu-id="9cf84-146">Les déclencheurs DML sont détenus par le propriétaire des tables sur lesquelles ils sont appliqués.</span><span class="sxs-lookup"><span data-stu-id="9cf84-146">DML triggers are owned by the same owner as the tables on which they are applied.</span></span>|<span data-ttu-id="9cf84-147">Le propriétaire d'une notification d'événements sur une file d'attente peut être différent de celui de l'objet auquel la notification est appliquée.</span><span class="sxs-lookup"><span data-stu-id="9cf84-147">The owner of an event notification on a queue may have a different owner than the object on which it is applied.</span></span>|  
|<span data-ttu-id="9cf84-148">Les déclencheurs prennent en charge la clause EXECUTE AS.</span><span class="sxs-lookup"><span data-stu-id="9cf84-148">Triggers support the EXECUTE AS clause.</span></span>|<span data-ttu-id="9cf84-149">Les notifications d'événements ne prennent pas en charge la clause EXECUTE AS.</span><span class="sxs-lookup"><span data-stu-id="9cf84-149">Event notifications do not support the EXECUTE AS clause.</span></span>|  
|<span data-ttu-id="9cf84-150">Les informations d’événement de déclencheur DDL peuvent être capturées à l’aide de la fonction EVENTDATA, qui retourne un `xml` type de données.</span><span class="sxs-lookup"><span data-stu-id="9cf84-150">DDL trigger event information can be captured using the EVENTDATA function, which returns an `xml` data type.</span></span>|<span data-ttu-id="9cf84-151">Les notifications d’événements envoient des `xml` informations d’événement à un Service Service Broker.</span><span class="sxs-lookup"><span data-stu-id="9cf84-151">Event notifications send `xml` event information to a Service Broker service.</span></span> <span data-ttu-id="9cf84-152">Les informations sont mises en forme dans le même schéma que celui de la fonction EVENTDATA.</span><span class="sxs-lookup"><span data-stu-id="9cf84-152">The information is formatted to the same schema as that of the EVENTDATA function.</span></span>|  
|<span data-ttu-id="9cf84-153">Les métadonnées concernant les déclencheurs se trouvent dans les affichages catalogue **sys.triggers** et **sys.server_triggers** .</span><span class="sxs-lookup"><span data-stu-id="9cf84-153">Metadata about triggers is found in the **sys.triggers** and **sys.server_triggers** catalog views.</span></span>|<span data-ttu-id="9cf84-154">Les métadonnées concernant les notifications d’événements se trouvent dans les affichages catalogue **sys.event_notifications** et **sys.server_event_notifications** .</span><span class="sxs-lookup"><span data-stu-id="9cf84-154">Metadata about event notifications is found in the **sys.event_notifications** and **sys.server_event_notifications** catalog views.</span></span>|  
  
### <a name="event-notifications-vs-sql-trace"></a><span data-ttu-id="9cf84-155">Notifications d'événements et Trace SQL</span><span class="sxs-lookup"><span data-stu-id="9cf84-155">Event Notifications vs. SQL Trace</span></span>  
 <span data-ttu-id="9cf84-156">Le tableau suivant répertorie les similitudes et les différences dans l'utilisation des notifications d'événements et de Trace SQL dans le cadre de la surveillance des événements de serveur.</span><span class="sxs-lookup"><span data-stu-id="9cf84-156">The following table compares and contrasts using event notifications and SQL Trace for monitoring server events.</span></span>  
  
|<span data-ttu-id="9cf84-157">Trace SQL</span><span class="sxs-lookup"><span data-stu-id="9cf84-157">SQL Trace</span></span>|<span data-ttu-id="9cf84-158">Notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-158">Event Notifications</span></span>|  
|---------------|-------------------------|  
|<span data-ttu-id="9cf84-159">Trace SQL n'engendre aucun surcroît d'utilisation de temps système lié aux transactions.</span><span class="sxs-lookup"><span data-stu-id="9cf84-159">SQL Trace generates no performance overhead associated with transactions.</span></span> <span data-ttu-id="9cf84-160">L'empaquetage des données est efficace.</span><span class="sxs-lookup"><span data-stu-id="9cf84-160">Packaging of data is efficient.</span></span>|<span data-ttu-id="9cf84-161">Les ressources système sont sollicitées davantage lors de la création des données d'événements au format XML et de l'envoi des notifications d'événements.</span><span class="sxs-lookup"><span data-stu-id="9cf84-161">There is performance overhead associated with creating the XML-formatted event data and sending the event notification.</span></span>|  
|<span data-ttu-id="9cf84-162">Trace SQL peut surveiller toutes les classes d'événements de trace.</span><span class="sxs-lookup"><span data-stu-id="9cf84-162">SQL Trace can monitor any trace event class.</span></span>|<span data-ttu-id="9cf84-163">Les notifications d'événements peuvent surveiller un sous-ensemble des classes d'événements de trace ainsi que tous les événements DDL (Data Definition Language).</span><span class="sxs-lookup"><span data-stu-id="9cf84-163">Event notifications can monitor a subset of trace event classes and also all data definition language (DDL) events.</span></span>|  
|<span data-ttu-id="9cf84-164">Vous pouvez personnaliser les colonnes de données à générer dans l'événement de trace.</span><span class="sxs-lookup"><span data-stu-id="9cf84-164">You can customize which data columns to generate in a trace event.</span></span>|<span data-ttu-id="9cf84-165">Le schéma des données d'événements au format XML renvoyées par les notifications d'événements est fixe.</span><span class="sxs-lookup"><span data-stu-id="9cf84-165">The schema of the XML-formatted event data returned by event notifications is fixed.</span></span>|  
|<span data-ttu-id="9cf84-166">Les événements de trace générés par DDL sont toujours générés, même si l'instruction DDL est annulée.</span><span class="sxs-lookup"><span data-stu-id="9cf84-166">Trace events generated by DDL are always generated, regardless of whether the DDL statement is rolled back.</span></span>|<span data-ttu-id="9cf84-167">Les notifications d'événements ne se déclenchent pas si l'événement de l'instruction DDL correspondante est annulé.</span><span class="sxs-lookup"><span data-stu-id="9cf84-167">Event notifications do not fire if the event in the corresponding DDL statement is rolled back.</span></span>|  
|<span data-ttu-id="9cf84-168">La gestion du flux intermédiaire des données d'événement de trace implique le remplissage et la gestion de fichiers ou de tables de trace.</span><span class="sxs-lookup"><span data-stu-id="9cf84-168">Managing the intermediate flow of trace event data involves populating and managing trace files or trace tables.</span></span>|<span data-ttu-id="9cf84-169">La gestion intermédiaire des données de notification d'événements est accomplie automatiquement via les files d'attente de Service Broker.</span><span class="sxs-lookup"><span data-stu-id="9cf84-169">Intermediate management of event notification data is accomplished automatically through Service Broker queues.</span></span>|  
|<span data-ttu-id="9cf84-170">Les traces doivent être redémarrées à chaque démarrage du serveur.</span><span class="sxs-lookup"><span data-stu-id="9cf84-170">Traces must be restarted every time the server restarts.</span></span>|<span data-ttu-id="9cf84-171">Après avoir été inscrites, les notifications d'événements perdurent au fil des cycles serveur et sont incluses dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="9cf84-171">After being registered, event notifications persist across server cycles and are transacted.</span></span>|  
|<span data-ttu-id="9cf84-172">Après avoir été lancé, le déclenchement des traces ne peut plus être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="9cf84-172">After being initiated, the firing of traces cannot be controlled.</span></span> <span data-ttu-id="9cf84-173">Les options d'heure d'arrêt et de filtrage permettent de spécifier l'heure de lancement.</span><span class="sxs-lookup"><span data-stu-id="9cf84-173">Stop times and filter times can be used to specify when they initiate.</span></span> <span data-ttu-id="9cf84-174">Les traces sont accessibles par interrogation du fichier de trace correspondant.</span><span class="sxs-lookup"><span data-stu-id="9cf84-174">Traces are accessed by polling the corresponding trace file.</span></span>|<span data-ttu-id="9cf84-175">Une notification d'événements peut être contrôlée en exécutant l'instruction WAITFOR sur la file d'attente qui reçoit le message généré par la notification.</span><span class="sxs-lookup"><span data-stu-id="9cf84-175">Event notifications can be controlled by using the WAITFOR statement against the queue that receives the message generated by the event notification.</span></span> <span data-ttu-id="9cf84-176">Elle est accessible par interrogation de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9cf84-176">They can be accessed by polling the queue.</span></span>|  
|<span data-ttu-id="9cf84-177">ALTER TRACE est l'autorisation minimale requise pour créer une trace.</span><span class="sxs-lookup"><span data-stu-id="9cf84-177">ALTER TRACE is the least permission that is required to create a trace.</span></span> <span data-ttu-id="9cf84-178">Une autorisation permettant de créer un fichier de trace sur l'ordinateur est également nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9cf84-178">Permission is also required to create a trace file on the corresponding computer.</span></span>|<span data-ttu-id="9cf84-179">L'autorisation minimale dépend du type de notification d'événements créée.</span><span class="sxs-lookup"><span data-stu-id="9cf84-179">Least permission depends on the type of event notification being created.</span></span> <span data-ttu-id="9cf84-180">L'autorisation RECEIVE sur la file d'attente correspondante est également requise.</span><span class="sxs-lookup"><span data-stu-id="9cf84-180">RECEIVE permission is also needed on the corresponding queue.</span></span>|  
|<span data-ttu-id="9cf84-181">Les traces peuvent être reçues à distance.</span><span class="sxs-lookup"><span data-stu-id="9cf84-181">Traces can be received remotely.</span></span>|<span data-ttu-id="9cf84-182">Les notifications d'événements ne peuvent pas être reçues à distance.</span><span class="sxs-lookup"><span data-stu-id="9cf84-182">Event notifications can be received remotely.</span></span>|  
|<span data-ttu-id="9cf84-183">Les événements de trace sont mis en œuvre au moyen de procédures stockées système.</span><span class="sxs-lookup"><span data-stu-id="9cf84-183">Trace events are implemented by using system stored procedures.</span></span>|<span data-ttu-id="9cf84-184">Les notifications d’événements sont implémentées à l’aide d’une combinaison d’instructions [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssSB](../../includes/sssb-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cf84-184">Event notifications are implemented by using a combination of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssSB](../../includes/sssb-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>|  
|<span data-ttu-id="9cf84-185">Les données d’événements de trace sont accessibles par programmation en interrogeant la table de trace correspondante, en analysant le fichier de trace ou au moyen de la classe TraceReader SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects).</span><span class="sxs-lookup"><span data-stu-id="9cf84-185">Trace event data can be accessed programmatically by querying the corresponding trace table, parsing the trace file, or using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) TraceReader Class.</span></span>|<span data-ttu-id="9cf84-186">Les données d'événements sont accessibles par programme en émettant une requête XQuery sur les données d'événements au format XML ou au moyen de classes Event SMO.</span><span class="sxs-lookup"><span data-stu-id="9cf84-186">Event data is accessed programmatically by issuing XQuery against the XML-formatted event data, or by using the SMO Event classes.</span></span>|  
  
## <a name="event-notification-tasks"></a><span data-ttu-id="9cf84-187">Tâches relatives aux notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-187">Event Notification Tasks</span></span>  
  
|<span data-ttu-id="9cf84-188">Tâche</span><span class="sxs-lookup"><span data-stu-id="9cf84-188">Task</span></span>|<span data-ttu-id="9cf84-189">Rubrique</span><span class="sxs-lookup"><span data-stu-id="9cf84-189">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="9cf84-190">Décrit comment créer et implémenter des notifications d'événements.</span><span class="sxs-lookup"><span data-stu-id="9cf84-190">Describes how to create and implement event notifications.</span></span>|[<span data-ttu-id="9cf84-191">Implémenter des notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-191">Implement Event Notifications</span></span>](implement-event-notifications.md)|  
|<span data-ttu-id="9cf84-192">Décrit comment configurer la sécurité du dialogue [!INCLUDE[ssSB](../../includes/sssb-md.md)] pour les notifications d'événements qui envoient des messages à Service Broker sur un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="9cf84-192">Describes how to configure [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog security for event notifications that send messages to a service broker on a remote server.</span></span>|[<span data-ttu-id="9cf84-193">Configurer la sécurité du dialogue pour les notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-193">Configure Dialog Security for Event Notifications</span></span>](configure-dialog-security-for-event-notifications.md)|  
|<span data-ttu-id="9cf84-194">Décrit comment retourner des informations sur les notifications d'événements.</span><span class="sxs-lookup"><span data-stu-id="9cf84-194">Describes how to return information about event notifications.</span></span>|[<span data-ttu-id="9cf84-195">Obtenir des informations concernant les notifications d'événements</span><span class="sxs-lookup"><span data-stu-id="9cf84-195">Get Information About Event Notifications</span></span>](get-information-about-event-notifications.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9cf84-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cf84-196">See Also</span></span>  
 <span data-ttu-id="9cf84-197">[Déclencheurs DDL](../triggers/ddl-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="9cf84-197">[DDL Triggers](../triggers/ddl-triggers.md) </span></span>  
 <span data-ttu-id="9cf84-198">[Déclencheurs DML](../triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="9cf84-198">[DML Triggers](../triggers/dml-triggers.md) </span></span>  
 [<span data-ttu-id="9cf84-199">Trace SQL</span><span class="sxs-lookup"><span data-stu-id="9cf84-199">SQL Trace</span></span>](../sql-trace/sql-trace.md)  
  
  