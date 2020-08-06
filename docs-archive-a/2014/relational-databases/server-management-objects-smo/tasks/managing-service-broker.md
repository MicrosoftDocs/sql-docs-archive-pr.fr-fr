---
title: Gestion des Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce166825bb7adea241bac13defeca1a78b4f29cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695512"
---
# <a name="managing-service-broker"></a><span data-ttu-id="dc32a-102">Gestion de Service Broker</span><span class="sxs-lookup"><span data-stu-id="dc32a-102">Managing Service Broker</span></span>
  <span data-ttu-id="dc32a-103">Dans SMO, les objets [!INCLUDE[ssSB](../../../includes/sssb-md.md)] sont disponibles dans l'espace de noms `Microsoft.SqlServer.Management.Smo.Broker` qui nécessite une référence à Microsoft.SqlServer.Smo.dll.</span><span class="sxs-lookup"><span data-stu-id="dc32a-103">In SMO, the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects are found in the `Microsoft.SqlServer.Management.Smo.Broker` namespace, which requires a reference to the Microsoft.SqlServer.Smo.dll.</span></span> <span data-ttu-id="dc32a-104">Une référence à Microsoft.SqlServer.ServiceBrokerEnum.dll est également requise pour la prise en charge des informations de classe.</span><span class="sxs-lookup"><span data-stu-id="dc32a-104">A reference to the Microsoft.SqlServer.ServiceBrokerEnum.dll is also required for supporting class information.</span></span>  
  
 <span data-ttu-id="dc32a-105">SMO fournit un ensemble d'objets [!INCLUDE[ssSB](../../../includes/sssb-md.md)] qui permettent une gestion par programme (DDL) de l'implémentation de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dc32a-105">SMO provides a set of [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects that permit programmatic management (DDL) of the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation.</span></span> <span data-ttu-id="dc32a-106">Ceci inclut la définition des types de messages, des contrats, des files d'attente et des services.</span><span class="sxs-lookup"><span data-stu-id="dc32a-106">This includes defining the message types, contracts, queues, and services.</span></span> <span data-ttu-id="dc32a-107">SMO n'est pas un outil d'administration conçu pour la manipulation des données ; il ne prend donc pas en charge l'envoi et la réception de messages [!INCLUDE[ssSB](../../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dc32a-107">Because SMO is a management tool that is not intended for data manipulation, sending and receiving [!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages is not supported by SMO.</span></span>  
  
 <span data-ttu-id="dc32a-108">Dans SMO, l'objet <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> est la classe de niveau supérieur sous laquelle toutes les fonctionnalités de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] résident.</span><span class="sxs-lookup"><span data-stu-id="dc32a-108">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> object is the top-level class under which all the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] functionality resides.</span></span> <span data-ttu-id="dc32a-109">[!INCLUDE[ssSB](../../../includes/sssb-md.md)] doit être implémenté pour chaque base de données participant à l'application de messagerie distribuée.</span><span class="sxs-lookup"><span data-stu-id="dc32a-109">A [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation is required for each database that is participating in the distributed messaging application.</span></span> <span data-ttu-id="dc32a-110">Par conséquent, l'objet <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> est un enfant de l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>.</span><span class="sxs-lookup"><span data-stu-id="dc32a-110">Therefore, the <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="dc32a-111">L'objet <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> contient des collections des objets suivants utilisés pour définir l'implémentation de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="dc32a-111">The <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object contains collections of the following objects that are used to define the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation:</span></span>  
  
-   <span data-ttu-id="dc32a-112">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> représentent les types de messages qui définissent le contenu des messages.</span><span class="sxs-lookup"><span data-stu-id="dc32a-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> objects represent message types that define the content of messages.</span></span>  
  
-   <span data-ttu-id="dc32a-113">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> représentent les contrats qui spécifient la direction et le type des messages dans une conversation donnée.</span><span class="sxs-lookup"><span data-stu-id="dc32a-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> objects represent contracts that specify the direction and type of messages in a given conversation.</span></span>  
  
-   <span data-ttu-id="dc32a-114">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> stockent les messages avant envoi et après réception.</span><span class="sxs-lookup"><span data-stu-id="dc32a-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> objects store messages prior to sending and after they are received.</span></span> <span data-ttu-id="dc32a-115">Ils garantissent une communication asynchrone entre les services et offrent d'autres avantages, tels que le verrouillage automatique des messages dans le même groupe de conversations.</span><span class="sxs-lookup"><span data-stu-id="dc32a-115">They provide asynchronous communication between services, as well as other benefits, such as automatically locking messages in the same conversation group.</span></span>  
  
-   <span data-ttu-id="dc32a-116">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> représentent les services [!INCLUDE[ssSB](../../../includes/sssb-md.md)], qui correspondent aux points de terminaison adressables pour des conversations.</span><span class="sxs-lookup"><span data-stu-id="dc32a-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> objects represent [!INCLUDE[ssSB](../../../includes/sssb-md.md)] services, which are the addressable endpoints for conversations.</span></span> <span data-ttu-id="dc32a-117">Les messages [!INCLUDE[ssSB](../../../includes/sssb-md.md)] sont envoyés d'un service à l'autre.</span><span class="sxs-lookup"><span data-stu-id="dc32a-117">[!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages are sent from one service to another service.</span></span> <span data-ttu-id="dc32a-118">Un service spécifie une file d'attente pour la conservation des messages et précise les contrats pour lesquels le service peut être la cible.</span><span class="sxs-lookup"><span data-stu-id="dc32a-118">A service specifies a queue to hold messages, and specifies the contracts for which the service can be the target.</span></span>  
  
-   <span data-ttu-id="dc32a-119">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> représentent les paramètres que [!INCLUDE[ssSB](../../../includes/sssb-md.md)] utilise pour la sécurité et l'authentification lorsqu'il communique avec un service distant.</span><span class="sxs-lookup"><span data-stu-id="dc32a-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> objects represent the settings that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] uses for security and authentication when communicating with a remote service.</span></span>  
  
-   <span data-ttu-id="dc32a-120">Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> désignent un itinéraire [!INCLUDE[ssSB](../../../includes/sssb-md.md)] qui contient les informations d'emplacement du service et de la base de données sur lesquels il est défini.</span><span class="sxs-lookup"><span data-stu-id="dc32a-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> objects represents a [!INCLUDE[ssSB](../../../includes/sssb-md.md)] route, which contains the location information for the service and the database on which it is defined.</span></span> <span data-ttu-id="dc32a-121">Un itinéraire est requis pour la remise des messages.</span><span class="sxs-lookup"><span data-stu-id="dc32a-121">A route is required for message delivery.</span></span> <span data-ttu-id="dc32a-122">Par défaut, chaque base de données contient un itinéraire qui précise l'emplacement en tant qu'instance actuelle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc32a-122">By default, each database contains a route that specifies the location as the current instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc32a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc32a-123">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [<span data-ttu-id="dc32a-124">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="dc32a-124">SQL Server Service Broker</span></span>](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  