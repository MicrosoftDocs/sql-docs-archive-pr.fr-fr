---
title: Se connecter à un serveur de rapports en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603234"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="a16df-102">Se connecter à un serveur de rapports en mode natif</span><span class="sxs-lookup"><span data-stu-id="a16df-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="a16df-103">Utilisez cette boîte de dialogue pour vous connecter à une instance du serveur de rapports [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieure) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , locale ou distante.</span><span class="sxs-lookup"><span data-stu-id="a16df-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="a16df-104">Vous ne pouvez pas utiliser cet outil pour vous connecter aux versions antérieures de serveurs de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a16df-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="a16df-105">Vous ne pouvez vous connecter qu'à une instance à la fois.</span><span class="sxs-lookup"><span data-stu-id="a16df-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="a16df-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.</span><span class="sxs-lookup"><span data-stu-id="a16df-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a16df-107">Le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas nécessaire pour configurer et administrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a16df-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="a16df-108">Vous utilisez l'Administration centrale de SharePoint et les scripts PowerShell pour configurer un serveur de rapports en mode SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a16df-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="a16df-109">Pour plus d’informations, consultez [installer Reporting Services mode SharePoint pour sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="a16df-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a16df-110">Le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) est installé avec un niveau de privilège « highestAvailable ».</span><span class="sxs-lookup"><span data-stu-id="a16df-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="a16df-111">Ce comportement est normal.</span><span class="sxs-lookup"><span data-stu-id="a16df-111">This behavior is by design.</span></span> <span data-ttu-id="a16df-112">Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a besoin de la communication avec des API WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a16df-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="a16df-113">Une partie de la communication WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requiert un niveau supérieur ou d'administration des privilèges.</span><span class="sxs-lookup"><span data-stu-id="a16df-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="a16df-114">Pour vous connecter à une instance locale du serveur de rapports, utilisez les valeurs par défaut et cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="a16df-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="a16df-115">Le gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit le nom du serveur local et détecte l'instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="a16df-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="a16df-116">Dans la plupart des cas, vous pouvez cliquer sur **Se connecter** sans avoir à modifier les valeurs.</span><span class="sxs-lookup"><span data-stu-id="a16df-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="a16df-117">Si vous avez installé plusieurs instances, vous devez sélectionner celle que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="a16df-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="a16df-118">Pour vous connecter à une instance de serveur de rapports distante, tapez le nom du serveur, cliquez sur **Rechercher**, sélectionnez l'instance, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="a16df-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="a16df-119">Pour ouvrir cette boîte de dialogue, démarrez le gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a16df-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="a16df-120">Cette boîte de dialogue apparaît immédiatement lorsque vous démarrez l'outil.</span><span class="sxs-lookup"><span data-stu-id="a16df-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="a16df-121">Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a16df-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a16df-122">Options</span><span class="sxs-lookup"><span data-stu-id="a16df-122">Options</span></span>  
 <span data-ttu-id="a16df-123">**Nom de serveur**</span><span class="sxs-lookup"><span data-stu-id="a16df-123">**Server Name**</span></span>  
 <span data-ttu-id="a16df-124">Entrez le nom de réseau de l'ordinateur sur lequel [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieure) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="a16df-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="a16df-125">Tapez simplement le nom de l'ordinateur, sans inclure de préfixe ou de barre oblique.</span><span class="sxs-lookup"><span data-stu-id="a16df-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="a16df-126">**Trouver**</span><span class="sxs-lookup"><span data-stu-id="a16df-126">**Find**</span></span>  
 <span data-ttu-id="a16df-127">Recherchez l'ordinateur spécifié dans **Nom du serveur**.</span><span class="sxs-lookup"><span data-stu-id="a16df-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="a16df-128">**Instance du serveur de rapports**</span><span class="sxs-lookup"><span data-stu-id="a16df-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="a16df-129">Sélectionnez l'instance à laquelle se connecter si plusieurs instances de serveur de rapports sont installées.</span><span class="sxs-lookup"><span data-stu-id="a16df-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="a16df-130">Seules les instances valides sont disponibles pour la sélection.</span><span class="sxs-lookup"><span data-stu-id="a16df-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="a16df-131">Si vous exécutez côte à côte des versions antérieures de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ces instances n'apparaîtront pas dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a16df-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="a16df-132">**Connexion**</span><span class="sxs-lookup"><span data-stu-id="a16df-132">**Connect**</span></span>  
 <span data-ttu-id="a16df-133">Connectez-vous au serveur et à l'instance que vous avez spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a16df-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16df-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a16df-134">See Also</span></span>  
 [<span data-ttu-id="a16df-135">Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;</span><span class="sxs-lookup"><span data-stu-id="a16df-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  