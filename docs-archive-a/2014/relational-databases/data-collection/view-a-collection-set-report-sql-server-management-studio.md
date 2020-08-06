---
title: Afficher un rapport de jeu d’éléments de collecte (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612966"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>Afficher un rapport de jeu d'éléments de collecte (SQL Server Management Studio)
  Après avoir configuré l'entrepôt de données de gestion, vous pouvez afficher un rapport sur un jeu d'éléments de collecte dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Des rapports sont fournis pour les jeux d'éléments de collecte de données système installés pendant l'installation. Les rapports proposés sont les suivants :  
  
-   Résumé sur l'utilisation du disque  
  
-   Historique des statistiques sur les requêtes  
  
-   Historique de l'activité du serveur  
  
 Cette procédure affiche le rapport pour le jeu d’éléments de collecte **Utilisation du disque** . Vous pouvez suivre la même procédure générale pour afficher les rapports des autres jeux d'éléments de collecte de données système.  
  
### <a name="to-view-a-collection-set-report"></a>Pour afficher un rapport de jeu d'éléments de collecte  
  
1.  Les tables d'un rapport sont créées lorsque les données collectées sont téléchargées pour la première fois. Si vous essayez de consulter un rapport avant ce premier téléchargement, une erreur se produit et aucun rapport n'est affiché. Pour charger des données pour le jeu d’éléments de collecte Utilisation du disque, dans l’Explorateur d’objets, développez le dossier **Gestion** , **Collecte de données**, puis **Jeux d’éléments de collecte de données système**, cliquez avec le bouton droit sur le jeu d’éléments de collecte **Utilisation du disque** et cliquez enfin sur **Collecter et télécharger maintenant**.  
  
2.  Pour afficher le rapport, dans l’Explorateur d’objets, développez le dossier **Gestion** , cliquez avec le bouton droit sur **Collecte de données**, pointez sur **Rapports**, sur **Entrepôt de données de gestion**, puis cliquez sur **Résumé sur l’utilisation du disque**.  
  
    > [!NOTE]  
    >  Certains rapports peuvent afficher un bouton Calendrier sous la chronologie de collecte de données. Cliquez sur ce bouton pour accéder au **Calendrier des rapports de collecte de données**.  
  
#### <a name="data-collection-report-calendar"></a>Calendrier des rapports de collecte de données  
 Utilisez cette boîte de dialogue pour spécifier la date de début, l'heure de début et la durée des données pour lesquelles vous voulez créer un rapport. Par exemple, vous pouvez générer un rapport sur l'activité d'utilisation du disque d'un serveur pour une période spécifique de 12 heures mercredi dernier.  
  
 **Date de début**  
 Entrez une date de début pour les données du rapport ou sélectionnez-la dans le calendrier.  
  
 **Heure de début**  
 Entrez une heure de début pour les données du rapport ou spécifiez-la en cliquant sur les flèches.  
  
 **Durée**  
 Spécifiez la plage de temps à inclure dans le rapport. La valeur par défaut est 240 minutes. Les valeurs possibles pour la sélection sont 15 minutes, 60 minutes, 240 minutes (4 heures), 720 minutes (12 heures) et 1440 minutes (24 heures).  
  
## <a name="see-also"></a>Voir aussi  
 [Collecte de données](data-collection.md)   
 [Rapports personnalisés dans Management Studio](../../ssms/object/custom-reports-in-management-studio.md)   
 [Configurer l’entrepôt de données de gestion &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
