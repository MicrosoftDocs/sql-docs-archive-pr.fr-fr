---
title: Configurer un pare-feu Windows pour l’accès au moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], firewall systems
- firewall systems, [Database Engine]
- security [SQL Server], firewalls
ms.assetid: 0093b43c-c6b5-4574-9b30-3a0e91e1a1f9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f76eecb4dd48f3e7f54cad79953773f8432f416e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614855"
---
# <a name="configure-a-windows-firewall-for-database-engine-access"></a><span data-ttu-id="7073b-102">Configurer un pare-feu Windows pour accéder au moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="7073b-102">Configure a Windows Firewall for Database Engine Access</span></span>
  <span data-ttu-id="7073b-103">Cette rubrique explique comment configurer un pare-feu Windows pour l'accès du moteur de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7073b-103">This topic describes how to configure a Windows firewall for Database Engine access in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="7073b-104">Les systèmes de pare-feu empêchent les accès non autorisés aux ressources de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7073b-104">Firewall systems help prevent unauthorized access to computer resources.</span></span> <span data-ttu-id="7073b-105">Pour accéder à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] par le biais d'un pare-feu, vous devez configurer le pare-feu de l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour autoriser l'accès.</span><span class="sxs-lookup"><span data-stu-id="7073b-105">To access an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] through a firewall, you must configure the firewall on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allow access.</span></span>  
  
 <span data-ttu-id="7073b-106">Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span><span class="sxs-lookup"><span data-stu-id="7073b-106">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span> <span data-ttu-id="7073b-107">De nombreux systèmes de pare-feu sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="7073b-107">There are many firewall systems available.</span></span> <span data-ttu-id="7073b-108">Pour obtenir des informations spécifiques à votre système, consultez la documentation du pare-feu.</span><span class="sxs-lookup"><span data-stu-id="7073b-108">For information specific to your system, see the firewall documentation.</span></span>  
  
 <span data-ttu-id="7073b-109">Deux principales étapes permettent d'autoriser l'accès :</span><span class="sxs-lookup"><span data-stu-id="7073b-109">The principal steps to allow access are:</span></span>  
  
