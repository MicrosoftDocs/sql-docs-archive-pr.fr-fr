---
title: Se connecter à SQL Server par le biais d’un serveur proxy (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: de22ad6043c509f08471a6bea40c0efa18d76842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611281"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Se connecter à SQL Server par le biais d'un serveur proxy (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment se connecter à SQL Server via un serveur proxy dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Pour pouvoir écouter à distance au moyen de RWS (Remote WinSock), définissez la table d'adresses locales (LAT, Local Address Table) du serveur proxy pour que l'adresse du nœud à l'écoute se situe en dehors de la plage des entrées LAT.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Pour autoriser les connexions à SQL Server via Microsoft Proxy Server  
  
1.  Suivez les étapes décrites dans [Configurer un serveur pour écouter un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md) pour déterminer quels ports TCP/IP sont utilisés par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou pour configurer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour qu’il utilise le port de votre choix.  
  
2.  Dans votre serveur proxy, définissez la table d'adresses locales de ce serveur pour que l'adresse du nœud à l'écoute se situe en dehors de la plage des entrées de la table. Pour plus d'informations, consultez la documentation de votre serveur proxy.  
  
  
