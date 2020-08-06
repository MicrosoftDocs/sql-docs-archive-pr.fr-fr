---
title: Attacher une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb11b5c257007872e92d3f0a7eadb3e46b4969cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709592"
---
# <a name="attach-a-database"></a>Attacher une base de données
  Cette rubrique explique comment attacher une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez utiliser cette fonctionnalité pour copier, déplacer, ou mettre à niveau une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Composants requis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour attacher une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après la mise à niveau d'une base de données](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   La base de données doit d'abord être détachée. Toute tentative d'attachement d'une base de données qui n'a pas été détachée retourne une erreur. Pour plus d’informations, consultez [Détacher une base de données](detach-a-database.md).  
  
-   Lorsque vous attachez une base de données, tous les fichiers de données (fichiers MDF et LDF) doivent être disponibles. Si un fichier de données possède un chemin différent de celui qui existait lorsque la base de données a été créée pour la première fois ou attachée pour la dernière fois, vous devez spécifier le chemin actuel du fichier.  
  
-   Au moment d’attacher une base de données, si les fichiers MDF et LDF se trouvent dans des répertoires différents et qu’un des chemins contient \\\\?\GlobalRoot, l’opération échoue.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
Nous vous recommandons de déplacer les bases de données à l’aide de la `ALTER DATABASE` procédure de réadressage planifiée, au lieu d’utiliser le détachement et l’attachement. Pour plus d’informations, consultez [Déplacer des bases de données utilisateur](move-user-databases.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
Les autorisations d'accès au fichier sont définies au cours de plusieurs opérations de base de données, notamment le détachement ou l'attachement d'une base de données. Pour plus d'informations sur les autorisations de fichier définies lors du détachement et de l'attachement d'une base de données, consultez [Sécurisation des fichiers de données et des fichiers journaux](https://technet.microsoft.com/library/ms189128.aspx) dans la documentation en ligne de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
Nous vous recommandons de ne pas attacher ni restaurer de bases de données provenant de sources inconnues ou non approuvées. Ces bases de données peuvent contenir du code malveillant susceptible d'exécuter du code [!INCLUDE[tsql](../../includes/tsql-md.md)] indésirable ou de provoquer des erreurs en modifiant le schéma ou la structure physique des bases de données. Avant d’utiliser une base de données issue d’une source inconnue ou non approuvée, exécutez [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur la base de données sur un serveur autre qu’un serveur de production et examinez également le code, notamment les procédures stockées ou le code défini par l’utilisateur, de la base de données. Pour plus d’informations sur l’attachement de bases de données et sur les modifications apportées aux métadonnées à cette occasion, consultez [Attacher et détacher une base de données &#40;SQL Server&#41](database-detach-and-attach-sql-server.md).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
Requiert l’autorisation `CREATE DATABASE`, `CREATE ANY DATABASE` ou `ALTER ANY DATABASE`.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
### <a name="to-attach-a-database"></a>Pour attacher une base de données  
  
1.  Dans l'Explorateur d'objets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Cliquez avec le bouton droit sur **Bases de données** , puis cliquez sur **Attacher**.  
  
3.  Dans la boîte de dialogue **Attacher des bases de données** , pour spécifier la base de données à attacher, cliquez sur **Ajouter**, dans la boîte de dialogue **Rechercher les fichiers de base de données** , sélectionnez l'unité de disque contenant la base de données et développez l'arborescence pour rechercher et sélectionner le fichier .mdf de la base de données. Par exemple :  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > Une tentative de sélection d'une base de données déjà attachée génère une erreur.  
  
     **Bases de données à attacher**  
     Affiche des informations sur les bases de données sélectionnées.  
  
     \<no column header>  
     Affiche une icône indiquant l'état de l'opération d'attachement. Les icônes possibles sont décrites dans la section **État** ci-dessous.  
  
     **Emplacement du fichier MDF**  
     Affiche le chemin d'accès et le nom du fichier MDF sélectionné.  
  
     **Database Name**  
     Affiche le nom de la base de données.  
  
     **Attacher en tant que**  
     Permet de spécifier éventuellement un autre nom sous lequel la base de données doit être attachée.  
  
     **Propriétaire**  
     Fournit une liste déroulante des propriétaires de bases de données possibles dans laquelle vous pouvez sélectionner un autre propriétaire.  
  
     **État**  
     Affiche l'état de la base de données conformément au tableau ci-après.  
  
    |Icône|Texte d'état|Description|  
    |----------|-----------------|-----------------|  
    |(Aucune icône)|(Aucun texte)|L'opération d'attachement n'a pas démarré ou est peut-être en attente pour cet objet. Il s'agit de la valeur par défaut lorsque la boîte de dialogue est ouverte.|  
    |Triangle vert dirigé vers la droite|En cours|L'opération d'attachement a démarré, mais n'est pas terminée.|  
    |Coche verte|Succès|L'attachement de l'objet a réussi.|  
    |Cercle rouge contenant une croix blanche|Error|L'opération d'attachement a rencontré une erreur et ne s'est pas terminée correctement.|  
    |Cercle contenant deux quartiers noirs (à gauche et à droite) et deux quartiers blancs (en haut et en bas)|Arrêté|L'opération d'attachement n'a pas réussi, car l'utilisateur l'a interrompue.|  
    |Cercle contenant une flèche courbe pointant dans le sens inverse des aiguilles d'une montre|Restauré|L'opération d'attachement a réussi, mais a été restaurée en raison d'une erreur lors de l'attachement d'un autre objet.|  
  
     **Message**  
     Affiche un message vierge ou un lien hypertexte « Fichier introuvable ».  
  
     **Ajouter**  
     Permet de rechercher les principaux fichiers de base de données nécessaires. Lorsque l'utilisateur sélectionne un fichier .mdf, les informations applicables sont automatiquement remplies dans les champs respectifs de la grille **Bases de données à attacher** .  
  
     **Remove**  
     Supprime le fichier sélectionné de la grille **Bases de données à attacher** .  
  
     **Détails de la base de données "** *<nom_base_de_données>* **"**  
     Affiche le nom des fichiers à attacher. Pour vérifier ou changer le nom du chemin d’accès d’un fichier, cliquez sur le bouton **Parcourir** ( **...** ).  
  
    > [!NOTE]  
    > Si un fichier n'existe pas, la colonne **Message** affiche « Introuvable ». Si un fichier journal est introuvable, cela signifie qu'il se trouve dans un autre répertoire ou qu'il a été supprimé. Vous devez mettre à jour le chemin d'accès du fichier dans la grille **Détails de la base de données** pour désigner l'emplacement correct ou supprimer le fichier journal de la grille. Si un fichier de données .ndf est introuvable, vous devez mettre à jour son chemin d'accès dans la grille pour désigner l'emplacement correct.  
  
     **Nom du fichier d'origine**  
     Affiche le nom du fichier attaché appartenant à la base de données.  
  
     **Type de fichier**  
     Indique le type du fichier, **Données** ou **Journal**.  
  
     **Chemin d'accès au fichier actuel**  
     Affiche le chemin d'accès au fichier de base de données sélectionné. Le chemin d'accès peut être modifié manuellement.  
  
     **Message**  
     Affiche un message vierge ou un lien hypertexte «**Fichier introuvable**».  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
### <a name="to-attach-a-database"></a>Pour attacher une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Utilisez l’instruction [Create Database](/sql/t-sql/statements/create-database-sql-server-transact-sql) avec `FOR ATTACH` Close.  
  
     Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple attache les fichiers de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] et renomme la base de données `MyAdventureWorks`.  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > Vous pouvez aussi utiliser la procédure stockée [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) ou [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) . Toutefois, ces procédures seront supprimées dans une future version de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Nous vous recommandons d’utiliser CREATe DATABASE... POUR ATTACH à la place.  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> Suivi : Après la mise à niveau d'une base de données SQL Server  
 rès vous mettez à niveau une base de données à l’aide de la méthode Attach, la base de données est immédiatement disponible et est automatiquement mise à niveau. Si la base de données comprend des index de recherche en texte intégral, la mise à niveau les importe, les réinitialise ou les reconstruit, selon le paramètre de la propriété de serveur **Option de mise à niveau des index de recherche en texte intégral** . Si l’option de mise à niveau a la valeur **Importer** ou **Reconstruire**, les index de recherche en texte intégral ne sont pas disponibles pendant la mise à niveau. Selon le volume de données indexé, l'importation peut prendre plusieurs heures et la reconstruction jusqu'à dix fois plus longtemps. Notez également que quand l’option de mise à niveau est **Importer**, si un catalogue de texte intégral n’est pas disponible, les index de recherche en texte intégral associés sont reconstruits.  
  
Si le niveau de compatibilité d'une base de données utilisateur est à 100 ou supérieur avant la mise à niveau, il reste le même après la mise à niveau. Si le niveau de compatibilité était à 90 avant la mise à niveau, dans la base de données mise à niveau, le niveau de compatibilité est défini à 100, ce qui correspond au niveau de compatibilité le plus bas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Détacher une base de données](detach-a-database.md)  
  
  
