---
title: Remise par partage de fichiers dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bba83a89612f8601adedd827edad0e587d096d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613814"
---
# <a name="file-share-delivery-in-reporting-services"></a><span data-ttu-id="34469-102">Remise par partage de fichiers dans Reporting Services</span><span class="sxs-lookup"><span data-stu-id="34469-102">File Share Delivery in Reporting Services</span></span>
  <span data-ttu-id="34469-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de remise de partage de fichiers qui vous permet de remettre un rapport dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="34469-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes a file share delivery extension so that you can deliver a report to a folder.</span></span> <span data-ttu-id="34469-104">Cette extension est disponible par défaut et elle ne nécessite aucune configuration supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="34469-104">The file share delivery extension is available by default and requires no additional configuration.</span></span> <span data-ttu-id="34469-105">Pour que la remise de fichier réussisse, vous devez définir des autorisations d'accès en écriture sur le dossier partagé.</span><span class="sxs-lookup"><span data-stu-id="34469-105">In order for file delivery to succeed, you must set write access permissions on the shared folder.</span></span> <span data-ttu-id="34469-106">En outre, les utilisateurs qui demandent l'accès aux rapports doivent avoir des autorisations de lecture sur le dossier partagé.</span><span class="sxs-lookup"><span data-stu-id="34469-106">In addition, users who require access to the reports must have read permissions on the shared folder.</span></span>  
  
 <span data-ttu-id="34469-107">Pour distribuer un rapport dans un partage de fichiers, vous devez définir un abonnement standard ou piloté par les données.</span><span class="sxs-lookup"><span data-stu-id="34469-107">To distribute a report to a file share, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="34469-108">Vous ne pouvez vous abonner et ne demander la remise que d'un seul rapport à la fois.</span><span class="sxs-lookup"><span data-stu-id="34469-108">You can subscribe to and request delivery for only one report at a time.</span></span> <span data-ttu-id="34469-109">Pour savoir comment utiliser la remise par partage de fichiers pour un abonnement piloté par les données, consultez [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="34469-109">To learn how to use file share delivery in a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span> <span data-ttu-id="34469-110">Par ailleurs, le compte qui exécute des abonnements de partage de fichiers distants nécessite des droits pour ouvrir une session locale sur l'ordinateur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34469-110">Additionally, the account that runs remote file share subscriptions requires rights to log on locally on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] computer.</span></span>  
  
||  
|-|  
|<span data-ttu-id="34469-111">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint</span><span class="sxs-lookup"><span data-stu-id="34469-111">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="34469-112">Dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="34469-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="34469-113">Caractéristiques d'un rapport qui est remis dans un dossier partagé</span><span class="sxs-lookup"><span data-stu-id="34469-113">Characteristics of a Report That is Delivered to a Shared Folder</span></span>](#bkmk_Characteristics)  
  
