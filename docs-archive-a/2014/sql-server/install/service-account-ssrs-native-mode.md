---
title: Compte de service (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serviceaccount.F1
ms.assetid: face8120-4d32-4c6c-a1e8-99f27d1ff15d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2734be073896dbf41e3628c43b78ea30f80b6adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704687"
---
# <a name="service-account-ssrs-native-mode"></a>Compte de service (SSRS en mode natif)
  Utilisez la page Compte de service pour spécifier le compte sous lequel le service Report Server est exécuté. Ce compte est au départ configuré pendant l'installation. Vous pouvez le modifier si vous souhaitez modifier le compte ou le mot de passe. Le service Web Report Server, le Gestionnaire de rapports et l'application de traitement en arrière-plan s'exécutent tous sous l'identité du service que vous spécifiez dans cette page.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.  
  
 Le compte que vous spécifiez pour le service Report Server requiert une autorisation pour accéder au Registre, aux fichiers programme de serveur de rapports et à la base de données du serveur de rapports. Toutes les autorisations sont configurées automatiquement pour le compte lorsque vous utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour définir le compte. Si vous utilisez le compte de service pour vous connecter à la base de données du serveur de rapports, le Configuration Manager crée une connexion de base de données pour le compte et configure les autorisations de base de données en affectant le compte au RSExecRole sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance qui héberge la base de données du serveur de rapports. La base de données du serveur de rapports est le seul magasin de données dans lequel un serveur de rapports écrit. Le compte de service ne requiert pas d'autorisations à d'autres magasins de données.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et sélectionnez le lien dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!IMPORTANT]  
>  Lorsque vous devez mettre à jour le compte ou le mot de passe, il est vivement recommandé d'utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . L'utilisation du Gestionnaire de configuration pour mettre à jour le compte garantit que les autres paramètres internes qui dépendent de l'identité de service sont mis à jour automatiquement en même temps.  
  
