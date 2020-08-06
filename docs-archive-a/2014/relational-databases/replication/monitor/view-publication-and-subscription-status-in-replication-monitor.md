---
title: Afficher l’état des publications et des abonnements dans le Moniteur de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f1f714e18a961546a4e5a7f6709beca8d525800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709172"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Afficher l'état des publications et des abonnements dans le Moniteur de réplication
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] moniteur de réplication affiche des informations d’État pour les publications et les abonnements :  
  
-   L'état d'une publication est déterminé par l'état de la priorité la plus élevée de ses abonnements. Par exemple, si un abonnement à une publication comporte une erreur et qu'un autre présente un problème de performances, un état d'erreur est affiché pour la publication.  
  
-   L'état d'une publication est déterminé par l'état des agents qui servent l'abonnement. Pour la réplication de fusion, il s'agit de l'Agent de fusion. Pour la réplication transactionnelle, il s'agit de l'Agent de lecture du journal ou de l'Agent de distribution (l'état de la priorité la plus élevée est affiché ; l'état peut également être déterminé par l'Agent de lecture de la file d'attente en cas d'utilisation d'abonnements de mise à jour en attente). Pour la réplication d'instantané, il s'agit de l'Agent d'instantané ou de l'Agent de distribution (l'état de priorité la plus élevée est affiché).  
  
 Les tableaux présentés dans les sections suivantes répertorient les valeurs d'état possibles pour les publications et les abonnements. Trois valeurs d'état sont affichées uniquement si un seuil est atteint ou dépassé :  
  
-   Expiration de l'abonnement  
  
     Cette valeur d'état s'applique à tous les types de réplication. Pour plus d’informations, voir [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Critique pour les performances  
  
     Cette valeur d'état s'applique à la réplication transactionnelle et à la réplication de fusion. Pour plus d’informations, consultez [Analyser les performances avec le Moniteur de réplication](monitor-performance-with-replication-monitor.md).  
  
-   Fusion longue  
  
     Cette valeur d'état s'applique à la réplication de fusion. Pour plus d’informations, consultez [Analyser les performances avec le Moniteur de réplication](monitor-performance-with-replication-monitor.md).  
  
 Outre l'état des publications et des abonnements, la réplication de fusion fournit des statistiques au niveau de l'article qui donnent des informations détaillées sur : la durée d'achèvement d'une phase de fusion, le temps passé pour traiter un article donné, le type de connexion utilisé par un Abonné et bien d'autres informations encore. Les statistiques sont affichées dans la fenêtre de l'Agent de fusion dans le moniteur de réplication. La réplication d'instantané et la réplication transactionnelle fournissent des informations détaillées sur le traitement de l'Agent de distribution.  
  
 **Pour afficher l'état des publications et des abonnements**  
  
-   Moniteur de réplication : [afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](view-information-and-perform-tasks-replication-monitor.md).
  
  
## <a name="publication-status-values"></a>Valeurs d'état des publications  
 Le tableau suivant montre les valeurs d'état des publications et leurs icônes correspondantes dans l'ordre de la priorité.  
  
|Statut|Icône|  
|------------|----------|  
|Error|![Icône d’IU : erreur](../media/repl-icon-error.gif "Icône d’IU : erreur")|  
|Critique pour les performances|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d’IU : nouvelle tentative de l’agent de réplication](../media/repl-icon-retry.gif "Icône d’IU : nouvelle tentative de l’agent de réplication")|  
|OK|aucun|  
  
## <a name="subscription-status-values"></a>Valeurs d'état des abonnements  
 Les tableaux suivants montrent les valeurs d'état des abonnements et leurs icônes correspondantes dans l'ordre de la priorité. Un abonnement peut avoir deux états en même temps (par exemple, **Expire bientôt/Expiré** et **Nouvelle tentative de la commande qui a échoué**) ; l'état de haute priorité est affiché.  
  
 Les valeurs d'état **Critique pour les performances**, **Expire bientôt/Expiré**et **Non initialisé** sont des avertissements. Lorsqu'un avertissement est affiché, le moniteur de réplication indique également si un agent est en cours d'exécution. Par exemple, l'état peut être **En cours d'exécution, Critique pour les performances**.  
  
### <a name="transactional-subscriptions"></a>Abonnements transactionnels  
  
|Statut|Icône|  
|------------|----------|  
|Error|![Icône d’IU : erreur](../media/repl-icon-error.gif "Icône d’IU : erreur")|  
|Critique pour les performances|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Expire bientôt/Expiré|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Abonnement non initialisé|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d’IU : nouvelle tentative de l’agent de réplication](../media/repl-icon-retry.gif "Icône d’IU : nouvelle tentative de l’agent de réplication")|  
|Non exécuté|![Icône d’IU : agent de réplication arrêté](../media/repl-icon-stopped.gif "Icône d’IU : agent de réplication arrêté")|  
|Exécution en cours|![Icône d’IU : agent de réplication en cours d’exécution](../media/repl-icon-running.gif "Icône d’IU : agent de réplication en cours d’exécution")|  
  
### <a name="merge-subscriptions"></a>Abonnements de fusion  
  
|Statut|Icône|  
|------------|----------|  
|Error|![Icône d’IU : erreur](../media/repl-icon-error.gif "Icône d’IU : erreur")|  
|Critique pour les performances|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Fusion longue|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Expire bientôt/Expiré|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Abonnement non initialisé|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d’IU : nouvelle tentative de l’agent de réplication](../media/repl-icon-retry.gif "Icône d’IU : nouvelle tentative de l’agent de réplication")|  
|Synchronisation|![Icône d’IU : agent de réplication en cours d’exécution](../media/repl-icon-running.gif "Icône d’IU : agent de réplication en cours d’exécution")|  
|Sans synchronisation|![Icône d’IU : agent de réplication arrêté](../media/repl-icon-stopped.gif "Icône d’IU : agent de réplication arrêté")|  
  
### <a name="snapshot-subscriptions"></a>Abonnements d'instantanés  
  
|Statut|Icône|  
|------------|----------|  
|Error|![Icône d’IU : erreur](../media/repl-icon-error.gif "Icône d’IU : erreur")|  
|Expire bientôt/Expiré|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Abonnement non initialisé|![Icône d’IU : avertissement](../media/repl-icon-warn.gif "Icône d’IU : avertissement")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d’IU : nouvelle tentative de l’agent de réplication](../media/repl-icon-retry.gif "Icône d’IU : nouvelle tentative de l’agent de réplication")|  
|Synchronisation|![Icône d’IU : agent de réplication en cours d’exécution](../media/repl-icon-running.gif "Icône d’IU : agent de réplication en cours d’exécution")|  
|Sans synchronisation|![Icône d’IU : agent de réplication arrêté](../media/repl-icon-stopped.gif "Icône d’IU : agent de réplication arrêté")|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../monitoring-replication.md)  
  
  
