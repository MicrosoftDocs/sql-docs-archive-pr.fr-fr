---
title: Changer le compte de démarrage du service pour SQL Server (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c14c1756ac66c4a377271a13e61a307e53ac1ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697152"
---
# <a name="change-the-service-startup-account-for-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="1ec8c-102">Modifier le compte de démarrage du service pour SQL Server (Gestionnaire de configuration SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1ec8c-102">Change the Service Startup Account for SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="1ec8c-103">Cette rubrique explique comment utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager pour changer les options de démarrage des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour changer les comptes de service qui sont utilisés par [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ec8c-103">This topic describes how to Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change the start up options of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and to change the service accounts that are used by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="1ec8c-104">Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-104">in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="1ec8c-105">Pour plus d’informations sur la sélection d’un compte de service adéquat, consultez [Configurer les comptes de service Windows et les autorisations](configure-windows-service-accounts-and-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8c-105">For more information about how to select an appropriate service account, see [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ec8c-106">Lorsque vous modifiez le compte de démarrage du service pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]) doit être redémarré pour que la modification soit prise en compte.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-106">When you change the service startup account for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service (the [!INCLUDE[ssDE](../../includes/ssde-md.md)]) must be restarted for the change to take effect.</span></span> <span data-ttu-id="1ec8c-107">Lorsque le service redémarre, toutes les bases de données associées à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne seront pas disponibles tant que le service n'a pas redémarré correctement.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-107">When the service is restarted, all databases associated with that instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be unavailable until the service successfully restarts.</span></span> <span data-ttu-id="1ec8c-108">Si vous devez modifier le compte de démarrage du service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , veillez à effectuer cette opération au cours des opérations de maintenance planifiées régulièrement ou lorsqu'il est possible de mettre les bases de données hors ligne sans interrompre les opérations quotidiennes.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-108">If you have to change the service startup account of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, make sure that you do so during regularly scheduled maintenance or when the databases can be taken offline without interrupting daily operations.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ec8c-109">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="1ec8c-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1ec8c-110">Limitations et restrictions</span><span class="sxs-lookup"><span data-stu-id="1ec8c-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1ec8c-111">Serveurs en cluster</span><span class="sxs-lookup"><span data-stu-id="1ec8c-111">Clustered servers</span></span>  
  
     <span data-ttu-id="1ec8c-112">La modification du compte de service utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être effectuée à partir du nœud actif du cluster [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ec8c-112">Changing the service account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be performed from the active node of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cluster.</span></span>  
  
     <span data-ttu-id="1ec8c-113">Lors de l'exécution sur Windows Server 2008 (dans une configuration autre que celle par défaut utilisant des groupes de domaines), la modification du compte de service utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arrête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mettant les groupes de ressources hors ligne.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-113">When running on Windows Server 2008 (in a non-default configuration using Domain groups), changing the service account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by taking the resource groups offline.</span></span>  
  
-   <span data-ttu-id="1ec8c-114">Mise à niveau de SKU ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] vers SKU non-Express)</span><span class="sxs-lookup"><span data-stu-id="1ec8c-114">SKU Upgrade ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] to non-Express SKU)</span></span>  
  
     <span data-ttu-id="1ec8c-115">Au cours de l'installation de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est configuré pour utiliser le compte de service réseau, mais est désactivé.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-115">During [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installation, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is configured to use the Network Service account but disabled.</span></span> <span data-ttu-id="1ec8c-116">Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut changer le compte affecté au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, mais le service ne peut pas être activé ou démarré.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager can change the account assigned for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service but the service cannot be enabled or started.</span></span> <span data-ttu-id="1ec8c-117">Après la mise à niveau d'une référence SKU de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] vers non-Express, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'est pas automatiquement activé, mais il peut l'être lorsque cela est nécessaire en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et en modifiant le mode de démarrage du service par Manuel ou Automatique.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-117">After SKU upgrade from [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] to non-Express, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is not automatically enabled, but can be enabled when needed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and changing the service start mode to Manual or Automatic.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1ec8c-118">Utilisation du Gestionnaire de configuration SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ec8c-118">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a><span data-ttu-id="1ec8c-119">Pour modifier le compte de démarrage du service SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ec8c-119">To change the SQL Server service startup account</span></span>  
  
1.  <span data-ttu-id="1ec8c-120">Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-120">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ec8c-121">Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-121">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="1ec8c-122">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="1ec8c-122">**Windows 10**:</span></span>  
    >          <span data-ttu-id="1ec8c-123">Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans la **page de démarrage**, tapez SQLServerManager12. msc (pour [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ).</span><span class="sxs-lookup"><span data-stu-id="1ec8c-123">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="1ec8c-124">Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 12 par un nombre plus petit.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-124">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="1ec8c-125">Le fait de cliquer sur SQLServerManager12.msc ouvre le Gestionnaire de Configuration.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-125">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="1ec8c-126">Pour épingler le Configuration Manager à la page de démarrage ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **ouvrir l’emplacement du fichier**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-126">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="1ec8c-127">Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **épingler pour démarrer** ou **Épingler à la barre des tâches**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-127">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="1ec8c-128">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="1ec8c-128">**Windows 8**:</span></span>  
    >          <span data-ttu-id="1ec8c-129">Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans l’icône **Rechercher** , sous **applications**, tapez **SQLServerManager \<version> . msc** , par exemple `SQLServerManager12.msc` , puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-129">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="1ec8c-130">Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Services SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-130">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="1ec8c-131">Dans le volet d’informations, cliquez avec le bouton droit sur le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dont vous souhaitez modifier le compte de démarrage de service, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-131">In the details pane, right-click the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for which you want to change the service startup account, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1ec8c-132">Dans la boîte de dialogue **Propriétés de SQL Server \<***instancename***>** , cliquez sur l’onglet **Ouvrir une session** et sélectionnez un type de compte **Ouvrir une session en tant que**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-132">In the **SQL Server \<***instancename***> Properties** dialog box, click the **Log On** tab, and select a **Log on as** account type.</span></span>  
  
5.  <span data-ttu-id="1ec8c-133">Après avoir sélectionné le nouveau compte de démarrage de service, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ec8c-133">After selecting the new service startup account, click **OK**.</span></span>  
  
     <span data-ttu-id="1ec8c-134">Un message vous demande si vous souhaitez redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ec8c-134">A message box asks whether you want to restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
6.  <span data-ttu-id="1ec8c-135">Cliquez sur **Oui**, puis fermez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ec8c-135">Click **Yes**, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec8c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ec8c-136">See Also</span></span>  
 <span data-ttu-id="1ec8c-137">[Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="1ec8c-137">[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](start-stop-pause-resume-restart-sql-server-services.md) </span></span>  
 [<span data-ttu-id="1ec8c-138">Configurer WMI pour afficher l'état du serveur dans les outils SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ec8c-138">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  