## <a name="options"></a>Options  
 **Utiliser un compte intégré**  
 Sélectionnez **Service réseau**, **Système Local**ou **Service local** dans la liste. Seul **Service réseau** est recommandé ; toutefois, vous pouvez configurer le compte de façon à utiliser tout compte disponible.  
  
 **Utiliser un autre compte**  
 Sélectionnez cette option pour spécifier un compte d'utilisateur Windows. Vous pouvez entrer un compte d'utilisateur Windows local ou un compte d'utilisateur de domaine. Spécifiez un compte de domaine au format suivant : * \<domain> \\<utilisateur \> *. Spécifiez un compte d’utilisateur Windows local dans ce format : * \<computer name> \\<utilisateur \> *. Vous pouvez sélectionner uniquement un compte existant ; vous ne pouvez pas créer de nouveaux comptes dans l'outil Configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Le nom du compte ne doit pas comporter plus de 20 caractères.  
  
 Si votre réseau utilise l'authentification Kerberos et que vous configurez le serveur de rapports pour s'exécuter sous un compte d'utilisateur de domaine, vous devez inscrire le service avec le compte d'utilisateur. Pour plus d’informations, consultez [Inscrire un nom de principal du service &#40;SPN&#41; pour un serveur de rapports](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Si vous changez de type de compte (par exemple, en remplaçant un compte Windows par un autre ou en remplaçant un compte intégré par un compte de domaine Windows), vous serez invité à créer une copie de sauvegarde de la clé de chiffrement. La copie de sauvegarde sera restaurée automatiquement lorsque vous sélectionnerez le nouveau compte.  
  
> [!NOTE]  
>  Le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vous invite à sauvegarder et à restaurer la clé de chiffrement à chaque modification du compte de service. Ces étapes sont nécessaires pour garantir que les données chiffrées restent disponibles pour le serveur de rapports. Pour plus d’informations sur ces actions, consultez [clés de chiffrement &#40;SSRS en mode natif&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).  
  
 De plus, si vous disposez d'un serveur de rapports configuré pour s'exécuter en mode intégré SharePoint et que vous modifiez le compte de service à l'aide du Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez également ouvrir l'Administration centrale de SharePoint et vous servir de la page [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **de** pour réappliquer les paramètres du serveur de rapport et de l'instance. Cette étape accordera aux bases de données SharePoint le nouvel accès au compte de service, requis pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à un produit ou une technologie SharePoint. Pour plus d’informations sur la façon d’accorder l’accès à la base de données dans l’administration centrale de SharePoint, consultez [configuration et administration d’un serveur de rapports &#40;Reporting Services le mode sharepoint&#41;](../../../2014/reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md) et [Reporting Services l’installation du mode sharepoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
## <a name="choosing-an-account"></a>Choix d'un compte  
 Pour de meilleurs résultats, spécifiez un compte qui a des autorisations de connexion réseau, avec un accès aux contrôleurs de domaine réseau et aux passerelles ou serveurs SMTP d'entreprise. Le tableau suivant fournit une synthèse des comptes et des recommandations pour leur utilisation.  
  
|Compte|Explication|  
|-------------|-----------------|  
|Comptes d'utilisateurs de domaine|Si vous avez un compte d'utilisateur de domaine Windows qui possède les autorisations minimales requises pour les opérations de serveur de rapports, vous devez l'utiliser.<br /><br /> Un compte d'utilisateur de domaine est recommandé car il isole le service Report Server des autres applications. L'exécution de plusieurs applications sous un compte partagé, tel que Service réseau, accroît le risque qu'un utilisateur malveillant prenne le contrôle du serveur de rapports car une violation de la sécurité pour l'une des applications peut facilement s'étendre à toutes les applications qui s'exécutent sous le même compte.<br /><br /> Un compte d'utilisateur de domaine est requis si vous configurez le serveur de rapports pour la délégation contrainte, ou pour le mode intégré SharePoint avec des produits SharePoint 2010 qui requièrent des comptes d'utilisateurs de domaine plutôt que des comptes d'ordinateurs intégrés.<br /><br /> Notez que si vous utilisez un compte d'utilisateur de domaine, vous devrez modifier régulièrement le mot de passe si votre organisation impose une stratégie d'expiration des mots de passe. Vous devrez peut-être également inscrire le service avec le compte d'utilisateur. Pour plus d’informations, consultez [Inscrire un nom de principal du service &#40;SPN&#41; pour un serveur de rapports](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).<br /><br /> Évitez d'utiliser un compte d'utilisateur Windows local. En général, les comptes locaux ne disposent pas des autorisations suffisantes pour accéder aux ressources sur d'autres ordinateurs. Pour plus d’informations sur la manière dont l’utilisation d’un compte local limite la fonctionnalité du serveur de rapports, consultez [Considérations relatives à l’utilisation des comptes locaux](#localaccounts) dans cette rubrique.|  
|**Service réseau**|**Service réseau** est un compte intégré doté des privilèges minimaux, qui possède les autorisations d’ouverture de session sur le réseau. Ce compte est recommandé si vous n'avez pas de compte d'utilisateur de domaine disponible ou si vous souhaitez éviter toute interruption de service qui peut se produire à cause des stratégies d'expiration de mot de passe.<br /><br /> Si vous sélectionnez **Service réseau**, essayez de réduire le nombre d’autres services qui s’exécutent sous le même compte. Une violation de la sécurité pour l'une des applications compromettra la sécurité de toutes les autres applications qui s'exécutent sous le même compte.|  
|**Service local**|**Service local** est un compte prédéfini qui s’apparente à un compte d’utilisateur Windows local authentifié. Les services qui s’exécutent au moyen du compte **Service local** accèdent aux ressources réseau dans le cadre d’une session nulle, sans informations d’identification. Ce compte ne convient pas aux scénarios de déploiement intranet où le serveur de rapports doit se connecter à une base de données de serveur de rapports distante ou à un contrôleur de domaine réseau afin d'authentifier un utilisateur avant d'ouvrir un rapport ou de traiter un abonnement.|  
|**Système local**|**Système local** est un compte doté de privilèges élevés qui n’est pas obligatoire pour l’exécution d’un serveur de rapports. Évitez ce compte pour les installations de serveur de rapports. Choisissez un compte de domaine ou **Service réseau** à la place.|  
  
##  <a name="considerations-for-using-local-accounts"></a><a name="localaccounts"></a>Considérations relatives à l’utilisation des comptes locaux  
 La principale considération liée à l'utilisation des comptes locaux concerne l'obligation, pour le serveur de rapports, de pouvoir accéder aux serveurs de base de données, serveurs de messagerie et contrôleurs de domaine distants. Si vous configurez le serveur de rapports pour qu'il s'exécute en tant que compte d'utilisateur Windows local, Service local ou Système Local, vous introduisez des considérations qui doivent être prises en compte lors de la définition d'autres paramètres de configuration et de la création et remise d'abonnement :  
  
-   L'exécution du service sous un compte local limitera ultérieurement vos options si vous configurez une connexion à une base de données de serveur de rapports distante. En particulier, si vous utilisez une base de données de serveur de rapports distante, vous devez configurer la connexion afin d'utiliser un compte d'utilisateur de domaine ou un utilisateur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui dispose de l'autorisation d'ouverture de session sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distante.  
  
-   L'exécution du service sous un compte local introduira de nouvelles conditions requises en matière de création d'abonnement. Le serveur de rapports stocke des informations sur l'utilisateur qui crée l'abonnement. Si l'utilisateur crée l'abonnement alors qu'il est connecté sous un compte de domaine, le service Report Server essaie de se connecter à un contrôleur de domaine pour authentifier l'utilisateur lors du traitement de l'abonnement. Si le service s'exécute sous un compte local, la demande d'authentification échoue lorsque le serveur de rapports essaie d'envoyer la demande à un contrôleur de domaine distant. Pour contourner cette limitation, vous pouvez utiliser une extension personnalisée d'authentification basée sur les formulaires ou faire en sorte que tous les utilisateurs se connectent à un serveur de rapports sous un compte d'utilisateur local.  
  
-   L'exécution du service sous un compte local introduira de nouvelles conditions requises en matière de remise des abonnements. Certaines extensions de remise ont les informations du compte d'utilisateur dans la définition de l'abonnement. Si vous envoyez des rapports à des adresses de messagerie basées sur des comptes d'utilisateur de domaine et que vous exécutez le service Report Server sous un compte local, il ne peut pas accéder à un contrôleur de domaine distant pour résoudre le compte de messagerie cible.  
  
-   Les comptes de service Windows intégrés (Service local ou Service réseau) ne sont pas pris en charge comme comptes de service du serveur de rapports sur un ordinateur qui est contrôleur de domaine.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer un compte de service &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
