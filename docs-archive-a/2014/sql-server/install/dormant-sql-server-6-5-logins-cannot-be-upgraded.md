---
title: Impossible de mettre à niveau les connexions SQL Server dormantes 6,5 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604929"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Les connexions SQL Server 6.5 dormantes ne peuvent pas être mises à niveau
  Le Conseiller de mise à niveau a détecté un nom de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dont le mot de passe ne peut pas être directement mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour activer cette connexion, vous devez redéfinir le mot de passe. Vous pouvez redéfinir le mot de passe en utilisant ALTER LOGIN.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Le nouveau mot de passe sera validé par rapport à la stratégie de complexité des mots de passe de votre système, sauf si la vérification de la stratégie est désactivée. Nous vous recommandons d'utiliser des mots de passe complexes et de ne pas désactiver la vérification de la stratégie. L'option MUST_CHANGE oblige l'utilisateur à choisir un nouveau mot de passe. Cette étape est recommandée, mais elle n’est pas obligatoire.  
  
 Vous pouvez identifier les connexions dormantes à l'aide de la requête suivante :  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
