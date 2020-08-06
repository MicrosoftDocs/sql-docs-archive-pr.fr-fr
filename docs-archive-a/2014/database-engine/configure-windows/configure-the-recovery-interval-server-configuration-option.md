---
title: Configurer l’option de configuration de serveur recovery interval | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 560d514ba8dd1503b59b3b59ecf404d876e24cd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601687"
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a>Configurer l'option de configuration de serveur recovery interval
  Cette rubrique explique comment configurer l'option de configuration de serveur **recovery interval** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **recovery interval** définit une limite supérieure de durée de récupération pour une base de données. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilise la valeur spécifiée pour cette option afin de déterminer approximativement à quelle fréquence les [points de contrôle automatique](../../relational-databases/logs/database-checkpoints-sql-server.md) génèrent des points de contrôle automatique sur une base de données spécifiée.  
  
 La valeur par défaut pour l'intervalle de récupération est 0, ce qui permet au [!INCLUDE[ssDE](../../includes/ssde-md.md)] de configurer automatiquement l'intervalle de récupération. En général, avec l'intervalle de récupération par défaut, les points de contrôle automatique sont générés environ une fois par minute pour les bases de données actives et la durée de récupération est inférieure à une minute. Des valeurs supérieures indiquent la durée de récupération maximale approximative, en minutes. Par exemple, si vous affectez à l'intervalle de récupération la valeur « 3 », cela indique que la durée de récupération maximale est d'environ trois minutes.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option de configuration de serveur recovery interval, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l’option recovery interval](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   L'option intervalle de récupération affecte uniquement les bases de données qui utilisent le temps de récupération cible par défaut (0). Pour remplacer l'intervalle de récupération de serveur sur une base de données, configurez un temps de récupération cible autre que celui par défaut sur la base de données. Pour plus d’informations, consultez [Modifier la durée de récupération cible d’une base de données &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   En général, il est recommandé de conserver la valeur 0 pour l'option intervalle de récupération, sauf si vous rencontrez des problèmes de performances. Si vous décidez d'augmenter la valeur de l'option intervalle de récupération, nous vous recommandons de l'augmenter progressivement par petits incréments et d'évaluer l'effet de chaque augmentation incrémentielle sur les performances de récupération.  
  
-   Si vous utilisez **sp_configure** pour attribuer à l’option **intervalle de récupération** une valeur supérieure à 60 (minutes), spécifiez RECONFIGURE WITH OVERRIDE. WITH OVERRIDE désactive le contrôle de la valeur de configuration (pour les valeurs non valides ou non recommandées).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour définir l'intervalle de récupération**  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Paramètres de base de données** .  
  
3.  Sous **Récupération**, dans la zone **Intervalle de récupération (minutes)** , tapez ou sélectionnez une valeur de 0 à 32767 pour définir la durée maximale en minutes que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut consacrer à la récupération de chaque base de données, au démarrage. La valeur par défaut est égale à 0, ce qui correspond à une configuration automatique par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les bases de données actives, cela représente concrètement une durée de récupération inférieure à une minute et un point de contrôle chaque minute environ.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-set-the-recovery-interval"></a>Pour définir l'intervalle de récupération  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `recovery interval` la valeur `3` minutes.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-recovery-internal-option"></a><a name="FollowUp"></a> Suivi : Après avoir configuré l’option recovery interval  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier la durée de récupération cible d’une base de données &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)   
 [Points de contrôle de base de données &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [show advanced options (option de configuration de serveur)](show-advanced-options-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
