---
title: Obtenir des informations concernant les notifications d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8d8271b6279910321058d01c7b2f96b1df62bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700913"
---
# <a name="get-information-about-event-notifications"></a>Obtenir des informations concernant les notifications d'événements
  Les affichages catalogue suivants vous permettent d'interroger les métadonnées concernant les notifications d'événements.  
  
 **Pour obtenir des informations sur les notifications d'événements qui ne se produisent pas au niveau du serveur**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Pour afficher les métadonnées sur une notification d’événement dans l’affichage catalogue **sys.event_notifications** créée au niveau de la base de données, vous devez au moins disposer de l’autorisation CONTROL, ALTER, TAKE OWNERSHIP ou VIEW DEFINITION sur la base de données, être propriétaire de la notification d’événement ou disposer de l’autorisation ALTER ANY DATABASE EVENT NOTIFICATION. Pour les notifications d'événements créées sur une file d'attente spécifique, vous devez au moins disposer de l'autorisation CONTROL, ALTER, TAKE OWNERSHIP ou VIEW DEFINITION sur l'objet, être propriétaire de la notification d'événement ou disposer de l'autorisation ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Pour obtenir des informations sur les notifications d'événements qui se produisent au niveau du serveur**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Vous devez au moins disposer de l’autorisation CONTROL ou VIEW ANY DEFINITION sur le serveur, être la connexion ou le propriétaire de la notification d’événement ou disposer de l’autorisation ALTER ANY EVENT NOTIFICATION pour afficher les métadonnées concernant toute notification d’événement dans **sys.server_event_notifications**.  
  
 **Pour obtenir des informations sur tous les événements pouvant déclencher des notifications**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Cette vue de catalogue ne retourne pas de groupes d'événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Notifications d'événements](event-notifications.md)  
  
  
