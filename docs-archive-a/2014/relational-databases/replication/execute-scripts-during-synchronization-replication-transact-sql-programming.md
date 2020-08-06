---
title: Exécuter des scripts pendant la synchronisation (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bc217ad160a0238cc4247600d65eb32f156071f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601350"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Exécuter des scripts pendant la synchronisation (programmation Transact-SQL de la réplication)
  La réplication prend en charge l'exécution de script à la demande pour les Abonnés à des publications transactionnelles et de fusion. Cette fonctionnalité copie le script vers le répertoire de travail de réplication puis utilise **sqlcmd** pour appliquer le script à l'Abonné. Par défaut, en cas d'échec lors de l'application du script pour un abonnement à une publication transactionnelle, l'Agent de distribution s'arrêtera. Vous pouvez spécifier un script [!INCLUDE[tsql](../../includes/tsql-md.md)] à exécuter par programme à l'aide des procédures stockées de réplication.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Pour spécifier un script à exécuter pour tous les Abonnés à une publication d'instantané, transactionnelle ou de fusion  
  
1.  Composez et testez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sera exécuté à la demande.  
  
2.  Enregistrez le fichier de script dans un emplacement accessible à l'Agent d'instantané pour la publication.  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql). Spécifiez ** \@ publication**, le nom du fichier de script avec le chemin UNC complet créé à l’étape 2 pour ** \@ scriptfile**et l’une des valeurs suivantes pour ** \@ SkipError**:  
  
    -   **0** – l'agent arrêtera d'exécuter le script en cas d'erreur.  
  
    -   **1** – l'agent enregistrera les erreurs rencontrées et continuera à exécuter le script.  
  
4.  Le script spécifié sera exécuté sur chaque Abonné lorsque l'agent s'exécutera de nouveau pour synchroniser l'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchroniser les données](synchronize-data.md)  
  
  
