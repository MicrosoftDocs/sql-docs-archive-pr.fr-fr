---
title: Rôles de niveau serveur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.Security.BUILTIN.administrators
- sql12.Security.NT_AUTHORITY.SYSTEM
helpviewer_keywords:
- roles [SQL Server], server-level
- principals [SQL Server], server-level
- CONTROL SERVER permission
- fixed server roles [SQL Server]
- credentials [SQL Server], roles
- sysadmin fixed server role
- server-level roles [SQL Server]
- authentication [SQL Server], roles
ms.assetid: 7adf2ad7-015d-4cbe-9e29-abaefd779008
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4e8f2e75eb5272f30153814e923048b4f5c4f8b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700955"
---
# <a name="server-level-roles"></a>Rôles de niveau serveur
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit des rôles au niveau du serveur pour vous aider à gérer les autorisations sur les serveurs. Ces rôles sont des principaux de sécurité qui regroupent d'autres principaux. Les autorisations des rôles serveur ont une portée à l'échelle du serveur. (Les*rôles* sont semblables aux *groupes* du système d’exploitation Microsoft Windows.)  
  
 Les rôles serveur fixes sont fournis pour des raisons de commodité et de compatibilité descendante. Attribuez des autorisations plus spécifiques chaque fois que cela est possible.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit neuf rôles serveur fixes. Les autorisations attribuées aux rôles serveur fixes ne peuvent pas être modifiées. Depuis [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], il est possible de créer des rôles serveur définis par l'utilisateur et de leur ajouter des autorisations au niveau du serveur.  
  
 Vous pouvez ajouter des principaux au niveau du serveur (connexions[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , comptes et groupes Windows) à des rôles serveur. Chaque membre d'un rôle serveur fixe peut ajouter des connexions à ce rôle. Les membres de rôles serveur définis par l'utilisateur ne peuvent pas ajouter d'autres principaux de serveur à ces rôles.  
  
## <a name="fixed-server-level-roles"></a>Rôles serveur fixes  
 Le tableau ci-dessous répertorie les rôles serveur fixes et leurs fonctionnalités.  
  
|Rôles serveur fixes|Description|  
|------------------------------|-----------------|  
|administrateur système|Les membres du rôle serveur fixe sysadmin peuvent effectuer n'importe quelle activité sur le serveur.|  
|serveradmin|Les membres du rôle serveur fixe serveradmin peuvent modifier les options de configuration à l'échelle du serveur et arrêter le serveur.|  
|securityadmin|Les membres du rôle serveur fixe securityadmin gèrent les connexions et leurs propriétés. Ils peuvent assigner des autorisations GRANT, DENY et REVOKE au niveau du serveur. Ils peuvent également attribuer des autorisations GRANT, DENY et REVOKE au niveau de la base de données s'ils ont accès à une base de données. En outre, ils peuvent réinitialiser les mots de passe pour les connexions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> Note de sécurité la possibilité d’accorder l’accès au et de configurer des autorisations utilisateur permet à l’administrateur de la sécurité d’affecter la plupart des autorisations de serveur. ** \* \* \* \* ** [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Le `securityadmin` rôle doit être traité comme équivalent au `sysadmin` rôle.|  
|processadmin|Les membres du rôle serveur fixe processadmin peuvent mettre fin aux processus en cours d'exécution dans une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|setupadmin|Les membres du rôle serveur fixe setupadmin peuvent ajouter et supprimer des serveurs liés à l’aide d’instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] . (L’appartenance au rôle sysadmin est nécessaire pour utiliser [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)|  
|bulkadmin|Les membres du rôle serveur fixe bulkadmin peuvent exécuter l'instruction BULK INSERT.|  
|diskadmin|Le rôle serveur fixe diskadmin permet de gérer les fichiers disque.|  
|dbcreator|Les membres du rôle serveur fixe dbcreator peuvent créer, modifier, supprimer et restaurer n'importe quelle base de données.|  
|public|Chaque connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] appartient au rôle serveur public. Lorsqu'un principal de serveur ne s'est pas vu accorder ou refuser des autorisations spécifiques sur un objet sécurisable, l'utilisateur hérite des autorisations accordées à public sur cet objet. Vous ne devez affecter des autorisations publiques à un objet que lorsque vous souhaitez que ce dernier soit disponible pour tous les utilisateurs. Vous ne pouvez pas modifier l’appartenance au rôle public.<br /><br /> Remarque : le rôle public est implémenté différemment des autres rôles. Toutefois, les autorisations peuvent être accordées, refusées ou révoquées à partir du rôle public.|  
  
