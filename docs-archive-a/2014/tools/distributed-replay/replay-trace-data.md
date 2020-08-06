---
title: Relire les données de trace | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 19ff5285-fb9d-4fd1-97c4-ec72c311c384
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6c929d7c617ba4dc496eedabaccbbe50da32d08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601242"
---
# <a name="replay-trace-data"></a><span data-ttu-id="80cf2-102">Relire les données de trace</span><span class="sxs-lookup"><span data-stu-id="80cf2-102">Replay Trace Data</span></span>
  <span data-ttu-id="80cf2-103">Vous pouvez démarrer une relecture distribuée avec la fonctionnalité [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay après avoir préparé les données de trace d’entrée.</span><span class="sxs-lookup"><span data-stu-id="80cf2-103">You can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature after you have prepared the input trace data.</span></span> <span data-ttu-id="80cf2-104">Pour plus d’informations, consultez [préparer les données de Trace d’entrée](prepare-the-input-trace-data.md).</span><span class="sxs-lookup"><span data-stu-id="80cf2-104">For more information, see [Prepare the Input Trace Data](prepare-the-input-trace-data.md).</span></span>  
  
 <span data-ttu-id="80cf2-105">Utilisez l’option de **relecture** de l’outil d’administration pour initialiser l’étape de relecture d’événements de la relecture distribuée.</span><span class="sxs-lookup"><span data-stu-id="80cf2-105">Use the administration tool **replay** option to initiate the event replay stage of the distributed replay.</span></span> <span data-ttu-id="80cf2-106">Cette étape consiste en deux parties : la répartition des données de trace et le démarrage et la synchronisation de la relecture distribuée.</span><span class="sxs-lookup"><span data-stu-id="80cf2-106">This stage consists of two parts: the trace data dispatch and the starting and synchronizing of the distributed replay.</span></span>  
  
 <span data-ttu-id="80cf2-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span><span class="sxs-lookup"><span data-stu-id="80cf2-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span></span>  
  
 <span data-ttu-id="80cf2-108">Vous pouvez relire les données de trace dans l'un de ces deux modes de mise en séquence : mode simultané (stress) ou mode de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="80cf2-108">You can replay trace data in one of two sequencing modes: stress mode or synchronization mode.</span></span> <span data-ttu-id="80cf2-109">Le comportement par défaut consiste à relire les données de trace en mode simultané (stress).</span><span class="sxs-lookup"><span data-stu-id="80cf2-109">The default behavior is to replay trace data in stress mode.</span></span> <span data-ttu-id="80cf2-110">Pour plus d'informations sur l'étape de relecture d'événements et les modes de mise en séquence, consultez [SQL Server Distributed Replay](sql-server-distributed-replay.md).</span><span class="sxs-lookup"><span data-stu-id="80cf2-110">For more information about the event replay stage and sequencing modes, see [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80cf2-111">Les données de trace d'entrée doivent être capturées dans une version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compatible avec Distributed Replay.</span><span class="sxs-lookup"><span data-stu-id="80cf2-111">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="80cf2-112">Les données de trace d'entrée doivent également être compatibles avec le serveur cible sur lequel vous souhaitez relire les données de trace.</span><span class="sxs-lookup"><span data-stu-id="80cf2-112">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="80cf2-113">Pour plus d'informations sur les conditions requises en matière de version, consultez [Distributed Replay Requirements](distributed-replay-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80cf2-113">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-replay-the-trace"></a><span data-ttu-id="80cf2-114">Pour relire la trace</span><span class="sxs-lookup"><span data-stu-id="80cf2-114">To replay the trace</span></span>  
  
1.  <span data-ttu-id="80cf2-115">**Modifier les paramètres de configuration de la relecture (facultatif)**  : Si vous voulez modifier les paramètres de configuration de la relecture, tels que le mode de mise en séquence et différentes valeurs de mise à l’échelle, vous devez modifier l’élément `<ReplayOptions>` du fichier XML `DReplay.exe.replay.config`de configuration de relecture.</span><span class="sxs-lookup"><span data-stu-id="80cf2-115">**(Optional) Modify replay configuration settings**: If you want to modify the replay configuration settings, such as the sequencing mode and various scaling values, you must modify the `<ReplayOptions>` element of the XML-based replay configuration file `DReplay.exe.replay.config`.</span></span> <span data-ttu-id="80cf2-116">Vous pouvez également modifier l'élément `<OutputOptions>` pour spécifier des paramètres de sortie, tels que l'enregistrement ou non du nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="80cf2-116">You can also modify the `<OutputOptions>` element to specify output settings, such as whether to record the row count.</span></span> <span data-ttu-id="80cf2-117">Si vous modifiez le fichier de configuration de relecture, nous vous recommandons de modifier une copie plutôt que l'original.</span><span class="sxs-lookup"><span data-stu-id="80cf2-117">If you modify the replay configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="80cf2-118">Pour modifier des paramètres, suivez la procédure suivante :</span><span class="sxs-lookup"><span data-stu-id="80cf2-118">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="80cf2-119">Faites une copie du fichier par défaut de configuration de relecture, `DReplay.exe.replay.config`, et renommez le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="80cf2-119">Make a copy of the default replay configuration file, `DReplay.exe.replay.config`, and rename the new file.</span></span> <span data-ttu-id="80cf2-120">Le fichier par défaut de configuration de relecture se trouve dans le dossier d'installation de l'outil d'administration.</span><span class="sxs-lookup"><span data-stu-id="80cf2-120">The default replay configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="80cf2-121">Modifiez les paramètres de configuration de relecture dans le nouveau fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="80cf2-121">Modify the replay configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="80cf2-122">Quand vous initialisez l’étape de relecture d’événements (étape suivante), utilisez le paramètre *config_file* de l’option **replay** pour spécifier l’emplacement du fichier de configuration modifié.</span><span class="sxs-lookup"><span data-stu-id="80cf2-122">When initiating the event replay stage (the next step), use the *config_file* parameter of the **replay** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="80cf2-123">Pour plus d’informations sur le fichier de configuration de prétraitement, consultez [Configure Distributed Replay](configure-distributed-replay.md)(Configurer Distributed Replay).</span><span class="sxs-lookup"><span data-stu-id="80cf2-123">For more information about the replay configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="80cf2-124">**Lancez l’étape de relecture d’événement** : Pour démarrer la relecture distribuée, vous devez exécuter l’outil d’administration avec l’option de **relecture**.</span><span class="sxs-lookup"><span data-stu-id="80cf2-124">**Initiate the event replay stage**: To start the distributed replay, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="80cf2-125">Pour plus d’informations, consultez [Option preprocess &#40;outil d’administration Distributed Replay&#41;](replay-option-distributed-replay-administration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="80cf2-125">For more information, see [Replay Option &#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="80cf2-126">Ouvrez l'utilitaire d'invite de commandes Windows (`CMD.exe`) et accédez à l'emplacement d'installation de l'outil d'administration Distributed Replay (`DReplay.exe`).</span><span class="sxs-lookup"><span data-stu-id="80cf2-126">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="80cf2-127">(Facultatif) Utilisez le paramètre *controller* , **-m**, pour spécifier le contrôleur, si le service du contrôleur s’exécute sur un ordinateur différent de l’outil d’administration.</span><span class="sxs-lookup"><span data-stu-id="80cf2-127">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="80cf2-128">Utilisez le paramètre *répertoire_de_travail_contrôleur* , **-d**, pour spécifier l’emplacement où le fichier intermédiaire a été enregistré sur le contrôleur lors de l’étape de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="80cf2-128">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file was saved on the controller during the preprocess stage.</span></span>  
  
    4.  <span data-ttu-id="80cf2-129">(Facultatif) Utilisez le paramètre **-o** pour capturer l’activité de relecture dans un fichier de trace de résultats sur chaque client.</span><span class="sxs-lookup"><span data-stu-id="80cf2-129">(Optional) Use the **-o** parameter to capture the replay activity in a result trace file on each client.</span></span>  
  
    5.  <span data-ttu-id="80cf2-130">(Facultatif) Utilisez le paramètre *serveur_cible* , **-s**, pour spécifier l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans laquelle les clients de relecture distribuée doivent relire la charge de travail de la trace.</span><span class="sxs-lookup"><span data-stu-id="80cf2-130">(Optional) Use the *target_server* parameter, **-s**, to specify the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where the distributed replay clients should replay the trace workload.</span></span> <span data-ttu-id="80cf2-131">Ce paramètre n'est pas nécessaire si vous avez utilisé l'élément `<Server>` pour spécifier le serveur cible dans l'élément `<ReplayOptions>` du fichier de configuration de relecture.</span><span class="sxs-lookup"><span data-stu-id="80cf2-131">This parameter is not required if you used the `<Server>` element to specify the target server in the `<ReplayOptions>` element of the replay configuration file.</span></span>  
  
    6.  <span data-ttu-id="80cf2-132">Utilisez le paramètre *clients* , **-w**, pour spécifier les clients de relecture distribuée qui doivent participer à la relecture.</span><span class="sxs-lookup"><span data-stu-id="80cf2-132">Use the *clients* parameter, **-w**, to specify the distributed replay clients that should participate in the replay.</span></span> <span data-ttu-id="80cf2-133">Répertoriez les noms des ordinateurs clients, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="80cf2-133">List the client computer names, separated by commas.</span></span> <span data-ttu-id="80cf2-134">Remarque : Les adresses IP ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="80cf2-134">Note: IP addresses are not allowed.</span></span>  
  
    7.  <span data-ttu-id="80cf2-135">(Facultatif) Utilisez le paramètre *fichier_configuration* , **-c**, pour spécifier l’emplacement du fichier de configuration de relecture.</span><span class="sxs-lookup"><span data-stu-id="80cf2-135">(Optional) Use the *config_file* parameter, **-c**, to specify location of the replay configuration file.</span></span> <span data-ttu-id="80cf2-136">Utilisez ce paramètre pour pointer sur le nouveau fichier de configuration si vous avez modifié une copie du fichier de configuration de relecture par défaut.</span><span class="sxs-lookup"><span data-stu-id="80cf2-136">Use this parameter to point to the new configuration file if you have modified a copy of the default replay configuration file.</span></span>  
  
    8.  <span data-ttu-id="80cf2-137">(Facultatif) Utilisez le paramètre *status_interval* , **-f**, pour spécifier si vous voulez que l’outil d’administration affiche des messages d’état à une fréquence autre que 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="80cf2-137">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency other than 30 seconds.</span></span>  
  
     <span data-ttu-id="80cf2-138">Par exemple, la syntaxe suivante initialise l’étape de relecture sur le même ordinateur que le service du contrôleur, utilise un répertoire de travail du contrôleur situé dans `c:\WorkingDir`, capture l’activité de relecture sur chaque client participant, utilise les clients `client1` et `client2` pour effectuer la relecture et obtient les paramètres de configuration de relecture restants à partir d’un fichier de configuration de relecture modifié qui se trouve dans `c:\modifiedreplay.config`:</span><span class="sxs-lookup"><span data-stu-id="80cf2-138">For example, the following syntax initiates the replay stage on the same computer as the controller service, uses a controller working directory located at `c:\WorkingDir`, captures the replay activity on each participating client, uses clients `client1` and `client2` to perform the replay, and obtains the remaining replay configuration settings from a modified replay configuration file located at `c:\modifiedreplay.config`:</span></span>  
  
     `dreplay replay -d c:\WorkingDir -o -w client1,client2 -c c:\modifiedreplay.config`  
  
3.  <span data-ttu-id="80cf2-139">Lorsque la relecture distribuée est terminée, l'outil d'administration retourne les informations de résumé.</span><span class="sxs-lookup"><span data-stu-id="80cf2-139">When the distributed replay has finished, the administration tool returns summary information.</span></span> <span data-ttu-id="80cf2-140">Si vous avez spécifié l’option **-o** , l’activité de relecture a été enregistrée dans des fichiers de trace de résultats sur chaque client.</span><span class="sxs-lookup"><span data-stu-id="80cf2-140">If you specified the **-o** option, the replay activity has been saved in result trace files on each client.</span></span> <span data-ttu-id="80cf2-141">Pour plus d’informations sur les fichiers de trace de résultats, consultez [passez en revue les résultats de relecture](review-the-replay-results.md).</span><span class="sxs-lookup"><span data-stu-id="80cf2-141">For more information about the result trace files, see [Review the Replay Results](review-the-replay-results.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80cf2-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80cf2-142">See Also</span></span>  
 <span data-ttu-id="80cf2-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="80cf2-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="80cf2-144">[Options de ligne de commande de l’outil d’administration &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="80cf2-144">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="80cf2-145">Configurer Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="80cf2-145">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  