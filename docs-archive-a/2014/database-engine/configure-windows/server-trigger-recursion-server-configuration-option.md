---
title: server trigger recursion (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23a4997bd1a6f8b2c04af34d5cdc3229575901a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707851"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion (Option de configuration de serveur)
  Utilisez l’option **server trigger recursion** pour permettre ou non l’exécution de manière récursive des déclencheurs au niveau du serveur. Lorsque cette option a la valeur 1 (ON), les déclencheurs au niveau du serveur peuvent être exécutés de manière récursive. Lorsqu'elle a la valeur 0 (OFF), les déclencheurs ne peuvent pas être exécutés de manière récursive. Seule la récursivité directe est désactivée lorsque l'option server trigger recursion a la valeur 0 (OFF). (Pour désactiver la récursivité indirecte, affectez à l’option **nested triggers** la valeur 0.) La valeur par défaut de cette option est 1 (ON). Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
 Pour plus d’informations, consultez [Créer des déclencheurs imbriqués](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
