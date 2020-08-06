---
title: Configurer un serveur de rapports en mode natif pour l’administration locale (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611561"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a>Configurer un serveur de rapports en mode natif pour l'administration locale (SSRS)
  Le déploiement d'un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur l'un des systèmes d'exploitation suivants requiert davantage d'étapes de configuration si vous souhaitez administrer l'instance du serveur de rapports localement. Cette rubrique explique comment configurer le serveur de rapports pour l'administration locale. Si vous n’avez pas encore installé ou configuré le serveur de rapports, consultez [installer SQL Server 2014 à partir de l’Assistant installation &#40;&#41;d'](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) installation et [gérer un serveur de rapports Reporting Services en mode natif](manage-a-reporting-services-native-mode-report-server.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 Étant donné que les systèmes d'exploitation indiqués limitent les autorisations, les membres du groupe Administrateurs local exécutent la plupart des applications comme s'ils utilisaient le compte Utilisateur standard.  
  
 Même si cette solution améliore la sécurité globale de votre système, elle vous empêche d'utiliser les attributions de rôle prédéfinies et intégrées que Reporting Services crée pour les administrateurs locaux.  
  
-   [Présentation des modifications de configuration](#bkmk_configuraiton_overview)  
  
-   [Pour configurer un serveur de rapports local et l'administration du gestionnaire de rapports](#bkmk_configure_local_server)  
  
-   [Pour configurer SQL Server Management Studio (SSMS) pour l'administration du serveur de rapports local](#bkmk_configure_ssms)  
  
-   [Pour configurer SQL Server Data Tools BI (SSDT) pour la publication sur un serveur de rapports local](#bkmk_configure_ssdt)  
  
-   [Informations supplémentaires](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a>Vue d’ensemble des modifications de configuration  
 Les modifications de configuration suivantes configurent le serveur afin d'utiliser des autorisations standard pour gérer le contenu et les opérations du serveur de rapports.  
  
-   Ajoutez les URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aux sites approuvés. Par défaut, Internet Explorer est exécuté en **Mode protégé**sur les systèmes d’exploitation répertoriés, une fonctionnalité qui empêche les demandes du navigateur d’atteindre les processus globaux qui s’exécutent sur le même ordinateur. Vous pouvez désactiver le mode protégé pour les applications du serveur de rapports en les ajoutant comme Sites de confiance.  
  
-   Créez les attributions de rôle qui vous accordent en tant qu'administrateur du serveur de rapports l'autorisation de gérer le contenu et les opérations sans devoir utiliser la fonctionnalité **Exécuter en tant qu'administrateur** sur Internet Explorer. En créant des attributions de rôle pour votre compte d'utilisateur Windows, vous accédez à un serveur de rapports avec les autorisations Gestionnaire de contenu et Administrateur système via des attributions de rôle explicites qui remplacent les attributions de rôle prédéfinies et intégrées créées par Reporting Services.  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a>Pour configurer le serveur de rapports local et l’administration de Gestionnaire de rapports  
 Complétez les étapes de configuration de cette section si vous souhaitez accéder à un serveur de rapports local et vous voyez des erreurs semblables à la suivante :  
  
-   L'utilisateur `'Domain\[user name]`» ne dispose pas des autorisations requises. Vérifiez que les autorisations suffisantes ont été accordées et qu'aucune restriction liée au contrôle de compte d'utilisateur (UAC) Windows ne pose problème.  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a>Paramètres du site de confiance dans le navigateur  
  
1.  Ouvrez une fenêtre du navigateur avec les autorisations Exécuter en tant qu'administrateur. Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, cliquez avec le bouton droit sur **Internet Explorer**et sélectionnez **Exécuter en tant qu’administrateur**.  
  
2.  Cliquez sur **Autoriser** pour continuer.  
  
3.  Dans l'adresse URL, entrez l'URL du Gestionnaire de rapports. Pour obtenir des instructions, consultez [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Cliquez sur **Outils**.  
  
5.  Cliquez sur **Options Internet**.  
  
6.  Cliquez sur **Sécurité**.  
  
7.  Cliquez sur **Sites de confiance**.  
  
8.  Cliquez sur **Sites**.  
  
9. Ajoutez `http://<your-server-name>`.  
  
10. Décochez la case **Nécessite la certification du serveur (https:) pour tous les sites dans cette zone** si vous n’utilisez pas HTTPS pour le site par défaut.  
  
11. Cliquez sur **Ajouter**.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> Paramètres du dossier du gestionnaire de rapports  
  
1.  Dans le Gestionnaire de rapports, sur la page d'accueil, cliquez sur **Paramètres du dossier**.  
  
2.  Dans la page Paramètres du dossier, cliquez sur **Sécurité**.  
  
3.  Cliquez sur **Nouvelle attribution de rôle**.  
  
4.  Dans le champ **Nom d'utilisateur ou de groupe** entrez votre compte d'utilisateur Windows au format : `<domain>\<user>`.  
  
5.  Sélectionnez **Gestionnaire de contenu**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a> Paramètres du site du gestionnaire de rapports  
  
1.  Ouvrez votre navigateur avec des privilèges d'administrateur et accédez au gestionnaire de rapports, `http://<server name>/reports`.  
  
2.  Cliquez sur **Paramètres du site** dans l'angle supérieur de la page d'accueil.  
  
    > [!TIP]  
    >  **Remarque :** si vous ne voyez pas l'option **Paramètre du site** , fermez et rouvrez votre navigateur et accédez au gestionnaire de rapports avec des privilèges d'administrateur.  
  
3.  Cliquez sur **sécurité**.  
  
4.  Cliquez sur **Nouvelle attribution de rôle**.  
  
5.  Dans le champ **Nom d'utilisateur ou de groupe** entrez votre compte d'utilisateur Windows au format : `<domain>\<user>`.  
  
6.  Sélectionnez **Administrateur système**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  Fermez le Gestionnaire de rapports.  
  
9. Rouvrez le Gestionnaire de rapports dans Internet Explorer, sans utiliser **Exécuter en tant qu’administrateur**.  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a>Pour configurer SQL Server Management Studio (SSMS) pour l’administration du serveur de rapports local  
 Par défaut, vous ne pouvez accéder à toutes les propriétés du serveur de rapports disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] à moins de démarrer [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des privilèges d'administrateur.  
  
 **Pour configurer les propriétés et attributions de rôles [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** , vous n'avez donc pas besoin de démarrer [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des autorisations élevées chaque fois :  
  
-   Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, sur **SQL Server 2014**, cliquez avec le bouton droit sur **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, puis cliquez sur **Exécuter en tant qu’administrateur**.  
  
-   Connectez-vous à votre serveur local [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Dans le nœud **Sécurité** , cliquez sur **Rôles système**.  
  
-   Cliquez avec le bouton droit sur **Administrateur système** , puis cliquez sur **Propriétés**.  
  
-   Dans la page **Propriétés de rôle système** , sélectionnez **Afficher les propriétés du serveur de rapports**. Sélectionnez toute autre propriété que vous souhaitez associer aux membres du rôle d'administrateur système.  
  
-   Cliquez sur **OK**.  
  
-   Fermez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Pour ajouter un utilisateur au rôle système « administrateur système », consultez la section [Paramètres du site du gestionnaire de rapports](#bkmk_configure_site_settings) plus haut dans cette rubrique.  
  
 Maintenant, lorsque vous ouvrez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et vous ne sélectionnez pas explicitement **Exécuter en tant qu'administrateur** , vous avez accès aux propriétés du serveur de rapports.  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a>Pour configurer SQL Server Data Tools BI (SSDT) pour la publication sur un serveur de rapports local  
 Si vous avez installé [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] sur l’un des systèmes d’exploitation répertoriés dans la première section de cette rubrique et que vous souhaitez que SSDT interagisse avec un serveur de rapports local en mode natif, vous rencontrerez des erreurs d’autorisation sauf si vous ouvrez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] avec des autorisations élevées ou si vous configurez des rôles Reporting Services. Par exemple, si vous n'avez pas les autorisations suffisantes, vous rencontrerez des avertissements semblables au suivant :  
  
-   Lorsque vous tentez de déployer des éléments de rapport sur le serveur de rapports local, vous voyez un message d'erreur similaire au suivant dans la fenêtre **Liste d'erreurs** :  
  
    -   Les autorisations accordées à l’utilisateur « Domaine\\<nom utilisateur\> » sont insuffisantes pour effectuer cette opération.  
  
 **Pour exécuter avec des autorisations élevées chaque fois que vous ouvrez SSDT :**  
  
1.  Dans l’écran d’accueil, tapez, `sql server` puis cliquez avec le bouton droit sur **SQL Server Data Tools pour Visual Studio**. Cliquez sur **Exécuter en tant qu’administrateur**  
  
     **Ou**, sur les systèmes d'exploitation plus anciens :  
  
     Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, sur **SQL Server 2014**, cliquez avec le bouton droit sur **Outils de données SQL Server**, puis cliquez sur **Exécuter en tant qu'administrateur**.  
  
2.  Cliquez sur **Continuer**.  
  
3.  Cliquez sur **Exécuter le programme**.  
  
 Vous devez maintenant être en mesure de déployer les rapports et autres éléments sur un serveur de rapports local.  
  
 **Pour configurer les propriétés et attributions de rôles [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous n'avez donc pas besoin de démarrer SSDT avec des autorisations élevées chaque fois :**  
  
-   Consultez les sections [Paramètres du dossier du gestionnaire de rapports](#bkmk_configure_folder_settings) et [Paramètres du site du gestionnaire de rapports](#bkmk_configure_site_settings) plus haut dans cette rubrique.  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a>Informations supplémentaires  
 Une étape de configuration supplémentaire et courante pour l'administration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste à ouvrir le port 80 dans le Pare-feu Windows pour autoriser l'accès à l'ordinateur du serveur de rapports. Pour obtenir des instructions, consultez [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer un serveur de rapports Reporting Services en mode natif](manage-a-reporting-services-native-mode-report-server.md)  
  
  
