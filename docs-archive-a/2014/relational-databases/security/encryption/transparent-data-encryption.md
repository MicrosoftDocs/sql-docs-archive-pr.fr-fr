---
title: Chiffrement TDE (Transparent Data Encryption) | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: a8118f0781d7c9e3d839c029c6bdaf8b01e074b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610564"
---
# <a name="transparent-data-encryption-tde"></a>Transparent Data Encryption (TDE)
  Le*chiffrement transparent des données* (TDE) chiffre les fichiers de données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] (processus appelé chiffrement des données au repos). Vous pouvez prendre plusieurs précautions pour sécuriser la base de données telles que la conception d’un système sécurisé, le chiffrement de ressources confidentielles et la création d'un pare-feu autour des serveurs de base de données. Toutefois, dans un scénario où le support physique (par exemple, les lecteurs ou les bandes de sauvegarde) est volé, une personne malveillante peut juste restaurer ou attacher la base de données et consulter les données. Une solution consiste à chiffrer les données sensibles dans la base de données et à protéger les clés utilisées pour chiffrer les données avec un certificat. Cela empêche toute personne qui ne dispose pas des clés d'utiliser les données, mais ce type de protection doit être planifié à l'avance.

 TDE effectue le chiffrement et le déchiffrement d’E/S en temps réel des données et des fichiers journaux. Le chiffrement utilise une clé de chiffrement de base de données stockée dans l’enregistrement de démarrage de base de données à des fins de disponibilité lors de la récupération. La clé de chiffrement de base de données est une clé symétrique sécurisée à l'aide d'un certificat stocké dans la base de données MASTER du serveur ou une clé asymétrique protégée par un module EKM. Le chiffrement transparent des données protège les données « au repos », autrement dit les fichiers de données et les fichiers journaux. Il permet de se conformer à de nombreuses lois, règles et instructions établies dans différents secteurs professionnels. Cela permet aux développeurs de logiciels de chiffrer des données à l'aide des algorithmes de chiffrement AES et 3DES sans modifier les applications existantes.

> [!IMPORTANT]
>  Le chiffrement transparent des données ne permet pas le chiffrement via des canaux de communication. Pour plus d’informations sur le chiffrement des données sur les canaux de communication, consultez [Activer les connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).
> 
>  **Rubriques connexes :**
> 
>  -   [Transparent Data Encryption avec Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)
> -   [Déplacer une base de données protégée par le chiffrement transparent des données vers un autre serveur SQL Server](move-a-tde-protected-database-to-another-sql-server.md)
> -   [Activer TDE à l’aide de EKM](enable-tde-on-sql-server-using-ekm.md)

