---
title: Configurer l’option de configuration de serveur two digit year cutoff | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c31c1d87c8b743132dd90d495f73ef711dc1f813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603615"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a>Configurer l'option de configuration de serveur two digit year cutoff
  Cette rubrique explique comment configurer l'option de configuration de serveur **two digit year cutoff** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **two digit year cutoff** spécifie un entier compris entre 1753 et 9999 qui représente l’année de troncature permettant d’interpréter les années sur deux chiffres comme des années sur quatre chiffres. L'intervalle de temps par défaut pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est 1950-2049, qui correspond à 2049 comme année de troncature. Cela signifie que l'année 49 est interprétée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme étant 2 049, et l'année 50 comme étant 1 950. L'année 99 est interprétée comme étant 1 999. Pour maintenir une compatibilité ascendante, laissez ce paramètre avec sa valeur par défaut.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option two digit year cutoff, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l’option two digit year cutoff](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Les objets OLE Automation utilisent 2030 comme année de coupure à deux chiffres. Vous pouvez utiliser l'option **Année de coupure à deux chiffres** pour assurer la cohérence des dates entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications clientes. Cependant, pour éviter toute ambiguïté sur les dates, utilisez des années sur quatre chiffres dans vos données.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>Pour configurer l'option two digit year cutoff  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Paramètres divers du serveur** .  
  
3.  Sous **Prise en charge de l'année (à deux chiffres)** , dans la zone **Lors de l'entrée d'une année sur deux chiffres**, **l'interpréter comme une année entre** , entrez ou sélectionnez une valeur correspondant à la dernière année de la période.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>Pour configurer l'option two digit year cutoff  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `two digit year cutoff` la valeur `2030`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a> Suivi : Après avoir configuré l’option two digit year cutoff  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
