---
title: Définir un article | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614512"
---
# <a name="define-an-article"></a>Définir un article
  Cette rubrique explique comment définir un article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)], ou des objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour définir un article, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Les noms d'article ne peuvent inclure aucun des caractères suivants : % , * , [ , ] , | , : , " , ? , ' , \ , / , \< , >. Si des objets de la base de données incluent l'un de ces caractères et que vous souhaitez les répliquer, vous devez spécifier un nom d'article qui est différent du nom d'objet.  
  
##  <a name="security"></a><a name="Security"></a> Sécurité  
 Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](https://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Créez des publication et définissez des articles avec l'Assistant Nouvelle publication. Après avoir créé une publication, affichez et modifiez les propriétés de publication dans la boîte de dialogue **Propriétés de la publication – \<Publication>** . Pour plus d’informations sur la création d’une publication à partir d’une base de données Oracle, consultez [Créer une publication à partir d’une base de données Oracle](create-a-publication-from-an-oracle-database.md).  
  
#### <a name="to-create-a-publication-and-define-articles"></a>Pour créer une publication et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis cliquez avec le bouton droit sur le dossier **Publications locales** .  
  
3.  Cliquez sur **Nouvelle publication**.  
  
4.  Exécutez les pages de l'Assistant Nouvelle publication pour.  
  
    -   Spécifier un serveur de distribution si la distribution n'a pas été configurée sur le serveur. Pour plus d’informations sur la configuration de la distribution, consultez [Configurer la publication et la distribution](../configure-publishing-and-distribution.md).  
  
         Si vous spécifiez dans la page **Serveur de distribution** que le serveur de publication se comportera comme son propre serveur de distribution (serveur de distribution local), et si ce serveur n'est pas configuré comme serveur de distribution, l'Assistant Nouvelle publication configurera ce serveur. Vous spécifierez un dossier d'instantanés par défaut pour le serveur de distribution dans la page **Dossier d'instantanés** . Le dossier d'instantanés correspond à un simple répertoire que vous définissez sous la forme d'un partage ; les agents qui lisent et écrivent dans le dossier doivent disposer des autorisations suffisantes pour pouvoir y accéder. Pour plus d’informations sur une sécurisation appropriée du dossier, consultez [Sécuriser le dossier d’instantanés](../security/secure-the-snapshot-folder.md).  
  
         Si vous spécifiez qu'un autre serveur doit jouer le rôle de serveur de distribution, vous devez entrer un mot de passe dans la page **Mot de passe d'administration** pour les connexions effectuées du serveur de publication sur le serveur de distribution. Ce mot de passe doit correspondre à celui qui a été spécifié lorsque le serveur de publication a été activé sur le serveur de distribution distant.  
  
         Pour plus d'informations, voir [Configure Distribution](../configure-distribution.md).  
  
    -   Choisissez une base de données de publication.  
  
    -   Sélectionnez un type de publication. Pour plus d’informations, consultez [Types de réplication](../types-of-replication.md).  
  
    -   Spécifiez les données et les objets de base de données à publier ; en option, filtrez les colonnes des articles des tables, et définissez des propriétés d'articles.  
  
    -   En option, filtrez les lignes des articles des tables. Pour plus d’informations, consultez [Filtrer des données publiées](filter-published-data.md).  
  
    -   Définissez la planification de l'Agent d'instantané.  
  
    -   Spécifiez les informations de connexion sous lesquelles les Agents de réplication suivants s'exécuteront et se connecteront :  
  
         \- Agent d’instantané pour toutes les publications.  
  
         \- Agent de lecture du journal pour toutes les publications transactionnelles.  
  
         \- Agent de lecture de la file d’attente pour les publications transactionnelles acceptant les abonnements avec mise à jour.  
  
         Pour plus d'informations, consultez [Replication Agent Security Model](../security/replication-agent-security-model.md) et [Replication Security Best Practices](../security/replication-security-best-practices.md).  
  
    -   En option, scriptez la publication. Pour plus d'informations, voir [Scripting Replication](../scripting-replication.md).  
  
    -   Spécifiez le nom de la publication.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Une fois une publication créée, des articles peuvent être créés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées pour créer un article dépendent du type de publication pour laquelle l'article est défini. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>Pour définir un article pour une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication**, le nom de l' ** \@ article pour l’article, l'** objet de base de données qui est publié pour ** \@ source_object**et tous les autres paramètres facultatifs. Utilisez ** \@ source_owner** pour spécifier la propriété de schéma de l’objet, si ce n’est pas **dbo**. Si l’article n’est pas un article de table basée sur un journal, spécifiez le type d’article pour ** \@ type**. pour plus d’informations, consultez [spécifier les types d’articles &#40;la programmation Transact-SQL de la réplication&#41;](specify-article-types-replication-transact-sql-programming.md).  
  
2.  Pour filtrer horizontalement les lignes d'une table ou pour afficher un article, utilisez [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) pour définir la clause du filtre. Pour plus d'informations, voir [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md).  
  
3.  Pour filtrer verticalement les colonnes d'une table ou afficher un article, utilisez [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql). Pour plus d'informations, voir [Définir et modifier un filtre de colonne](define-and-modify-a-column-filter.md).  
  
4.  Exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) si l'article est filtré.  
  
