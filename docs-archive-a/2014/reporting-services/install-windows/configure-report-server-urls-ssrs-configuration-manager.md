---
title: Configurer des URL de serveurs de rapports (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Server Windows service, virtual directories
- report servers [Reporting Services], virtual directories
- virtual directories [Reporting Services]
- Report Manager [Reporting Services], virtual directories
ms.assetid: a0134ef0-086c-443e-93b9-7213a3d76393
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e32135ce1affb8e92ce1bdbac4f7fcb6e22326f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601974"
---
# <a name="configure-report-server-urls--ssrs-configuration-manager"></a>Configurer des URL de serveurs de rapports (Gestionnaire de configuration de SSRS)
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les URL permettent d'accéder au service Web Report Server et au Gestionnaire de rapports. Avant de pouvoir utiliser l'une et l'autre application, vous devez configurer au moins une URL pour le service Web et pour le Gestionnaire de rapports. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit des valeurs par défaut pour les URL des deux applications qui s’accommodent bien à la plupart des scénarios de déploiement, dont les déploiements côte à côte avec d’autres applications et services web.  
  
-   Si vous avez installé la configuration par défaut, les URL ont été créées automatiquement à l'aide des valeurs par défaut.  
  
-   Si vous utilisez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour créer ou modifier les URL, vous pouvez accepter les valeurs par défaut pour une URL ou spécifier des valeurs personnalisées. Un lien de test de l'URL apparaît sur la page lorsque vous définissez l'URL afin que vous puissiez confirmer immédiatement que les paramètres vous avez spécifiés résultent en une connexion valide. Pour obtenir des instructions pas à pas sur la configuration et le test d’une URL, consultez [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md).  
  
## <a name="defining-a-report-server-url"></a>Définition d'une URL de serveur de rapports  
 L'URL identifie précisément l'emplacement d'une instance d'une application du serveur de rapports sur votre réseau. Lorsque vous créez une URL de serveur de rapports, vous devez spécifier les éléments suivants.  
  
|Élément|Description|  
|----------|-----------------|  
|Nom de l’hôte|Un réseau TCP/IP utilise une adresse IP pour identifier de manière unique un périphérique sur le réseau. Il existe une adresse IP physique pour chaque carte réseau installée dans un ordinateur. Si l'adresse IP est résolue en en-tête d'hôte, vous pouvez spécifier l'en-tête de l'hôte. Si vous déployez le serveur de rapports sur un réseau d'entreprise, vous pouvez utiliser le nom réseau de l'ordinateur.|  
|Port|Un port TCP est un point de terminaison sur le périphérique. Le serveur de rapports écoute les demandes sur un port désigné.|  
|Répertoire virtuel|Un port est souvent partagé par plusieurs applications ou services Web. Pour cette raison, une URL de serveur de rapports inclut toujours un répertoire virtuel qui correspond à l'application obtenant la demande. Vous devez spécifier des noms de répertoire virtuel uniques pour chaque application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui écoute sur les mêmes port et adresse IP.|  
|Paramètres SSL|Les URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être configurées pour utiliser un certificat SSL existant que vous avez installé précédemment sur l'ordinateur. Pour plus d’informations, consultez [Configurer des connexions SSL sur un serveur de rapports en mode natif](../security/configure-ssl-connections-on-a-native-mode-report-server.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
## <a name="default-urls"></a>URL par défaut  
 Lorsque vous accédez à un serveur de rapports ou au Gestionnaire de rapports via son URL, celle-ci doit inclure le nom d'hôte et pas l'adresse IP. Sur un réseau TCP/IP, l'adresse IP se résout en un nom d'hôte (ou le nom de réseau de l'ordinateur). Si vous avez utilisé les valeurs par défaut pour configurer les URL, vous devez être en mesure d'accéder au service Web Report Server à l'aide d'URL qui spécifient le nom d'ordinateur ou localhost comme nom d'hôte :  
  
-   http:// \<computername> /reportserver  
  
-   http://localhost/reportserver  
  
 Les paramètres qui rendent cet URL disponibles apparaissent dans le tableau suivant. Ce tableau montre les valeurs par défaut qui activent une connexion de serveur de rapports via les URL incluant un nom d'hôte :  
  
|Élément|Valeur|Explication|  
|----------|-----------|-----------------|  
|Adresse IP|Assigné|Le service DNS (Domain Name Service) de votre réseau résout le nom d'hôte sur l'URL en adresse IP de l'ordinateur. Tant que l'adresse IP est spécifiée dans l'URL que vous définissez, une demande envoyée à un hôte spécifique atteint sa cible.|  
|Port|80|Le port 80 est le port par défaut pour les connexions TCP/IP sur un ordinateur. Comme le serveur de rapports écoute sur le port 80, vous pouvez omettre le numéro de port de l'URL. Si vous spécifiez un autre port, vous devez le spécifier dans l'URL.|  
|Répertoire virtuel|ReportServer|Remarquez que les deux exemples d'URL incluent le nom de répertoire virtuel. À moins que vous ne personnalisiez la définition d'URL, vous devez toujours spécifier le nom du répertoire virtuel de l'application dans l'URL.|  
  
> [!NOTE]  
>  Une réservation d'URL sous-jacente active tout nom d'hôte valide à utiliser dans une URL. L'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crée une réservation d'URL dans HTTP.SYS à l'aide de la syntaxe qui permet aux variations du nom d'hôte de se résoudre en une instance de serveur de rapports particulière. Pour plus d’informations sur les réservations d’URL, consultez [À propos des réservations et de l’inscription d’URL &#40;Gestionnaire de configuration de SSRS&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md).  
  
## <a name="server-side-permissions-on-a-report-server-url"></a>Autorisations côté serveur sur une URL de serveur de rapports  
 Les autorisations sur chaque point de terminaison d'une URL sont accordées exclusivement au compte de service Report Server. Seul ce compte possède les droits pour accepter les demandes dirigées vers les URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les listes de contrôle d'accès discrétionnaire (DACL) sont créées et maintenues pour le compte lorsque vous configurez l'identité de service à travers le programme d'installation ou l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous modifiez le compte de service, l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] met à jour toutes les réservations d'URL que vous avez créées pour recueillir les nouvelles informations sur le compte. Pour plus d’informations, consultez [Syntaxe de réservation d’URL &#40;Gestionnaire de configuration de SSRS&#41;](url-reservation-syntax-ssrs-configuration-manager.md).  
  
## <a name="authenticating-client-requests-sent-to-a-report-server-url"></a>Authentification des demandes de clients envoyées à une URL de serveur de rapports  
 Par défaut, le type d'authentification pris en charge sur les points de terminaison d'URL est l'authentification Windows. Il s'agit de l'extension de sécurité par défaut. Si vous implémentez un fournisseur d'authentifications personnalisé ou par formulaire, vous devez modifier les paramètres d'authentification sur le serveur de rapports. Le cas échéant, vous pouvez aussi modifier les paramètres d'authentification Windows afin qu'ils correspondent au sous-système d'authentification utilisé dans votre réseau. Pour plus d’informations, consultez [Authentification avec le serveur de rapports](../security/authentication-with-the-report-server.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)  
 Cette rubrique fournit des instructions pour définir et modifier une réservation d'URL dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [À propos des réservations et de l’inscription d’URL &#40;Gestionnaire de configuration de SSRS&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md)  
 Les URL sont utilisées pour accéder aux applications et aux rapports. Cette rubrique explique les URL d'application et les URL par défaut, ainsi que la façon dont l'inscription et les réservations d'URL fonctionnent dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Syntaxe de réservation d’URL &#40;Gestionnaire de configuration de SSRS&#41;](url-reservation-syntax-ssrs-configuration-manager.md)  
 Les réservations d’URL par défaut que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise sont valides pour la plupart des scénarios. Toutefois, si vous souhaitez restreindre l'accès ou étendre le déploiement pour activer l'accès Internet ou extranet, il se peut que vous ayez à personnaliser les paramètres pour qu'ils correspondent à vos impératifs. Cette rubrique décrit la syntaxe d'une réservation d'URL et fournit des recommandations pour créer des réservations personnalisées pour votre déploiement.  
  
 [URL des fichiers de configuration &#40;Gestion de configuration de SSRS&#41;](urls-in-configuration-files-ssrs-configuration-manager.md)  
 Le fichier RSReportServer.config contient plusieurs entrées pour les réservations d'URL et les URL utilisées par le Gestionnaire de rapports et la remise du courrier électronique du serveur de rapports. Cette rubrique résume les paramètres de configuration d'URL afin que vous puissiez apprendre à les comparer.  
  
 [Réservations d’URL pour les déploiements de serveur de rapports multi-instance &#40;Gestionnaire de configuration de SSRS&#41;](url-reservations-for-multi-instance-report-server-deployments.md)  
 Lorsque vous installez plusieurs instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un même ordinateur, vous augmentez la probabilité de rencontrer une duplication d'URL lors de l'inscription. Pour éviter ces erreurs, suivez les recommandations de cette rubrique pour créer des réservations d'URL spécifiques à l'instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une URL &#40;SSRS Configuration Manager&#41;](configure-a-url-ssrs-configuration-manager.md)   
 [URL du service Web &#40;SSRS en mode natif&#41;](../../sql-server/install/web-service-url-ssrs-native-mode.md)  
  
  
