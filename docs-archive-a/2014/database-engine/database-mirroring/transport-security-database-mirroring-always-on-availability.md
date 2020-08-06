---
title: Sécurité de transport pour la mise en miroir de bases de données et groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- cryptography [SQL Server], database mirroring
- certificates [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- transport security
- database mirroring [SQL Server], security
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 944f66f3a08ff008720d78802aadfb0fee3801e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701747"
---
# <a name="transport-security-for-database-mirroring-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="36a24-102">Sécurité du transport de la mise en miroir de bases de données et des groupes de disponibilité AlwaysOn (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="36a24-102">Transport Security for Database Mirroring and AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="36a24-103">La sécurité du transport implique l'authentification et, éventuellement, le chiffrement des messages échangés entre les bases de données.</span><span class="sxs-lookup"><span data-stu-id="36a24-103">Transport security involves authentication and, optionally, encryption of messages exchanged between the databases.</span></span> <span data-ttu-id="36a24-104">Pour la mise en miroir de bases de données et [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], l'authentification et le chiffrement sont configurés sur le point de terminaison de la mise en miroir.</span><span class="sxs-lookup"><span data-stu-id="36a24-104">For database mirroring and [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], authentication and encryption are configured on the database mirroring endpoint.</span></span> <span data-ttu-id="36a24-105">Pour une présentation des points de terminaison de mise en miroir de bases de données, consultez [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="36a24-105">For an introduction to database mirroring endpoints, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span></span>  
  

  
##  <a name="authentication"></a><a name="Authentication"></a> <span data-ttu-id="36a24-106">Authentification</span><span class="sxs-lookup"><span data-stu-id="36a24-106">Authentication</span></span>  
 <span data-ttu-id="36a24-107">L'authentification est le processus qui permet de vérifier qu'un utilisateur est la personne qu'il prétend être.</span><span class="sxs-lookup"><span data-stu-id="36a24-107">Authentication is the process of verifying that a user is who the user claims to be.</span></span> <span data-ttu-id="36a24-108">Les connexions entre les points de terminaison de mise en miroir de bases de données requièrent une authentification.</span><span class="sxs-lookup"><span data-stu-id="36a24-108">Connections between database mirroring endpoints require authentication.</span></span> <span data-ttu-id="36a24-109">Les demandes de connexion éventuellement formulées par un partenaire ou un témoin doivent être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="36a24-109">Connection requests from a partner or witness, if any, must be authenticated.</span></span>  
  
 <span data-ttu-id="36a24-110">Le type d'authentification utilisé pour la mise en miroir de bases de données ou [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] par une instance de serveur est une propriété du point de terminaison de la mise en miroir.</span><span class="sxs-lookup"><span data-stu-id="36a24-110">The type of authentication used by a server instance for database mirroring or [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] is a property of the database mirroring endpoint.</span></span> <span data-ttu-id="36a24-111">Deux types de sécurité de transport sont disponibles pour les points de terminaison de mise en miroir de bases de données : l’authentification Windows (SSPI, Security Support Provider Interface) et l’authentification basée sur les certificats.</span><span class="sxs-lookup"><span data-stu-id="36a24-111">Two types of transport security are available for database mirroring endpoints: Windows Authentication (the Security Support Provider Interface (SSPI)) and certificate-based authentication.</span></span>  
  
### <a name="windows-authentication"></a><span data-ttu-id="36a24-112">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="36a24-112">Windows Authentication</span></span>  
 <span data-ttu-id="36a24-113">Avec l'authentification Windows, chaque instance de serveur se connecte à l'autre partie à l'aide des informations d'identification Windows du compte d'utilisateur Windows sous lequel le processus est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="36a24-113">Under Windows Authentication, each server instance logs in to the other side using the Windows credentials of the Windows user account under which the process is running.</span></span> <span data-ttu-id="36a24-114">L'authentification Windows peut nécessiter une configuration manuelle des comptes de connexion, comme suit :</span><span class="sxs-lookup"><span data-stu-id="36a24-114">Windows Authentication might require some manual configuration of login accounts, as follows:</span></span>  
  
-   <span data-ttu-id="36a24-115">Si les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnent comme des services sous le même compte de domaine, aucune configuration supplémentaire n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="36a24-115">If the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] run as services under the same domain account, no extra configuration is required.</span></span>  
  
