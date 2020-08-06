---
title: Définir la méthode de propagation des modifications de données des articles transactionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
- propagating data changes [SQL Server replication]
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3f8be8b6df1034b06d0aaff6ee61c0c494833c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702707"
---
# <a name="set-the-propagation-method-for-data-changes-to-transactional-articles"></a>Définir la méthode de propagation des modifications de données des articles transactionnels
  Cette rubrique explique comment définir la méthode de propagation pour les modifications de données d'articles transactionnels dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Par défaut, la réplication transactionnelle propage les modifications vers les Abonnés à l'aide d'un ensemble de procédures stockées pour chaque article. Vous pouvez remplacer ces procédures par des procédures personnalisées. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour définir la méthode de propagation des modifications de données d'articles transactionnels à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   La modification des fichiers d'instantanés générés par la réplication nécessite la plus grande prudence. Vous devez tester et prendre en charge la logique personnalisée dans les procédures stockées personnalisées. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] n'assure pas la prise en charge de la logique personnalisée.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez la méthode de propagation dans l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>** , accessible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-the-propagation-method"></a>Pour spécifier la méthode de propagation  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une table, puis cliquez sur **Propriétés de l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
3.  Dans l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>** , dans la section **Remise d’instruction**, spécifiez la méthode de propagation pour chaque opération à l’aide des menus **Format de remise INSERT**, **Format de remise UPDATE** et **Format de remise DELETE**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### <a name="to-generate-and-use-custom-stored-procedures"></a>Pour générer et utiliser des procédures stockées personnalisées  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une table, puis cliquez sur **Propriétés de l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
     Dans l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>** , dans la section **Remise d’instruction**, sélectionnez la syntaxe CALL dans le menu du format de remise approprié (**Format de remise INSERT**, **Format de remise UPDATE** ou **Format de remise DELETE**), puis tapez le nom de la procédure à utiliser dans **Procédure stockée INSERT**, **Procédure stockée DELETE** ou **Procédure stockée UPDATE**. Pour plus d’informations sur la syntaxe CALL, consultez la section « Syntaxe d’appel des procédures stockées » dans [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
5.  Lorsque l'instantané de la publication est généré, il inclut la procédure spécifiée à l'étape précédente. Les procédures utilisent la syntaxe CALL spécifiée, mais incluent également la logique par défaut utilisée par la réplication.  
  
     Une fois l'instantané généré, accédez au dossier d'instantanés de la publication à laquelle cet article appartient, puis recherchez le fichier **.sch** dont le nom est identique à celui de l'article. Ouvrez ce fichier à l'aide du Bloc-notes ou d'un autre éditeur de texte, recherchez la commande CREATE PROCEDURE pour les procédures stockées INSERT, UPDATE ou DELETE, puis modifiez la définition de la procédure pour fournir une logique personnalisée de propagation des modifications de données. Si l'instantané est régénéré, vous devez recréer la procédure personnalisée.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 La réplication transactionnelle vous permet de contrôler comment les modifications sont propagées du serveur de publication aux Abonnés et cette méthode de propagation peut être définie par programme lorsqu'un article est créé et modifié ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!NOTE]  
>  Vous pouvez spécifier une méthode de propagation différente pour chaque type d'opération DML (Data Manipulation Language) (insertion, mise à jour ou suppression) effectué sur une ligne de données publiées.  
  
 Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-that-uses-transact-sql-commands-to-propagate-data-changes"></a>Pour créer un article qui utilise des commandes Transact-SQL pour propager des modifications de données  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour **\@publication**, le nom de l’article pour **\@article**, l’objet de base de données qui est publié pour **\@source_object** et la valeur **SQL** pour au moins un des paramètres suivants :  
  
    -   **\@ins_cmd** : contrôle la réplication des commandes [INSERT](/sql/t-sql/statements/insert-transact-sql).  
  
    -   **\@upd_cmd** : contrôle la réplication des commandes [UPDATE](/sql/t-sql/queries/update-transact-sql).  
  
    -   **\@del_cmd** : contrôle la réplication des commandes [DELETE](/sql/t-sql/statements/delete-transact-sql).  
  
    > [!NOTE]  
    >  Lors de la spécification de la valeur **SQL** pour un des paramètres ci-dessus, les commandes de ce type seront répliquées sur l'Abonné sous la forme de la commande [!INCLUDE[tsql](../../../includes/tsql-md.md)] appropriée.  
  
     Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
#### <a name="to-create-an-article-that-does-not-propagate-data-changes"></a>Pour créer un article qui ne propage pas les modifications de données  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour **\@publication**, le nom de l’article pour **\@article**, l’objet de base de données qui est publié pour **\@source_object** et la valeur **NONE** pour au moins un des paramètres suivants :  
  
    -   **\@ins_cmd** : contrôle la réplication des commandes [INSERT](/sql/t-sql/statements/insert-transact-sql).  
  
    -   **\@upd_cmd** : contrôle la réplication des commandes [UPDATE](/sql/t-sql/queries/update-transact-sql).  
  
    -   **\@del_cmd** : contrôle la réplication des commandes [DELETE](/sql/t-sql/statements/delete-transact-sql).  
  
    > [!NOTE]  
    >  Lors de la spécification de la valeur **NONE** pour un des paramètres ci-dessus, les commandes de ce type ne seront pas répliquées sur l'Abonné.  
  
     Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
#### <a name="to-create-an-article-with-user-modified-custom-stored-procedures"></a>Pour créer un article avec des procédures stockées personnalisées modifiées par utilisateur  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour **\@publication**, le nom de l’article pour **\@article**, l’objet de base de données qui est publié pour **\@source_object**, une valeur pour le masque de bits **\@schema_option** qui contient la valeur **0x02** (permet la génération automatique de procédures stockées personnalisées) et au moins un des paramètres suivants :  
  
    -   ** \@ ins_cmd** : spécifiez la valeur <strong>Call sp_MSins_*article_name*</strong>, où **_article_name_** est la valeur spécifiée pour ** \@ article**.  
  
    -   ** \@ del_cmd** : spécifiez la valeur <strong>Call sp_MSdel_*article_name* </strong> ou <strong>XCALL sp_Msdel_*article_name*</strong>, où **_article_name_** est la valeur spécifiée pour _ * \@ article * *.  
  
    -   ** \@ upd_cmd** -spécifiez la valeur <strong>scalal sp_Msupd_*article_name*</strong>, <strong>Call sp_Msupd_*article_name*</strong>, <strong>XCALL sp_MSupd__article_name *</strong> ou <strong>MCALL sp_Msupd_* article_name *</strong>, où _**article_name**_ est la valeur spécifiée pour ** \@ article**.  
  
    > [!NOTE]  
    >  Pour chacun des paramètres de commande ci-dessus, vous pouvez spécifier votre propre nom pour les procédures stockées que la réplication génère.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la syntaxe CALL, SCALL, XCALL et MCALL, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Une fois l'instantané généré, accédez au dossier d'instantanés de la publication à laquelle cet article appartient, puis recherchez le fichier **.sch** dont le nom est identique à celui de l'article. Ouvrez ce fichier à l'aide de Notepad.exe, recherchez la commande CREATE PROCEDURE pour les procédures stockées INSERT, UPDATE ou DELETE, puis modifiez la définition de la procédure pour fournir une logique personnalisée de propagation des modifications de données. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-with-custom-scripting-in-the-custom-stored-procedures-to-propagate-data-changes"></a>Pour créer un article avec des scripts personnalisés dans les procédures stockées personnalisées pour propager les modifications de données  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour **\@publication**, le nom de l’article pour **\@article**, l’objet de base de données qui est publié pour **\@source_object**, une valeur pour le masque de bits **\@schema_option** qui contient la valeur **0x02** (permet la génération automatique de procédures stockées personnalisées) et au moins un des paramètres suivants :  
  
    -   ** \@ ins_cmd** : spécifiez la valeur <strong>Call sp_MSins_*article_name*</strong>, où _**article_name**_ est la valeur spécifiée pour ** \@ article**.  
  
    -   ** \@ del_cmd** : spécifiez la valeur <strong>Call sp_MSdel_*article_name* </strong> ou <strong>XCALL sp_Msdel_*article_name*</strong>, où _**article_name**_ est la valeur spécifiée pour ** \@ article**.  
  
    -   ** \@ upd_cmd** : spécifiez la valeur <strong>scalal sp_Msupd_*article_name*</strong>, <strong>Call sp_Msupd_*article_name*</strong>, <strong>XCALL sp_Msupd_*article_name*</strong>, <strong>MCALL sp_Msupd_*article_name*</strong>, où _**article_name**_ est la valeur spécifiée pour ** \@ article**.  
  
    > [!NOTE]  
    >  Pour chacun des paramètres de commande ci-dessus, vous pouvez spécifier votre propre nom pour les procédures stockées que la réplication génère.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la syntaxe CALL, SCALL, XCALL et MCALL, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Dans la base de données de publication du serveur de publication, utilisez l'instruction [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) pour modifier [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) afin qu'il retourne un script [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) pour les procédures stockées personnalisées INSERT, UPDATE et DELETE. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-change-the-method-of-propagating-changes-for-an-existing-article"></a>Pour modifier la méthode de propagation des modifications pour un article existant  
  
1.  Exécutez [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)dans la base de données de publication du serveur de publication. Spécifiez **\@publication**, **\@article**, la valeur **ins_cmd**, **upd_cmd** ou **del_cmd** pour **\@property**, ainsi que la méthode de propagation appropriée pour **\@value**.  
  
2.  Répétez l'étape 1 pour chaque méthode de propagation à modifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier le mode de propagation des modifications des articles transactionnels](../transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Créer une publication](create-a-publication.md)  
  
  