-   [<span data-ttu-id="34469-114">Dossiers cibles</span><span class="sxs-lookup"><span data-stu-id="34469-114">Target Folders</span></span>](#bkmk_target_folders)  
  
-   [<span data-ttu-id="34469-115">Formats de fichier</span><span class="sxs-lookup"><span data-stu-id="34469-115">File Formats</span></span>](#bkmk_file_formats)  
  
-   [<span data-ttu-id="34469-116">Options de fichier</span><span class="sxs-lookup"><span data-stu-id="34469-116">File Options</span></span>](#bkmk_file_options)  
  
##  <a name="characteristics-of-a-report-that-is-delivered-to-a-shared-folder"></a><a name="bkmk_Characteristics"></a><span data-ttu-id="34469-117">Caractéristiques d’un rapport qui est remis à un dossier partagé</span><span class="sxs-lookup"><span data-stu-id="34469-117">Characteristics of a Report That is Delivered to a Shared Folder</span></span>  
 <span data-ttu-id="34469-118">Contrairement aux rapports qui sont hébergés et gérés par un serveur de rapports, les rapports qui sont remis dans un dossier partagé sont des fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="34469-118">Unlike reports that are hosted and managed by a report server, reports that are delivered to a shared folder are static files.</span></span> <span data-ttu-id="34469-119">Les fonctionnalités interactives qui sont définies pour le rapport ne fonctionnent pas pour les rapports qui sont stockés en tant que fichiers dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="34469-119">Interactive features that are defined for the report do not work for reports that are stored as files on the file system.</span></span> <span data-ttu-id="34469-120">Les fonctionnalités d'interaction sont représentées comme des éléments statiques.</span><span class="sxs-lookup"><span data-stu-id="34469-120">Interaction features are represented as static elements.</span></span> <span data-ttu-id="34469-121">Par exemple, si vous remettez un rapport de matrice, le fichier généré offre une vue de niveau supérieur du rapport ; vous ne pouvez pas étendre les lignes et les colonnes pour afficher les données associées.</span><span class="sxs-lookup"><span data-stu-id="34469-121">For example, if you deliver a matrix report, the resulting file shows the top-level view of the report; you cannot expand rows and columns to view supporting data.</span></span> <span data-ttu-id="34469-122">Si le rapport contient des graphiques, la présentation par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="34469-122">If the report includes charts, the default presentation is used.</span></span> <span data-ttu-id="34469-123">Si le rapport contient un lien vers un autre rapport, le lien apparaît sous forme de texte statique.</span><span class="sxs-lookup"><span data-stu-id="34469-123">If the report links through to another report, the link is rendered as static text.</span></span> <span data-ttu-id="34469-124">Si vous voulez conserver les fonctionnalités interactives dans un rapport remis, utilisez la remise par courrier électronique à la place.</span><span class="sxs-lookup"><span data-stu-id="34469-124">If you want to retain interactive features in a delivered report, use e-mail delivery instead.</span></span> <span data-ttu-id="34469-125">Pour plus d’informations, consultez [Remise par courrier électronique dans Reporting Services](e-mail-delivery-in-reporting-services.md).</span><span class="sxs-lookup"><span data-stu-id="34469-125">For more information, see [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
##  <a name="target-folders"></a><a name="bkmk_target_folders"></a><span data-ttu-id="34469-126">Dossiers cibles</span><span class="sxs-lookup"><span data-stu-id="34469-126">Target Folders</span></span>  
 <span data-ttu-id="34469-127">Lorsque vous définissez un abonnement qui utilise la remise dans un partage de fichiers, vous devez spécifier un dossier existant comme dossier cible.</span><span class="sxs-lookup"><span data-stu-id="34469-127">When defining a subscription that uses file share delivery, you must specify an existing folder as the target folder.</span></span> <span data-ttu-id="34469-128">Le serveur de rapports ne crée pas de dossiers sur le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="34469-128">The report server does not create folders on the file system.</span></span> <span data-ttu-id="34469-129">Le dossier que vous spécifiez doit être accessible via une connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="34469-129">The folder that you specify must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="34469-130">Vérifiez que les utilisateurs qui afficheront les rapports dans le dossier partagé ont une autorisation Lecture.</span><span class="sxs-lookup"><span data-stu-id="34469-130">Verify that users who will view the reports in the shared folder have Read permission.</span></span>  
  
 <span data-ttu-id="34469-131">Lors de la spécification d'un dossier cible dans un abonnement, utilisez le format UNC (Uniform Naming Convention) qui inclut le nom réseau de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="34469-131">When specifying the target folder in a subscription, use Uniform Naming Convention (UNC) format that includes the computer's network name.</span></span> <span data-ttu-id="34469-132">N'incluez pas de barre oblique inverse à la fin du chemin d'accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="34469-132">Do not include trailing backslashes in the folder path.</span></span> <span data-ttu-id="34469-133">L'exemple suivant illustre un chemin UNC :</span><span class="sxs-lookup"><span data-stu-id="34469-133">The following example illustrates a UNC path:</span></span>  
  
```  
\\<servername>\reportarchive\operations\2003  
```  
  
 <span data-ttu-id="34469-134">Lorsque vous créez le dossier, tenez compte des limites de connexion requises.</span><span class="sxs-lookup"><span data-stu-id="34469-134">When you create the folder, consider the connection limits you require.</span></span> <span data-ttu-id="34469-135">Le serveur de rapports nécessite deux connexions, mais vous devez inclure suffisamment de connexions pour la prise en charge des utilisateurs complémentaires qui veulent ouvrir des rapports sur le dossier partagé.</span><span class="sxs-lookup"><span data-stu-id="34469-135">The report server requires two connections, but you must include enough connections to accommodate additional users who want to open reports on the shared folder.</span></span>  
  
##  <a name="file-formats"></a><a name="bkmk_file_formats"></a> <span data-ttu-id="34469-136">Formats de fichier</span><span class="sxs-lookup"><span data-stu-id="34469-136">File Formats</span></span>  
 <span data-ttu-id="34469-137">Les rapports peuvent être rendus dans plusieurs formats de fichier, tels que HTML ou Excel.</span><span class="sxs-lookup"><span data-stu-id="34469-137">Reports can be rendered in a variety of file formats, such as HTML or Excel.</span></span> <span data-ttu-id="34469-138">Pour enregistrer le rapport dans un format de fichier spécifique, sélectionnez le format de rendu au moment de la création de l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="34469-138">To save the report in a specific file format, select that rendering format when creating your subscription.</span></span> <span data-ttu-id="34469-139">Par exemple, en choisissant **Excel** , vous enregistrez le rapport sous la forme d'un fichier [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34469-139">For example, choosing **Excel** saves the report as a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] file.</span></span> <span data-ttu-id="34469-140">Bien que vous puissiez choisir n'importe quel format de rendu pris en charge, certains formats sont mieux adaptés que d'autres.</span><span class="sxs-lookup"><span data-stu-id="34469-140">Although you can choose from any supported rendering format, some formats work better than others when rendering to a file.</span></span>  
  
 <span data-ttu-id="34469-141">Pour la remise par partage de fichiers, choisissez un format qui assure la remise du rapport dans un seul fichier, où toutes les images et le contenu associé sont inclus dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="34469-141">For file share delivery, choose a format that delivers the report in a single file, where all images and related content are included in the report.</span></span> <span data-ttu-id="34469-142">Les formats appropriés sont les suivants : archive Web, PDF, TIFF et Excel.</span><span class="sxs-lookup"><span data-stu-id="34469-142">Suitable formats include Web archive, PDF, TIFF, and Excel.</span></span> <span data-ttu-id="34469-143">Évitez le format HTML 4.0.</span><span class="sxs-lookup"><span data-stu-id="34469-143">Avoid HTML4.0.</span></span> <span data-ttu-id="34469-144">Si votre rapport comporte des images, le format HTML 4.0 ne permettra pas de les inclure dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="34469-144">If your report includes images, the HTML 4.0 formats will not include them in the file.</span></span>  
  
##  <a name="file-options"></a><a name="bkmk_file_options"></a> <span data-ttu-id="34469-145">Options de fichier</span><span class="sxs-lookup"><span data-stu-id="34469-145">File Options</span></span>  
 <span data-ttu-id="34469-146">Lorsque vous créez un abonnement, vous pouvez choisir les options qui déterminent comment le nom de fichier est créé et s'il est remplacé par des versions plus récentes dans le temps.</span><span class="sxs-lookup"><span data-stu-id="34469-146">When you create a subscription, you can choose options that determine how the file name is created and whether it is replaced by newer versions over time.</span></span> <span data-ttu-id="34469-147">Un nom de fichier complet comprend trois parties : un nom, une extension et du texte ou un nombre ajouté au fichier pour créer un nom de fichier unique.</span><span class="sxs-lookup"><span data-stu-id="34469-147">A fully qualified file name has three parts: a name, an extension, and text or a number that is appended to the file to create a unique file name.</span></span> <span data-ttu-id="34469-148">Les options de remplacement déterminent si le texte ou le nombre est ajouté au nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="34469-148">Overwrite options determine whether the text or number is added to the file name.</span></span>  
  
 <span data-ttu-id="34469-149">Le nom de fichier est basé sur le nom du rapport, mais vous pouvez indiquer un nom personnalisé dans l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="34469-149">The file name is based on the report name, but you can provide a custom name in the subscription.</span></span> <span data-ttu-id="34469-150">L'extension est facultative, mais si vous la spécifiez, le serveur de rapports créera une extension qui correspond au format de rendu.</span><span class="sxs-lookup"><span data-stu-id="34469-150">The extension is optional, but if you specify it, the report server will create an extension that corresponds to the rendering format.</span></span>  
  
 <span data-ttu-id="34469-151">Vous pouvez spécifier des options de remplacement afin de réutiliser le même nom de fichier pour chaque remise de rapport ou pour créer un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="34469-151">You can specify overwrite options to reuse the same file name for each report delivery or to create a new file.</span></span> <span data-ttu-id="34469-152">Pour remplacer le fichier, vous devez utiliser les mêmes nom et extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="34469-152">To overwrite the file, you must use the same file name and extension.</span></span>  
  
 <span data-ttu-id="34469-153">Pour créer des noms de fichiers uniques pour la remise de rapport, il existe une autre approche qui consiste à inclure un élément d'horodatage dans le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="34469-153">An alternative approach to creating unique files for every delivery is to include a timestamp in the file name.</span></span> <span data-ttu-id="34469-154">Pour ce faire, ajoutez la variable `@timestamp` au nom de fichier (par exemple, *CompanySales@timestamp*).</span><span class="sxs-lookup"><span data-stu-id="34469-154">To do this, add the `@timestamp` variable to the file name (for example, *CompanySales@timestamp*).</span></span> <span data-ttu-id="34469-155">Avec cette approche, le nom de fichier est unique par définition : il ne sera jamais remplacé.</span><span class="sxs-lookup"><span data-stu-id="34469-155">With this approach, the file name is unique by definition, so it will never be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34469-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34469-156">See Also</span></span>  
 [<span data-ttu-id="34469-157">Créez, modifiez et supprimez les abonnements standard &#40;Reporting Services en mode natif&#41;</span><span class="sxs-lookup"><span data-stu-id="34469-157">Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;</span></span>](create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  