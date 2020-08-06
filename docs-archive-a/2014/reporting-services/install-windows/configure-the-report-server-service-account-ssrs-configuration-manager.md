---
title: Configurer le compte de service Report Server (Gestionnaire de configuration de SSRS) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: b860a9c916f7dd9c1bdef4f5218845c66239ebe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696479"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a>Configurer le compte de service Report Server (Gestionnaire de configuration de SSRS)

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est implémenté en tant que service unique qui contient un service Web Report Server, le Gestionnaire de rapports et une application de traitement en arrière-plan utilisée pour le traitement des rapports planifié et la remise d'abonnement. Cette rubrique explique comment le compte de service est configuré initialement et comment modifier le compte ou le mot de passe à l'aide de l'outil de configuration de Reporting Services.  
  
## <a name="initial-configuration"></a>Configuration initiale

 Le compte de service Report Server est défini pendant l'installation. Vous pouvez exécuter le service au moyen d'un compte d'utilisateur de domaine ou d'un compte intégré tel que `NetworkService`. Il n’existe pas de compte par défaut ; quel que soit le compte que vous spécifiez dans la page [configuration du serveur-comptes de service](../../sql-server/install/server-configuration-service-accounts.md) de l’Assistant Installation devient le compte initial du service Report Server.  
  
> [!IMPORTANT]
> Bien que le service Web Report Server et le Gestionnaire de rapports soient des applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)], elles ne s'exécutent pas sous le compte [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. L'architecture de service unique exécute les deux applications ASP.NET dans la même identité de processus Report Server. Il s'agit d'une modification importante par rapport aux versions précédentes, dans lesquelles le service Web Report Server et le Gestionnaire de rapports s'exécutaient sous l'identité du processus de travail [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] spécifiée dans les services Internet (IIS).
  
## <a name="changing-the-service-account"></a>Modification du compte de service

 Pour afficher et reconfigurer des informations sur le compte de service, utilisez toujours l'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les informations sur l'identité du service sont stockées en interne dans plusieurs emplacements. L'utilisation de l'outil garantit que toutes les références sont mises à jour en conséquence chaque fois que vous modifiez le compte ou le mot de passe. L'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] exécute les étapes supplémentaires suivantes pour s'assurer que le serveur de rapports reste disponible :  
  
- Il ajoute automatiquement le nouveau compte au groupe de serveurs de rapports créés sur l'ordinateur local. Ce groupe est spécifié dans les listes de contrôle d'accès qui assurent la sécurité des fichiers de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
- Il met à jour automatiquement les autorisations de connexion sur l’instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilisée pour héberger la base de données du serveur de rapports. Le nouveau compte est ajouté au rôle **RSExecRole**.  
  
     La connexion de base de données pour l'ancien compte n'est pas supprimée automatiquement. Assurez-vous de supprimer les comptes qui ne sont plus utilisés. Pour plus d’informations, consultez [Administrer une base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../report-server/report-server-database-ssrs-native-mode.md) dans la documentation en ligne de SQL Server.  
  
     L'accord des autorisations de base de données au nouveau compte de service a lieu uniquement si vous avez configuré en premier lieu la connexion de base de données du serveur de rapports de façon à utiliser le compte de service. Si vous avez configuré la connexion de base de données du serveur de rapports de façon à utiliser un compte d'utilisateur de domaine ou une connexion de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les informations de connexion ne sont pas affectées par la mise à jour du compte de service.  
  
- Il met à jour automatiquement la clé de chiffrement pour inclure les informations de profil du nouveau compte.  
  
    > [!NOTE]  
    > Si le serveur de rapports est intégré au déploiement avec montée en puissance parallèle, seul le serveur de rapports en cours de mise à jour est affecté. Il n'y a aucune incidence sur les clés de chiffrement des autres serveurs de rapports de ce déploiement.  
  
 Pour obtenir des instructions sur la façon de définir le compte, consultez [configurer un compte de Service &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).  
  
## <a name="choosing-an-account"></a>Choix d'un compte

 Vous pouvez configurer le service Report Server pour qu'il s'exécute sous l'un des types de comptes suivants :  
  
- Compte d'utilisateur Windows le moins privilégié  
  
- NetworkService  
  
- LocalSystem  
  
- LocalService  
  
 Il n'existe pas d'approche optimale unique pour le choix d'un type de compte. Chaque compte présente des avantages et des inconvénients que vous devez prendre en compte. Si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un serveur de production, les meilleures pratiques suggèrent de configurer le service pour qu'il s'exécute sous un compte d'utilisateur de domaine, afin d'éviter tout dommage étendu en cas de détournement d'un compte partagé par un utilisateur malveillant. Cela simplifie également l'audit de l'activité d'ouverture de session pour ce compte. L'un des inconvénients liés à l'utilisation d'un compte d'utilisateur Windows est que si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un réseau qui utilise l'authentification Kerberos, vous devez inscrire le service avec le compte d'utilisateur. Pour plus d’informations, consultez [Inscrire un nom de principal du service &#40;SPN&#41; pour un serveur de rapports](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Les instructions et les liens suivants de cette section peuvent vous aider à choisir l'approche la plus appropriée pour votre déploiement.  
  