## <a name="about-tde"></a>À propos du chiffrement transparent des données
 Le chiffrement du fichier de base de données est effectué au niveau de la page. Les pages d'une base de données chiffrée sont chiffrées avant d'être écrites sur le disque et déchiffrées lorsqu'elles sont lues en mémoire. Le chiffrement transparent des données n'augmente pas la taille de la base de données chiffrée.

 **Informations applicables à[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**

 Quand vous utilisez le chiffrement transparent des données avec [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12 ([version préliminaire dans certaines régions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) le certificat de niveau serveur stocké dans la base de données master est automatiquement créé pour vous par la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]. Pour déplacer une base de données avec chiffrement transparent des données sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] , vous devez déchiffrer la base de données, la déplacer, puis réactiver le chiffrement transparent des données sur la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]de destination. Pour obtenir des instructions pas à pas pour le chiffrement transparent des données sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], consultez [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md).

 L'aperçu de l'état du chiffrement transparent des données s'applique même au sous-ensemble des régions géographiques où la famille de versions V12 de [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] est annoncée comme ayant l'état de disponibilité générale. Le chiffrement transparent des données (TDE) pour [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] n'est pas destiné à être utilisé dans les bases de données de production tant que [!INCLUDE[msCoName](../../../includes/msconame-md.md)] n'annonce pas qu'il est promu de l'aperçu à l'état de disponibilité générale. Pour plus d'informations sur la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12, consultez [Nouveautés d'Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).

 **Informations applicables à[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**

 Une fois sécurisée, la base de données peut être restaurée à l'aide du certificat approprié. Pour plus d'informations sur les certificats, consultez [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).

 Lorsque vous activez le chiffrement transparent des données, vous devez immédiatement sauvegarder le certificat et la clé privée associée au certificat. Dans l'éventualité où le certificat ne serait plus disponible ou que vous deviez restaurer ou attacher la base de données sur un autre serveur, vous devez disposer de sauvegardes du certificat et de la clé privée, sans quoi vous ne pourrez pas ouvrir la base de données. Le certificat de chiffrement doit être conservé même si le chiffrement transparent des données n'est plus activé sur la base de données. Même si la base de données n'est pas chiffrée, des parties du journal des transactions peuvent toujours être protégées, et le certificat peut être nécessaire pour certaines opérations tant que la sauvegarde complète de la base de données n'a pas été effectuée. Un certificat qui a dépassé sa date d'expiration peut toujours être utilisé pour chiffrer et déchiffrer les données avec le chiffrement transparent des données.

 **Hiérarchie de chiffrement**

 L'illustration ci-dessous montre l'architecture du chiffrement TDE. Seuls les éléments de niveau base de données (la clé de chiffrement de base de données et les parties ALTER DATABASE) sont configurables par l'utilisateur lors de l'utilisation du chiffrement transparent des données sur la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].

 ![Affiche la hiérarchie décrite dans la rubrique.](../../../database-engine/media/tde-architecture.gif "Affiche la hiérarchie décrite dans la rubrique.")

## <a name="using-transparent-data-encryption"></a>Utilisation du chiffrement transparent des données
 Pour utiliser le chiffrement transparent des données, procédez comme suit :

||
|-|
|**S'applique à**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|

-   Créez une clé principale.

-   Créez ou obtenez un certificat protégé par la clé principale.

-   Créez une clé de chiffrement de base de données et protégez-la à l'aide du certificat.

-   Configurez la base de données pour qu'elle utilise le chiffrement.

 L'exemple ci-dessous illustre le chiffrement et le déchiffrement de la base de données `AdventureWorks2012` à l'aide d'un certificat installé sur le serveur nommé `MyServerCert`.

```
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

 Les opérations de chiffrement et de déchiffrement sont planifiées sur des threads d'arrière-plan par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Vous pouvez consulter l'état de ces opérations à l'aide des affichages catalogue et des vues de gestion dynamique mentionnés dans la liste fournie plus loin dans cette rubrique.

> [!CAUTION]
>  Les fichiers de sauvegarde des bases de données pour lesquelles le chiffrement transparent des données est activé sont également chiffrés à l'aide de la clé de chiffrement de base de données. En conséquence, lorsque vous restaurez ces sauvegardes, le certificat qui protège la clé de chiffrement de base de données doit être disponible. Cela signifie qu'en plus de sauvegarder la base de données, vous devez vous assurer que vous conservez des sauvegardes des certificats du serveur pour empêcher toute perte de données. Une perte de données interviendra si le certificat n'est plus disponible. Pour plus d'informations, consultez [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).

## <a name="commands-and-functions"></a>Commandes et fonctions
 Les certificats TDE doivent être chiffrés par la clé principale de base de données pour être acceptés par les instructions suivantes. S'ils sont chiffrés uniquement par mot de passe, les instructions les refuseront en tant que chiffreurs.

> [!IMPORTANT]
>  Si des certificats ayant été utilisés par le chiffrement transparent des données sont modifiés de sorte qu'ils soient protégés par mot de passe, la base de données ne sera plus disponible après un redémarrage.

 Le tableau suivant fournit des liens et des explications pour les commandes et les fonctions TDE.

|Commande ou fonction|Objectif|
|-------------------------|-------------|
|[CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)|Crée une clé permettant de chiffrer une base de données.|
|[ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-encryption-key-transact-sql)|Modifie la clé qui permet de chiffrer une base de données.|
|[DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-transact-sql)|Supprime la clé qui était utilisée pour chiffrer une base de données.|
|[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Présente l'option `ALTER DATABASE` qui est utilisée pour activer le chiffrement transparent des données.|

## <a name="catalog-views-and-dynamic-management-views"></a>Affichages catalogue et vues de gestion dynamique
 Le tableau suivant indique les affichages catalogue et les vues de gestion dynamique du chiffrement transparent des données.

|Affichage catalogue ou vue de gestion dynamique|Objectif|
|---------------------------------------------|-------------|
|[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|Affichage catalogue qui affiche des informations sur la base de données.|
|[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)|Affichage catalogue qui indique les certificats inclus dans une base de données.|
|[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)|Vue de gestion dynamique qui fournit des informations sur les clés de chiffrement utilisées dans une base de données et sur l'état de chiffrement d'une base de données.|

## <a name="permissions"></a>Autorisations
 Chaque fonctionnalité et commande TDE requiert des autorisations individuelles, décrites dans les tableaux précédents.

 La consultation des métadonnées impliquées dans le chiffrement transparent des données requiert l'autorisation VIEW DEFINITION sur le certificat.

## <a name="considerations"></a>Considérations
 Lorsqu'une analyse de rechiffrement est en cours pour une opération de chiffrement de la base de données, les opérations de maintenance sur la base de données sont désactivées. Vous pouvez utiliser le paramètre de mode utilisateur unique de la base de données pour effectuer l'opération de maintenance. Pour plus d’informations, consultez [Définir une base de données en mode mono-utilisateur](../../databases/set-a-database-to-single-user-mode.md).

 Vous pouvez déterminer l'état de chiffrement de la base de données en utilisant la vue de gestion dynamique sys.dm_database_encryption_keys. Pour plus d’informations, consultez la section « Affichages catalogue et vues de gestion dynamique » plus haut dans cette rubrique.

 Dans le chiffrement transparent des données, tous les fichiers et groupes de fichiers de la base de données sont chiffrés. Si des groupes de fichiers de la base de données sont marqués comme READ ONLY, l'opération de chiffrement de la base de données échoue.

 Si une base de données est utilisée dans la mise en miroir de bases de données ou la copie des journaux de transaction, les deux bases de données seront chiffrées. Les transactions du journal sont chiffrées lorsqu'elles sont envoyées dans l'intervalle.

> [!IMPORTANT]
>  Tous les nouveaux index de recherche en texte intégral sont chiffrés lorsqu'une base de données est définie pour le chiffrement. Les index de recherche en texte intégral créés précédemment sont importés au cours de la mise à niveau et sont inclus dans le chiffrement transparent des données une fois les données chargées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'activation d'un index en texte intégral sur une colonne peut entraîner l'écriture des données de cette colonne en texte brut sur le disque au cours d'une analyse d'indexation de texte intégral. Nous vous recommandons de ne pas créer d'index de recherche en texte intégral sur des données chiffrées sensibles.

 Le taux de compression des données chiffrées est beaucoup moins élevé que celui des données non chiffrées correspondantes. Si le chiffrement transparent des données est utilisé pour chiffrer une base de données, la compression de la sauvegarde ne permettra pas d'appliquer un fort taux de compression au stockage de la sauvegarde. Par conséquent, l'utilisation conjointe du chiffrement transparent des données et de la compression de la sauvegarde n'est pas recommandée.

### <a name="restrictions"></a>Restrictions
 Les opérations suivantes ne sont pas autorisées au cours du chiffrement initial de la base de données, de la modification d'une clé ou du déchiffrement de la base de données :

-   Suppression d'un fichier d'un groupe de fichiers dans la base de données

-   Suppression de la base de données

-   Mise hors connexion de la base de données

-   Détachement d'une base de données

-   Passage d'une base de données ou d'un groupe de fichiers à l'état READ ONLY

 Les opérations suivantes ne sont pas autorisées durant les instructions CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY ou ALTER DATABASE...SET ENCRYPTION :

-   Suppression d'un fichier d'un groupe de fichiers dans la base de données

-   Suppression de la base de données

-   Mise hors connexion de la base de données

-   Détachement d'une base de données

-   Passage d'une base de données ou d'un groupe de fichiers à l'état READ ONLY

-   Utilisation d'une commande ALTER DATABASE

-   Démarrage d'une base de données ou d'une sauvegarde de fichiers de base de données

-   Démarrage d'une base de données ou d'une restauration de fichiers de base de données

-   Création d'un instantané

 Les opérations ou conditions suivantes empêchent l'exécution des instructions CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY ou ALTER DATABASE...SET ENCRYPTION :

-   La base de données est en lecture seule ou a des groupes de fichiers en lecture seule.

-   Une commande ALTER DATABASE est en cours d'exécution.

-   Une sauvegarde de données est en cours d'exécution.

-   La base de données est dans une condition hors connexion ou de restauration.

-   Un instantané est en cours.

-   Tâches de maintenance de base de données.

 Lors de la création de fichiers de base de données, l'initialisation instantanée des fichiers n'est pas disponible lorsque le chiffrement transparent des données est activé.

 Afin de chiffrer la clé de chiffrement de base de données avec une clé asymétrique, la clé asymétrique doit résider sur un fournisseur de gestion de clés extensible.

### <a name="transparent-data-encryption-and-transaction-logs"></a>Chiffrement transparent des données et journaux de transactions
 L'activation du chiffrement transparent des données sur une base de données a pour effet de « réinitialiser » la partie restante du journal des transactions virtuel pour imposer le journal des transactions virtuel suivant. Cela garantit qu'aucun texte en clair n'est conservé dans les journaux des transactions après que la base de données a été définie pour le chiffrement. Vous pouvez rechercher l'état du chiffrement des fichiers journaux en consultant la colonne `encryption_state` dans la vue `sys.dm_database_encryption_keys`, comme dans l'exemple suivant :

```
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state 
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

 Pour plus d’informations sur l’architecture des fichiers journaux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [Journal des transactions &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md).

 Toutes les données écrites dans le journal des transactions avant une modification de la clé de chiffrement de base de données seront chiffrées à l'aide de la clé de chiffrement de base de données précédente.

 Lorsque la clé de chiffrement d'une base de données a été modifiée deux fois, une sauvegarde de fichier journal doit être effectuée pour rendre possible une nouvelle modification de la clé de chiffrement.

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Chiffrement transparent des données et base de données système tempdb
 La base de données système tempdb est chiffrée si toute autre base de données sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est chiffrée à l'aide du chiffrement transparent des données. Cela peut avoir un impact sur les performances des bases de données non chiffrées situées sur la même instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la base de données système tempdb, consultez [Base de données tempdb](../../databases/tempdb-database.md).

### <a name="transparent-data-encryption-and-replication"></a>Chiffrement transparent des données et réplication
 La réplication ne réplique pas automatiquement sous forme chiffrée les données d'une base sur laquelle le chiffrement transparent des données est activé. Vous devez activer séparément le chiffrement transparent des données si vous souhaitez protéger les bases de données de distribution et d'abonné. La réplication d'instantané, ainsi que la distribution initiale de données pour la réplication transactionnelle et la réplication de fusion, peut stocker des données dans des fichiers intermédiaires non chiffrés, par exemple, des fichiers bcp.  Au cours de la réplication transactionnelle ou de la réplication de fusion, le chiffrement peut être activé pour protéger le canal de communication. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).

### <a name="transparent-data-encryption-and-filestream-data"></a>Chiffrement transparent des données et données FILESTREAM
 Les données FILESTREAM ne sont pas chiffrées même si le chiffrement transparent des données est activé.

### <a name="transparent-data-encryption-and-buffer-pool-extension"></a>Chiffrement transparent des données et Extension du Pool de mémoires tampons
 Les fichiers associés à l'extension du pool de mémoires tampons ne sont pas chiffrés lorsque la base de données est chiffrée à l'aide du chiffrement transparent des données. Vous devez utiliser les outils de chiffrement au niveau du système de fichiers tels que Bitlocker ou EFS pour les fichiers associés à l'extension du pool de mémoires tampons.

## <a name="transparent-data-encryption-and-in-memory-oltp"></a>Chiffrement transparent des données et OLTP en mémoire
 Le chiffrement transparent des données (TDE) peut être activé sur une base de données contenant des objets de l'OLTP en mémoire. Les enregistrements de journal de l'OLTP en mémoire sont chiffrés si le chiffrement transparent des données (TDE) est activé. Les données dans un groupe de fichiers MEMORY_OPTIMIZED_DATA ne sont pas chiffrées si le TDE est activé.

## <a name="see-also"></a>Voir aussi
 [Déplacer une base de données protégée TDE vers une autre SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [activer TDE à l’aide de EKM](enable-tde-on-sql-server-using-ekm.md) [transparent Data Encryption avec Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [chiffrement de SQL Server](sql-server-encryption.md) [SQL Server et des clés de chiffrement de base de données &#40;](sql-server-and-database-encryption-keys-database-engine.md) moteur de base de données&#41;Security Center pour SQL Server moteur de base de données [et Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FileStream](../../blob/filestream-sql-server.md) &#40;SQL Server&#41;


