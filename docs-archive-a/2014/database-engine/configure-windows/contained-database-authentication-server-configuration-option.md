---
title: Authentification de la base de données autonome (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf5bf07c8b0913ff81f31ff0ca64a18eee0f2ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611277"
---
# <a name="contained-database-authentication-server-configuration-option"></a>Authentification de la base de données autonome (option de configuration de serveur)
  Utilisez l'option **authentification de la base de données autonome** pour activer des bases de données autonomes sur l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Cette option de serveur vous permet de contrôler **l’authentification de la base de données autonome**.  
  
-   Lorsque l'option **authentification de la base de données autonome** est désactivée (0) pour l'instance, les bases de données autonomes ne peuvent pas être créées ou attachées au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Lorsque l'option **authentification de la base de données autonome** est activée (1) pour l'instance, les bases de données autonomes peuvent être créées ou attachées au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Une base de données autonome inclut tous les paramètres et métadonnées de la base de données requis pour définir la base de données ; sa configuration ne dépend pas de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] où la base de données est installée. Les utilisateurs peuvent se connecter à la base de données sans authentifier de connexion au niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Isoler la base de données du moteur de base de données permet de la déplacer facilement vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Inclure tous les paramètres de base de données dans la base de données permet aux propriétaires de base de données de gérer tous les paramètres de configuration pour la base de données. Pour plus d'informations sur les bases de données autonomes, consultez [Bases de données autonomes](../../relational-databases/databases/contained-databases.md).  
  
 Si une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comporte des bases de données autonomes, le paramètre **contained database authentication** peut avoir la valeur 0 grâce à l'instruction **RECONFIGURE WITH OVERRIDE** . Lorsque le paramètre **contained database authentication** a la valeur 0, l'authentification des bases de données autonomes est désactivée.  
  
> [!IMPORTANT]  
>  Quand des bases de données autonomes sont activées, les utilisateurs de base de données dotés de l'autorisation ALTER ANY USER, comme les membres des rôles de base de données db_owner et db_accessadmin, peuvent accorder l'accès aux bases de données et ce faisant, accorder l'accès à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela signifie que le contrôle de l'accès au serveur n'est plus limité aux membres du rôle serveur fixe sysadmin et securityadmin et aux connexions avec le niveau de serveur CONTROL SERVER et l'autorisation ALTER ANY LOGIN. Avant d'autoriser des bases de données autonomes, vous devez comprendre les risques qui leur sont associés. Pour plus d'informations, consultez [Meilleures pratiques de sécurité recommandées avec les bases de données autonomes](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active des bases de données autonomes sur l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
