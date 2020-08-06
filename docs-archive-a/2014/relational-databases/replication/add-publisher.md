---
title: Boîte de dialogue’ajouter un serveur de publication'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.addpublisher.f1
helpviewer_keywords:
- Add Publisher dialog box
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c7e607c04aa74db7e5facf13051bf0c47c9dae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601410"
---
# <a name="sql-server-replication-add-publisher-dialog-box"></a>Réplication SQL Server boîte de dialogue « Ajouter un serveur de publication » 
  La boîte de dialogue **Ajouter un serveur de publication** permet d'ajouter des serveurs de publication dans le volet de gauche du Moniteur de réplication. Après avoir ajouté un serveur de publication, sélectionnez le serveur de publication dans le volet de gauche pour afficher les informations sur ce dernier dans le volet de droite.  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Cliquez pour sélectionner un type de serveur de publication à ajouter, afin d'ouvrir la boîte de dialogue **Se connecter au serveur** . Les options sont :  
  
-   **Ajouter un serveur de publication SQL Server...**  
  
     Connectez-vous au serveur de publication à l'aide de la boîte de dialogue **Se connecter au serveur** .  
  
-   **Ajouter un serveur de publication Oracle...**  
  
     Connectez-vous au serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associé au serveur de publication Oracle à l’aide de la boîte de dialogue **Se connecter au serveur**.  
  
-   **Spécifier un serveur de distribution et ajouter ses serveurs de publication...**  
  
     Connectez-vous au serveur de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associé à un ou plusieurs serveurs de publication à l'aide de la boîte de dialogue **Se connecter au serveur** .  
  
 Après vous être connecté au serveur de publication ou au serveur de distribution, le nom du serveur de publication et celui de son serveur de distribution figurent dans la grille dans la partie supérieure de la boîte de dialogue.  
  
> [!NOTE]  
>  Le serveur de distribution et le serveur de publication sont généralement exécutés sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais le serveur de distribution peut être exécuté sur une autre instance (cette configuration s'appelle un serveur de distribution distant).  
  
 **Remove**  
 Sélectionnez un serveur de publication dans la grille située dans la partie supérieure de la boîte de dialogue et cliquez sur **Supprimer** pour supprimer le serveur de publication de la liste des serveurs de publication à ajouter.  
  
> [!NOTE]  
>  Ce bouton ne permet pas de supprimer un serveur de publication qui figure dans le Moniteur de réplication. Pour supprimer un serveur de publication déjà affiché, cliquez avec le bouton droit de la souris sur le serveur de publication dans le volet de gauche du Moniteur de réplication et cliquez sur **Supprimer**.  
  
 **Se connecter automatiquement au démarrage du Moniteur de réplication**  
 Sélectionnez cette option pour permettre au Moniteur de réplication de se connecter automatiquement au serveur de distribution et d'extraire les informations d'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette case à cocher est désactivée, vous devez vous connecter manuellement après le lancement du Moniteur de réplication : cliquez avec le bouton droit dans le volet de gauche du Moniteur de réplication et cliquez sur **Se connecter**.  
  
 **Actualiser automatiquement le statut de ce serveur de publication et de ses publications**  
 Sélectionnez cette option pour permettre au Moniteur de réplication d'actualiser l'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette option est sélectionnée, le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état du serveur de publication et de ses publications. La fréquence d'interrogation est définie par l'option **Fréquence d'actualisation** . Pour plus d’informations sur l’actualisation du moniteur de réplication, consultez [Mise en cache, actualisation et performances du moniteur de réplication](monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Fréquence d'actualisation**  
 Entrez une valeur (en secondes) pour définir la fréquence à laquelle le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état. Une valeur basse augmente la fréquence d'interrogation, ce qui peut affecter les performances du serveur de distribution si vous contrôlez un grand nombre de serveurs de publication. Il est recommandé de tester le système pour déterminer la valeur appropriée. L'option **Fréquence d'actualisation** est également utilisée si vous sélectionnez **Actualisation automatique** dans une fenêtre de détail du Moniteur de réplication.  
  
 **Afficher ce ou ces serveurs de publication dans le groupe suivant**  
 Sélectionnez un groupe de serveurs de publication dans la liste. Le serveur de publication se trouve dans ce groupe dans le volet de gauche. Les groupes permettent d'organiser les serveurs de publication et n'ont aucun impact sur le fonctionnement de la réplication. Si aucun groupe n'est défini et que vous voulez en créer un, cliquez sur **Nouveau groupe**.  
  
 **Nouveau groupe**  
 Cliquez pour créer un nouveau groupe de serveurs de publication. Un groupe de serveurs de publication permet d'organiser aisément les serveurs de publication dans le Moniteur de réplication. Les groupes n'affectent pas la réplication des données ni la relation entre les serveurs dans une topologie de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
