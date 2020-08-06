---
title: Authentification avec le serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- connections [Reporting Services], accounts
- Windows authentication [Reporting Services]
- authentication [Reporting Services]
- Forms authentication
ms.assetid: 753c2542-0e97-4d8f-a5dd-4b07a5cd10ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 396c9b4d80525c9c688a41245618755442979dc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602721"
---
# <a name="authentication-with-the-report-server"></a><span data-ttu-id="11791-102">Authentification avec le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-102">Authentication with the Report Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="11791-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS) offre plusieurs options configurables pour authentifier les utilisateurs et les applications clientes sur le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS) offers several configurable options for authenticating users and client applications against the report server.</span></span> <span data-ttu-id="11791-104">Par défaut, le serveur de rapports utilise l'authentification intégrée Windows et suppose des relations approuvées dans lesquelles le client et les ressources réseau sont dans le même domaine ou dans un domaine approuvé.</span><span class="sxs-lookup"><span data-stu-id="11791-104">By default, the report server uses Windows Integrated authentication and assumes trusted relationships where client and network resources are in the same domain or in a trusted domain.</span></span> <span data-ttu-id="11791-105">Selon la topologie de votre réseau et les besoins de votre organisation, vous pouvez personnaliser le protocole d’authentification utilisé pour l’authentification intégrée de Windows, utiliser l’authentification de base ou une extension personnalisée d’authentification basée sur les formulaires que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="11791-105">Depending on your network topology and the needs of your organization, you can customize the authentication protocol that is used for Windows Integrated authentication, use Basic authentication, or use a custom forms-based authentication extension that you provide.</span></span> <span data-ttu-id="11791-106">Chacun de ces types d'authentification peut être activé ou désactivé individuellement.</span><span class="sxs-lookup"><span data-stu-id="11791-106">Each of the authentication types can be turned on or off individually.</span></span> <span data-ttu-id="11791-107">Vous pouvez activer plusieurs types d’authentification si vous voulez que le serveur de rapports accepte des demandes de plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="11791-107">You can enable more than one authentication type if you want the report server to accept requests of multiple types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11791-108">Dans les versions précédentes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], la prise en charge de l’authentification était entièrement assurée par IIS.</span><span class="sxs-lookup"><span data-stu-id="11791-108">In previous versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], all authentication support was provided by IIS.</span></span> <span data-ttu-id="11791-109">Depuis la version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IIS n'est plus utilisé.</span><span class="sxs-lookup"><span data-stu-id="11791-109">Starting with the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] release, IIS is no longer used.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="11791-110">gère toutes les requêtes d'authentification en interne.</span><span class="sxs-lookup"><span data-stu-id="11791-110">handles all authentication requests internally.</span></span>  
  
 <span data-ttu-id="11791-111">Tous les utilisateurs ou applications qui demandent l'accès au contenu et aux opérations du serveur de rapports doivent être authentifiés avant que l'accès ne soit autorisé.</span><span class="sxs-lookup"><span data-stu-id="11791-111">All users or applications who request access to report server content or operations must be authenticated before access is allowed.</span></span>  
  
## <a name="authentication-types"></a><span data-ttu-id="11791-112">Types d'authentification</span><span class="sxs-lookup"><span data-stu-id="11791-112">Authentication Types</span></span>  
 <span data-ttu-id="11791-113">Tous les utilisateurs ou applications qui demandent l'accès au contenu et aux opérations du serveur de rapports doivent être authentifiés à l'aide du type d'authentification configuré sur le serveur de rapports avant que l'accès ne soit autorisé.</span><span class="sxs-lookup"><span data-stu-id="11791-113">All users or applications who request access to report server content or operations must be authenticated using the authentication type configured on the report server before access is allowed.</span></span> <span data-ttu-id="11791-114">Le tableau suivant décrit les types d'authentification pris en charge par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11791-114">The following table describes the authentication types supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="11791-115">Nom de type d'authentification</span><span class="sxs-lookup"><span data-stu-id="11791-115">AuthenticationType Name</span></span>|<span data-ttu-id="11791-116">Valeur de la couche d'authentification HTTP</span><span class="sxs-lookup"><span data-stu-id="11791-116">HTTP Authentication Layer value</span></span>|<span data-ttu-id="11791-117">Utilisé par défaut</span><span class="sxs-lookup"><span data-stu-id="11791-117">Used by default</span></span>|<span data-ttu-id="11791-118">Description</span><span class="sxs-lookup"><span data-stu-id="11791-118">Description</span></span>|  
