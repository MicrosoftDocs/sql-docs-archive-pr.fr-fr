---
title: PH timeout (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697159"
---
# <a name="ph-timeout-server-configuration-option"></a>PH timeout (option de configuration de serveur)
  Utilisez l’option ph timeout pour spécifier le délai, en secondes, dont dispose le gestionnaire de protocole de texte intégral pour se connecter à une base de données. La valeur par défaut est 60 secondes. Augmentez la valeur de ph timeout si vos tentatives de connexion dépassent ce délai en raison de problèmes réseau temporaires.  
  
 Le gestionnaire de protocole de texte intégral est hébergé dans l'hôte de démon de filtre et sert à rechercher dans SQL Server les données à indexer en texte intégral. Pour plus d’informations sur les composants de la recherche en texte intégral, consultez [Recherche en texte intégral](../../relational-databases/search/full-text-search.md).  
  
 Lorsque vous tentez d'extraire une ligne de données, si le gestionnaire de protocole ne peut pas se connecter à SQL Server dans le délai spécifié, il émet une erreur de temporisation pour cette ligne. L'outil d'extraction de texte intégral réessaiera ultérieurement. Pour plus d’informations sur l’outil d’extraction de texte intégral, consultez [Alimenter des index de recherche en texte intégral](../../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
