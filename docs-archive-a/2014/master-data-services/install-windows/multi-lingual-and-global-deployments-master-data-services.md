---
title: Déploiements multilingues et globaux (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f10dfa1a1bb001bd6b207064de7c1cf2dee452d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706576"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a><span data-ttu-id="c7d23-102">Déploiements multilingues et globaux (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c7d23-102">Multi-Lingual and Global Deployments (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="c7d23-103">prend en charge le déploiement de composants et d'outils dans toutes les langues prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7d23-103">supports deployment of components and tools in all languages supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7d23-104">Pour plus d'informations, consultez [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="c7d23-104">For more information, see [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).</span></span>  
  
## <a name="how-languages-are-used"></a><span data-ttu-id="c7d23-105">Utilisation des langues</span><span class="sxs-lookup"><span data-stu-id="c7d23-105">How languages are used</span></span>  
 <span data-ttu-id="c7d23-106">Le tableau suivant décrit la prise en charge des langues pour les composants et outils des [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c7d23-106">The following table describes the language support for the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] components and tools.</span></span>  
  
|<span data-ttu-id="c7d23-107">Composant ou outil</span><span class="sxs-lookup"><span data-stu-id="c7d23-107">Component or Tool</span></span>|<span data-ttu-id="c7d23-108">Description</span><span class="sxs-lookup"><span data-stu-id="c7d23-108">Description</span></span>|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="c7d23-109">Programme d'installation</span><span class="sxs-lookup"><span data-stu-id="c7d23-109">Setup</span></span>|<span data-ttu-id="c7d23-110">Sélectionnez le programme d'installation en anglais si vous souhaitez que l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] soit disponible et prise en charge dans d'autres langues que celle du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="c7d23-110">Select the English Setup program when you want the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to be available and supported in languages that differ from the Setup language.</span></span> <span data-ttu-id="c7d23-111">Pour plus d'informations, consultez la description du [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c7d23-111">For more information, see the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] description below.</span></span>|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|<span data-ttu-id="c7d23-112">La langue d'installation détermine celle du [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c7d23-112">The Setup language determines the [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] language.</span></span> <span data-ttu-id="c7d23-113">Par exemple, si vous choisissez l'allemand comme langue d'installation, le [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] est disponible en allemand sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c7d23-113">For example, if you choose German for the Setup language, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] is available in German on that computer.</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|<span data-ttu-id="c7d23-114">Lorsque vous exécutez le programme d'installation en anglais, l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est disponible et prise en charge dans toutes les langues d'application.</span><span class="sxs-lookup"><span data-stu-id="c7d23-114">When you run Setup in English, the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application is available and supported in all application languages.</span></span> [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="c7d23-115">peut être affiché dans n’importe quelle de ces langues d’application et accepter des données spécifiques aux paramètres régionaux basés sur les préférences linguistiques du navigateur web client.</span><span class="sxs-lookup"><span data-stu-id="c7d23-115">can display in any of those application languages and accept locale-specific input based on the language preferences of the client web browser.</span></span> <span data-ttu-id="c7d23-116">Si les préférences linguistiques sont configurées pour une langue d'application non prise en charge, la langue par défaut du [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est l'anglais.</span><span class="sxs-lookup"><span data-stu-id="c7d23-116">If the language preferences are configured for a non-supported application language, [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] defaults to English.</span></span><br /><br /> <span data-ttu-id="c7d23-117">Lorsque vous exécutez le programme d'installation dans une langue autre que l'anglais, les ressources sont incluses pour toutes les autres langues de l'application, mais le fait que les clients utilisent [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] dans une langue autre que la langue d'installation sélectionnée n'est pas un scénario pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c7d23-117">When you run Setup in a language other than English, resources are included for the all other application languages but it is not a supported scenario for clients to use [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in a language other than the selected Setup language.</span></span> <span data-ttu-id="c7d23-118">Si vous essayez d'accéder au [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] dans une langue différente de la langue d'installation, vous pouvez rencontrer des problèmes avec l'entrée et l'affichage des données dans l'application.</span><span class="sxs-lookup"><span data-stu-id="c7d23-118">If you try to access [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in a language different from the Setup language, you might experience problems with data display and input in the application.</span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="c7d23-119">base de données</span><span class="sxs-lookup"><span data-stu-id="c7d23-119">database</span></span>|<span data-ttu-id="c7d23-120">Les informations dans la base de données des [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ne sont pas spécifiques à des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="c7d23-120">Information in the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database is not specific to any locale.</span></span> <span data-ttu-id="c7d23-121">Cela permet au [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] de décider du mode d'affichage des informations, telles que les dates et nombres, au format déterminé par les préférences linguistiques du navigateur Web client.</span><span class="sxs-lookup"><span data-stu-id="c7d23-121">This enables [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to determine how to display information, such as dates and numbers, in the format determined by the language preferences of the client web browser.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7d23-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7d23-122">See Also</span></span>  
 [<span data-ttu-id="c7d23-123">Installer Master Data Services</span><span class="sxs-lookup"><span data-stu-id="c7d23-123">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  