1.  <span data-ttu-id="7073b-110">Configurez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] afin qu'il utilise un port TCP/IP particulier.</span><span class="sxs-lookup"><span data-stu-id="7073b-110">Configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use a specific TCP/IP port.</span></span> <span data-ttu-id="7073b-111">L'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise le port 1433, mais il est possible de modifier ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="7073b-111">The default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] uses port 1433, but that can be changed.</span></span> <span data-ttu-id="7073b-112">Le port utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est indiqué dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7073b-112">The port used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span> <span data-ttu-id="7073b-113">Les instances [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] et [!INCLUDE[ssEW](../../includes/ssew-md.md)], ainsi que les instances nommées du [!INCLUDE[ssDE](../../includes/ssde-md.md)], utilisent des ports dynamiques.</span><span class="sxs-lookup"><span data-stu-id="7073b-113">Instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], and named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] use dynamic ports.</span></span> <span data-ttu-id="7073b-114">Pour configurer ces instances pour utiliser un port spécifique, consultez [Configurer un serveur pour l’écoute sur un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span><span class="sxs-lookup"><span data-stu-id="7073b-114">To configure these instances to use a specific port, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
2.  <span data-ttu-id="7073b-115">Configurez le pare-feu pour permettre l'accès à ce port aux utilisateurs ou aux ordinateurs autorisés.</span><span class="sxs-lookup"><span data-stu-id="7073b-115">Configure the firewall to allow access to that port for authorized users or computers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7073b-116">Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser permet aux utilisateurs de se connecter à des instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui n'écoutent pas sur le port 1433 sans connaître le numéro de port.</span><span class="sxs-lookup"><span data-stu-id="7073b-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service lets users connect to instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that are not listening on port 1433, without knowing the port number.</span></span> <span data-ttu-id="7073b-117">Pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, vous devez ouvrir le port UDP 1434.</span><span class="sxs-lookup"><span data-stu-id="7073b-117">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, you must open UDP port 1434.</span></span> <span data-ttu-id="7073b-118">Pour garantir un environnement sécurisé optimal, laissez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser désactivé et configurez les clients pour qu'ils se connectent avec ce numéro de port.</span><span class="sxs-lookup"><span data-stu-id="7073b-118">To promote the most secure environment, leave the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service stopped, and configure clients to connect using the port number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7073b-119">Par défaut, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows active le pare-feu Windows ; ce dernier ferme alors le port 1433 pour empêcher des ordinateurs reliés à Internet de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7073b-119">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows enables the Windows Firewall, which closes port 1433 to prevent Internet computers from connecting to a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your computer.</span></span> <span data-ttu-id="7073b-120">Les connexions à l'instance par défaut à l'aide du protocole TCP/IP sont impossibles si vous ne rouvrez pas le port 1433.</span><span class="sxs-lookup"><span data-stu-id="7073b-120">Connections to the default instance using TCP/IP are not possible unless you reopen port 1433.</span></span> <span data-ttu-id="7073b-121">Les procédures suivantes présentent les étapes de base permettant de configurer le pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="7073b-121">The basic steps to configure the Windows firewall are provided in the following procedures.</span></span> <span data-ttu-id="7073b-122">Pour plus d'informations, consultez la documentation Windows.</span><span class="sxs-lookup"><span data-stu-id="7073b-122">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="7073b-123">Si la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'écoute sur un port fixe et l'ouverture du port est une solution qui ne vous convient pas, vous pouvez également inscrire le fichier exécutable de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Sqlservr.exe) en tant qu'exception pour les programmes verrouillés.</span><span class="sxs-lookup"><span data-stu-id="7073b-123">As an alternative to configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a fixed port and opening the port, you can list the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable (Sqlservr.exe) as an exception to the blocked programs.</span></span> <span data-ttu-id="7073b-124">Optez pour cette méthode si vous souhaitez continuer à utiliser des ports dynamiques.</span><span class="sxs-lookup"><span data-stu-id="7073b-124">Use this method when you want to continue to use dynamic ports.</span></span> <span data-ttu-id="7073b-125">Vous ne pouvez accéder qu'à une seule instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7073b-125">Only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be accessed in this way.</span></span>  
  
 <span data-ttu-id="7073b-126">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="7073b-126">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7073b-127">**Avant de commencer :**</span><span class="sxs-lookup"><span data-stu-id="7073b-127">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7073b-128">Sécurité</span><span class="sxs-lookup"><span data-stu-id="7073b-128">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7073b-129">**Pour configurer un pare-feu Windows donnant accès au moteur de base de données avec :**</span><span class="sxs-lookup"><span data-stu-id="7073b-129">**To configure a Windows Firewall for Database Engine access, using:**</span></span>  
  
     [<span data-ttu-id="7073b-130">Gestionnaire de configuration SQL Server</span><span class="sxs-lookup"><span data-stu-id="7073b-130">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
## <a name="before-you-begin"></a><span data-ttu-id="7073b-131">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7073b-131">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7073b-132">Sécurité</span><span class="sxs-lookup"><span data-stu-id="7073b-132">Security</span></span>  
 <span data-ttu-id="7073b-133">L'ouverture de ports dans votre pare-feu peut exposer votre serveur à des attaques malveillantes.</span><span class="sxs-lookup"><span data-stu-id="7073b-133">Opening ports in your firewall can leave your server exposed to malicious attacks.</span></span> <span data-ttu-id="7073b-134">Assurez-vous de comprendre le fonctionnement des systèmes de pare-feu avant d'ouvrir des ports.</span><span class="sxs-lookup"><span data-stu-id="7073b-134">Make sure that you understand firewall systems before you open ports.</span></span> <span data-ttu-id="7073b-135">Pour plus d'informations, consultez [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span><span class="sxs-lookup"><span data-stu-id="7073b-135">For more information, see [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7073b-136">Utilisation du Gestionnaire de configuration SQL Server</span><span class="sxs-lookup"><span data-stu-id="7073b-136">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="7073b-137">S'applique à Windows Vista, Windows 7 et Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="7073b-137">Applies to Windows Vista, Windows 7, and Windows Server 2008</span></span>  
  
 <span data-ttu-id="7073b-138">Les procédures suivantes configurent le Pare-feu Windows à l'aide du composant logiciel enfichable MMC (Microsoft Management Console) de fonctions avancées de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7073b-138">The following procedures configure the Windows Firewall by using the Windows Firewall with Advanced Security Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="7073b-139">Le Pare-feu Windows avec fonctions avancées de sécurité configure uniquement le profil actuel.</span><span class="sxs-lookup"><span data-stu-id="7073b-139">The Windows Firewall with Advanced Security only configures the current profile.</span></span> <span data-ttu-id="7073b-140">Pour plus d’informations sur le Pare-feu Windows avec fonctions avancées de sécurité, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span><span class="sxs-lookup"><span data-stu-id="7073b-140">For more information about the Windows Firewall with Advanced Security, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)</span></span>  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access"></a><span data-ttu-id="7073b-141">Pour ouvrir un port dans le pare-feu Windows pour l'accès TCP</span><span class="sxs-lookup"><span data-stu-id="7073b-141">To open a port in the Windows firewall for TCP access</span></span>  
  
1.  <span data-ttu-id="7073b-142">Dans le menu **Démarrer** , cliquez sur **Exécuter**, tapez **WF.msc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7073b-142">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="7073b-143">Dans le **Pare-feu Windows avec fonctions avancées de sécurité**, dans le volet gauche, cliquez avec le bouton droit sur **Règles de trafic entrant**, puis cliquez sur **Nouvelle règle** dans le volet Action.</span><span class="sxs-lookup"><span data-stu-id="7073b-143">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="7073b-144">Dans la boîte de dialogue **Type de règle** , sélectionnez **Port**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-144">In the **Rule Type** dialog box, select **Port**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7073b-145">Dans la boîte de dialogue **Protocoles et ports** , sélectionnez **TCP**.</span><span class="sxs-lookup"><span data-stu-id="7073b-145">In the **Protocol and Ports** dialog box, select **TCP**.</span></span> <span data-ttu-id="7073b-146">Sélectionnez **ports locaux spécifiques**, puis tapez le numéro de port de l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , par exemple `1433` pour l’instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="7073b-146">Select **Specific local ports**, and then type the port number of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], such as `1433` for the default instance.</span></span> <span data-ttu-id="7073b-147">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-147">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="7073b-148">Dans la boîte de dialogue **Action** , sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-148">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="7073b-149">Dans la boîte de dialogue **Profil** , sélectionnez des profils qui décrivent l'environnement de connexion de l'ordinateur lorsque vous souhaitez vous connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-149">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="7073b-150">Dans la boîte de dialogue **Nom**, entrez un nom et une description pour cette règle, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="7073b-150">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
#### <a name="to-open-access-to-sql-server-when-using-dynamic-ports"></a><span data-ttu-id="7073b-151">Pour ouvrir l'accès à SQL Server lors de l'utilisation de ports dynamiques</span><span class="sxs-lookup"><span data-stu-id="7073b-151">To open access to SQL Server when using dynamic ports</span></span>  
  
1.  <span data-ttu-id="7073b-152">Dans le menu **Démarrer** , cliquez sur **Exécuter**, tapez **WF.msc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7073b-152">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="7073b-153">Dans le **Pare-feu Windows avec fonctions avancées de sécurité**, dans le volet gauche, cliquez avec le bouton droit sur **Règles de trafic entrant**, puis cliquez sur **Nouvelle règle** dans le volet Action.</span><span class="sxs-lookup"><span data-stu-id="7073b-153">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="7073b-154">Dans la boîte de dialogue **Type de règle** , sélectionnez **Programme**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-154">In the **Rule Type** dialog box, select **Program**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7073b-155">Dans la boîte de dialogue **Programme** , sélectionnez **Ce chemin d'accès au programme**.</span><span class="sxs-lookup"><span data-stu-id="7073b-155">In the **Program** dialog box, select **This program path**.</span></span> <span data-ttu-id="7073b-156">Cliquez sur **Parcourir**et accédez à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous voulez accéder par le biais du pare-feu, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7073b-156">Click **Browse**, and navigate to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to access through the firewall, and then click **Open**.</span></span> <span data-ttu-id="7073b-157">Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**.</span><span class="sxs-lookup"><span data-stu-id="7073b-157">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is at **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**.</span></span> <span data-ttu-id="7073b-158">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="7073b-159">Dans la boîte de dialogue **Action** , sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-159">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="7073b-160">Dans la boîte de dialogue **Profil** , sélectionnez des profils qui décrivent l'environnement de connexion de l'ordinateur lorsque vous souhaitez vous connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7073b-160">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="7073b-161">Dans la boîte de dialogue **Nom**, entrez un nom et une description pour cette règle, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="7073b-161">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
  