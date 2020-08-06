---
title: Utilitaires d’invite de commandes du serveur de rapports (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07da79ea46ca0e9e23abb7197730821d8c31bfa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603243"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a><span data-ttu-id="ff488-102">Utilitaires d'invite de commandes du serveur de rapports (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff488-102">Report Server Command Prompt Utilities (SSRS)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ff488-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend plusieurs utilitaires de ligne de commande qui permettent d’administrer un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="ff488-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes several command line utilities that you can use to administer a report server.</span></span> <span data-ttu-id="ff488-104">Ces utilitaires sont installés automatiquement lorsque vous installez un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="ff488-104">These utilities are installed automatically when you install a report server.</span></span>  
  
|<span data-ttu-id="ff488-105">Name</span><span class="sxs-lookup"><span data-stu-id="ff488-105">Name</span></span>|<span data-ttu-id="ff488-106">Fichier de commandes</span><span class="sxs-lookup"><span data-stu-id="ff488-106">Command file</span></span>|<span data-ttu-id="ff488-107">Mode de déploiement pris en charge</span><span class="sxs-lookup"><span data-stu-id="ff488-107">Supported Deployment mode</span></span>|<span data-ttu-id="ff488-108">Description</span><span class="sxs-lookup"><span data-stu-id="ff488-108">Description</span></span>|  
|----------|------------------|-------------------------------|-----------------|  
|<span data-ttu-id="ff488-109">Utilitaire RSS</span><span class="sxs-lookup"><span data-stu-id="ff488-109">RSS utility</span></span>|<span data-ttu-id="ff488-110">rs.exe</span><span class="sxs-lookup"><span data-stu-id="ff488-110">rs.exe</span></span>|<span data-ttu-id="ff488-111">Mode natif et mode SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ff488-111">Native mode and SharePoint mode.</span></span> <span data-ttu-id="ff488-112">La version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] inclut la prise en charge du mode SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ff488-112">The [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] release introduced SharePoint mode support.</span></span>|<span data-ttu-id="ff488-113">[L’utilitaire rs.exe](rs-exe-utility-ssrs.md) est un hôte de script que vous pouvez utiliser pour réaliser des opérations contenant des scripts.</span><span class="sxs-lookup"><span data-stu-id="ff488-113">The [rs utility](rs-exe-utility-ssrs.md) is a script host that you can use to perform scripted operations.</span></span> <span data-ttu-id="ff488-114">Par son intermédiaire, vous exécutez des scripts [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] pour publier des rapports, créer des éléments dans une base de données de serveur de rapports, copier des données entre des bases de données de serveurs de rapports, etc.</span><span class="sxs-lookup"><span data-stu-id="ff488-114">Use this tool to run [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts that copy data between report server databases, publish reports, create items in a report server database, and more.</span></span> <span data-ttu-id="ff488-115">Pour en savoir plus sur l’utilisation de scripts permettant d’administrer un serveur, consultez [Écrire des scripts pour les tâches d’administration et de déploiement](script-deployment-and-administrative-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="ff488-115">To learn more about using scripts to administer a server, see [Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md).</span></span>|  
|<span data-ttu-id="ff488-116">Applets de commande Powershell</span><span class="sxs-lookup"><span data-stu-id="ff488-116">Powershell cmdlets</span></span>||<span data-ttu-id="ff488-117">SharePoint uniquement</span><span class="sxs-lookup"><span data-stu-id="ff488-117">SharePoint only</span></span>|<span data-ttu-id="ff488-118">Pour obtenir la liste des applets de commande PowerShell, consultez [Applets de commande PowerShell pour le mode SharePoint de Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span><span class="sxs-lookup"><span data-stu-id="ff488-118">For a list of the of the powershell cmdlets, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>|  
|<span data-ttu-id="ff488-119">rsconfig (utilitaire)</span><span class="sxs-lookup"><span data-stu-id="ff488-119">Rsconfig utility</span></span>|<span data-ttu-id="ff488-120">rsconfig.exe</span><span class="sxs-lookup"><span data-stu-id="ff488-120">rsconfig.exe</span></span>|<span data-ttu-id="ff488-121">Natif uniquement</span><span class="sxs-lookup"><span data-stu-id="ff488-121">Native only</span></span>|<span data-ttu-id="ff488-122">[L’utilitaire rsconfig](rsconfig-utility-ssrs.md) sert à configurer et à gérer une connexion de serveur de rapports à une base de données connexe,</span><span class="sxs-lookup"><span data-stu-id="ff488-122">The [rsconfig utility](rsconfig-utility-ssrs.md) is used to configure and manage a report server connection to the report server database.</span></span> <span data-ttu-id="ff488-123">mais aussi à définir un compte d'utilisateur pour le traitement des rapports autonomes.</span><span class="sxs-lookup"><span data-stu-id="ff488-123">You can also use it to specify a user account to use for unattended report processing.</span></span> <span data-ttu-id="ff488-124">Pour plus d’informations, consultez [Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="ff488-124">For more information, see [Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md).</span></span> <span data-ttu-id="ff488-125">Pour en savoir plus sur la configuration de la connexion, consultez [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span><span class="sxs-lookup"><span data-stu-id="ff488-125">To learn more about connection configuration, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>|  
|<span data-ttu-id="ff488-126">Utilitaire Rskeymgmt</span><span class="sxs-lookup"><span data-stu-id="ff488-126">Rskeymgmt Utility</span></span>|<span data-ttu-id="ff488-127">rskeymgmt.exe</span><span class="sxs-lookup"><span data-stu-id="ff488-127">rskeymgmt.exe</span></span>|<span data-ttu-id="ff488-128">Natif uniquement</span><span class="sxs-lookup"><span data-stu-id="ff488-128">Native only</span></span>|<span data-ttu-id="ff488-129">[L’utilitaire rskeymgmt](rskeymgmt-utility-ssrs.md) est un outil de gestion de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="ff488-129">The [rskeymgmt utility](rskeymgmt-utility-ssrs.md) is an encryption key management tool.</span></span> <span data-ttu-id="ff488-130">Utilisez-le pour sauvegarder, appliquer, recréer et supprimer des clés symétriques.</span><span class="sxs-lookup"><span data-stu-id="ff488-130">You can use it to back up, apply, recreate, and delete symmetric keys.</span></span> <span data-ttu-id="ff488-131">Cet outil sert également à attacher une instance de serveur de rapports à une base de données de serveur de rapports partagée.</span><span class="sxs-lookup"><span data-stu-id="ff488-131">You can also use this tool to attach a report server instance to a shared report server database.</span></span> <span data-ttu-id="ff488-132">Rskeymgmt est utile dans les opérations de récupération de base de données.</span><span class="sxs-lookup"><span data-stu-id="ff488-132">Rskeymgmt can be used in database recovery operations.</span></span> <span data-ttu-id="ff488-133">Réutilisez une base de données dans une nouvelle installation en appliquant un exemplaire sauvegardé de clé symétrique.</span><span class="sxs-lookup"><span data-stu-id="ff488-133">You can reuse an existing database in a new installation by applying a back up copy of the symmetric key.</span></span> <span data-ttu-id="ff488-134">Si les clés ne peuvent pas être récupérées, cet outil permet de supprimer le contenu chiffré dont vous ne vous servez plus.</span><span class="sxs-lookup"><span data-stu-id="ff488-134">If the keys cannot be recovered, this tool provides a way to delete encrypted content that you no longer use.</span></span> <span data-ttu-id="ff488-135">Pour en savoir plus sur la gestion des clés et le stockage des données confidentielles, consultez [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) et [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).</span><span class="sxs-lookup"><span data-stu-id="ff488-135">To learn more about key management and storage of sensitive data, see [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) and [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ff488-136">Si vous préférez utiliser un outil à interface utilisateur graphique, choisissez le gestionnaire de configuration de Reporting Services au lieu de `rsconfig` et de `rskeymgmt`.</span><span class="sxs-lookup"><span data-stu-id="ff488-136">If you prefer to use a tool that has a graphical user interface, you can use the Reporting Services Configuration manager instead of `rsconfig` and `rskeymgmt`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff488-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff488-137">See Also</span></span>  
 <span data-ttu-id="ff488-138">[Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ff488-138">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="ff488-139">[Outils de Reporting Services](reporting-services-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ff488-139">[Reporting Services Tools](reporting-services-tools.md) </span></span>  
 [<span data-ttu-id="ff488-140">Serveur de rapports Reporting Services &#40;mode natif&#41;</span><span class="sxs-lookup"><span data-stu-id="ff488-140">Reporting Services Report Server &#40;Native Mode&#41;</span></span>](../report-server/reporting-services-report-server-native-mode.md)  
  
  