---
title: Configuration réseau du serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- connections [SQL Server], server network configuration
- Database Engine [SQL Server], network configurations
- server network configuration [SQL Server]
- protocols [SQL Server], choosing
- ports [SQL Server], changing
- server configuration [SQL Server]
ms.assetid: 890c09a1-6dad-4931-aceb-901c02ae34c5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 97acd6deaa251d4eea9ef1e00c0554c13011c469
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706731"
---
# <a name="server-network-configuration"></a>Configuration réseau du serveur
  Les tâches de configuration réseau du serveur incluent l'activation de protocoles, la modification du port ou du canal utilisé par un protocole, la configuration du chiffrement, la configuration du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, l'exposition ou le masquage du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] sur le réseau et l'inscription du nom principal du serveur. La plupart du temps, vous n'avez pas besoin de modifier la configuration réseau du serveur. Reconfigurez uniquement les protocoles réseau du serveur si des spécifications réseau spéciales l'imposent.  
  
 La configuration réseau pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'effectue à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez l'utilitaire Réseau Serveur fourni avec ces produits.  
  
## <a name="protocols"></a>Protocoles  
 Utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour activer ou désactiver les protocoles employés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et pour configurer les options disponibles pour les protocoles. Vous pouvez spécifier plusieurs protocoles. Vous devez activer tous les protocoles que les clients doivent utiliser. Tous les protocoles ont un accès égal au serveur. Pour plus d’informations sur les protocoles à utiliser, consultez [Activer ou désactiver un protocole réseau de serveur](enable-or-disable-a-server-network-protocol.md).  
  
### <a name="changing-a-port"></a>Changement d'un port  
 Vous pouvez configurer le protocole TCP/IP pour écouter un port désigné. Par défaut, l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)] écoute le port TCP 1433. Les instances nommées du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et de [!INCLUDE[ssEW](../../includes/ssew-md.md)] sont configurées pour des ports dynamiques. Cela signifie qu'elles sélectionnent un port disponible lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser aide les clients à identifier le port au moment de leur connexion.  
  
 Lors d'une configuration pour des ports dynamiques, le port utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut changer à chaque démarrage. Lors de la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à travers un pare-feu, vous devez ouvrir le port utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Configurez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser un port spécifique, de façon que vous puissiez configurer le pare-feu pour permettre une communication au serveur. Pour plus d’informations, consultez [Configurer un serveur pour écouter un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
### <a name="changing-a-named-pipe"></a>Changement d'un canal nommé  
 Vous pouvez configurer le protocole de canal nommé de manière à écouter un canal nommé désigné. Par défaut, l'instance par défaut de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] est à l’écoute sur le canal \\\\.\pipe\sql\query pour l’instance par défaut et sur \\\\.\pipe\MSSQL$ *\<instancename>* \sql\query pour une instance nommée. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut être à l'écoute que sur un canal nommé, mais vous pouvez donner un autre nom au canal si vous le souhaitez. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser aide les clients à identifier le canal au moment de leur connexion. Pour plus d’informations, consultez [Configurer un serveur pour l’écoute d’un canal de remplacement &#40;Gestionnaire de configuration SQL Server&#41;](configure-a-server-to-listen-on-an-alternate-pipe.md).  
  
## <a name="force-encryption"></a>Forcer le chiffrement  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut être configuré pour imposer un chiffrement lors d'une communication avec des applications clientes. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="extended-protection-for-authentication"></a>Protection étendue de l'authentification  
 La prise en charge de la Protection étendue de l'authentification en utilisant la liaison de canal et la liaison de service est disponible pour les systèmes d'exploitation qui prennent en charge la Protection étendue. Pour plus d’informations, consultez [Se connecter au moteur de base de données à l’aide de la protection étendue](connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="authenticating-by-using-kerberos"></a>Authentification à l'aide de Kerberos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge l'authentification Kerberos. Pour plus d’informations, consultez [Inscrire un nom de principal du service pour les connexions Kerberos](register-a-service-principal-name-for-kerberos-connections.md) et [Gestionnaire de Configuration de Microsoft Kerberos pour SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
### <a name="registering-a-server-principal-name-spn"></a>Inscription d'un nom principal de service (SPN)  
 Le service d'authentification Kerberos utilise un nom de principal de service (SPN) pour authentifier un service. Pour plus d’informations, consultez [Inscrire un nom de principal du service pour les connexions Kerberos](register-a-service-principal-name-for-kerberos-connections.md).  
  
 Les noms de principaux du service peuvent également être utilisés pour sécuriser davantage l'authentification client lors d'une connexion avec NTLM. Pour plus d’informations, consultez [Se connecter au moteur de base de données à l’aide de la protection étendue](connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="sql-server-browser-service"></a>SQL Server Browser Service  
 Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser fonctionne sur le serveur et aide les ordinateurs clients à trouver des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser n'a pas besoin d'être configuré, mais doit fonctionner sous certains scénarios de connexion. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, consultez [Service SQL Server Browser &#40;moteur de base de données et SSAS&#41;](sql-server-browser-service-database-engine-and-ssas.md).  
  
## <a name="hiding-sql-server"></a>Masquage de SQL Server  
 Lors de l'exécution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser répond aux requêtes, avec le nom, la version et les informations de connexion de chaque instance installée. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'indicateur **HideInstance** indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ne doit pas répondre avec des informations sur cette instance de serveur. Les applications clientes peuvent toujours se connecter, mais elles doivent disposer des informations de connexion requises. Pour plus d’informations, consultez [Masquer une instance du moteur de base de données de SQL Server](../sql-server-database-engine-overview.md).  
  
## <a name="related-content"></a>Contenu associé  
 [Configuration du réseau client](client-network-configuration.md)  
  
 [Gérer les services du moteur de base de données](manage-the-database-engine-services.md)  
  
  