|-----------------------------|-------------------------------------|---------------------|-----------------|  
|<span data-ttu-id="11791-119">RSWindowsNegotiate</span><span class="sxs-lookup"><span data-stu-id="11791-119">RSWindowsNegotiate</span></span>|<span data-ttu-id="11791-120">Negotiate</span><span class="sxs-lookup"><span data-stu-id="11791-120">Negotiate</span></span>|<span data-ttu-id="11791-121">Oui</span><span class="sxs-lookup"><span data-stu-id="11791-121">Yes</span></span>|<span data-ttu-id="11791-122">Tente d'utiliser Kerberos en premier pour l'authentification intégrée de Windows, mais revient à NTLM si Active Directory ne peut pas accorder de ticket pour la demande du client au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-122">Attempts to use Kerberos for Windows Integrated authentication first, but falls back to NTLM if Active Directory cannot grant a ticket for the client request to the report server.</span></span> <span data-ttu-id="11791-123">Negotiate revient à NTLM uniquement si le ticket n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="11791-123">Negotiate will only fall back to NTLM if the ticket is not available.</span></span> <span data-ttu-id="11791-124">Si les premières tentatives entraînent une erreur plutôt qu'un ticket manquant, le serveur de rapports n'effectue pas de deuxième tentative.</span><span class="sxs-lookup"><span data-stu-id="11791-124">If the first attempt results in an error rather than a missing ticket, the report server does not make a second attempt.</span></span>|  
|<span data-ttu-id="11791-125">RSWindowsNTLM</span><span class="sxs-lookup"><span data-stu-id="11791-125">RSWindowsNTLM</span></span>|<span data-ttu-id="11791-126">NTLM</span><span class="sxs-lookup"><span data-stu-id="11791-126">NTLM</span></span>|<span data-ttu-id="11791-127">Oui</span><span class="sxs-lookup"><span data-stu-id="11791-127">Yes</span></span>|<span data-ttu-id="11791-128">Utilise NTLM pour l'authentification intégrée de Windows.</span><span class="sxs-lookup"><span data-stu-id="11791-128">Uses NTLM for Windows Integrated authentication.</span></span><br /><br /> <span data-ttu-id="11791-129">Les informations d'identification ne seront pas déléguées ou empruntées sur d'autres demandes.</span><span class="sxs-lookup"><span data-stu-id="11791-129">The credentials will not be delegated or impersonated on other requests.</span></span> <span data-ttu-id="11791-130">Les demandes suivantes suivent une nouvelle séquence de stimulation/réponse.</span><span class="sxs-lookup"><span data-stu-id="11791-130">Subsequent requests will follow a new challenge-response sequence.</span></span> <span data-ttu-id="11791-131">Selon les paramètres de sécurité du réseau, le système peut demander à un utilisateur des informations d'identification ou la demande d'authentification est gérée de façon transparente.</span><span class="sxs-lookup"><span data-stu-id="11791-131">Depending on network security settings, a user might be prompted for credentials or the authentication request will be handled transparently.</span></span>|  
|<span data-ttu-id="11791-132">RSWindowsKerberos</span><span class="sxs-lookup"><span data-stu-id="11791-132">RSWindowsKerberos</span></span>|<span data-ttu-id="11791-133">Kerberos</span><span class="sxs-lookup"><span data-stu-id="11791-133">Kerberos</span></span>|<span data-ttu-id="11791-134">Non</span><span class="sxs-lookup"><span data-stu-id="11791-134">No</span></span>|<span data-ttu-id="11791-135">Utilise Kerberos pour l'authentification intégrée de Windows.</span><span class="sxs-lookup"><span data-stu-id="11791-135">Uses Kerberos for Windows Integrated authentication.</span></span> <span data-ttu-id="11791-136">La configuration de Kerberos passe par celle des noms des principes du service (SPN) pour vos comptes de service, lequel requiert des privilèges d'administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="11791-136">You must configure Kerberos by setting up setup service principle names (SPNs) for your service accounts, which requires domain administrator privileges.</span></span> <span data-ttu-id="11791-137">Si vous configurez la délégation d'identité à l'aide de Kerberos, le jeton de l'utilisateur qui demande un rapport peut également être utilisé sur une connexion supplémentaire aux sources de données externes qui fournissent des données aux rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-137">If you set up identity delegation with Kerberos, the token of the user who is requesting a report can also be used on an additional connection to the external data sources that provide data to reports.</span></span><br /><br /> <span data-ttu-id="11791-138">Avant de spécifier RSWindowsKerberos, vérifiez que le type de navigateur que vous utilisez prend bien en charge ce dernier.</span><span class="sxs-lookup"><span data-stu-id="11791-138">Before you specify RSWindowsKerberos, be sure that the browser type you are using actually supports it.</span></span> <span data-ttu-id="11791-139">Si vous utilisez Internet Explorer, l'authentification Kerberos est prise en charge uniquement par l'intermédiaire de Negotiate.</span><span class="sxs-lookup"><span data-stu-id="11791-139">If you are using Internet Explorer, Kerberos authentication is only supported through Negotiate.</span></span> <span data-ttu-id="11791-140">Internet Explorer ne formule pas de demande d'authentification qui spécifie Kerberos directement.</span><span class="sxs-lookup"><span data-stu-id="11791-140">Internet Explorer will not formulate an authentication request that specifies Kerberos directly.</span></span>|  
|<span data-ttu-id="11791-141">RSWindowsBasic</span><span class="sxs-lookup"><span data-stu-id="11791-141">RSWindowsBasic</span></span>|<span data-ttu-id="11791-142">De base</span><span class="sxs-lookup"><span data-stu-id="11791-142">Basic</span></span>|<span data-ttu-id="11791-143">Non</span><span class="sxs-lookup"><span data-stu-id="11791-143">No</span></span>|<span data-ttu-id="11791-144">L'authentification de base est définie dans le protocole HTTP et peut être utilisée uniquement pour authentifier des requêtes HTTP au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-144">Basic authentication is defined in the HTTP protocol and can only be used to authenticate HTTP requests to the report server.</span></span><br /><br /> <span data-ttu-id="11791-145">Les informations d'identification sont passées dans la requête HTTP à l'aide de l'encodage en base 64.</span><span class="sxs-lookup"><span data-stu-id="11791-145">Credentials are passed in the HTTP request in base64 encoding.</span></span> <span data-ttu-id="11791-146">Si vous avez recours à l'authentification de base, utilisez le protocole SSL (Secure Sockets Layer) pour chiffrer les informations du compte d'utilisateur avant de les envoyer sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="11791-146">If you use Basic authentication, use Secure Sockets Layer (SSL) to encrypt user account information before it is sent across the network.</span></span> <span data-ttu-id="11791-147">Le protocole SSL fournit un canal chiffré pour l'envoi d'une demande de connexion du client au serveur de rapports via une connexion HTTP TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="11791-147">SSL provides an encrypted channel for sending a connection request from the client to the report server over an HTTP TCP/IP connection.</span></span> <span data-ttu-id="11791-148">Pour plus d’informations, consultez [Using SSL to Encrypt Confidential Data](https://go.microsoft.com/fwlink/?LinkId=71123) (Chiffrer les données confidentielles à l’aide de SSL) sur le site web [!INCLUDE[msCoName](../../includes/msconame-md.md)] TechNet.</span><span class="sxs-lookup"><span data-stu-id="11791-148">For more information, see [Using SSL to Encrypt Confidential Data](https://go.microsoft.com/fwlink/?LinkId=71123) on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] TechNet Web site.</span></span>|  
|<span data-ttu-id="11791-149">Custom</span><span class="sxs-lookup"><span data-stu-id="11791-149">Custom</span></span>|<span data-ttu-id="11791-150">(Anonyme)</span><span class="sxs-lookup"><span data-stu-id="11791-150">(Anonymous)</span></span>|<span data-ttu-id="11791-151">Non</span><span class="sxs-lookup"><span data-stu-id="11791-151">No</span></span>|<span data-ttu-id="11791-152">L'authentification anonyme dirige le serveur de rapports pour ignorer l'en-tête d'authentification dans une requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="11791-152">Anonymous authentication directs the report server to ignore authentication header in an HTTP request.</span></span> <span data-ttu-id="11791-153">Le serveur de rapports accepte toutes les demandes, mais appelle une authentification par formulaire [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] personnalisée que vous fournissez pour authentifier l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11791-153">The report server accepts all requests, but call on a custom [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] Forms authentication that you provide to authenticate the user.</span></span><br /><br /> <span data-ttu-id="11791-154">Spécifiez `Custom` uniquement si vous déployez un module d'authentification personnalisé qui gère toutes les demandes d'authentification sur le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-154">Specify `Custom` only if you are deploying a custom authentication module that handles all authentication requests on the report server.</span></span> <span data-ttu-id="11791-155">Vous ne pouvez pas utiliser le type d'authentification Personnalisé avec l'extension d'authentification Windows par défaut.</span><span class="sxs-lookup"><span data-stu-id="11791-155">You cannot use the Custom authentication type with the default Windows Authentication extension.</span></span>|  
  
## <a name="unsupported-authentication-methods"></a><span data-ttu-id="11791-156">Méthodes d'authentification non prises en charge</span><span class="sxs-lookup"><span data-stu-id="11791-156">Unsupported Authentication Methods</span></span>  
 <span data-ttu-id="11791-157">Les méthodes et demandes d'authentification suivantes ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="11791-157">The following authentication methods and requests are not supported.</span></span>  
  
|<span data-ttu-id="11791-158">Méthode d'authentification</span><span class="sxs-lookup"><span data-stu-id="11791-158">Authentication method</span></span>|<span data-ttu-id="11791-159">Explication</span><span class="sxs-lookup"><span data-stu-id="11791-159">Explanation</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="11791-160">Anonyme</span><span class="sxs-lookup"><span data-stu-id="11791-160">Anonymous</span></span>|<span data-ttu-id="11791-161">Le serveur de rapports n'accepte pas de demandes non authentifiées d'un utilisateur anonyme, à l'exception des déploiements qui incluent une extension d'authentification personnalisée.</span><span class="sxs-lookup"><span data-stu-id="11791-161">The report server will not accept unauthenticated requests from an anonymous user, except for those deployments that include a custom authentication extension.</span></span><br /><br /> <span data-ttu-id="11791-162">Le Générateur de rapports accepte des demandes non authentifiées si vous activez l'accès au Générateur de rapports sur un serveur de rapports configuré pour l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="11791-162">Report Builder will accept unauthenticated requests if you enable Report Builder access on a report server that is configured for Basic authentication.</span></span><br /><br /> <span data-ttu-id="11791-163">Pour tous les autres cas, les demandes anonymes sont rejetées avec une erreur État HTTP 401 Accès Refusé avant que la demande ne parvienne à [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11791-163">For all other cases, anonymous requests are rejected with an HTTP Status 401 Access Denied error before the request reaches [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="11791-164">Les clients qui reçoivent cette erreur doivent reformuler la demande avec un type d'authentification valide.</span><span class="sxs-lookup"><span data-stu-id="11791-164">Clients receiving 401 Access Denied must reformulate the request with a valid authentication type.</span></span>|  
|<span data-ttu-id="11791-165">Technologies d'authentification uniques (SSO)</span><span class="sxs-lookup"><span data-stu-id="11791-165">Single sign-on technologies (SSO)</span></span>|<span data-ttu-id="11791-166">Il n’existe pas de prise en charge native pour les technologies d’authentification unique dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11791-166">There is no native support for single sign-on technologies in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="11791-167">Pour utiliser cette technologie, vous devez créer une extension d'authentification personnalisée.</span><span class="sxs-lookup"><span data-stu-id="11791-167">If you want to use a single sign-on technology, you must create a custom authentication extension.</span></span><br /><br /> <span data-ttu-id="11791-168">L'environnement d'hébergement du serveur de rapports ne prend pas en charge les filtres ISAPI.</span><span class="sxs-lookup"><span data-stu-id="11791-168">The report server hosting environment does not support ISAPI filters.</span></span> <span data-ttu-id="11791-169">Si la technologie SSO que vous utilisez est implémentée sous la forme d'un filtre ISAPI, vous pouvez envisager d'utiliser la prise en charge intégrée ISA Server pour RSASecueID ou le protocole RADIUS.</span><span class="sxs-lookup"><span data-stu-id="11791-169">If the SSO technology you are using is implemented as an ISAPI filter, consider using the ISA Server built-in support for RSASecueID or the RADIUS protocol.</span></span> <span data-ttu-id="11791-170">Sinon, vous pouvez créer un ISA Server ISAPI ou un HTTPModule pour RS, mais il est recommandé d'utiliser ISA Server directement.</span><span class="sxs-lookup"><span data-stu-id="11791-170">Otherwise, you can create an ISA Server ISAPI or an HTTPModule for RS, but it is recommended you use ISA Server directly.</span></span>|  
|<span data-ttu-id="11791-171">Passport</span><span class="sxs-lookup"><span data-stu-id="11791-171">Passport</span></span>|<span data-ttu-id="11791-172">Non pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11791-172">Not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>|  
|<span data-ttu-id="11791-173">Digest</span><span class="sxs-lookup"><span data-stu-id="11791-173">Digest</span></span>|<span data-ttu-id="11791-174">Non pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11791-174">Not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>|  
  
## <a name="configuration-of-authentication-settings"></a><span data-ttu-id="11791-175">Configuration des paramètres d'authentification</span><span class="sxs-lookup"><span data-stu-id="11791-175">Configuration of Authentication Settings</span></span>  
 <span data-ttu-id="11791-176">Les paramètres d'authentification sont configurés pour la sécurité par défaut lorsque l'URL du serveur de rapports est réservée.</span><span class="sxs-lookup"><span data-stu-id="11791-176">Authentication settings are configured for default security when the report server URL is reserved.</span></span> <span data-ttu-id="11791-177">Si vous modifiez ces paramètres de manière incorrecte, le serveur de rapports retourne des erreurs HTTP 401 Accès Refusé pour les requêtes HTTP qui ne peuvent pas être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="11791-177">If you modify these settings incorrectly, the report server will return HTTP 401 Access Denied errors for HTTP requests that cannot be authenticated.</span></span> <span data-ttu-id="11791-178">Le choix d'un type d'authentification nécessite de savoir comment l'authentification Windows est prise en charge sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="11791-178">Choosing an authentication type requires that you already know how Windows Authentication is supported in your network.</span></span> <span data-ttu-id="11791-179">Vous devez spécifier au moins un type d'authentification.</span><span class="sxs-lookup"><span data-stu-id="11791-179">At least one authentication type must be specified.</span></span> <span data-ttu-id="11791-180">Plusieurs types d'authentification peuvent être spécifiés pour RSWindows.</span><span class="sxs-lookup"><span data-stu-id="11791-180">Multiple authentication types can be specified for RSWindows.</span></span> <span data-ttu-id="11791-181">Les types d’authentification RSWindows (c’est-à-dire,,, `RSWindowsBasic` `RSWindowsNTLM` `RSWindowsKerberos` et **RSWindowsNegotiate**) s’excluent mutuellement avec personnalisé.</span><span class="sxs-lookup"><span data-stu-id="11791-181">RSWindows authentication types (that is, `RSWindowsBasic`, `RSWindowsNTLM`, `RSWindowsKerberos`, and **RSWindowsNegotiate**) are mutually exclusive with Custom.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="11791-182">Reporting Services ne valide pas les paramètres que vous spécifiez pour déterminer s'ils sont corrects pour votre environnement d'informatique.</span><span class="sxs-lookup"><span data-stu-id="11791-182">Reporting Services does not validate the settings you specify to determine whether they are correct for your computing environment.</span></span> <span data-ttu-id="11791-183">La sécurité par défaut peut ne pas fonctionner pour votre installation, ou et vous pouvez spécifier des paramètres de configuration qui ne sont pas valides pour votre infrastructure de sécurité.</span><span class="sxs-lookup"><span data-stu-id="11791-183">It is possible that default security will not work for your installation, or that you will specify configuration settings that are not valid for your security infrastructure.</span></span> <span data-ttu-id="11791-184">Pour cette raison, il est important de tester prudemment votre déploiement de serveur de rapports dans un environnement de test contrôlé avant de le déployer à plus grande échelle dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="11791-184">For this reason, it is important that you carefully test your report server deployment in controlled test environment before making it available to your larger organization.</span></span>  
  
 <span data-ttu-id="11791-185">Le service Web Report Server et le Gestionnaire de rapports font toujours appel au même type d'authentification.</span><span class="sxs-lookup"><span data-stu-id="11791-185">The Report Server Web service and Report Manager always use the same authentication type.</span></span> <span data-ttu-id="11791-186">Vous ne pouvez pas configurer d'autres types d'authentification pour les fonctionnalités du service Report Server.</span><span class="sxs-lookup"><span data-stu-id="11791-186">You cannot configure different authentication types for the feature areas of the Report Server service.</span></span> <span data-ttu-id="11791-187">Si vous disposez d'un déploiement par montée en puissance parallèle, veillez à dupliquer toutes vos modifications sur tous les nœuds dans le déploiement.</span><span class="sxs-lookup"><span data-stu-id="11791-187">If you have a scale-out deployment, be sure to duplicate all of your changes on all nodes in the deployment.</span></span> <span data-ttu-id="11791-188">Vous ne pouvez pas configurer d'autres nœuds dans le même déploiement pour utiliser des types d'authentification différents.</span><span class="sxs-lookup"><span data-stu-id="11791-188">You cannot configure different nodes in the same scale-out to use different authentication types.</span></span>  
  
 <span data-ttu-id="11791-189">Le traitement en arrière-plan n'accepte pas de demandes d'utilisateurs finaux, cependant il authentifie toutes les demandes à des fins d'exécution sans assistance.</span><span class="sxs-lookup"><span data-stu-id="11791-189">Background processing does not accept requests from end-users, however it does authenticate all requests for unattended execution purposes.</span></span> <span data-ttu-id="11791-190">Il utilise toujours l'authentification Windows et authentifie des demandes à l'aide du service Report Server ou du compte d'exécution sans assistance s'il est configuré.</span><span class="sxs-lookup"><span data-stu-id="11791-190">It always uses Windows Authentication and it authenticates requests using the Report Server service or the unattended execution account if it is configured.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11791-191">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="11791-191">In This Section</span></span>  
  
-   [<span data-ttu-id="11791-192">Configurer une authentification Windows sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-192">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)  
  
-   [<span data-ttu-id="11791-193">Configurer une authentification de base sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-193">Configure Basic Authentication on the Report Server</span></span>](configure-basic-authentication-on-the-report-server.md)  
  
-   [<span data-ttu-id="11791-194">Configurer l'authentification personnalisée ou par formulaire sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-194">Configure Custom or Forms Authentication on the Report Server</span></span>](configure-custom-or-forms-authentication-on-the-report-server.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="11791-195">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="11791-195">Related Tasks</span></span>  
  
|<span data-ttu-id="11791-196">Descriptions de tâche</span><span class="sxs-lookup"><span data-stu-id="11791-196">Task Descriptions</span></span>|<span data-ttu-id="11791-197">Liens</span><span class="sxs-lookup"><span data-stu-id="11791-197">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="11791-198">Configurez le type d'authentification intégrée de Windows.</span><span class="sxs-lookup"><span data-stu-id="11791-198">Configure the Windows Integrated authentication type.</span></span>|[<span data-ttu-id="11791-199">Configurer une authentification Windows sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-199">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)|  
|<span data-ttu-id="11791-200">Configurez le type d'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="11791-200">Configure the Basic authentication type.</span></span>|[<span data-ttu-id="11791-201">Configurer une authentification de base sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-201">Configure Basic Authentication on the Report Server</span></span>](configure-basic-authentication-on-the-report-server.md)|  
|<span data-ttu-id="11791-202">Configurez soit l'authentification par formulaire, soit un type d'authentification personnalisé.</span><span class="sxs-lookup"><span data-stu-id="11791-202">Configure forms authentication or otherwise a Custom authentication type.</span></span>|[<span data-ttu-id="11791-203">Configurer l'authentification personnalisée ou par formulaire sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-203">Configure Custom or Forms Authentication on the Report Server</span></span>](configure-custom-or-forms-authentication-on-the-report-server.md)|  
|<span data-ttu-id="11791-204">Pour gérer le scénario d'authentification personnalisé, activez le gestionnaire de rapports.</span><span class="sxs-lookup"><span data-stu-id="11791-204">Enable the report manager to handle the custom authentication scenario.</span></span>|[<span data-ttu-id="11791-205">Configurer le Gestionnaire de rapports pour passer des cookies d’authentification personnalisée</span><span class="sxs-lookup"><span data-stu-id="11791-205">Configure Report Manager to Pass Custom Authentication Cookies</span></span>](configure-the-web-portal-to-pass-custom-authentication-cookies.md)|  
  
## <a name="see-also"></a><span data-ttu-id="11791-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11791-206">See Also</span></span>  
 <span data-ttu-id="11791-207">[Octroi d'autorisations sur un serveur de rapports en mode natif](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="11791-207">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="11791-208">[Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="11791-208">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="11791-209">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="11791-209">(create-and-manage-role-assignments.md)</span></span>   
 [<span data-ttu-id="11791-210">Spécifier des informations d'identification et de connexion pour les sources de données de rapports</span><span class="sxs-lookup"><span data-stu-id="11791-210">Specify Credential and Connection Information for Report Data Sources</span></span>](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
 <span data-ttu-id="11791-211">[Implémentation d’une extension de sécurité](../extensions/security-extension/implementing-a-security-extension.md) </span><span class="sxs-lookup"><span data-stu-id="11791-211">[Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md) </span></span>  
 <span data-ttu-id="11791-212">[Configurer des connexions SSL sur un serveur de rapports en mode natif](configure-ssl-connections-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="11791-212">[Configure SSL Connections on a Native Mode Report Server](configure-ssl-connections-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="11791-213">[Configurer l’accès Générateur de rapports](../report-server/configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="11791-213">[Configure Report Builder Access](../report-server/configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="11791-214">[Présentation des extensions de sécurité](../extensions/security-extension/security-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="11791-214">[Security Extensions Overview](../extensions/security-extension/security-extensions-overview.md) </span></span>  
 <span data-ttu-id="11791-215">[Authentification dans Reporting Services](../extensions/security-extension/authentication-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="11791-215">[Authentication in Reporting Services](../extensions/security-extension/authentication-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="11791-216">Autorisation dans Reporting Services</span><span class="sxs-lookup"><span data-stu-id="11791-216">Authorization in Reporting Services</span></span>](../extensions/security-extension/authorization-in-reporting-services.md)  
  
  