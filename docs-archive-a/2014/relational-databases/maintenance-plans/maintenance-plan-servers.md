---
title: Plan de maintenance (Serveurs) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c971edc9b641846068313f47ca410715ec552014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603975"
---
# <a name="maintenance-plan-servers"></a>Plan de maintenance (Serveurs)
  La boîte de dialogue **Serveurs** permet de sélectionner les serveurs sur lesquels vous souhaitez exécuter le plan de maintenance.  
  
 Pour créer un plan de maintenance multiserveur, vous devez configurer un environnement multiserveur contenant un serveur maître et un ou plusieurs serveurs cibles. Pour les plans de maintenance multiserveurs, le serveur local doit être configuré comme serveur maître. Dans les environnements multiserveurs, cette boîte de dialogue affiche le serveur maître **(local)** et tous les serveurs cibles correspondants. Un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créé pour le serveur local. Celui-ci est activé ou désactivé selon que vous avez sélectionné le serveur **(local)** . Si des serveurs cibles sont sélectionnés, un travail multiserveur est créé et téléchargé vers chacun des serveurs cibles sélectionnés. Si aucun serveur cible n'est sélectionné, le travail multiserveur est supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](maintenance-plans.md)   
 [Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)   
 [Créer un serveur maître](../../ssms/agent/make-a-master-server.md)   
 [Créer un serveur cible](../../ssms/agent/make-a-target-server.md)  
  
  
