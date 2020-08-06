---
title: Sauvegarder une clé primaire de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9a66d28fea8289719d3efb2351409e0f14379ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709087"
---
# <a name="back-up-a-database-master-key"></a>Sauvegarder une clé primaire de base de données
  Cette rubrique explique comment sauvegarder une clé principale de base de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La clé principale d'une base de données permet de chiffrer d'autres clés et certificats à l'intérieur d'une base de données. Si celle-ci est supprimée ou endommagée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] risque de ne pas pouvoir déchiffrer ces clés, et les données chiffrées qui les utilisent seront perdues. C'est pourquoi vous devez sauvegarder la clé principale de la base de données et stocker la sauvegarde dans un emplacement sécurisé, en dehors de votre lieu de travail.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour sauvegarder une clé principale de base de données à l'aide de Transact-SQL](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   La clé principale doit être ouverte et, par conséquent, déchiffrée avant d'être sauvegardée. Si elle est chiffrée avec la clé principale de service, il n'est pas nécessaire que la clé principale soit ouverte explicitement. En revanche, si la clé principale est chiffrée seulement à l'aide d'un mot de passe, elle doit être ouverte explicitement.  
  
-   Nous vous conseillons de sauvegarder la clé principale dès sa création et de stocker cette sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CONTROL sur la base de données.  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="Procedure"></a>Utilisation de SQL Server Management Studio avec Transact-SQL  
  
#### <a name="to-back-up-the-database-master-key"></a>Pour sauvegarder la clé principale de base de données  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contenant la clé principale de base de données à sauvegarder.  
  
2.  Choisissez un mot de passe qui servira à chiffrer la clé principale de base de données sur le support de sauvegarde. Ce mot de passe est sujet à des vérifications de complexité.  
  
3.  Procurez-vous un support de sauvegarde amovible pour stocker une copie de la clé sauvegardée.  
  
4.  Identifiez un répertoire NTFS où créer la sauvegarde de la clé. C'est à cet emplacement que vous allez créer le fichier spécifié à l'étape suivante. Le répertoire doit être protégé par des listes de contrôle d'accès très restrictives.  
  
5.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
7.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Assurez-vous que les deux sont spécifiques à votre installation de serveur et de clé.  
  
8.  Copiez le fichier sur le support de sauvegarde et vérifiez la copie.  
  
9. Conservez la sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
 Pour plus d’informations, consultez [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) et [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
  
