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
# <a name="managing-service-broker"></a>Gestion de Service Broker
  Dans SMO, les objets [!INCLUDE[ssSB](../../../includes/sssb-md.md)] sont disponibles dans l'espace de noms `Microsoft.SqlServer.Management.Smo.Broker` qui nécessite une référence à Microsoft.SqlServer.Smo.dll. Une référence à Microsoft.SqlServer.ServiceBrokerEnum.dll est également requise pour la prise en charge des informations de classe.  
  
 SMO fournit un ensemble d'objets [!INCLUDE[ssSB](../../../includes/sssb-md.md)] qui permettent une gestion par programme (DDL) de l'implémentation de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] . Ceci inclut la définition des types de messages, des contrats, des files d'attente et des services. SMO n'est pas un outil d'administration conçu pour la manipulation des données ; il ne prend donc pas en charge l'envoi et la réception de messages [!INCLUDE[ssSB](../../../includes/sssb-md.md)] .  
  
 Dans SMO, l'objet <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> est la classe de niveau supérieur sous laquelle toutes les fonctionnalités de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] résident. [!INCLUDE[ssSB](../../../includes/sssb-md.md)] doit être implémenté pour chaque base de données participant à l'application de messagerie distribuée. Par conséquent, l'objet <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> est un enfant de l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> contient des collections des objets suivants utilisés pour définir l'implémentation de [!INCLUDE[ssSB](../../../includes/sssb-md.md)] :  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> représentent les types de messages qui définissent le contenu des messages.  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> représentent les contrats qui spécifient la direction et le type des messages dans une conversation donnée.  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> stockent les messages avant envoi et après réception. Ils garantissent une communication asynchrone entre les services et offrent d'autres avantages, tels que le verrouillage automatique des messages dans le même groupe de conversations.  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> représentent les services [!INCLUDE[ssSB](../../../includes/sssb-md.md)], qui correspondent aux points de terminaison adressables pour des conversations. Les messages [!INCLUDE[ssSB](../../../includes/sssb-md.md)] sont envoyés d'un service à l'autre. Un service spécifie une file d'attente pour la conservation des messages et précise les contrats pour lesquels le service peut être la cible.  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> représentent les paramètres que [!INCLUDE[ssSB](../../../includes/sssb-md.md)] utilise pour la sécurité et l'authentification lorsqu'il communique avec un service distant.  
  
-   Les objets <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> désignent un itinéraire [!INCLUDE[ssSB](../../../includes/sssb-md.md)] qui contient les informations d'emplacement du service et de la base de données sur lesquels il est défini. Un itinéraire est requis pour la remise des messages. Par défaut, chaque base de données contient un itinéraire qui précise l'emplacement en tant qu'instance actuelle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [SQL Server Service Broker](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
