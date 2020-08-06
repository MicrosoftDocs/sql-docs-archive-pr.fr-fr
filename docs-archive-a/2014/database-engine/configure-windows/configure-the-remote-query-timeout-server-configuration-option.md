---
title: Configurer l’option de configuration de serveur remote query timeout | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 74f82d621d7f0375a6a3ca604abba00f83fc6024
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707863"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a>Configurer l'option de configuration de serveur remote query timeout
  Cette rubrique explique comment configurer l'option de configuration de serveur **remote query timeout** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **remote query timeout** spécifie la durée, en secondes, d'une opération distante au terme de laquelle le délai d'attente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expire. La valeur par défaut de cette option est 600, qui correspond à une attente de 10 minutes. Cette valeur s'applique à une connexion sortante émise par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] comme requête distante. Elle n'a aucun effet sur les requêtes reçues par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Pour désactiver le délai d'attente, affectez-lui la valeur 0. Une requête attend jusqu’à ce qu’elle se termine.  
  
 Pour les requêtes hétérogènes, l’option **remote query timeout** spécifie le nombre de secondes (initialisé dans l’objet commande à l’aide de la propriété d’ensemble de lignes DBPROP_COMMANDTIMEOUT) pendant lesquelles un fournisseur distant peut attendre les résultats avant l’expiration de la requête. Cette valeur est également utilisée pour définir DBPROP_GENERALTIMEOUT si elle est prise en charge par le fournisseur distant. Cela entraînera l'expiration du délai de toutes les autres opérations après le nombre de secondes spécifié.  
  
 Pour les procédures stockées distantes, l'option **remote query timeout** spécifie le nombre de secondes devant s'écouler après l'envoi d'une instruction distante `EXEC` avant que le délai d'attente ne soit atteint.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Composants requis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option remote query timeout, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l’option remote query timeout](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   Les connexions au serveur distant doivent être autorisées avant que cette valeur puisse être définie.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a>Pour configurer l'option Délai d'attente de la requête distante  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Connexions** .  
  
3.  Sous **Connexions au serveur distant**, dans la zone **Délai d'attente de la requête distante** , tapez ou sélectionnez une valeur comprise entre 0 et 2 147 483 647 pour définir le nombre maximal de secondes de l'attente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a>Pour configurer l'option Délai d'attente de la requête distante  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `remote query timeout` la valeur `0` afin de désactiver le délai d’attente.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-remote-query-timeout-option"></a><a name="FollowUp"></a> Suivi : Après avoir configuré l’option remote query timeout  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Propriétés et comportements de l’ensemble de lignes](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
