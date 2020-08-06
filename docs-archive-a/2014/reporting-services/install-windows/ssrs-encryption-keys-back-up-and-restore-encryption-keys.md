---
title: Sauvegarder et restaurer les clés de chiffrement Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backing up encryption keys [Reporting Services]
- restoring encryption keys [Reporting Services]
- encryption keys [Reporting Services]
- symmetric keys [Reporting Services]
ms.assetid: 6773d5df-03ef-4781-beb7-9f6825bac979
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8e7e61f58632898fc6150210598a671157639a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710303"
---
# <a name="back-up-and-restore-reporting-services-encryption-keys"></a>Sauvegarder et restaurer les clés de chiffrement Reporting Services
  Une part importante de la configuration d'un serveur de rapports est réservée à la création d'une copie de sauvegarde de la clé symétrique utilisée pour le chiffrement d'informations confidentielles. Cet exemplaire de clé sauvegardée est nécessaire dans de nombreuses opérations courantes. Elle vous permet de réutiliser une base de données de serveur de rapports existante dans une nouvelle installation.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint  
  
 La restauration de la copie de sauvegarde de la clé de chiffrement est indispensable lorsque l'un des événements suivants se produit :  
  
-   Modification effectuée sur le nom du compte de service Windows Report Server ou réinitialisation du mot de passe. Lorsque vous utilisez le Gestionnaire de configuration de Reporting Services, la sauvegarde de la clé est intégrée à une opération de changement de nom du compte de service.  
  
    > [!NOTE]  
    >  La réinitialisation et la modification d'un mot de passe sont deux opérations différentes. La réinitialisation d'un mot de passe requiert l'autorisation permettant de remplacer des informations de compte sur le contrôleur de domaine. Cette opération est effectuée par un administrateur système lorsqu'un utilisateur a oublié ou ne connaît pas un mot de passe particulier. Seule la réinitialisation d'un mot de passe nécessite la restauration de la clé symétrique. Le changement régulier d'un mot de passe de compte ne vous oblige pas à réinitialiser la clé symétrique.  
  
-   Attribution d'un nouveau nom à l'ordinateur ou à l'instance qui héberge le serveur de rapports (une instance de serveur de rapports repose sur un nom d'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ).  
  
-   Migration d'une installation de serveur de rapports ou configuration d'un serveur de rapports afin d'utiliser une base de données de serveur de rapports différente.  
  
-   Récupération d'une installation de serveur de rapports suite à une défaillance matérielle.  
  
 Une seule copie de sauvegarde de la clé symétrique est nécessaire. Il existe une correspondance unilatérale entre une base de données de serveur de rapports et une clé symétrique. Bien que vous n'ayez besoin que d'un seul exemplaire de clé sauvegardé, il peut s'avérer nécessaire de restaurer cette clé à plusieurs reprises si vous exécutez plusieurs serveurs de rapports dans un modèle de déploiement évolutif. En effet, chaque instance de serveur de rapports nécessite sa copie de la clé symétrique pour verrouiller et déverrouiller des données dans la base de données du serveur de rapports.  
  
  
## <a name="backing-up-the-encryption-keys"></a>Sauvegarde des clés de chiffrement  
 La sauvegarde de la clé symétrique est un processus qui consiste à écrire la clé dans le fichier que vous spécifiez, puis à brouiller ces données à l'aide du mot de passe que vous fournissez. En aucun cas la clé symétrique ne peut être conservée sans être chiffrée, vous devez donc fournir un mot de passe afin de chiffrer la clé au moment de son enregistrement sur un disque. Une fois le fichier créé, vous devez le stocker dans un endroit sécurisé et **vous souvenir du mot de passe** qui permet de déverrouiller le fichier. Pour sauvegarder la clé symétrique, utilisez les outils suivants :  
  
 **Mode natif :** le Gestionnaire de configuration de Reporting Services ou l'utilitaire **rskeymgmt** .  
  
 **Mode SharePoint :** pages de l'Administration centrale de SharePoint ou PowerShell.  
  
####  <a name="backup-sharepoint-mode-report-servers"></a><a name="bkmk_backup_sharepoint"></a> Sauvegarde de serveurs de rapports en mode SharePoint  
 Pour les serveurs de rapports en mode SharePoint, vous pouvez utiliser des commandes PowerShell ou utiliser les pages de gestion pour l'application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez la section « Gestion des clés » de l’article [Gérer une application de service Reporting Services SharePoint](../manage-a-reporting-services-sharepoint-service-application.md).  
  