- [Compte de Service &#40;&#41;en mode natif SSRS ](../../sql-server/install/service-account-ssrs-native-mode.md).  
  
- [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) dans la documentation en ligne de SQL Server.  
  
- [Guide de planification de la sécurité des services et des comptes de service](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).  
  
## <a name="updating-an-expired-password"></a>Mise à jour d'un mot de passe  expiré

 Si le service Report Server s'exécute sous un compte de domaine et que le mot de passe expire avant que vous puissiez le mettre à jour dans l'outil de configuration de Reporting Services, le service ne démarrera pas tant que vous n'aurez pas spécifié un nouveau mot de passe. Si le service ne peut pas être démarré, vous ne pouvez pas utiliser l'outil de configuration de Reporting Services pour vous connecter à ce serveur afin de mettre à jour le compte. Dans ce cas, vous devez utiliser une combinaison d'outils pour remettre le serveur en ligne.  
  
 Pour réinitialiser le mot de passe, procédez comme suit :  
  
1. Dans le menu **Démarrer** , pointez sur **panneau de configuration**, pointez sur outils d' **administration**, puis cliquez sur **services**.  
  
2. Cliquez avec le bouton droit sur **SQL Server Reporting Services**, puis sélectionnez **Propriétés**.  
  
3. Cliquez sur **ouvrir une session**, puis tapez le nouveau mot de passe.  
  
4. Après avoir mis à jour le mot de passe, démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et mettez à jour le mot de passe dans la page Compte de service. Cette étape supplémentaire est nécessaire pour mettre à jour les informations de compte stockées de manière interne par le serveur de rapports.  
  
 Si le mot de passe du compte de service pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] expire, l'erreur `rsReportServerDatabaseUnavailable` se produit si vous tentez de vous connecter au serveur de rapports. La réinitialisation du mot de passe résout cette erreur.  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a>Configuration du service Report Server pour un serveur de rapports intégré à SharePoint

 Si vous exécutez un serveur de rapports en mode intégré SharePoint, vous devez mettre à jour les informations de compte de service stockées dans la base de données de configuration SharePoint si l'une des conditions suivantes est remplie :  
  
- Modification du compte de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (par exemple, basculement de NetworkService vers un compte d'utilisateur de domaine).  
  
- Extension d'une batterie de serveurs SharePoint de façon à inclure une application Web SharePoint supplémentaire. Si la batterie de serveurs est configurée pour l'intégration au serveur de rapports et que l'application nouvellement ajoutée est configure pour s'exécuter sous un compte d'utilisateur différent de celui des autres applications de la batterie, vous devez mettre à jour les informations d'accès à la base de données.  
  
 Une fois les informations d'accès à la base de données réinitialisées, vous devez redémarrer le service [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] pour vous assurer que l'ancienne connexion n'est plus utilisée.  
  
1. Dans **Outils d’administration**, cliquez sur **administration centrale de SharePoint 2010**.  
  
2. Cliquez sur **gestion des applications**.  
  
3. Dans la section Reporting Services, cliquez sur **accorder l’accès à la base de données**.  
  
4. Cliquez sur **OK**. La boîte de dialogue Entrer les informations d'identification s'affiche.  
  
5. Entrez les informations d'identification d'un utilisateur membre du groupe Administrateurs local sur l'ordinateur qui héberge le serveur de rapports. Ces informations seront utilisées pour une connexion ponctuelle à l'ordinateur du serveur de rapports afin de récupérer les informations du compte de service. Le nom de connexion de base de données créé pour chaque compte de service est mis à jour dans les bases de données SharePoint.  
  
6. Pour redémarrer le service, cliquez sur **opérations**.  
  
7. Dans topologie et services, cliquez sur **services sur le serveur**.  
  
8. Pour application Web Windows SharePoint Services, cliquez sur **arrêter**.  
  
9. Attendez que le service s'arrête.  
  
10. Cliquez sur **Start**.  
  
> [!NOTE]  
> Les produits et technologies SharePoint 2010 requièrent des comptes de domaine pour la configuration du service comme l'intégration du mode Reporting Services SharePoint.  
  
## <a name="next-steps"></a>Étapes suivantes

 [Configurez un compte de service &#40;ssrs Configuration Manager&#41;compte de](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [service &#40;SSRS en mode natif&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [configurer des url de serveur de rapports &#40;SSRS Configuration Manager](configure-report-server-urls-ssrs-configuration-manager.md)&#41;gestionnaire de configuration de Reporting Services &#40;[en mode natif](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)&#41;
