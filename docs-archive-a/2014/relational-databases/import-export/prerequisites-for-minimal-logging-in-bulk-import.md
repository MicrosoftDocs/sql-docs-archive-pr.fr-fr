---
title: Prérequis pour une journalisation minimale dans l’importation en bloc | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4711e25dcfcc99e14894e47166638673c61a6831
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708404"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a>Prérequis pour une journalisation minimale dans l’importation en bloc
  Pour une base de données en mode de récupération complète, toutes les opérations d'insertion de lignes effectuées par importation en bloc sont entièrement enregistrées dans le journal des transactions. Les importations de données de grande taille peuvent entraîner un remplissage rapide du journal des transactions si le mode de récupération complète est utilisé. Par opposition, en mode de récupération simple ou en mode de récupération utilisant les journaux de transactions, la journalisation minimale des opérations d'importation en bloc réduit la possibilité qu'une importation en bloc remplira l'espace de journal. La journalisation minimale est également plus efficace qu'une journalisation complète.  
  
> [!NOTE]  
>  Le mode de récupération utilisant les journaux de transactions est conçu pour remplacer temporairement le mode de récupération complète durant les grandes opérations en bloc.  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a>Conditions à remplir par les tables pour la journalisation minimale des opérations d'importation en bloc  
 La journalisation minimale nécessite que la table cible remplisse les conditions suivantes :  
  
-   La table n'est pas en cours de réplication.  
  
-   Le verrouillage de la table est activé (à l'aide de TABLOCK).  
  
    > [!NOTE]  
    >  Bien que les insertions de données ne soient pas consignées dans le journal des transactions lors des opérations d'importation en bloc à journalisation minimale, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] consigne tout de même les allocations d'extensions chaque fois qu'une nouvelle extension est allouée à la table.  
  
-   La table n'est pas une table mémoire optimisée.  
  
 La possibilité de journalisation minimale pour une table dépend également du fait que celle-ci soit indexée et, si elle l'est, du fait qu'elle soit vide :  
  
-   Si la table ne possède aucun index, les pages de données bénéficient de la journalisation minimale.  
  
-   Si la table ne possède pas d'index cluster, mais possède un ou plusieurs index non cluster, les pages de données bénéficient toujours de la journalisation minimale. La manière dont les pages d'index sont journalisées dépend toutefois du remplissage de la table :  
  
    -   Si la table est vide, les pages d'index bénéficient de la journalisation minimale.  
  
    -   Si la table n'est pas vide, les pages d'index bénéficient de la journalisation complète.  
  
        > [!NOTE]  
        >  Si vous démarrez avec une table vide et importez les données en bloc en plusieurs traitements, les pages de données et d'index bénéficient de la journalisation minimale pour le premier traitement, mais à partir du deuxième traitement, seules les pages de données bénéficient de cette journalisation minimale.  
  
-   Si la table possède un index cluster et est vide, les pages de données et d'index bénéficient de la journalisation minimale. Par contre, si une table possède un index cluster et n'est pas vide, les pages de données et d'index bénéficient de la journalisation complète, quel que soit le mode de récupération choisi.  
  
    > [!NOTE]  
    >  Si vous démarrez avec une table vide et importez les données en bloc en plusieurs traitements, les pages de données et d'index bénéficient de la journalisation minimale pour le premier traitement, mais à partir du deuxième traitement, seules les pages de données bénéficient de la journalisation en bloc.  
  
> [!NOTE]  
>  Lorsque la réplication transactionnelle est activée, les opérations BULK INSERT sont entièrement journalisées, même dans le mode de récupération utilisant les journaux de transactions.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Afficher ou modifier le mode de récupération d’une base de données &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)   
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
  
