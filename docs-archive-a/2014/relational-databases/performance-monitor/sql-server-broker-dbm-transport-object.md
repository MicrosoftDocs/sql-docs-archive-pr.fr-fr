---
title: Objet de transport SQL Server, Broker et DBM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker / DBM Transport object
- SQLServer:Broker/DBM Transport
ms.assetid: eddb60b6-20a9-416c-adf3-4bc1687944fa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d44aa5b316a076f759d65a17f7e15c0a9ede786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612773"
---
# <a name="sql-server-broker-and-dbm-transport-object"></a>SQL Server, Broker et Objet DBM Transport
  L’objet de performance **Broker / DBM Transport** contient des compteurs de performances qui recueillent des informations concernant l’activité réseau relative à Service Broker et à la mise en miroir de bases de données. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
|Compteur SQL Server Broker/DBM Transport|Description|  
|------------------------------------------------|-----------------|  
|**Octets actuels pour les E/S reçues**|Ce compteur donne le nombre d'octets à lire par les opérations de réception de transport en cours d'exécution.|  
|**Octets actuels pour les E/S envoyées**|Ce compteur retrace le nombre d'octets composant les fragments des messages faisant l'objet d'un envoi en cours sur le réseau.|  
|**Fragments de message actuels pour les E/S envoyées**|Ce compteur reprend le nombre total de fragments de message faisant l'objet d'un envoi en cours sur le réseau.|  
|**Fragments de message P1 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 1 envoyés sur le réseau par seconde.|  
|**Fragments de message P2 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 2 envoyés sur le réseau par seconde.|  
|**Fragments de message P3 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 3 envoyés sur le réseau par seconde.|  
|**Fragments de message P4 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 4 envoyés sur le réseau par seconde.|  
|**Fragments de message P5 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 5 envoyés sur le réseau par seconde.|  
|**Fragments de message P6 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 6 envoyés sur le réseau par seconde.|  
|**Fragments de message P7 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 7 envoyés sur le réseau par seconde.|  
|**Fragments de message P8 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 8 envoyés sur le réseau par seconde.|  
|**Fragments de message P9 envoyés/s**|Ce compteur indique le nombre de fragments de message de priorité 9 envoyés sur le réseau par seconde.|  
|**Fragments de message P10 envoyés/s**|Ce compteur désigne le nombre de fragments de message de priorité 10 envoyés sur le réseau par seconde.|  
|**Taille moyenne des fragments de message envoyés**|Ce compteur précise la taille moyenne des fragments de message envoyés sur le réseau.|  
|**Fragments de message envoyés/s**|Ce compteur désigne le nombre de fragments de message de toutes les priorités envoyés sur le réseau par seconde.|  
|**Fragments de message reçus/s**|Ce compteur reprend le nombre de fragments de message reçus sur le réseau par seconde.|  
|**Taille moyenne des fragments de message reçus**|Ce compteur précise la taille moyenne des fragments de message reçus sur le réseau.|  
|**Nombre de connexions ouvertes**|Ce compteur désigne le nombre de connexions réseau que le Service Broker a d'ouvertes.|  
|**Octets en attente pour les E/S reçues**|Ce compteur indique le nombre d'octets contenus dans les fragments de message reçus du réseau mais n'ayant pas encore été placés dans la file d'attente ou ayant été abandonnés.|  
|**Octets en attente pour les E/S envoyées**|Ce compteur reprend le nombre total d'octets dans les fragments de message prêts à être envoyés sur le réseau.|  
|**Fragments de message en attente pour les E/S reçues**|Ce compteur précise le nombre de fragments de message reçus du réseau mais n'ayant pas encore été placés dans la file d'attente ou ayant été abandonnés.|  
|**Fragments de message en attente pour les E/S envoyées**|Ce compteur retrace le nombre total d'octets dans les fragments de message prêts à être envoyés sur le réseau.|  
|**Total des octets d'E/S reçus**|Ce compteur indique le nombre total d'octets reçus sur le réseau par les points de terminaison Service Broker et de mise en miroir de bases de données.|  
|**Octets d'E/S reçus/s**|Ce compteur reprend le nombre total d'octets reçus par seconde sur le réseau par les points de terminaison Service Broker et de mise en miroir de bases de données.|  
|**Longueur moyenne des E/S reçues**|Ce compteur désigne le nombre moyen d'octets pour une opération de réception de transport.|  
|**E/S reçues/s**|Ce compteur indique le nombre d'opérations d'E/S du transport en réception par seconde que la couche Service Broker/DBM transport a effectuées. Il se peut qu'une opération de réception du transport contienne plusieurs fragments de message.|  
|**Total des octets d'E/S envoyés**|Ce compteur indique le nombre total d'octets transmis sur le réseau par les points de terminaison Service Broker et de mise en miroir de bases de données.|  
|**Octets d'E/S envoyés/s**|Ce compteur reprend le nombre total d'octets envoyés par seconde sur le réseau par les points de terminaison Service Broker et de mise en miroir de bases de données.|  
|**Longueur moyenne des E/S envoyées**|Ce compteur précise la taille moyenne en octets des opérations d'envoi de transport. Il se peut qu'une opération d'envoi du transport contienne plusieurs fragments de message.|  
|**E/S envoyées/s**|Ce compteur indique le nombre d'opérations d'E/S du transport en envoi par seconde qui ont été effectuées. Il se peut qu'une opération d'envoi du transport contienne plusieurs fragments de message.|  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_broker_forwarded_messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-forwarded-messages-transact-sql)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
