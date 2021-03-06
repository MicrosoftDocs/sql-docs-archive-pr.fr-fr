---
title: Gérer les événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ca6d56440b06d285cbb90f8d92325d59a452c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695259"
---
# <a name="manage-events"></a>Gérer les événements
  Vous pouvez transférer à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tous les messages d'événements qui correspondent à un niveau de gravité d'erreur ou le dépassent. Cette fonction est qualifiée de *transfert d'événements*. Le serveur de transfert est un serveur dédié qui peut également être un serveur maître. Le transfert d'événements permet de centraliser la gestion des alertes pour un groupe de serveurs, réduisant ainsi la charge de travail sur les serveurs à utilisation intense.  
  
 Lorsqu'un serveur reçoit des événements pour un groupe d'autres serveurs, le serveur qui reçoit les événements est qualifié de *serveur de gestion des alertes*. Dans un environnement multiserveur, il est recommandé de désigner le serveur maître comme serveur de gestion des alertes.  
  
## <a name="advantages-of-using-an-alerts-management-server"></a>Avantages de l'utilisation du serveur de gestion des alertes  
 Les avantages liés à la désignation d'un serveur de gestion des alertes sont les suivants :  
  
-   **Centralisation**. Il est possible d'effectuer un contrôle centralisé et une vue consolidée des événements de plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un seul serveur.  
  
-   **Extensibilité**. De nombreux serveurs physiques peuvent être administrés comme un serveur logique unique. En fonction des besoins, vous pouvez ajouter et supprimer des serveurs dans ce groupe de serveurs physiques.  
  
-   **Efficacité**. Le temps de configuration est réduit car vous ne devez définir les alertes et les opérateurs qu'une seule fois.  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a>Inconvénients de l'utilisation du serveur de gestion des alertes  
 Les inconvénients liés à la désignation d'un serveur de gestion des alertes sont les suivants :  
  
-   **Augmentation du trafic**. Le transfert d'événements à un serveur de gestion des alertes peut augmenter le trafic réseau. Cette augmentation peut être modérée en limitant le transfert d'événements aux événements qui se situent au-dessus d'un niveau de gravité désigné.  
  
-   **Point de défaillance unique**. Si le serveur de gestion des alertes se déconnecte, aucune alerte n'est émise pour aucun événement sur le groupe de serveurs géré.  
  
-   **Charge du serveur**. La gestion des alertes des événements transférés provoque une augmentation de la charge de traitement sur le serveur de gestion des alertes.  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a>Directives concernant l'utilisation d'un serveur de gestion des alertes  
 Lors de la configuration d'un serveur de gestion des alertes, procédez comme suit :  
  
-   Afin de recevoir les événements transférés, le serveur de gestion des alertes doit être une instance par défaut de SQL Server.  
  
-   Évitez d'exécuter des applications critiques ou qui nécessitent une utilisation intensive sur le serveur de gestion des alertes.  
  
-   Planifiez avec soin le trafic réseau impliqué dans la configuration de plusieurs serveurs pour partager le même serveur de gestion des alertes. En cas d'encombrement, réduisez le nombre de serveurs utilisant un serveur particulier de gestion des alertes.  
  
     Les serveurs inscrits dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] constituent la liste des serveurs disponibles devant être choisis par ce serveur comme serveur de transfert des alertes.  
  
-   Définissez sur l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les alertes qui nécessitent une réponse serveur spécifique, au lieu de transférer les alertes aux serveurs de gestion des alertes.  
  
     Le serveur de gestion des alertes considère tous les serveurs qui lui transfèrent des événements comme un ensemble logique. Par exemple, un serveur de gestion des alertes répond de la même façon à un événement 605 émanant du serveur A ou du serveur B.  
  
-   Après avoir configuré votre système d'alerte, vérifiez régulièrement la présence d'événements de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Microsoft Windows.  
  
     Les conditions d'échec rencontrées par le moteur d'alertes sont consignées dans le journal des applications Windows local avec le nom source « Agent SQL Server ». Par exemple, si l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas envoyer par courrier électronique une notification telle qu'elle a été définie, un événement est consigné dans le journal des applications.  
  
 Si une alerte définie localement est désactivée et si un événement qui aurait dû déclencher l'alerte se produit, l'événement est transféré au serveur de gestion des alertes (s'il remplit la condition de transfert d'alerte). Ce transfert permet la mise en fonction ou non de priorités locales (alertes définies localement qui sont également définies sur le serveur de gestion des alertes) sur le site local, selon les besoins de l'utilisateur. Vous pouvez également demander que les événements soient transférés, même s'ils sont gérés par des alertes locales.  
  
 Les tâches suivantes sont courantes pour la gestion des événements dans un environnement multiserveur :  
  
 **Pour désigner un serveur de gestion des alertes**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
 **Pour définir la réponse à une alerte**  
  
-   [SQL Server Management Studio](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a>Exécution des travaux déclenchés par un événement  
 Vous pouvez définir un travail à exécuter en réponse à une alerte. Par exemple, vous pouvez exécuter un travail qui corrige un problème détecté par l'alerte ou approfondit son diagnostic.  
  
> [!NOTE]  
>  Un travail pouvant déclencher un événement, veillez à ne pas créer de boucle récursive de travail d'alerte.  
  
## <a name="see-also"></a>Voir aussi  
 [Messagessys.sys&#40;&#41;Transact-SQL](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  
