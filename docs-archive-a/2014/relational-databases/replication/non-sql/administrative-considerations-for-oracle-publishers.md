---
title: Considérations sur l’administration des serveurs de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3104b507987a4a236d39dd0ae1f8e3c29358c730
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612234"
---
# <a name="administrative-considerations-for-oracle-publishers"></a>Considérations sur l'administration des serveurs de publication Oracle
  Quand un serveur de publication Oracle est configuré et que les mécanismes de suivi des modifications de la réplication sont en place, les administrateurs du système de base de données Oracle peuvent continuer à utiliser les utilitaires de base de données standard d'Oracle et à effectuer des tâches courantes d'administration du système. Cependant, il faut être attentif aux effets que peuvent avoir certaines tâches d'administration sur les données publiées.  
  
 À l'exception de la suppression ou de la modification d'une colonne qui est publiée pour réplication, ou de la suppression ou de la modification de n'importe quel objet de réplication, ces considérations ne s'appliquent pas aux publications d'instantané.  
  
## <a name="importing-and-loading-data"></a>Importation et chargement de données  
 Les déclencheurs sont utilisés dans le suivi des modifications pour les publications transactionnelles sur Oracle. Les modifications apportées aux tables publiées peuvent être répliquées vers les Abonnés seulement si les déclencheurs de réplication s'exécutent quand une mise à jour, une insertion ou une suppression se produit. Les utilitaires Oracle Import et SQL*Loader d'Oracle ont tous deux des options qui affectent l'activation des déclencheurs quand des lignes sont insérées dans des tables répliquées avec ces utilitaires.  
  
### <a name="oracle-import"></a>Oracle Import  
 Avec Oracle Import, vous pouvez définir la valeur de l'option **ignore** à 'y' ou à 'n' (la valeur par défaut est 'n'). Si **ignore** est définie à 'n', la table est supprimée et recréée lors de l'importation. Cela supprime les déclencheurs de réplication et désactive la réplication. Si **ignore** est définie à 'y', l'importation va tenter de charger les lignes dans la table existante, ce qui active les déclencheurs de réplication. Par conséquent, vérifiez que **ignore** est défini à 'y' lors de l'importation dans une table répliquée avec l'outil Import.  
  
### <a name="sqlloader"></a>SQL*Loader  
 Avec SQL\*Loader, vous pouvez définir la valeur de l’option **direct** à ’True’ ou à ’False’ (la valeur par défaut est ’False’). Si **direct** est définie à 'False', les lignes sont insérées à l'aide d'instructions INSERT conventionnelles, qui activent les déclencheurs de réplication. Si **direct** est définie à 'True', la charge est optimisée et les déclencheurs ne sont pas activés. Par conséquent, vérifiez que **direct** est définie à 'False' lors du chargement dans une table répliquée avec l'outil SQL*Loader.  
  
## <a name="making-changes-to-published-objects"></a>Modifications d'objets publiés  
 Les actions suivantes ne requièrent pas de considérations particulières :  
  
-   Reconstruction d'index sur des tables publiées.  
  
-   Ajout de déclencheurs de l'utilisateur à une table publiée.  
  
 L'action suivante nécessite l'arrêt de toutes les activités sur les tables publiées :  
  
-   Déplacement d'une table publiée.  
  
 Les actions suivantes nécessitent la suppression de la publication, la réalisation de l'opération, puis la recréation de la publication :  
  
-   Troncation d'une table publiée.  
  
-   Renommage d'une table publiée.  
  
-   Ajout d'une colonne à une table publiée.  
  
-   Ajout ou modification d'une colonne qui est publiée pour réplication.  
  
-   Réalisation d'opérations sans journalisation.  
  
## <a name="dropping-or-modifying-replication-objects"></a>Suppression ou modification d'objets de réplication  
 Vous devez supprimer et reconfigurer le serveur de publication si vous supprimez ou si vous modifiez des tables, des déclencheurs, des séquences ou des procédures stockées de suivi au niveau d'un serveur de publication. Pour obtenir une liste partielle de ces objets, consultez [Objets créés sur le serveur de publication Oracle](objects-created-on-the-oracle-publisher.md).  
  
 Pour des informations sur la suppression et la reconfiguration du serveur de publication, consultez la section « Des modifications sont effectuées et nécessitent la reconfiguration du serveur de publication » dans la rubrique [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](configure-an-oracle-publisher.md)   
 [Problèmes et limitations de conception des serveurs de publication Oracle](design-considerations-and-limitations-for-oracle-publishers.md)   
 [Vue d’ensemble de la publication Oracle](oracle-publishing-overview.md)  
  
  
