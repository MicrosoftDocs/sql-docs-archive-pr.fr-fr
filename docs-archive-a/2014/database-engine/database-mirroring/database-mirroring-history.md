---
title: Historique de la mise en miroir de bases de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e32ad9bfdce15413d89fbd5ba3d79a5ef14f7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612465"
---
# <a name="database-mirroring-history"></a>Historique de la mise en miroir de bases de données
  Utilisez cette boîte de dialogue pour afficher l'historique d'état de la mise en miroir d'une base de données sur une instance de serveur spécifiée.  
  
 **Pour utiliser SQL Server Management Studio pour contrôler la mise en miroir de base de données**  
  
-   [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>Options  
 **Instance de serveur**  
 Nom de l'instance de serveur à partir de laquelle l'historique est généré.  
  
 **Sauvegarde de la base de données**  
 Nom de la base de données dont l'historique est généré.  
  
 **Filtrer la liste par**  
 Répertorie les valeurs de filtre. La sélection d'une nouvelle valeur a pour effet d'actualiser automatiquement la grille.  
  
 Les valeurs de filtre possibles sont les suivantes :  
  
-   Deux dernières heures  
  
-   Quatre dernières heures  
  
-   Huit dernières heures  
  
-   Dernier jour  
  
-   Deux derniers jours  
  
-   100 derniers enregistrements  
  
-   500 derniers enregistrements  
  
-   1 000 derniers enregistrements  
  
-   Tous les enregistrements  
  
 **Actualiser**  
 Permet d'actualiser la liste historique.  
  
> [!NOTE]  
>  Cette boîte de dialogue n'actualise pas automatiquement la liste historique. Pour ce faire, cliquez sur **Actualiser** ou sélectionnez une autre option de filtre. Seuls les membres du rôle de serveur fixe **sysadmin** peuvent mettre à jour l’historique de la mise en miroir.  
  
 **History**  
 Affiche la liste historique. Cliquez sur un en-tête de colonne pour trier la grille par rapport à cette colonne. La liste comporte les colonnes suivantes :  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**Durée enregistrée**|Horodatage de la ligne d'historique.|  
|**Rôle**|Rôle actuel de la mise en miroir de l'instance de serveur pour cette base de données : Principal ou Miroir.|  
|**État de la mise en miroir**|État de la base de données :<br /><br /> Déconnecté<br /><br /> Basculement en attente<br /><br /> Interrompu<br /><br /> Synchronisé<br /><br /> Synchronisation<br /><br /> Unknown|  
|**Connexion témoin**|État de la connexion témoin dans la session de mise en miroir de la base de données : Connecté ou Déconnecté. En l'absence de témoin, la valeur est NULL.|  
|**Journal non envoyé**|Taille, en kilo-octets (Ko), du journal non envoyé dans la file d'attente d'envoi sur l'instance de serveur principal.|  
|**Durée à envoyer**|Durée approximative requise par l’instance de serveur principal pour envoyer le journal qui se trouve actuellement dans la file d’attente d’envoi vers l’instance de serveur miroir ( *taux d’envoi*). Étant donné que le taux de transactions entrantes peut varier sensiblement, la durée d'envoi du journal est une estimation. Cependant, le taux d'envoi peut être utile pour obtenir une estimation approximative de la durée requise pour effectuer un basculement manuel.|  
|**Send Rate**|Taux d'envoi des transactions à l'instance de serveur miroir, en Ko par seconde.|  
|**Taux de nouvelles transactions**|Taux auquel des transactions entrantes sont ajoutées au journal du principal, en Ko par seconde. Pour déterminer si la mise en miroir est en retard, à jour ou en cours de mise à niveau, comparez cette valeur à la valeur du champ **Durée à envoyer** .|  
|**Transaction non envoyée la plus ancienne**|Âge de la transaction non envoyée la plus ancienne dans la file d'attente d'envoi. La durée de vie de cette transaction indique la quantité de transactions en minutes qui n'ont pas encore été envoyées à l'instance de serveur miroir. Cette valeur permet de mesurer la perte de données potentielle en termes de temps.|  
|**Journal non restauré**|Quantité de journal en attente dans la file d'attente de restauration par progression, en Ko.|  
|**Durée à restaurer**|Nombre approximatif de minutes requises pour que le journal actuellement dans la file d'attente de restauration par progression soit appliqué à la base de données miroir.|  
|**Taux de restauration**|Taux de restauration des transactions dans la base de données en miroir, en Ko par seconde.|  
|**Temps de traitement de validation de miroir**|Délai moyen par transaction en millisecondes (uniquement en modes synchrones). Ce délai correspond au temps de traitement pendant lequel l'instance de serveur principal attend que l'instance de serveur miroir écrive l'enregistrement du journal de transaction dans la file d'attente de restauration par progression.|  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
