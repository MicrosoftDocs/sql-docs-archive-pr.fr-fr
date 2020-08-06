---
title: Configuration du réseau client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], connections
- Database Engine [SQL Server], network configurations
- connections [SQL Server], client configuration
- client connections [SQL Server], about client network connections
- client computers [SQL Server]
- client connections [SQL Server]
- network connections [SQL Server], client configuration
ms.assetid: c382eacd-0a0c-40a4-958f-9b774eb2d734
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d0671a8d2913855fde047110d7907af8739dbd5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601103"
---
# <a name="client-network-configuration"></a>Configuration du réseau client
  Un logiciel client permet aux ordinateurs clients de se connecter à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un réseau. Un client est une application frontale utilisant les services fournis par un serveur tel que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. L'ordinateur sur lequel se trouve cette application est appelé *ordinateur client*.  
  
 Au niveau le plus simple, un client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut résider sur le même ordinateur qu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le plus souvent, cependant, un client se connecte à un ou plusieurs serveurs distants à travers un réseau. L'architecture client/serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lui permet de gérer de façon intégrée plusieurs clients et serveurs sur un réseau. Les configurations par défaut des clients suffisent à la plupart des situations.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent inclure des applications de différents types, telles que :  
  
-   Consommateurs OLE DB  
  
     Ces applications utilisent le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client pour se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur OLE DB sert d'interface entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications clientes, qui utilisent des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] telles que des ensembles de lignes OLE DB. L’utilitaire d’invite de commandes **sqlcmd** et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]sont des exemples d’applications OLE DB.  
  
-   Applications ODBC  
  
     Ces applications comprennent des utilitaires clients installés avec des versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tels que l’utilitaire d’invite de commandes **osql** , ainsi que d’autres applications qui utilisent le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client pour se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Clients DB-Library  
  
     Ces applications incluent l’utilitaire d’invite de commandes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **isql** et des clients écrits dans DB-Library. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assure une prise en charge pour les applications clientes utilisant DB-Library qui se limite aux fonctionnalités de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.  
  
> [!NOTE]  
>  Bien que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] prenne toujours en charge les connexions des applications existantes qui utilisent les API DB-Library et Embedded SQL, il n'inclut pas les fichiers ni la documentation nécessaires aux tâches de programmation dans les applications qui utilisent ces API. Une version future du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] n'intègrera plus la prise en charge des connexions à partir des applications DB-Library ou Embedded SQL. N'utilisez pas DB-Library ni Embedded SQL pour développer de nouvelles applications. Supprimez toutes les dépendances à DB-Library ou à Embedded SQL lorsque vous modifiez des applications existantes. À la place de ces API, utilisez l’espace de noms SQLClient ou une API telle que OLE DB ou ODBC. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’inclut pas la DLL DB-Library nécessaires à l’exécution de ces applications. Pour exécuter des applications DB-Library ou Embedded SQL, vous devez utiliser la DLL DB-Library à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5, de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 ou de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 Quel que soit le type d'application utilisé, la gestion d'un client consiste principalement à configurer sa connexion avec les composants serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En fonction des besoins spécifiques de votre site, la gestion du client va de la simple création du nom de l'ordinateur serveur à la génération d'une bibliothèque de configurations personnalisées permettant de prendre en charge un environnement multiserveur hétérogène.  
  
 La DLL de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client contient les bibliothèques réseau et est installée par le programme d'installation. Les protocoles réseau ne sont pas activés au démarrage des nouvelles installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les installations mises à niveau activent les protocoles activés précédemment. Les protocoles réseau sous-jacents sont installés en tant que partie intégrante de l'installation de Windows (ou à partir de l'icône Réseau du Panneau de configuration). Les outils ci-dessous permettent de gérer les clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestionnaire de configuration  
  
     Les composants réseau client et serveur sont gérés à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , qui associe l'utilitaire réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'utilitaire réseau client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le Gestionnaire de services des versions précédentes. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le Gestionnaire de configuration est un composant logiciel enfichable MMC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console). Il apparaît également comme un nœud dans le composant logiciel enfichable Windows Gestion de l'ordinateur. Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet d'activer, de désactiver, de configurer et de classer par priorité des bibliothèques réseau individuelles.  
  
-   Programme d’installation  
  
     Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour installer les composants réseau sur un ordinateur client. Les bibliothèques réseau individuelles peuvent être activées ou désactivées pendant l'installation si celle-ci est démarrée à partir de l'invite de commandes.  
  
-   Administrateur des sources de données ODBC  
  
     L'Administrateur des sources de données ODBC vous permet de créer et de modifier des sources de données ODBC sur des ordinateurs exécutant le système d'exploitation Microsoft Windows.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configurer des protocoles clients](configure-client-protocols.md)  
  
 [Créer ou supprimer un alias de serveur devant être utilisé par un client &#40;Gestionnaire de configuration SQL Server&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
 [Connexion à SQL Server](logging-in-to-sql-server.md)  
  
 [Ouvrir l'Administrateur de la source de données ODBC](open-the-odbc-data-source-administrator.md)  
  
 [Vérifier la version des pilotes ODBC de SQL Server &#40;Windows&#41;](check-the-odbc-sql-server-driver-version-windows.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Configuration réseau du serveur](server-network-configuration.md)  
  
 [Gérer les services du moteur de base de données](manage-the-database-engine-services.md)  
  
  