####  <a name="back-up-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_backup_configuration_manager"></a> Sauvegarder les clés de chiffrement - Gestionnaire de configuration Reporting Services (mode natif)  
  
1.  Démarrez le Gestionnaire de configuration de Reporting Services et connectez-vous à l'instance de serveur de rapports à configurer.  
  
2.  Cliquez sur **Clés de chiffrement**, puis sur **Sauvegarder**.  
  
3.  Tapez un mot de passe fort.  
  
4.  Spécifiez un fichier pour contenir la clé stockée. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ajoute une extension de fichier .snk au fichier. Prévoyez de conserver le fichier à part sur un disque, pour qu'il soit indépendant du serveur de rapports.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="back-up-encryption-keys--rskeymgmt-native-mode"></a><a name="bkmk_backup_rskeymgmt"></a>Sauvegarder des clés de chiffrement-rskeymgmt (mode natif)  
  
1.  Exécutez le fichier **rskeymgmt.exe** localement sur l'ordinateur qui héberge le serveur de rapports. Vous devez utiliser l'argument d'extraction `-e` pour copier la clé, fournir un nom de fichier et spécifier un mot de passe. L'exemple suivant illustre les arguments que vous devez spécifier :  
  
    ```cmd
    rskeymgmt -e -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="restore-encryption-keys"></a>Restaurer les clés de chiffrement  
 La restauration de la clé symétrique remplace la clé existante qui est stockée dans la base de données du serveur de rapports. Cette opération permet de remplacer une clé devenue inutilisable par son exemplaire précédemment enregistré sur disquette. La restauration des clés de chiffrement se traduit par les actions suivantes :  
  
-   La clé symétrique est ouverte à l'aide du fichier de sauvegarde protégé par mot de passe.  
  
-   La clé symétrique est chiffrée à l'aide de la clé publique du service Windows Report Server.  
  
-   La clé symétrique chiffrée est stockée dans la base de données du serveur de rapports.  
  
-   Les données de clé symétrique préalablement stockées (par exemple, des informations de clé déjà présentes dans la base de données du serveur de rapports en raison d'un précédent déploiement) sont supprimées.  
  
 Pour restaurer une clé de chiffrement, vous devez posséder un exemplaire de la clé de chiffrement dans un fichier et connaître le mot de passe permettant de déverrouiller l'exemplaire stocké. Si vous détenez la clé et le mot de passe, procédez à la restauration en exécutant l'outil de configuration de Reporting Services ou l'utilitaire **rskeymgmt** . La clé symétrique doit être identique à l'exemplaire qui verrouille et déverrouille les données chiffrées stockées à ce moment-là dans la base de données du serveur de rapports. Si vous restaurez un exemplaire non valide, le serveur de rapports est incapable d'accéder à ces données. Vous serez amené à supprimer toutes les valeurs chiffrées si jamais la restauration d'une clé valide est impossible. Si, pour une raison quelconque, vous ne pouvez pas restaurer la clé de chiffrement (vous ne possédez pas de copie de sauvegarde par exemple), supprimez la clé et le contenu chiffré. Pour plus d’informations, consultez [Supprimer et recréer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md). Pour plus d’informations sur la création de clés symétriques, consultez [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-encryption-keys-initialize-a-report-server.md).  
  
####  <a name="restore-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_restore_configuration_manager"></a>Restaurer les clés de chiffrement-Gestionnaire de configuration de Reporting Services (mode natif)  
  
1.  Démarrez le Gestionnaire de configuration de Reporting Services et connectez-vous à l'instance de serveur de rapports à configurer.  
  
2.  Dans la page clés de chiffrement, cliquez sur **restaurer**.  
  
3.  Sélectionnez le fichier .snk contenant la copie de sauvegarde.  
  
4.  Tapez le mot de passe permettant de déverrouiller le fichier.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="restore-encryption-keys---rskeymgmt-native-mode"></a><a name="bkmk_restore_rskeymgmt"></a> Restaurer les clés de chiffrement - rskeymgmt (mode natif)  
  
1.  Exécutez le fichier **rskeymgmt.exe** localement sur l'ordinateur qui héberge le serveur de rapports. Utilisez l'argument `-a` pour restaurer les clés. Vous devez fournir un nom de fichier complet et spécifier un mot de passe. L'exemple suivant illustre les arguments que vous devez spécifier :  
  
    ```cmd
    rskeymgmt -a -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-encryption-keys-manage-encryption-keys.md)  