5.  Si la publication contient des abonnements existants et si [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) retourne la valeur **0** dans la colonne **immediate_sync** , vous devez appeler [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) pour ajouter l'article à chaque abonnement existant.  
  
6.  Si la publication contient des abonnements par extraction existants, exécutez [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) au niveau du serveur de publication de manière à créer un nouvel instantané pour les abonnements par extraction existants qui contient uniquement le nouvel article.  
  
    > [!NOTE]  
    >  Pour les abonnements qui ne sont pas initialisés à l'aide d'un instantané, vous n'avez pas besoin d'exécuter [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) puisque cette procédure est exécutée par [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>Pour définir un article pour une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez le nom de la publication pour la ** \@ publication**, le nom de l’article ** \@ pour l’article et**l’objet qui est publié pour ** \@ source_object**. Pour filtrer horizontalement les lignes d’une table, spécifiez une valeur pour ** \@ subset_filterclause**. Pour plus d'informations, consultez [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) et [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md). Si l’article n’est pas un article de table, spécifiez le type d’article pour ** \@ type**. Pour plus d’informations, consultez [Spécifier les types d’articles &#40;programmation Transact-SQL de la réplication&#41;](specify-article-types-replication-transact-sql-programming.md).  
  
2.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) pour définir un filtre de jointure entre deux articles. Pour plus d'informations, voir [Définir et modifier un filtre de jointure entre des articles de fusion](define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) pour filtrer les colonnes d'une table. Pour plus d'informations, voir [Définir et modifier un filtre de colonne](define-and-modify-a-column-filter.md).  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple définit un article basé sur la table `Product` pour une publication transactionnelle, où l'article est filtré à la fois horizontalement et verticalement.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 Cet exemple définit des articles pour une publication de fusion, où l'article `SalesOrderHeader` est filtré statiquement sur **SalesPersonID**et où l'article `SalesOrderDetail` est filtré avec un filtre de jointure sur `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez définir des articles par programme à l'aide d'objets RMO (Replication Management Objects). Les classes RMO que vous utilisez pour définir un article dépendent du type de publication pour lequel l'article est défini.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Exemples (RMO)  
 L'exemple suivant ajoute un article avec des filtres des lignes et de colonnes à une publication transactionnelle.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 L'exemple suivant ajoute trois articles à une publication de fusion. Ces articles ont des filtres de colonnes, et deux filtres de jointure sont utilisés pour propager un filtre de lignes paramétrable aux autres articles.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](create-a-publication.md)   
 [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Ajouter et supprimer des articles de publications existantes](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Filtrer des données publiées](filter-published-data.md)   
 [Publier des données et des objets de base de données](publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
