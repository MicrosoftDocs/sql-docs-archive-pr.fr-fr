---
title: Gestion de clés extensible à l’aide d’Azure Key Vault (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 0e4bbc4f0c371c927988e6b91fdbf47307ad9d3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710532"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a>Gestion de clés extensible à l'aide d'Azure Key Vault (SQL Server)
  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] connecteur pour [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault permet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] au chiffrement de tirer parti du service Azure Key Vault en tant que fournisseur de [gestion de clés Extensible &#40;fournisseur de&#41;EKM](extensible-key-management-ekm.md) pour protéger ses clés de chiffrement.

 Contenu de cette rubrique :

-   [Utilisations de la gestion de clés extensible](#Uses)

-   [Étape 1 : Configuration du coffre de clés pour une utilisation par SQL Server](#Step1)

-   [Étape 2 : Installation du connecteur SQL Server](#Step2)

-   [Étape 3 : Configurer SQL Server pour utiliser un fournisseur EKM pour le coffre de clés](#Step3)

-   [Exemple A : chiffrement transparent des données à l'aide d'une clé asymétrique dans le coffre de clés](#ExampleA)

-   [Exemple B : chiffrement des sauvegardes à l'aide d'une clé asymétrique dans le coffre de clés](#ExampleB)

-   [Exemple C : chiffrement au niveau colonne à l'aide d'une clé asymétrique dans le coffre de clés](#ExampleC)

##  <a name="uses-of-ekm"></a><a name="Uses"></a>Utilisations de EKM
 Une organisation peut utiliser le chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour protéger les données sensibles. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]le chiffrement comprend [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), le [chiffrement au niveau des colonnes](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE) et le [chiffrement](../../backup-restore/backup-encryption.md)de la sauvegarde. Dans tous ces cas, les données sont chiffrées à l'aide d'une clé de chiffrement de données symétrique. La clé de chiffrement de données symétrique est ensuite protégée en la chiffrant avec une hiérarchie de clés stockées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Par ailleurs, l'architecture du fournisseur EKM permet à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de protéger les clés de chiffrement de données à l'aide d'une clé asymétrique stockée en dehors de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans un fournisseur de services de chiffrement externe. L'utilisation de l'architecture du fournisseur EKM ajoute une couche supplémentaire de sécurité et permet aux organisations de séparer la gestion des clés de celle des données.

 Le connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour Azure Key Vault permet à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'utiliser le service de coffre de clés extensible à hautes performances et haute disponibilité comme un fournisseur EKM pour la protection des clés de chiffrement. Vous pouvez utiliser le service de coffre de clés avec les installations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Machines virtuelles [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure et pour les serveurs locaux. Le service de coffre de clés offre également la possibilité d'utiliser des modules de sécurité matériels étroitement contrôlés et surveillés pour augmenter le niveau de protection des clés de chiffrement asymétriques. Pour plus d’informations sur le coffre de clés, consultez [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).

 L'illustration suivante résume le flux du processus de la gestion de clés extensible à l'aide du coffre de clés. Les numéros d'étapes de processus dans l'image ne sont pas censés correspondre aux numéros d'étapes d'installation qui suivent l'image.

 ![Gestion de clés extensible SQL Server avec Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "Gestion de clés extensible (EKM) SQL Server avec Azure Key Vault")

##  <a name="step-1-set-up-the-key-vault-for-use-by-sql-server"></a><a name="Step1"></a>Étape 1 : configurer le Key Vault pour une utilisation par SQL Server
 Les étapes suivantes vous permettent de configurer un coffre de clés en vue de l'utiliser avec le [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] pour la protection de clé de chiffrement. Un coffre est peut-être déjà en cours d'utilisation pour l'organisation. Si aucun coffre n'existe, l'administrateur Azure dans votre organisation chargé de gérer les clés de chiffrement peut créer un coffre, générer une clé asymétrique dans le coffre, puis autoriser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à utiliser la clé. Pour vous familiariser avec le service de coffre de clés, consultez la page [Prise en main du coffre de clés Azure](https://go.microsoft.com/fwlink/?LinkId=521402)et les informations de référence sur les [applets de commande du coffre de clés Azure](https://docs.microsoft.com/powershell/module/azurerm.keyvault) PowerShell.

> [!IMPORTANT]
>  Si vous avez plusieurs abonnements Azure, vous devez utiliser l'abonnement qui comprend [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

1.  **Créer un coffre :** Créez un coffre en suivant les instructions de la section **Créer un coffre de clés** de la page [Prise en main du coffre de clés Azure](https://go.microsoft.com/fwlink/?LinkId=521402). Notez le nom du coffre. Cette rubrique utilise **ContosoKeyVault** comme nom de coffre de clés.

2.  **Générer une clé asymétrique dans le coffre :** la clé asymétrique dans le coffre de clés permet de protéger les clés de chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Seule la partie publique de la clé asymétrique quitte le coffre, la partie privée n'étant jamais exportée par celui-ci. Toutes les opérations de chiffrement à l'aide de la clé asymétrique sont déléguées au coffre de clés Azure et sont protégées par la sécurité du coffre de clés.

     Il existe plusieurs méthodes pour générer une clé asymétrique et la stocker dans le coffre. Vous pouvez générer une clé en externe et l'importer dans le coffre en tant que fichier .pfx. Vous pouvez aussi créer la clé directement dans le coffre à l'aide des API du coffre de clés.

     Le connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nécessite que les clés asymétriques soient des clés RSA 2 048 bits, et le nom des clés peut uniquement contenir les caractères « a-z », « A-Z », « 0-9 » et « - ». Dans ce document, le nom de la clé asymétrique est appelé **ContosoMasterKey**. Remplacez-le par le nom unique que vous utilisez pour la clé.

    > [!IMPORTANT]
    >  L'importation de la clé asymétrique est fortement recommandée dans les scénarios de production, car elle permet à l'administrateur de déposer la clé dans un système de dépôt de clés (Key escrow). Si la clé asymétrique est créée dans le coffre, elle ne peut pas être déposée, car la clé privée ne peut jamais sortir du coffre. Les clés utilisées pour protéger les données critiques doivent être déposées. La perte d'une clé asymétrique rend une partie des données définitivement irrécupérable.

    > [!IMPORTANT]
    >  Le coffre de clés prend en charge plusieurs versions de la même clé nommée. Les clés à utiliser par le connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne doivent pas être gérées sous forme de versions, ni être restaurées. Si l'administrateur veut modifier la clé utilisée pour le chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , une nouvelle clé avec un autre nom doit être créée dans le coffre et utilisée pour chiffrer la clé de chiffrement des données.

     Pour plus d'informations sur la façon d'importer une clé dans le coffre de clés ou de créer une clé dans le coffre de clés (non recommandé pour un environnement de production), voir la section **Ajouter une clé ou une clé secrète dans le coffre de clés** de la page [Prise en main d’Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).

3.  **Obtenir les principaux du service Azure Active Directory à utiliser pour SQL Server :** quand l'organisation s'inscrit à un service cloud Microsoft, elle obtient un répertoire Azure Active Directory. Créez dans le répertoire Azure Active Directory des **principaux de service** qui permettront à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de s'authentifier auprès d'Azure Active Directory au moment d'accéder au coffre de clés.

    -   Un **principal de service** permet à un administrateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'accéder au coffre pendant la configuration de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour utiliser le chiffrement.

    -   Un autre **principal de service** permet au [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] d'accéder au coffre afin de désencapsuler les clés utilisées dans le chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

     Pour plus d'informations sur la façon d'inscrire une application et de générer un principal du service, consultez la section **Inscrire une application auprès d'Azure Active Directory** dans [Prise en main d'Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=521402). Le processus d'inscription retourne un **ID d'application** (également appelé **ID CLIENT**) et une **clé d'authentification** (également appelée **clé secrète**) pour chaque **principal du service**Azure Active Directory. Lorsqu’il est utilisé dans l' `CREATE CREDENTIAL` instruction, le trait d’Union doit être supprimé de l' **ID client**. Enregistrez ces éléments en vue de les utiliser dans les scripts ci-après :

    -   **Principal de service** pour une connexion **sysadmin** : **CLIENTID_sysadmin_login** et **SECRET_sysadmin_login**

    -   **Principal de service** pour le [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** et **SECRET_DBEngine**.

4.  **Accordez des autorisations pour que les principaux du service accèdent au Key Vault :** Les deux principaux **CLIENTID_sysadmin_login** et **CLIENTID_DBEngineService** requièrent les autorisations d' **extraction**, de **liste**, d' **wrapKey**et de **unwrapKey** dans le coffre de clés. Si vous prévoyez de créer des clés via [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vous devez également accorder l'autorisation **create** dans le coffre de clés.

    > [!IMPORTANT]
    >   Les utilisateurs doivent avoir au moins les opérations **wrapKey** et **unwrapKey** pour le coffre de clés.

     Pour plus d'informations sur l'octroi d'autorisations dans le coffre, voir la section **Autoriser l'application à utiliser la clé ou la clé secrète** de la page [Prise en main du coffre de clés Azure](https://go.microsoft.com/fwlink/?LinkId=521402).

     Liens vers la documentation du coffre de clés Azure

    -   [Qu’est-ce qu’Azure Key Vault ?](https://go.microsoft.com/fwlink/?LinkId=521401)

    -   [Prise en main d'Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402)

    -   Informations de référence sur les [applets de commande Azure Key Vault](https://docs.microsoft.com/powershell/module/azurerm.keyvault) de PowerShell

##  <a name="step-2-install-the-sql-server-connector"></a><a name="Step2"></a>Étape 2 : installer le connecteur SQL Server
 Le connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est téléchargé et installé par l'administrateur de l'ordinateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Le connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut être téléchargé à partir du [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=521700).  Recherchez le **connecteur SQL Server pour le coffre de clés Microsoft Azure**, passez en revue les détails, la configuration système requise et les instructions d'installation, téléchargez le connecteur et démarrez l'installation à l'aide de l'option **Exécuter**. Passez en revue la licence et acceptez-la, puis continuez.

 Par défaut, le connecteur est installé à l’emplacement **C:\Program Files\SQL Server Connector pour Microsoft Azure Key Vault**. Cet emplacement peut être changé lors de l'installation. (S'il est changé, adaptez les scripts ci-dessous).

 À la fin de l'installation, les éléments suivants sont installés sur l'ordinateur :

-   **Microsoft.AzureKeyVaultService.EKM.dll**: Il s'agit de la bibliothèque de liens dynamiques du fournisseur EKM de chiffrement qui doit être enregistrée avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE CRYPTOGRAPHIC PROVIDER.

-   **Connecteur SQL Server pour le coffre de clés Azure**: Il s'agit d'un service Windows qui permet au fournisseur EKM de chiffrement de communiquer avec le coffre de clés.

 L'installation du connecteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vous permet également de télécharger éventuellement des exemples de scripts pour le chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

##  <a name="step-3-configure-sql-server-to-use-an-ekm-provider-for-the-key-vault"></a><a name="Step3"></a>Étape 3 : configurer SQL Server pour utiliser un fournisseur EKM pour le Key Vault

###  <a name="permissions"></a><a name="Permissions"></a> Autorisations
 L'exécution de l'ensemble de ce processus nécessite l'autorisation CONTROL SERVER ou l'appartenance au rôle serveur fixe **sysadmin** . Des actions spécifiques nécessitent les autorisations suivantes :

-   Pour créer un fournisseur de chiffrement, l'autorisation CONTROL SERVER ou l'appartenance au rôle de serveur fixe **sysadmin** est requise.

-   Pour modifier une option de configuration et exécuter l'instruction RECONFIGURE, vous devez disposer de l'autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .

-   La création des informations d'identification nécessite l'autorisation ALTER ANY CREDENTIAL.

-   L'ajout d'informations d'identification à une connexion nécessite l'autorisation ALTER ANY LOGIN.

-   La création d'une clé asymétrique nécessite l'autorisation CREATE ASYMMETRIC KEY.

###  <a name="to-configure-sql-server-to-use-a-cryptographic-provider"></a><a name="TsqlProcedure"></a>Pour configurer SQL Server pour utiliser un fournisseur de services de chiffrement

1.  Configurez le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] pour utiliser la gestion de clés extensible et inscrivez (créez) le fournisseur de chiffrement avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

    ```sql
    -- Enable advanced options.
    USE master;
    GO

    sp_configure 'show advanced options', 1 ;
    GO
    RECONFIGURE ;
    GO
    -- Enable EKM provider
    sp_configure 'EKM provider enabled', 1 ;
    GO
    RECONFIGURE ;
    GO

    -- Create a cryptographic provider, using the SQL Server Connector
    -- which is an EKM provider for the Azure Key Vault. This example uses 
    -- the name AzureKeyVault_EKM_Prov.

    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov 
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';
    GO
    ```

2.  Définissez des informations d'identification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour une connexion d'administrateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour utiliser le coffre de clés, de façon à pouvoir configurer et gérer des scénarios de chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

    > [!IMPORTANT]
    >  L’argument **Identity** de `CREATE CREDENTIAL` requiert le nom du coffre de clés. L’argument **secret** de `CREATE CREDENTIAL` exige que *\<Client ID>* (sans trait d’Union) et *\<Secret>* soit passé ensemble sans espace entre eux.

     Dans l’exemple suivant, l' **ID client** ( `EF5C8E09-4D2A-4A76-9998-D93440D8115D` ) est supprimé des traits d’Union et entré en tant que chaîne `EF5C8E094D2A4A769998D93440D8115D` et le **secret** est représenté par la chaîne *SECRET_sysadmin_login*.

    ```sql
    USE master;
    CREATE CREDENTIAL sysadmin_ekm_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login' 
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;

    -- Add the credential to the SQL Server administrators domain login 
    ALTER LOGIN [<domain>/<login>]
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```

     Pour obtenir un exemple d’utilisation de variables pour les `CREATE CREDENTIAL` arguments et la suppression par programmation des tirets de l’ID client, consultez [Create Credential &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).

3.  Si vous avez importé une clé asymétrique comme décrit précédemment dans l'étape 1 de la section 3, ouvrez la clé en fournissant son nom dans l'exemple suivant.

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
    CREATION_DISPOSITION = OPEN_EXISTING;
    ```

     Bien que cela ne soit pas recommandé pour la production (la clé ne pouvant pas être exportée), il est possible de créer une clé asymétrique directement dans le coffre à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si vous n'avez pas déjà importé de clé, créez une clé asymétrique dans le coffre de clés à des fins de test en utilisant le script suivant. Exécutez le script à l'aide d'une connexion configurée avec les informations d'identification **sysadmin_ekm_cred** .

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH ALGORITHM = RSA_2048,
    PROVIDER_KEY_NAME = 'ContosoMasterKey';
    ```

> [!TIP]
>  Les utilisateurs reçoivent l'erreur **Impossible d’exporter la clé publique du fournisseur. Code d’erreur du fourniseur : 2053.** doit vérifier ses autorisations **get**, **list**, **wrapKey**et **unwrapKey** dans le coffre de clés.

 Pour plus d’informations, consultez les rubriques suivantes :

-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)

-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)

-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)

-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)

-   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)

-   [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)

## <a name="examples"></a>Exemples

###  <a name="example-a-transparent-data-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleA"></a>Exemple A : Transparent Data Encryption à l’aide d’une clé asymétrique du Key Vault
 Après avoir effectué les étapes ci-dessus, créez des informations d'identification et une connexion, puis créez une clé de chiffrement de base de données protégée par la clé asymétrique dans le coffre de clés. Utilisez la clé de chiffrement de base de données pour chiffrer une base de données avec le chiffrement transparent des données.

 Chiffrer une base de données nécessite l'autorisation CONTROL sur la base de données.

##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a>Pour activer le chiffrement transparent des données à l'aide de la gestion de clés extensible et du coffre de clés

1.  Créez des informations d'identification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] qui permettront d'accéder à la gestion de clés extensible du coffre de clés au moment du chargement de la base de données.

    > [!IMPORTANT]
    >  L’argument **Identity** de `CREATE CREDENTIAL` requiert le nom du coffre de clés. L’argument **secret** de `CREATE CREDENTIAL` exige que *\<Client ID>* (sans trait d’Union) et *\<Secret>* soit passé ensemble sans espace entre eux.

     Dans l'exemple suivant, l' **ID client** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) est débarrassé des tirets et entré comme chaîne `EF5C8E094D2A4A769998D93440D8115D` , tandis que la **clé secrète** est représentée par la chaîne *SECRET_DBEngine*.

    ```sql
    USE master;
    CREATE CREDENTIAL Azure_EKM_TDE_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine' 
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
    ```

2.  Créez une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisable par le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] pour le chiffrement transparent des données et ajoutez-y les informations d'identification. Cet exemple utilise la clé asymétrique CONTOSO_KEY stockée dans le coffre de clés, qui a été importée ou créée précédemment pour la base de données MASTER, comme décrit à l' [étape 3 de la section 3](#Step3) ci-dessus.

    ```sql
    USE master;
    -- Create a SQL Server login associated with the asymmetric key 
    -- for the Database engine to use when it loads a database 
    -- encrypted by TDE.
    CREATE LOGIN TDE_Login 
    FROM ASYMMETRIC KEY CONTOSO_KEY;
    GO 

    -- Alter the TDE Login to add the credential for use by the 
    -- Database Engine to access the key vault
    ALTER LOGIN TDE_Login 
    ADD CREDENTIAL Azure_EKM_TDE_cred ;
    GO
    ```

3.  Créez la clé de chiffrement de base de données (DEK) qui sera utilisée pour le chiffrement transparent des données. La clé de chiffrement de base de données peut être créée à l'aide de n'importe quelle longueur de clé ou algorithme pris en charge par SQL Server. La clé DEK est protégée par la clé asymétrique dans le coffre de clés.

     Cet exemple utilise la clé asymétrique CONTOSO_KEY stockée dans le coffre de clés, qui a été importée ou créée précédemment, comme décrit à l' [étape 3 de la section 3](#Step3) ci-dessus.

    ```sql
    USE ContosoDatabase;
    GO

    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_128 
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;
    GO

    -- Alter the database to enable transparent data encryption.
    ALTER DATABASE ContosoDatabase 
    SET ENCRYPTION ON ;
    GO
    ```

     Pour plus d’informations, consultez les rubriques suivantes :

    -   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)

    -   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)

###  <a name="example-b-encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleB"></a>Exemple B : chiffrement des sauvegardes à l’aide d’une clé asymétrique à partir du Key Vault
 Les sauvegardes chiffrées sont prises en charge à partir de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. L'exemple suivant crée et restaure une sauvegarde chiffrée avec une clé de chiffrement de données protégée par la clé asymétrique dans le coffre de clés.

```sql
USE master;
BACKUP DATABASE [DATABASE_TO_BACKUP]
TO DISK = N'[PATH TO BACKUP FILE]' 
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD, 
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);
GO
```

 Exemple de code de restauration.

```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;
GO
```

 Pour plus d’informations sur les options de sauvegarde, consultez [backup &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).

###  <a name="example-c-column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleC"></a>Exemple C : chiffrement au niveau des colonnes à l’aide d’une clé asymétrique à partir du Key Vault
 L'exemple suivant crée une clé symétrique protégée par la clé asymétrique dans le coffre de clés. La clé symétrique est ensuite utilisée pour chiffrer les données de la base de données.

 Cet exemple utilise la clé asymétrique CONTOSO_KEY stockée dans le coffre de clés, qui a été importée ou créée précédemment, comme décrit à l' [étape 3 de la section 3](#Step3) ci-dessus. Pour utiliser cette clé asymétrique dans la base de données `ContosoDatabase` , vous devez réexécuter l'instruction CREATE ASYMMETRIC KEY pour fournir à la base de données `ContosoDatabase` une référence à la clé.

```sql
USE [ContosoDatabase];
GO

-- Create a reference to the key in the key vault
CREATE ASYMMETRIC KEY CONTOSO_KEY 
FROM PROVIDER [AzureKeyVault_EKM_Prov]
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
CREATION_DISPOSITION = OPEN_EXISTING;

-- Create the data encryption key.
-- The data encryption key can be created using any SQL Server 
-- supported algorithm or key length.
-- The DEK will be protected by the asymmetric key in the key vault

CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY
    WITH ALGORITHM=AES_256
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

DECLARE @DATA VARBINARY(MAX);

--Open the symmetric key for use in this session
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY 
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

--Encrypt syntax
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));

-- Decrypt syntax
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));

--Close the symmetric key
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;
```

## <a name="see-also"></a>Voir aussi
 [Créer un fournisseur de services de chiffrement &#40;Transact-sql&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [créer des informations d’identification &#40;transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [créer une clé asymétrique &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [créer une clé symétrique &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [gestion de clés extensible &#40;EKM&#41;](extensible-key-management-ekm.md) [activer TDE à l’aide de EKM](enable-tde-on-sql-server-using-ekm.md) [Backup](../../backup-restore/backup-encryption.md) Encryption [créer une sauvegarde chiffrée](../../backup-restore/create-an-encrypted-backup.md)
