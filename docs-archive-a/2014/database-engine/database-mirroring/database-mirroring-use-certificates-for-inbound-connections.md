---
title: Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions entrantes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- inbound connections
- database mirroring [SQL Server], security
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c05397dfbd1740293c4b154ace1ed5704cec11a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601665"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-inbound-connections-transact-sql"></a>Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions entrantes (Transact-SQL)
  Cette rubrique décrit les étapes requises pour configurer les instances de serveur afin qu'elles utilisent les certificats pour authentifier les connexions entrantes dans le cadre de la mise en miroir de bases de données. Avant de définir des connexions entrantes, vous devez configurer les connexions sortantes sur chacune des instances du serveur. Pour plus d’informations, consultez [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).  
  
 La configuration des connexions entrantes se fait en quatre temps, à savoir :  
  
1.  Création d'une connexion pour l'autre système  
  
2.  Créez un utilisateur pour cette connexion.  
  
3.  Obtenez le certificat pour la mise en miroir du point de terminaison de l'autre instance du serveur.  
  
4.  Associez le certificat à l'utilisateur créé à l'étape 2.  
  
5.  Accordez à ce point de terminaison de mise en miroir l'autorisation CONNECT sur la connexion.  
  
 S'il existe un témoin, vous devez également configurer les connexions entrantes pour celui-ci. Cela exige la définition des noms de connexion, des utilisateurs et des certificats pour le témoin sur les deux partenaires, et inversement.  
  
 La procédure suivante décrit ces étapes en détail. Pour chaque étape, la procédure fournit un exemple de configuration d'une instance du serveur sur un système nommé HOST_A. La section Exemple qui l'accompagne explique les mêmes étapes pour une autre instance du serveur sur un système nommé HOST_B.  
  
### <a name="to-configure-server-instances-for-inbound-mirroring-connections-on-host_a"></a>Pour configurer les instances du serveur pour les connexions de mise en miroir entrantes (sur HOST_A)  
  
1.  Créez une connexion pour l'autre système.  
  
     L’exemple suivant crée une connexion pour le système, HOST_B, dans la base de données **master** de l’instance du serveur sur HOST_A. Dans cet exemple, la connexion s’appelle `HOST_B_login`. Remplacez le mot de passe donné en exemple par un mot de passe qui vous est propre.  
  
    ```sql  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     Pour plus d’informations, consultez [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
     Pour afficher les connexions existant pour cette instance du serveur, vous pouvez utiliser l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
    ```sql  
    SELECT * FROM sys.server_principals;  
    ```  
  
     Pour plus d’informations, consultez [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql).  
  
2.  Créez un utilisateur pour cette connexion.  
  
     L'exemple suivant crée un utilisateur, `HOST_B_user`, pour la connexion créée lors de l'étape précédente.  
  
    ```sql  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     Pour plus d’informations, consultez [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
     Pour afficher les utilisateurs existant pour cette instance du serveur, vous pouvez utiliser l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
    ```sql  
    SELECT * FROM sys.sysusers;  
    ```  
  
     Pour plus d’informations, consultez [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql).  
  
3.  Obtenez le certificat pour la mise en miroir du point de terminaison de l'autre instance du serveur.  
  
     Si vous ne l'avez pas encore fait lors de la configuration des connexions sortantes, obtenez une copie du certificat pour le point de terminaison de mise en miroir de l'instance du serveur distant. Pour ce faire, sauvegardez le certificat sur cette instance de serveur comme décrit dans [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md). Lors de la copie d'un certificat sur un autre système, utilisez une méthode de copie sécurisée. Veillez particulièrement à sécuriser tous vos certificats.  
  
     Pour plus d’informations, consultez [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).  
  
4.  Associez le certificat à l'utilisateur créé à l'étape 2.  
  
     L'exemple suivant associe le certificat de HOST_B avec son utilisateur sur HOST_A.  
  
    ```sql  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     Pour plus d’informations, consultez [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
     Pour afficher les certificats existant pour cette instance du serveur, vous pouvez utiliser l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
    ```sql  
    SELECT * FROM sys.certificates;  
    ```  
  
     Pour plus d’informations, consultez [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).  
  
5.  Accordez l'autorisation CONNECT à la connexion pour le point de terminaison de mise en miroir distant.  
  
     Par exemple, pour accorder l’autorisation sur HOST_A à l’instance du serveur distant sur HOST_B afin qu’elle puisse se connecter à sa connexion locale, c’est-à-dire à `HOST_B_login`, utilisez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes :  
  
    ```sql  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     Pour plus d’informations, consultez [Autorisations de point de terminaison GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
 Cette dernière étape conclut la configuration de l'authentification par certificat de HOST_B lors de sa connexion à HOST_A.  
  
 Il vous faut maintenant procéder de même pour les communications entrantes pour HOST_A sur HOST_B Ces étapes sont expliquées dans la partie consacrée aux connexions entrantes de l'exemple présenté dans la section Exemple ci-dessous.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant explique comment configurer HOST_B pour les connexions entrantes.  
  
> [!NOTE]  
>  Cet exemple utilise un fichier de certificat contenant le certificat HOST_A qui est créé par un extrait de code dans [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).  
  
```sql  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login;  
GO  
```  
  
 Si vous envisagez d'utiliser le mode haute sécurité avec basculement automatique, vous devez répéter les mêmes étapes pour configurer le témoin pour les connexions sortantes et entrantes.  
  
 Pour plus d’informations sur la création d’une base de données miroir, et obtenir un exemple Transact-SQL, consultez [Préparer une base de données miroir pour la mise en miroir &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
 Pour obtenir un exemple Transact-SQL d’établissement d’une session en mode hautes performances, consultez [Exemple : Configuration de la mise en miroir de bases de données à l’aide de certificats &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Lors de la copie d'un certificat sur un autre système, utilisez une méthode de copie sécurisée. Veillez particulièrement à sécuriser tous vos certificats.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de transport pour la mise en miroir de bases de données et les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [Autorisations GRANT sur point de terminaison &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)   
 [Configurer une base de données miroir chiffrée](set-up-an-encrypted-mirror-database.md)   
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Résoudre des problèmes de configuration de mise en miroir de bases de données &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
