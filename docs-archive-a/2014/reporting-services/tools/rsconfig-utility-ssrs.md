---
title: Utilitaire RS.exe (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704832"
---
# <a name="rsconfig-utility-ssrs"></a><span data-ttu-id="0f435-102">Utilitaire rsconfig (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0f435-102">rsconfig Utility (SSRS)</span></span>
  <span data-ttu-id="0f435-103">L’utilitaire **rsconfig.exe** chiffre et stocke des valeurs de connexion et de compte dans le fichier RSReportServer.config.</span><span class="sxs-lookup"><span data-stu-id="0f435-103">The **rsconfig.exe** utility encrypts and stores connection and account values in the RSReportServer.config file.</span></span> <span data-ttu-id="0f435-104">Les valeurs chiffrées incluent les informations de connexion à la base de données du serveur de rapports et les valeurs de compte utilisées pour le traitement des rapports sans assistance.</span><span class="sxs-lookup"><span data-stu-id="0f435-104">Encrypted values include report server database connection information and account values used for unattended report processing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f435-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f435-105">Syntax</span></span>  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f435-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f435-106">Arguments</span></span>  
  
|<span data-ttu-id="0f435-107">Terme</span><span class="sxs-lookup"><span data-stu-id="0f435-107">Term</span></span>|<span data-ttu-id="0f435-108">Facultatif/obligatoire</span><span class="sxs-lookup"><span data-stu-id="0f435-108">Optional/Required</span></span>|<span data-ttu-id="0f435-109">Définition</span><span class="sxs-lookup"><span data-stu-id="0f435-109">Definition</span></span>|  
|----------|------------------------|----------------|  
|<span data-ttu-id="0f435-110">**-?**</span><span class="sxs-lookup"><span data-stu-id="0f435-110">**-?**</span></span>|<span data-ttu-id="0f435-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f435-111">Optional.</span></span>|<span data-ttu-id="0f435-112">Affiche la syntaxe des arguments de Rsconfig.exe.</span><span class="sxs-lookup"><span data-stu-id="0f435-112">Displays the syntax of Rsconfig.exe arguments.</span></span>|  
|`-c`|<span data-ttu-id="0f435-113">Obligatoire si l'argument `-e` n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="0f435-113">Required if `-e` argument is not used.</span></span>|<span data-ttu-id="0f435-114">Spécifie la chaîne de connexion, les informations d'identification et les valeurs de source de données utilisées pour connecter un serveur de rapports à la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-114">Specifies the connection string, credentials, and data source values used to connect a report server to the report server database.</span></span><br /><br /> <span data-ttu-id="0f435-115">Cet argument ne prend pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="0f435-115">This argument does not take a value.</span></span> <span data-ttu-id="0f435-116">Cependant, des arguments supplémentaires doivent être spécifiés avec lui pour fournir l'ensemble des valeurs de connexion requises.</span><span class="sxs-lookup"><span data-stu-id="0f435-116">However, additional arguments must be specified with it to provide all of the required connection values.</span></span><br /><br /> <span data-ttu-id="0f435-117">Les arguments que vous pouvez spécifier avec `-c` include `-m` , **-s**, `-i` , `-d` , `-a` ,, `-u` `-p` et `-t` .</span><span class="sxs-lookup"><span data-stu-id="0f435-117">Arguments that you can specify with `-c` include `-m`, **-s**, `-i`,`-d`,`-a`,`-u`,`-p`, and`-t`.</span></span>|  
|`-e`|<span data-ttu-id="0f435-118">Obligatoire si l'argument `-c` n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="0f435-118">Required if `-c` argument is not used.</span></span>|<span data-ttu-id="0f435-119">Spécifie le compte d'exécution de rapport sans assistance.</span><span class="sxs-lookup"><span data-stu-id="0f435-119">Specifies the unattended report execution account.</span></span><br /><br /> <span data-ttu-id="0f435-120">Cet argument ne prend pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="0f435-120">This argument does not take a value.</span></span> <span data-ttu-id="0f435-121">Cependant, vous devez inclure des arguments supplémentaires sur la ligne de commande pour spécifier les valeurs qui sont chiffrées dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0f435-121">However, you must include additional arguments on the command line to specify that values that are encrypted in the configuration file.</span></span><br /><br /> <span data-ttu-id="0f435-122">Les arguments que vous pouvez spécifier avec `-e` incluent `-u` et `-p`.</span><span class="sxs-lookup"><span data-stu-id="0f435-122">Arguments that you can specify with `-e` include `-u` and `-p`.</span></span> <span data-ttu-id="0f435-123">Vous pouvez également définir `-t`.</span><span class="sxs-lookup"><span data-stu-id="0f435-123">You can also set `-t`.</span></span>|  
|<span data-ttu-id="0f435-124">`-m`  *nomd’ordinateur*</span><span class="sxs-lookup"><span data-stu-id="0f435-124">`-m`  *computername*</span></span>|<span data-ttu-id="0f435-125">Obligatoire si vous configurez une instance distante du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-125">Required if you are configuring a remote report server instance.</span></span>|<span data-ttu-id="0f435-126">Spécifie le nom de l'ordinateur qui héberge le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-126">Specifies the name of the computer that is hosting the report server.</span></span> <span data-ttu-id="0f435-127">Si cet argument est omis, la valeur par défaut est `localhost`.</span><span class="sxs-lookup"><span data-stu-id="0f435-127">If this argument is omitted, the default is `localhost`.</span></span>|  
|<span data-ttu-id="0f435-128">**-s**  *servername*</span><span class="sxs-lookup"><span data-stu-id="0f435-128">**-s**  *servername*</span></span>|<span data-ttu-id="0f435-129">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0f435-129">Required.</span></span>|<span data-ttu-id="0f435-130">Spécifie l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-130">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span>|  
|<span data-ttu-id="0f435-131">`-i`  *InstanceName*</span><span class="sxs-lookup"><span data-stu-id="0f435-131">`-i`  *instancename*</span></span>|<span data-ttu-id="0f435-132">Obligatoire si vous utilisez des instances nommées.</span><span class="sxs-lookup"><span data-stu-id="0f435-132">Required if you are using named instances.</span></span>|<span data-ttu-id="0f435-133">Si vous utilisez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommée pour héberger la base de données du serveur de rapports, cette valeur spécifie l'instance nommée.</span><span class="sxs-lookup"><span data-stu-id="0f435-133">If you used a named [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the report server database, this value specifies the named instance.</span></span>|  
|<span data-ttu-id="0f435-134">`-d`  *DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="0f435-134">`-d`  *databasename*</span></span>|<span data-ttu-id="0f435-135">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0f435-135">Required.</span></span>|<span data-ttu-id="0f435-136">Spécifie le nom de la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-136">Specifies the name of the report server database.</span></span>|  
|<span data-ttu-id="0f435-137">`-a`  *authmethod*</span><span class="sxs-lookup"><span data-stu-id="0f435-137">`-a`  *authmethod*</span></span>|<span data-ttu-id="0f435-138">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0f435-138">Required.</span></span>|<span data-ttu-id="0f435-139">Détermine la méthode d'authentification utilisée par le serveur de rapports pour la connexion à la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-139">Specifies the authentication method that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="0f435-140">Les valeurs valides sont `Windows` ou `SQL` (cet argument ne respecte pas la casse).</span><span class="sxs-lookup"><span data-stu-id="0f435-140">Valid values are `Windows` or `SQL` (this argument is not case-sensitive).</span></span><br /><br /> <span data-ttu-id="0f435-141">`Windows` spécifie que le serveur de rapports utilise l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="0f435-141">`Windows` specifies that the report server use Windows Authentication.</span></span><br /><br /> <span data-ttu-id="0f435-142">`SQL` spécifie que le serveur de rapports utilise l'authentification SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f435-142">`SQL` specifies that the report server use SQL Server Authentication.</span></span>|  
|<span data-ttu-id="0f435-143">`-u`  *[domaine \\ ] nom d’utilisateur*</span><span class="sxs-lookup"><span data-stu-id="0f435-143">`-u`  *[domain\\]username*</span></span>|<span data-ttu-id="0f435-144">Obligatoire avec `-e` Facultatif avec `-c`.</span><span class="sxs-lookup"><span data-stu-id="0f435-144">Required with `-e` Optional with `-c`.</span></span>|<span data-ttu-id="0f435-145">Spécifie un compte d'utilisateur pour la connexion à la base de données du serveur de rapports ou pour le compte sans assistance.</span><span class="sxs-lookup"><span data-stu-id="0f435-145">Specifies a user account for the report server database connection or for the unattended account.</span></span><br /><br /> <span data-ttu-id="0f435-146">Pour **rsconfig -e**, cet argument est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0f435-146">For **rsconfig -e**, this argument is required.</span></span> <span data-ttu-id="0f435-147">Il doit s’agir d’un compte d’utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="0f435-147">It must be a domain user account.</span></span><br /><br /> <span data-ttu-id="0f435-148">Pour **rsconfig-c** et `-a SQL` , cet argument doit spécifier une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.</span><span class="sxs-lookup"><span data-stu-id="0f435-148">For **rsconfig -c** and `-a SQL`, this argument must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span><br /><br /> <span data-ttu-id="0f435-149">Pour **rsconfig-c** et `-a Windows` , cet argument peut spécifier un utilisateur de domaine, un compte intégré ou des informations d’identification de compte de service.</span><span class="sxs-lookup"><span data-stu-id="0f435-149">For **rsconfig -c** and `-a Windows`, this argument may specify a domain user, a built-in account, or service account credentials.</span></span> <span data-ttu-id="0f435-150">Si vous spécifiez un compte de domaine, spécifiez *domain* et *username* sous la forme *domaine\nom_utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="0f435-150">If you are specifying a domain account, specify *domain* and *username* in the format *domain\username*.</span></span> <span data-ttu-id="0f435-151">Si vous utilisez un compte prédéfini, cet argument est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f435-151">If you are using a built-in account, this argument is optional.</span></span> <span data-ttu-id="0f435-152">Si vous souhaitez utiliser des informations d'identification de compte de service, omettez cet argument.</span><span class="sxs-lookup"><span data-stu-id="0f435-152">If you want to use service account credentials, omit this argument.</span></span>|  
|<span data-ttu-id="0f435-153">`-p`  *mot de passe*</span><span class="sxs-lookup"><span data-stu-id="0f435-153">`-p`  *password*</span></span>|<span data-ttu-id="0f435-154">Obligatoire si `-u` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f435-154">Required if `-u` is specified.</span></span>|<span data-ttu-id="0f435-155">Définit le mot de passe à utiliser avec l'argument *username* .</span><span class="sxs-lookup"><span data-stu-id="0f435-155">Specifies the password to use with the *username* argument.</span></span> <span data-ttu-id="0f435-156">Vous pouvez affecter une valeur vide à cet argument si le compte n'exige pas de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0f435-156">You can set this argument to a blank value if the account does not require a password.</span></span> <span data-ttu-id="0f435-157">Cette valeur respecte la casse pour les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="0f435-157">This value is case-sensitive for domain accounts.</span></span>|  
|`-t`|<span data-ttu-id="0f435-158">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f435-158">Optional.</span></span>|<span data-ttu-id="0f435-159">Envoie des messages d'erreur au journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="0f435-159">Outputs error messages to the trace log.</span></span> <span data-ttu-id="0f435-160">Cet argument ne prend pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="0f435-160">This argument does not take a value.</span></span> <span data-ttu-id="0f435-161">Pour plus d’informations, consultez [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span><span class="sxs-lookup"><span data-stu-id="0f435-161">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="0f435-162">Autorisations</span><span class="sxs-lookup"><span data-stu-id="0f435-162">Permissions</span></span>  
 <span data-ttu-id="0f435-163">Vous devez être un administrateur local sur l'ordinateur hébergeant le serveur de rapports que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="0f435-163">You must be a local administrator on the computer that hosts the report server you are configuring.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="0f435-164">Emplacement du fichier</span><span class="sxs-lookup"><span data-stu-id="0f435-164">File Location</span></span>  
 <span data-ttu-id="0f435-165">Rsconfig.exe se trouve dans le dossier **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span><span class="sxs-lookup"><span data-stu-id="0f435-165">Rsconfig.exe is located in **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="0f435-166">Vous pouvez exécuter l'utilitaire à partir de n'importe quel dossier de votre système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="0f435-166">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f435-167">Notes</span><span class="sxs-lookup"><span data-stu-id="0f435-167">Remarks</span></span>  
 <span data-ttu-id="0f435-168">Rsconfig.exe possède deux finalités :</span><span class="sxs-lookup"><span data-stu-id="0f435-168">Rsconfig.exe is used for two purposes:</span></span>  
  
-   <span data-ttu-id="0f435-169">Modifier les informations de connexion qu'un serveur de rapports utilise pour la connexion à une base de données de serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-169">To modify the connection information that a report server uses to connect to a report server database.</span></span>  
  
-   <span data-ttu-id="0f435-170">Configurer un compte spécial que le serveur de rapports utilise pour la connexion à un serveur de base de données distant lorsque d'autres informations d'identification ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="0f435-170">To configure a special account that the report server uses to log on to a remote database server when other credentials are not available.</span></span>  
  
 <span data-ttu-id="0f435-171">Vous pouvez exécuter l’utilitaire**rsconfig** sur une instance locale ou distante de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f435-171">You can run the**rsconfig** utility on a local or remote instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0f435-172">Vous ne pouvez pas employer l’utilitaire **rsconfig** pour déchiffrer et afficher des valeurs déjà définies.</span><span class="sxs-lookup"><span data-stu-id="0f435-172">You cannot use the **rsconfig** utility to decrypt and view values that are already set.</span></span>  
  
 <span data-ttu-id="0f435-173">Avant de pouvoir exécuter cet utilitaire, Windows Management Instrumentation (WMI) doit être installé sur l'ordinateur que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="0f435-173">Before you can run this utility, Windows Management Instrumentation (WMI) must be installed on the computer that you are configuring.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0f435-174">Exemples</span><span class="sxs-lookup"><span data-stu-id="0f435-174">Examples</span></span>  
 <span data-ttu-id="0f435-175">Les exemples suivants illustrent diverses manières d’utiliser **rsconfig**.</span><span class="sxs-lookup"><span data-stu-id="0f435-175">The following examples illustrate ways of using **rsconfig**.</span></span>  
  
#### <a name="specifying-a-domain-user-account"></a><span data-ttu-id="0f435-176">Utilisation d'un compte d'utilisateur de domaine</span><span class="sxs-lookup"><span data-stu-id="0f435-176">Specifying a Domain User Account</span></span>  
 <span data-ttu-id="0f435-177">Cet exemple illustre la configuration d'un serveur de rapports pour utiliser un compte d'utilisateur de domaine lors de la connexion à une base de données de serveur de rapports local.</span><span class="sxs-lookup"><span data-stu-id="0f435-177">This example shows how to configure a report server to use a domain user account when connecting to a local report server database.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a><span data-ttu-id="0f435-178">Spécification d'un compte d'utilisateur de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f435-178">Specifying a SQL Server Database User Account</span></span>  
 <span data-ttu-id="0f435-179">Cet exemple illustre la configuration d'un serveur de rapports afin d'utiliser une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour se connecter à une base de données du serveur de rapports distante.</span><span class="sxs-lookup"><span data-stu-id="0f435-179">This example shows how to configure a report server to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to connect to a remote report server database.</span></span>  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a><span data-ttu-id="0f435-180">Spécification d'un compte prédéfini</span><span class="sxs-lookup"><span data-stu-id="0f435-180">Specifying a Built-in Account</span></span>  
 <span data-ttu-id="0f435-181">Cet exemple illustre la configuration d'un serveur de rapports pour utiliser un compte prédéfini lors de la connexion à une base de données de serveur de rapports local.</span><span class="sxs-lookup"><span data-stu-id="0f435-181">This example shows how to configure a report server to use a built-in account when connecting to a local report server database.</span></span> <span data-ttu-id="0f435-182">Notez que `-u` n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="0f435-182">Notice that `-u` is not used.</span></span> <span data-ttu-id="0f435-183">Voici quelques exemples de valeurs de comptes intégrés prises en charge : NT AUTHORITY\SYSTEM pour système local et NT AUTHORITY\NETWORKSERVICE pour service réseau ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] uniquement).</span><span class="sxs-lookup"><span data-stu-id="0f435-183">Examples of supported built-in account values include NT AUTHORITY\SYSTEM for Local System and NT AUTHORITY\NETWORKSERVICE for Network Service ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] only).</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a><span data-ttu-id="0f435-184">Spécification d'un compte de service</span><span class="sxs-lookup"><span data-stu-id="0f435-184">Specifying a Service Account</span></span>  
 <span data-ttu-id="0f435-185">Cet exemple illustre la configuration d'un serveur de rapports pour l'utilisation du compte du service Windows Report Server et le compte du service Web lors de la connexion à une base de données de serveur de rapports local.</span><span class="sxs-lookup"><span data-stu-id="0f435-185">This example shows how to configure a report server to use the Report Server Windows service account and Web service account when connecting to a local report server database.</span></span> <span data-ttu-id="0f435-186">Notez que `-u` n'est pas utilisé et qu'aucune information de compte n'est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0f435-186">Notice that `-u` is not used and that no account information is specified.</span></span> <span data-ttu-id="0f435-187">Lorsque vous éliminez des valeurs de compte à partir de la commande, l’utilitaire **rsconfig** emploie une sécurité intégrée et le compte de service sous lequel chaque service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0f435-187">When you eliminate account values from the command, the **rsconfig** utility uses integrated security and the service account that each service runs under.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a><span data-ttu-id="0f435-188">Spécification du compte sans assistance sur un serveur local</span><span class="sxs-lookup"><span data-stu-id="0f435-188">Specifying the Unattended Account on a Local Server</span></span>  
 <span data-ttu-id="0f435-189">Cet exemple montre comment configurer le compte utilisé pour l'exécution d'un rapport sans assistance pour les rapports qui ne passent pas d'informations d'identification à la source de données externe.</span><span class="sxs-lookup"><span data-stu-id="0f435-189">This example shows how to configure the account used for unattended report execution for reports that do not pass credentials to the external data source.</span></span> <span data-ttu-id="0f435-190">Le compte doit être un compte de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="0f435-190">The account must be a Windows domain account.</span></span> <span data-ttu-id="0f435-191">Vous ne pouvez pas spécifier une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0f435-191">You cannot specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for the user name and password.</span></span> <span data-ttu-id="0f435-192">Le compte est configuré sur une instance locale du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0f435-192">The account is configured on a local report server instance.</span></span> <span data-ttu-id="0f435-193">Les messages d'erreur sont capturés dans les journaux de suivi dans le dossier ReportingServices\LogFiles.</span><span class="sxs-lookup"><span data-stu-id="0f435-193">Error messages are captured in the trace logs in the ReportingServices\LogFiles folder.</span></span>  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a><span data-ttu-id="0f435-194">Spécification du compte sans assistance sur un serveur distant</span><span class="sxs-lookup"><span data-stu-id="0f435-194">Specifying the Unattended Account on a Remote Server</span></span>  
 <span data-ttu-id="0f435-195">Cet exemple illustre la configuration du compte sur une instance distante du serveur de rapports de même version que Rsconfig.exe (par exemple, le serveur de rapports et Rsconfig.exe sont tous deux de version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2).</span><span class="sxs-lookup"><span data-stu-id="0f435-195">This example shows how to configure the account on a remote report server instance that is the same version as Rsconfig.exe (for example, the report server and Rsconfig.exe are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 version).</span></span> <span data-ttu-id="0f435-196">Les informations des messages d'erreur sont capturées dans les journaux de suivi sur le serveur distant.</span><span class="sxs-lookup"><span data-stu-id="0f435-196">Error message information is captured in the trace logs on the remote server.</span></span>  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f435-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f435-197">See Also</span></span>  
 <span data-ttu-id="0f435-198">[Configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-198">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="0f435-199">[Configurer le compte d’exécution sans assistance &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-199">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="0f435-200">[Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-200">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="0f435-201">[Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-201">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="0f435-202">[Fichiers de configuration de Reporting Services](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-202">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="0f435-203">[Utilitaires de ligne de commande du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0f435-203">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="0f435-204">Fichier de configuration RSReportServer</span><span class="sxs-lookup"><span data-stu-id="0f435-204">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  