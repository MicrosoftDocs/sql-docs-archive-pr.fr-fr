---
title: Abonnements pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 447114152365e098420f46d4b7e880e8f2907864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697884"
---
# <a name="updatable-subscriptions"></a>Abonnements pouvant être mis à jour
  Avec la réplication transactionnelle, les données répliquées doivent être traitées en lecture seule. Toutefois, vous pouvez modifier les données répliquées au niveau d’un abonné [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant des abonnements pouvant être mis à jour. Si vous devez modifier des données sur l'Abonné, vous pouvez choisir l'une des options suivantes selon vos besoins.  
  
|Type d'abonnement pouvant être mis à jour|Spécifications|  
|---------------------------------|------------------|  
|Mise à jour immédiate|Le serveur de publication et l'Abonné doivent être connectés pour mettre à jour les données sur l'Abonné.|  
|Mise à jour en attente|Le serveur de publication et l'Abonné n'ont pas besoin d'être connectés pour mettre à jour les données sur l'Abonné. Les mises à jour peuvent être effectuées hors ligne et synchronisées ensuite entre le serveur de publication et l'Abonné.|  
  
## <a name="options"></a>Options  
 **Répliquer les modifications de l'Abonné**  
 Activez la case à cocher dans la colonne **Répliquer** pour chaque abonné qui doit pouvoir effectuer des mises à jour. Pour les abonnés qui peuvent effectuer des mises à jour, sélectionnez l'option appropriée dans la zone de liste déroulante de la colonne **Valider sur le serveur de publication** :  
  
-   Sélectionnez **Enregistrer les modifications simultanément** pour un abonnement mis à jour immédiatement.  
  
-   Sélectionnez **Mettre les modifications en file d'attente et valider dès que possible** pour un abonnement mis à jour en file d'attente.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [S’abonner aux Publications](subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
