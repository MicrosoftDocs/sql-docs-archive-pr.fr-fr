---
title: Informations sur le serveur Web | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603921"
---
# <a name="web-server-information"></a>Informations sur le serveur Web
  Les informations sur le serveur Web sont nécessaires pour pouvoir utiliser l'option de synchronisation Web pour la réplication de fusion. Pour obtenir des informations sur la configuration de la synchronisation Web, consultez [Configurer la synchronisation Web](configure-web-synchronization.md).  
  
## <a name="options"></a>Options  
 **Adresse du serveur Web**  
 Si vous avez spécifié une adresse de serveur web dans la page **Capture instantanée FTP et Internet** de la boîte de dialogue **Propriétés de publication**, elle figure dans la zone de texte comme adresse par défaut. Acceptez cette adresse ou entrez une adresse de serveur Web qualifiée complète pour le serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) qui synchronise cet abonnement.  
  
 **Procédure de connexion de chaque Abonné au serveur Web**  
 Spécifiez le type d'authentification à utiliser pour la connexion au serveur Web. Il est recommandé d'utiliser l'authentification de base pour les connexions au serveur IIS avec SSL (Secure Sockets Layer). Si vous sélectionnez I'authentification de base, entrez la connexion et le mot de passe à utiliser pour se connecter de l'Abonné au serveur IIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [S’abonner aux Publications](subscribe-to-publications.md)   
 [Synchronisation web pour la réplication de fusion](web-synchronization-for-merge-replication.md)  
  
  