-   <span data-ttu-id="36a24-116">Si les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnent comme des services sous des comptes de domaine différents (dans les mêmes domaines ou dans des domaines approuvés), la connexion de chaque compte doit être créée en **maître** sur chacune des autres instances de serveur, et cette connexion doit disposer d’autorisations CONNECT sur le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="36a24-116">If the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the other server instances, and that login must be granted CONNECT permissions on the endpoint.</span></span>  
  
-   <span data-ttu-id="36a24-117">Si les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutent en tant que compte de service réseau, la connexion de chaque compte d’ordinateur hôte (*DomainName ***\\*** ComputerName $*) doit être créée dans **Master** sur chacun des autres serveurs, et cette connexion doit disposer des autorisations Connect sur le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="36a24-117">If the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the other servers, and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="36a24-118">En effet, une instance de serveur s'exécutant sous le compte de service réseau s'authentifie à l'aide du compte de domaine de l'ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="36a24-118">This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36a24-119">Pour obtenir un exemple de configuration d’une session de mise en miroir de bases de données utilisant l’authentification Windows, consultez [Exemple : Configuration de la mise en miroir de bases de données à l’aide de l’authentification Windows &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36a24-119">For an example of setting up a database mirroring session using Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span></span>  
  
### <a name="certificates"></a><span data-ttu-id="36a24-120">Certificats</span><span class="sxs-lookup"><span data-stu-id="36a24-120">Certificates</span></span>  
 <span data-ttu-id="36a24-121">Dans certaines situations, par exemple lorsque les instances de serveur ne se trouvent pas dans des domaines approuvés ou que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution en tant que service local, l'authentification Windows n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="36a24-121">In some situations, such as when server instances are not in trusted domains or when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running as a local service, Windows Authentication is unavailable.</span></span> <span data-ttu-id="36a24-122">Dans ces cas, ce ne sont pas des informations d'identification utilisateur, mais des certificats, qui sont nécessaires pour authentifier les demandes de connexion.</span><span class="sxs-lookup"><span data-stu-id="36a24-122">In such cases, instead of user credentials, certificates are required to authenticate connection requests.</span></span> <span data-ttu-id="36a24-123">Le point de terminaison de mise en miroir de chaque instance de serveur doit être configuré avec son propre certificat créé localement.</span><span class="sxs-lookup"><span data-stu-id="36a24-123">The mirroring endpoint of each server instance must be configured with its own locally created certificate.</span></span>  
  
 <span data-ttu-id="36a24-124">La méthode de chiffrement est établie lorsque le certificat est créé.</span><span class="sxs-lookup"><span data-stu-id="36a24-124">The encryption method is established when the certificate is created.</span></span> <span data-ttu-id="36a24-125">Pour plus d’informations, consultez [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span><span class="sxs-lookup"><span data-stu-id="36a24-125">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span> <span data-ttu-id="36a24-126">Gérez avec précaution les certificats que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="36a24-126">Carefully manage the certificates that you use.</span></span>  
  
 <span data-ttu-id="36a24-127">Une instance de serveur utilise la clé privée de son propre certificat pour établir son identité lors de la configuration d'une connexion.</span><span class="sxs-lookup"><span data-stu-id="36a24-127">A server instance uses the private key of its own certificate to establish its identity when setting up a connection.</span></span> <span data-ttu-id="36a24-128">L'instance de serveur qui reçoit la demande de connexion utilise la clé publique du certificat de l'émetteur pour authentifier l'identité de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="36a24-128">The server instance that receives the connection request uses the public key of the sender's certificate to authenticate the sender's identity.</span></span> <span data-ttu-id="36a24-129">Par exemple, considérons deux instances de serveur, en l'occurrence Serveur_A et Serveur_B.</span><span class="sxs-lookup"><span data-stu-id="36a24-129">For example, consider two server instances, Server_A and Server_B.</span></span> <span data-ttu-id="36a24-130">Serveur_A utilise sa clé privée pour chiffrer l'en-tête de connexion avant d'envoyer une demande de connexion à Serveur_B.</span><span class="sxs-lookup"><span data-stu-id="36a24-130">Server_A uses its private key to encrypt the connection header before sending a connection request to Server_B.</span></span> <span data-ttu-id="36a24-131">Serveur_B utilise la clé publique du certificat de Serveur_A pour déchiffrer l'en-tête de connexion.</span><span class="sxs-lookup"><span data-stu-id="36a24-131">Server_B uses the public key of Server_A's certificate to decrypt the connection header.</span></span> <span data-ttu-id="36a24-132">Si l'en-tête déchiffré est correct, Serveur_B sait que l'en-tête a été chiffré par Serveur_A et la connexion est authentifiée.</span><span class="sxs-lookup"><span data-stu-id="36a24-132">If the decrypted header is correct, Server_B knows that the header was encrypted by Server_A, and the connection is authenticated.</span></span> <span data-ttu-id="36a24-133">Si l'en-tête déchiffré est incorrect, Serveur_B sait que la demande de connexion n'est pas authentique et refuse la connexion.</span><span class="sxs-lookup"><span data-stu-id="36a24-133">If the decrypted header is incorrect, Server_B knows that the connection request is inauthentic and refuses the connection.</span></span>  
  
##  <a name="data-encryption"></a><a name="DataEncryption"></a> <span data-ttu-id="36a24-134">Chiffrement des données</span><span class="sxs-lookup"><span data-stu-id="36a24-134">Data Encryption</span></span>  
 <span data-ttu-id="36a24-135">Par défaut, un point de terminaison de mise en miroir de bases de données requiert le chiffrement des données envoyées via les connexions de mise en miroir.</span><span class="sxs-lookup"><span data-stu-id="36a24-135">By default, a database mirroring endpoint requires encryption of data sent over mirroring connections.</span></span> <span data-ttu-id="36a24-136">Dans ce cas, le point de terminaison ne peut se connecter qu'aux points de terminaison utilisant également le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="36a24-136">In this case, the endpoint can connect only to endpoints that also use encryption.</span></span> <span data-ttu-id="36a24-137">Sauf si vous pouvez garantir que votre réseau est sécurisé, il est recommandé d'imposer le chiffrement des connexions de mise en miroir de bases de données.</span><span class="sxs-lookup"><span data-stu-id="36a24-137">Unless you can guarantee that your network is secure, we recommend that you require encryption for your database mirroring connections.</span></span> <span data-ttu-id="36a24-138">Toutefois, vous pouvez désactiver le chiffrement ou le rendre disponible sans qu'il soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="36a24-138">However, you can disable encryption or make it supported, but not required.</span></span> <span data-ttu-id="36a24-139">Si le chiffrement est désactivé, les données ne sont jamais chiffrées et le point de terminaison ne peut pas se connecter à un point de terminaison qui requiert le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="36a24-139">If encryption is disabled, data is never encrypted and the endpoint cannot connect to an endpoint that requires encryption.</span></span> <span data-ttu-id="36a24-140">Si le chiffrement est pris en charge, les données ne sont chiffrées que si le point de terminaison opposé prend en charge ou requiert le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="36a24-140">If encryption is supported, data is encrypted only if the opposite endpoint either supports or requires encryption.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36a24-141">Sur les points de terminaison de mise en miroir créés par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , le chiffrement est requis ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="36a24-141">Mirroring endpoints created by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] are created with encryption either required or disabled.</span></span> <span data-ttu-id="36a24-142">Pour attribuer au paramètre de chiffrement la valeur SUPPORTED, utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ENDPOINT.</span><span class="sxs-lookup"><span data-stu-id="36a24-142">To change the encryption setting to SUPPORTED, use the ALTER ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="36a24-143">Pour plus d’informations, consultez [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="36a24-143">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="36a24-144">Vous pouvez également contrôler les algorithmes de chiffrement qui peuvent être utilisés par un point de terminaison, en spécifiant une des valeurs ci-dessous pour l'option ALGORITHM dans une instruction CREATE ENDPOINT ou ALTER ENDPOINT :</span><span class="sxs-lookup"><span data-stu-id="36a24-144">Optionally, you can control the encryption algorithms that can be used by an endpoint, by specifying one of the following values for the ALGORITHM option in a CREATE ENDPOINT statement or ALTER ENDPOINT statement:</span></span>  
  
|<span data-ttu-id="36a24-145">valeur ALGORITHM</span><span class="sxs-lookup"><span data-stu-id="36a24-145">ALGORITHM value</span></span>|<span data-ttu-id="36a24-146">Description</span><span class="sxs-lookup"><span data-stu-id="36a24-146">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="36a24-147">RC4</span><span class="sxs-lookup"><span data-stu-id="36a24-147">RC4</span></span>|<span data-ttu-id="36a24-148">Indique que le point de terminaison doit utiliser l'algorithme RC4.</span><span class="sxs-lookup"><span data-stu-id="36a24-148">Specifies that the endpoint must use the RC4 algorithm.</span></span> <span data-ttu-id="36a24-149">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="36a24-149">This is the default.</span></span><br /><br /> <span data-ttu-id="36a24-150">Remarque : l’algorithme RC4 est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="36a24-150">Note: The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="36a24-151">Nous vous recommandons d'utiliser AES.</span><span class="sxs-lookup"><span data-stu-id="36a24-151">We recommend that you use AES.</span></span>|  
|<span data-ttu-id="36a24-152">AES</span><span class="sxs-lookup"><span data-stu-id="36a24-152">AES</span></span>|<span data-ttu-id="36a24-153">Indique que le point de terminaison doit utiliser l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="36a24-153">Specifies that the endpoint must use the AES algorithm.</span></span>|  
|<span data-ttu-id="36a24-154">AES RC4</span><span class="sxs-lookup"><span data-stu-id="36a24-154">AES RC4</span></span>|<span data-ttu-id="36a24-155">Indique que les deux points de terminaison négocieront un algorithme de chiffrement avec ce point de terminaison, en donnant la préférence à l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="36a24-155">Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the AES algorithm.</span></span>|  
|<span data-ttu-id="36a24-156">RC4 AES</span><span class="sxs-lookup"><span data-stu-id="36a24-156">RC4 AES</span></span>|<span data-ttu-id="36a24-157">Indique que les deux points de terminaison négocieront un algorithme de chiffrement avec ce point de terminaison, en donnant la préférence à l'algorithme RC4.</span><span class="sxs-lookup"><span data-stu-id="36a24-157">Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the RC4 algorithm.</span></span>|  
  
 <span data-ttu-id="36a24-158">Si les points de terminaison se connectant spécifient les deux algorithmes mais dans des ordres différents, le point de terminaison acceptant la connexion a le dernier mot.</span><span class="sxs-lookup"><span data-stu-id="36a24-158">If connecting endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36a24-159">L'algorithme RC4 est uniquement pris en charge pour des raisons de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="36a24-159">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="36a24-160">Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100.</span><span class="sxs-lookup"><span data-stu-id="36a24-160">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="36a24-161">(Non recommandé.) Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES.</span><span class="sxs-lookup"><span data-stu-id="36a24-161">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="36a24-162">Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures, le matériel chiffré à l’aide de RC4 ou de RC4_128 peut être déchiffré dans n’importe quel niveau de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="36a24-162">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]and higher versions,  material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
>   
>  <span data-ttu-id="36a24-163">Bien que sensiblement plus rapide que AES, RC4 est un algorithme relativement faible, tandis que AES est relativement fort.</span><span class="sxs-lookup"><span data-stu-id="36a24-163">Though considerably faster than AES, RC4 is a relatively weak algorithm, while AES is a relatively strong algorithm.</span></span> <span data-ttu-id="36a24-164">Par conséquent, nous vous recommandons d'utiliser l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="36a24-164">Therefore, we recommend that you use the AES algorithm.</span></span>  
  
 <span data-ttu-id="36a24-165">Pour plus d’informations sur la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] permettant de définir le chiffrement, consultez [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="36a24-165">For information about the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for specifying encryption, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="36a24-166">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="36a24-166">Related Tasks</span></span>  
 <span data-ttu-id="36a24-167">**Pour configurer la sécurité du transport pour un point de terminaison de mise en miroir de bases de données**</span><span class="sxs-lookup"><span data-stu-id="36a24-167">**To configure transport security for a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="36a24-168">Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="36a24-168">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="36a24-169">Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="36a24-169">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="36a24-170">Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="36a24-170">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="36a24-171">Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="36a24-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
## <a name="see-also"></a><span data-ttu-id="36a24-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36a24-172">See Also</span></span>  
 <span data-ttu-id="36a24-173">[Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="36a24-173">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="36a24-174">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36a24-174">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="36a24-175">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36a24-175">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="36a24-176">[Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span><span class="sxs-lookup"><span data-stu-id="36a24-176">[Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span></span>  
 <span data-ttu-id="36a24-177">[Gérer les métadonnées durant la mise à disposition d’une base de données sur une autre instance de serveur &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="36a24-177">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 <span data-ttu-id="36a24-178">[Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36a24-178">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="36a24-179">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36a24-179">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span></span>  
 <span data-ttu-id="36a24-180">[sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections) </span><span class="sxs-lookup"><span data-stu-id="36a24-180">[sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections) </span></span>  
 <span data-ttu-id="36a24-181">[Résolution des problèmes de configuration de mise en miroir de bases de données &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36a24-181">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="36a24-182">Résoudre les problèmes de configuration de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;supprimé</span><span class="sxs-lookup"><span data-stu-id="36a24-182">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
  
  