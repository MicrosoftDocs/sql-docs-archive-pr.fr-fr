---
title: Définir et modifier un filtre de colonne | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a655976f925f83d8c9446cab99016f32ab14887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614510"
---
# <a name="define-and-modify-a-column-filter"></a>Définir et modifier un filtre de colonne
  Cette rubrique décrit comment définir et modifier un filtre de colonne dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour définir et modifier un filtre de colonne à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Certaines colonnes ne peuvent pas être filtrées. Pour plus d’informations, consultez [Filtrer des données publiées](filter-published-data.md). Si vous modifiez un filtre de colonne après que des abonnements ont été initialisés, vous devez générer un nouvel instantané et réinitialiser tous les abonnements après avoir effectué la modification. Pour plus d’informations sur les exigences relatives aux changements de propriétés, consultez [Changer les propriétés des publications et des articles](change-publication-and-article-properties.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définissez des filtres de colonnes sur la page **Articles** de l'Assistant Nouvelle Publication. Pour plus d’informations sur l’utilisation de l’Assistant Nouvelle publication, consultez [Créer une publication](create-a-publication.md).  
  
 Définissez et modifiez des filtres de colonnes dans la page**Articles** de la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d’informations sur les propriétés des publications et des articles, consultez [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-column-filter"></a>Pour définir un filtre de colonne  
  
1.  Sur la page **Articles** de l'Assistant Nouvelle publication, développez la table à filtrer dans le volet **Objets à publier** .  
  
2.  Activez la case à cocher en regard des colonnes que vous voulez filtrer.  
  
#### <a name="to-modify-column-filtering"></a>Pour modifier le filtrage des colonnes  
  
1.  Dans la page **Articles** de la boîte de dialogue **Propriétés de la publication - \<Publication>** , développez la table à filtrer dans le volet **Objets à publier**.  
  
2.  Désactivez la case à cocher en regard de chaque colonne que vous voulez filtrer, et vérifiez que la case à cocher est activée pour chaque colonne qui doit être incluse dans l'article.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Lors de la création d'articles de table, vous pouvez définir les colonnes à inclure dans l'article et modifier ces colonnes une fois l'article défini. Vous pouvez créer et modifier par programme des colonnes filtrées en utilisant des procédures stockées de réplication.  
  
> [!NOTE]  
>  Les procédures suivantes supposent que la table sous-jacente n'a pas été modifiée. Pour plus d’informations sur la réplication des modifications du langage de définition de données (DDL) sur les tables publiées, consultez [Modifier le schéma dans les bases de données de publication](make-schema-changes-on-publication-databases.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Pour définir un filtre de colonne pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Définissez l'article à filtrer. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql). Les colonnes à inclure ou à supprimer de l'article sont alors définies.  
  
    -   En cas de publication de quelques colonnes d'une table en contenant de nombreuses, exécutez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **\@column** et affectez la valeur **add** à **\@operation**.  
  
    -   En cas de publication de la plupart des colonnes d’une table en contenant de nombreuses, exécutez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), en affectant la valeur **null** à **\@column** et la valeur **add** à **\@operation** pour ajouter toutes les colonnes. Exécutez ensuite [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), une fois pour chaque colonne qui est exclue, en affectant la valeur **drop** à **\@operation** et le nom de la colonne exclue à **\@column**.  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Spécifiez le nom de la publication pour **\@publication** et le nom de l’article filtré pour **\@article**. Les objets de synchronisation pour l'article filtré sont alors créés.  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Pour modifier un filtre de colonne de manière à inclure des colonnes supplémentaires pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **\@column** et affectez la valeur **add** à **\@operation**.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Spécifiez le nom de la publication pour **\@publication** et le nom de l’article filtré pour **\@article**. Si la publication contient des abonnements existants, affectez la valeur **1** à **\@change_active**. Les objets de synchronisation pour l'article filtré sont alors recréés.  
  
3.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
4.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser des abonnements](../reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Pour modifier un filtre de colonne de manière à supprimer des colonnes pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) une fois pour chaque colonne supprimée. Spécifiez le nom de la colonne pour **\@column** et affectez la valeur **drop** à **\@operation**.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Spécifiez le nom de la publication pour **\@publication** et le nom de l’article filtré pour **\@article**. Si la publication contient des abonnements existants, affectez la valeur **1** à **\@change_active**. Les objets de synchronisation pour l'article filtré sont alors recréés.  
  
3.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
4.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser des abonnements](../reinitialize-subscriptions.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a>Pour définir un filtre de colonne pour un article publié dans une publication de fusion  
  
1.  Définissez l'article à filtrer. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql). Les colonnes à inclure ou à supprimer de l'article sont alors définies.  
  
    -   En cas de publication de quelques colonnes d'une table en contenant de nombreuses, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **\@column** et affectez la valeur **add** à **\@operation**.  
  
    -   En cas de publication de la plupart des colonnes d’une table en contenant de nombreuses, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), en affectant la valeur **null** à **\@column** et la valeur **add** à **\@operation** pour ajouter toutes les colonnes. Exécutez ensuite [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), une fois pour chaque colonne qui est exclue, en affectant la valeur **drop** à **\@operation** et le nom de la colonne exclue à **\@column**.  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a>Pour modifier un filtre de colonne de manière à inclure des colonnes supplémentaires pour un article publié dans une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) une fois pour chaque colonne ajoutée. Spécifiez le nom de colonne pour **\@column**, affectez la valeur **add** à **\@operation** et la valeur **1** à **\@force_invalidate_snapshot** et à **\@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser des abonnements](../reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a>Pour modifier un filtre de colonne de manière à supprimer des colonnes pour un article publié dans une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) une fois pour chaque colonne supprimée. Spécifiez le nom de colonne pour **\@column**, affectez la valeur **drop** à **\@operation** et la valeur **1** à **\@force_invalidate_snapshot** et à **\@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser des abonnements](../reinitialize-subscriptions.md).  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Dans cet exemple de réplication transactionnelle, la colonne `DaysToManufacture` est supprimée d'un article reposant sur la table `Product` .  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 Dans cet exemple de réplication de fusion, la colonne `CreditCardApprovalCode` est supprimée d'un article reposant sur la table `SalesOrderHeader` .  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a>Voir aussi  
 [Changer les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Filtrer des données publiées](filter-published-data.md)   
 [Filtrer des données publiées en vue de la réplication de fusion](../merge/filter-published-data-for-merge-replication.md)  
  
  
