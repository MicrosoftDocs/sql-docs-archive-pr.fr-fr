---
title: Actualiser des données dans le moniteur de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f097dea21b06540293e9b60b7de9315323b4168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709191"
---
# <a name="refresh-data-in-replication-monitor"></a>Actualiser des données dans le Moniteur de réplication
  Dans le moniteur de réplication, la fenêtre principale et les fenêtres de détails (ces fenêtres lancées à partir de la fenêtre principale) peuvent être actualisées automatiquement ou manuellement. Pour actualiser une fenêtre manuellement, appuyez sur la touche F5. Par défaut, la fenêtre principale est actualisée automatiquement toutes les cinq secondes ; la fréquence peut être personnalisée pour chaque serveur de publication.  
  
 Les données affichées dans le moniteur de réplication sont recherchées dans une mémoire cache. Pour plus d’informations sur les relations entre la mémoire cache et l’actualisation du moniteur de réplication, consultez [Mise en cache, actualisation et performances du moniteur de réplication](caching-refresh-and-replication-monitor-performance.md). Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](start-the-replication-monitor.md).  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>Pour définir les options d'actualisation pour le moniteur de réplication  
  
1.  Cliquez avec le bouton droit dans le volet gauche du moniteur de réplication, puis cliquez sur **Paramètres du serveur de publication**.  
  
2.  Dans la boîte de dialogue **Paramètres du serveur de publication** , définissez les options **Actualisation automatique** et **Fréquence d'actualisation** . Le paramètre **Actualisation automatique** affecte la fenêtre principale du moniteur de réplication. Le paramètre **Fréquence d'actualisation** affecte également toutes les fenêtres de détails qui sont paramétrées pour s'actualiser automatiquement (les modifications du paramètre affectent seulement les fenêtres de détails ouvertes après la modification).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>Pour spécifier qu'une fenêtre de détails doit s'actualiser automatiquement  
  
1.  Ouvrez une fenêtre de détails dans le moniteur de réplication. Par exemple :  
  
    1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
    2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
    3.  Cliquez avec le bouton droit sur un abonnement, puis cliquez sur **Afficher les détails**.  
  
2.  Dans la fenêtre **Détail de l’abonnement \<SubscriptionName>** , cliquez sur **Action**, puis cliquez sur **Actualisation automatique**. La fréquence d'actualisation est déterminée par le paramètre **Fréquence d'actualisation** dans la boîte de dialogue **Paramètres du serveur de publication** .  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../monitoring-replication.md)  
  
  