## <a name="permissions-of-fixed-server-roles"></a>Autorisations des rôles serveur fixes  
 Certaines autorisations sont assignées à chaque rôle serveur fixe. Pour un graphique des autorisations assignées aux rôles serveur, consultez [Serveur fixe du moteur de base de données et rôles de base de données fixes](https://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).  
  
> [!IMPORTANT]  
>  L'autorisation `CONTROL SERVER` ressemble, mais n'est pas identique au rôle serveur fixe `sysadmin`. Les autorisations n'impliquent pas les appartenances au rôle et les appartenances au role n'accordent pas d'autorisation. (Par exemple, `CONTROL SERVER`n’implique pas l’appartenance au `sysadmin` rôle serveur fixe.) Toutefois, il est parfois possible d’emprunter l’identité entre les rôles et les autorisations équivalentes. La plupart des commandes `DBCC` et de nombreuses procédures système exigent l'appartenance au rôle serveur fixe `sysadmin`. Pour obtenir la liste des procédures stockées système 171 qui nécessitent `sysadmin` l’appartenance, consultez le billet de blog suivant de Andreas Wolter [Control Server vs. sysadmin/sa : autorisations, procédures système, DBCC, création de schéma automatique et escalade des privilèges-avertissements](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).  
  
## <a name="server-level-permissions"></a>Autorisations au niveau serveur  
 Seules des autorisations au niveau du serveur peuvent être ajoutées aux rôles serveur définis par l'utilisateur. Pour répertorier les autorisations au niveau du serveur, exécutez l'instruction suivante. Les autorisations au niveau du serveur sont :  
  
```sql  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 Pour plus d’informations sur les autorisations, consultez [Autorisations &#40;moteur de base de données&#41;](../permissions-database-engine.md) et [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
## <a name="working-with-server-level-roles"></a>Utilisation des rôles au niveau du serveur  
 Le tableau ci-dessous explique les commandes, vues et fonctions permettant d'utiliser les rôles serveur.  
  
|Fonctionnalité|Type|Description|  
|-------------|----------|-----------------|  
|[sp_helpsrvrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql)|Métadonnées|Retourne la liste des rôles au niveau du serveur.|  
|[sp_helpsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql)|Métadonnées|Retourne des informations sur les membres d'un rôle au niveau du serveur.|  
|[sp_srvrolepermission &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql)|Métadonnées|Affiche les autorisations d'un rôle au niveau du serveur.|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Métadonnées|Indique si une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est un membre du rôle au niveau du serveur spécifié.|  
|[sys.server_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)|Métadonnées|Retourne une ligne pour chaque membre de chaque rôle serveur.|  
|[sp_addsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql)|Commande|Ajoute une connexion en tant que membre d'un rôle serveur. Action déconseillée. Utilisez plutôt [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[sp_dropsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql)|Commande|Supprime une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou un utilisateur ou un groupe Windows d'un rôle serveur. Action déconseillée. Utilisez plutôt [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)|Commande|Crée un rôle serveur défini par l'utilisateur.|  
|[ALTER SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-role-transact-sql)|Commande|Modifie l'appartenance d'un rôle serveur ou modifie le nom d'un rôle serveur défini par l'utilisateur.|  
|[DROP SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-role-transact-sql)|Commande|Supprime un rôle de serveur défini par l'utilisateur.|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Fonction|Détermine l'appartenance du rôle serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles au niveau de la base de données](../authentication-access/database-level-roles.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)   
 [Sécurisation de SQL Server](../securing-sql-server.md)   
 [Autorisations du principal du serveur GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-principal-permissions-transact-sql)   
 [Autorisations du principal du serveur REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-server-principal-permissions-transact-sql)   
 [Autorisations du principal du serveur DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-server-principal-permissions-transact-sql)   
 [Créer un rôle serveur](../authentication-access/create-a-server-role.md)  
  
  
