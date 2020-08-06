---
title: Préparer l’importation de données en bloc (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03d45d9c79082b255e9b8b0e4804c50855a3ad7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708407"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a>Préparer l'importation de données en bloc (SQL Server)
  Vous pouvez exécuter la commande **bcp** , l’instruction BULK INSERT ou la fonction OPENROWSET(BULK) pour importer des données en bloc uniquement à partir d’un fichier de données.  
  
> [!NOTE]  
>  Il est possible d'écrire une application personnalisée qui importe des données en bloc à partir d'objets autres qu'un fichier texte. Pour importer des données en bloc à partir de mémoires tampons, utilisez les extensions bcp de l’interface de programmation d’applications (API) (ODBC) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ou l’interface OLE DB **IRowsetFastLoad** .  Pour importer des données en bloc à partir d’une table de données C#, utilisez l’API de copie en bloc ADO.NET, **SqlBulkCopy**.  
  
> [!NOTE]  
>  L'importation de données en bloc dans une table distante n'est pas prise en charge.  
  
 Quand vous importez des données en bloc dans une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un fichier de données, respectez les consignes suivantes :  
  
-   Procurez-vous les autorisations nécessaires à votre compte d'utilisateur.  
  
     Le compte d’utilisateur dans lequel vous utilisez **bcp**, l’instruction BULK INSERT ou l’instruction INSERT... SELECT * FROM OPENROWSET(BULK...) doit bénéficier des autorisations nécessaires sur la table (affectées par le propriétaire de la table). Pour plus d’informations sur les autorisations requises par chaque méthode, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)et [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
-   Utilisez le mode de récupération utilisant les journaux de transactions.  
  
     Cette instruction s'applique à une base de données employant le mode de sauvegarde complète. Le mode de récupération utilisant les journaux de transactions permet d’effectuer des opérations en bloc dans une table non indexée (un *segment*). La récupération utilisant les journaux de transactions permet d'éviter que le journal des transactions ne manque d'espace dans la mesure où les insertions de lignes ne sont pas consignées. Pour plus d’informations sur le mode de récupération utilisant les journaux de transactions, consultez [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).  
  
     Nous vous recommandons de modifier la base de données pour utiliser le mode de récupération utilisant les journaux de transactions juste avant l'opération d'importation en bloc. Rétablissez la base de données en mode de récupération complète immédiatement après. Pour plus d’informations, consultez [Afficher ou modifier le mode de récupération d’une base de données &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la manière de minimiser la journalisation au cours des opérations d’importation en bloc, consultez [Conditions requises pour une journalisation minimale dans l’importation en bloc](prerequisites-for-minimal-logging-in-bulk-import.md).  
  
-   Sauvegardez après l'importation en bloc de données.  
  
     Pour une base de données qui utilise le mode de récupération simple, il est recommandé de réaliser une sauvegarde complète ou différentielle après l'opération d'importation en bloc. Pour plus d’informations, consultez [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) ou [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).  
  
     Pour le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions, une sauvegarde de fichier journal suffit. Pour plus d’informations, consultez [Sauvegardes du journal des transactions &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).  
  
-   Supprimez les index de table pour améliorer les performances pour les importations en bloc importantes.  
  
     Cette instruction concerne l'importation d'une grande quantité de données comparée à la quantité de données déjà présente dans la table. Dans ce cas, la suppression des index de la table avant d'effectuer l'opération d'importation en bloc peut augmenter les performances considérablement.  
  
    > [!NOTE]  
    >  En revanche, si vous chargez une petite quantité de données comparée à la quantité de données figurant dans la table, la suppression des index est contre-productive. En effet, la durée de régénération des index peut se révéler supérieure au gain de temps réalisé durant l'opération d'importation en bloc.  
  
-   Recherchez et supprimez les caractères masqués dans le fichier de données.  
  
     De nombreux utilitaires et éditeurs de texte affichent les caractères masqués qui figurent généralement à la fin du fichier de données. Durant une opération d'importation en bloc, les caractères masqués d'un fichier de données ASCII peuvent causer des problèmes qui génèrent une erreur de type « une valeur NULL inattendue a été trouvée ». Il suffit en général de rechercher et de supprimer les caractères masqués pour éviter ce problème.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer et exporter des données en bloc à l’aide de l’utilitaire bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)   
 [Importer des données en bloc à l’aide de BULK INSERT ou OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Formats de données pour l’importation ou l’exportation en bloc &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
