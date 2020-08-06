---
title: 'Propriétés de l’alerte : nouvelle alerte (page Options) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705907"
---
# <a name="alert-properties-new-alert-options-page"></a>Propriétés de l’alerte : Nouvelle alerte (page Options)
  Utilisez cette page pour afficher et modifier les options des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alertes de l’agent.  
  
## <a name="options"></a>Options  
 **Courriel**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications par courrier électronique.  
  
 **Radiomessagerie**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications de radiomessagerie.  
  
 **Envoi réseau**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications d'envoi réseau.  
  
 **Message de notification supplémentaire à envoyer**  
 Tapez tout texte supplémentaire à inclure dans les messages de notification.  
  
 **Délai entre les réponses**  
 Spécifiez un délai pour les occurrences répétées de l'événement. Certains événements peuvent se produire fréquemment au court d'une courte période de temps. Dans ce cas, vous voudrez peut-être savoir que l'événement s'est produit sans vouloir de réponse pour chaque événement. Utilisez cette option pour spécifier un délai d’attente. Avec un délai, une fois que l’alerte a répondu à un événement, l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent attend le délai spécifié avant de répondre de nouveau, que l’événement se produise ou non pendant ce délai.  
  
 **Maximum**  
 Spécifiez un délai en minutes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
 **Durée**  
 Spécifiez un délai en secondes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Alertes](alerts.md)  
  
  
