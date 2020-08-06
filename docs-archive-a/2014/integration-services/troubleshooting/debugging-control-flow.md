---
title: Débogage du flux de contrôle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2e2feff6723a510cb773131cb6452bdc7a77cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703104"
---
# <a name="debugging-control-flow"></a><span data-ttu-id="f99c9-102">Débogage du flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="f99c9-102">Debugging Control Flow</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f99c9-103">et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] incluent des fonctionnalités et des outils permettant de résoudre les problèmes du flux de contrôle d’un package [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f99c9-103">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include features and tools that you can use to troubleshoot the control flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package.</span></span>

-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="f99c9-104">prend en charge les points d’arrêt sur les conteneurs et les tâches.</span><span class="sxs-lookup"><span data-stu-id="f99c9-104">supports breakpoints on containers and tasks.</span></span>

-   [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="f99c9-105">- Le concepteur SSIS fournit des rapports de progression au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-105">Designer provides progress reporting at run time.</span></span>

-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f99c9-106">propose des fenêtres de débogage.</span><span class="sxs-lookup"><span data-stu-id="f99c9-106">provides debug windows.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="f99c9-107">Points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="f99c9-107">Breakpoints</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="f99c9-108">Le concepteur propose la boîte de dialogue **Définir des points d’arrêt** dans laquelle vous pouvez définir des points d’arrêt en activant des conditions d’arrêt et en spécifiant le nombre d’occurrences d’un point d’arrêt avant la suspension de l’exécution du package.</span><span class="sxs-lookup"><span data-stu-id="f99c9-108">Designer provides the **Set Breakpoints** dialog box, in which you can set breakpoints by enabling break conditions and specifying the number of times a breakpoint can occur before the execution of the package is suspended.</span></span> <span data-ttu-id="f99c9-109">Les points d'arrêt peuvent être activés au niveau du package ou au niveau du composant.</span><span class="sxs-lookup"><span data-stu-id="f99c9-109">Breakpoints can be enabled at the package level, or at the level of the individual component.</span></span> <span data-ttu-id="f99c9-110">Si des conditions d’arrêt sont activées au niveau de la tâche ou du conteneur, l’icône de point d’arrêt apparaît en regard de la tâche ou du conteneur sur la surface de dessin de l’onglet **Flux de contrôle** . Si les conditions d’arrêt sont activées au niveau du package, l’icône de point d’arrêt apparaît sur l’étiquette de l’onglet **Flux de contrôle** .</span><span class="sxs-lookup"><span data-stu-id="f99c9-110">If break conditions are enabled at the task or container level, the breakpoint icon appears next to the task or container on the design surface of the **Control Flow** tab. If the break conditions are enabled on the package, the breakpoint icon appears on the label of the **Control Flow** tab.</span></span>

 <span data-ttu-id="f99c9-111">Lorsqu'un point d'arrêt est atteint, l'icône de point d'arrêt se transforme pour vous aider à identifier la source du point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-111">When a breakpoint is hit, the breakpoint icon changes to help you identify the source of the breakpoint.</span></span> <span data-ttu-id="f99c9-112">Vous pouvez ajouter, supprimer et modifier des points d'arrêt au cours de l'exécution du package.</span><span class="sxs-lookup"><span data-stu-id="f99c9-112">You can add, delete, and change breakpoints when the package is running.</span></span>

 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="f99c9-113">propose dix conditions d’arrêt que vous pouvez activer sur toutes les tâches et tous les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f99c9-113">provides ten break conditions that you can enable on all tasks and containers.</span></span> <span data-ttu-id="f99c9-114">Dans la boîte de dialogue **Définir des points d’arrêt** , vous pouvez activer des points d’arrêt pour les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f99c9-114">In the **Set Breakpoints** dialog box, you can enable breakpoints on the following conditions:</span></span>

|<span data-ttu-id="f99c9-115">Condition d'arrêt</span><span class="sxs-lookup"><span data-stu-id="f99c9-115">Break condition</span></span>|<span data-ttu-id="f99c9-116">Description</span><span class="sxs-lookup"><span data-stu-id="f99c9-116">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="f99c9-117">Lorsque la tâche ou le conteneur reçoit l'événement `OnPreExecute`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-117">When the task or container receives the `OnPreExecute` event.</span></span>|<span data-ttu-id="f99c9-118">Appelée lorsqu'une tâche est sur le point de s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="f99c9-118">Called when a task is about to execute.</span></span> <span data-ttu-id="f99c9-119">Cet événement est déclenché par une tâche ou un conteneur immédiatement avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-119">This event is raised by a task or a container immediately before it runs.</span></span>|
|<span data-ttu-id="f99c9-120">Lorsque la tâche ou le conteneur reçoit l'événement `OnPostExecute`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-120">When the task or container receives the `OnPostExecute` event.</span></span>|<span data-ttu-id="f99c9-121">Appelée immédiatement après la fin de la logique d'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f99c9-121">Called immediately after the execution logic of the task finishes.</span></span> <span data-ttu-id="f99c9-122">Cet événement est déclenché par une tâche ou un conteneur immédiatement après son exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-122">This event is raised by a task or container immediately after it runs.</span></span>|
|<span data-ttu-id="f99c9-123">Lorsque la tâche ou le conteneur reçoit l'événement `OnError`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-123">When the task or container receives the `OnError` event.</span></span>|<span data-ttu-id="f99c9-124">Appelée par une tâche ou un conteneur lorsqu'une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="f99c9-124">Called by a task or container when an error occurs.</span></span>|
|<span data-ttu-id="f99c9-125">Lorsque la tâche ou le conteneur reçoit l'événement `OnWarning`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-125">When the task or container receives the `OnWarning` event.</span></span>|<span data-ttu-id="f99c9-126">Appelée lorsque la tâche est dans un état qui ne justifie pas une erreur, mais garantit un avertissement.</span><span class="sxs-lookup"><span data-stu-id="f99c9-126">Called when the task is in a state that does not justify an error, but does warrant a warning.</span></span>|
|<span data-ttu-id="f99c9-127">Lorsque la tâche ou le conteneur reçoit l'événement `OnInformation`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-127">When the task or container receives the `OnInformation` event.</span></span>|<span data-ttu-id="f99c9-128">Appelée lorsque la tâche doit fournir des informations.</span><span class="sxs-lookup"><span data-stu-id="f99c9-128">Called when the task is required to provide information.</span></span>|
|<span data-ttu-id="f99c9-129">Lorsque la tâche ou le conteneur reçoit l'événement `OnTaskFailed`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-129">When the task or container receives the `OnTaskFailed` event.</span></span>|<span data-ttu-id="f99c9-130">Appelée par l'hôte de la tâche lorsqu'il échoue.</span><span class="sxs-lookup"><span data-stu-id="f99c9-130">Called by the task host when it fails.</span></span>|
|<span data-ttu-id="f99c9-131">Lorsque la tâche ou le conteneur reçoit l'événement `OnProgress`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-131">When the task or container receives the `OnProgress` event.</span></span>|<span data-ttu-id="f99c9-132">Appelée pour mettre à jour la progression de l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f99c9-132">Called to update progress about task execution.</span></span>|
|<span data-ttu-id="f99c9-133">Lorsque la tâche ou le conteneur reçoit l'événement `OnQueryCancel`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-133">When the task or container receives the `OnQueryCancel` event.</span></span>|<span data-ttu-id="f99c9-134">Appelée à tout moment du traitement de la tâche lorsque vous pouvez annuler l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f99c9-134">Called at any time in task processing when you can cancel execution.</span></span>|
|<span data-ttu-id="f99c9-135">Lorsque la tâche ou le conteneur reçoit l'événement `OnVariableValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-135">When the task or container receives the `OnVariableValueChanged` event.</span></span>|<span data-ttu-id="f99c9-136">Appelée par le runtime [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] lorsque la valeur d'une variable change.</span><span class="sxs-lookup"><span data-stu-id="f99c9-136">Called by the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime when the value of a variable changes.</span></span> <span data-ttu-id="f99c9-137">Le RaiseChangeEvent de la variable doit avoir la valeur `true` pour déclencher cet événement.</span><span class="sxs-lookup"><span data-stu-id="f99c9-137">The RaiseChangeEvent of the variable must be set to `true` to raise this event.</span></span><br /><br /> <span data-ttu-id="f99c9-138">**&#42;&#42; Avertissement &#42;&#42;** La variable associée à ce point d’arrêt doit être définie dans l’étendue du **conteneur**.</span><span class="sxs-lookup"><span data-stu-id="f99c9-138">**&#42;&#42; Warning &#42;&#42;** The variable associated with this breakpoint must be defined at the **container** scope.</span></span> <span data-ttu-id="f99c9-139">Si la variable est définie dans l'étendue du package, le point d'arrêt n'obtient pas de correspondance.</span><span class="sxs-lookup"><span data-stu-id="f99c9-139">If the variable is defined at the package scope, the breakpoint does not get hit.</span></span>|
|<span data-ttu-id="f99c9-140">Lorsque la tâche ou le conteneur reçoit l'événement `OnCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="f99c9-140">When the task or container receives the `OnCustomEvent` event.</span></span>|<span data-ttu-id="f99c9-141">Appelée par les tâches pour déclencher des événements personnalisés définis par la tâche.</span><span class="sxs-lookup"><span data-stu-id="f99c9-141">Called by tasks to raise custom task-defined events.</span></span>|

 <span data-ttu-id="f99c9-142">Outre les conditions d'arrêt disponibles pour toutes les tâches et tous les conteneurs, certaines tâches et certains conteneurs proposent des conditions d'arrêt spéciales permettant de définir des points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-142">In addition to the break conditions available to all tasks and containers, some tasks and containers include special break conditions for setting breakpoints.</span></span> <span data-ttu-id="f99c9-143">Vous pouvez ainsi activer une condition d'arrêt sur le conteneur de boucles For définissant un point d'arrêt qui suspend l'exécution au début de chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="f99c9-143">For example, you can enable a break condition on the For Loop container that sets a breakpoint that suspends execution at the start of each iteration of the loop.</span></span>

 <span data-ttu-id="f99c9-144">Pour le rendre plus flexible et plus puissant, vous pouvez modifier le comportement d'un point d'arrêt en spécifiant les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="f99c9-144">To add flexibility and power to a breakpoint, you can modify the behavior of a breakpoint by specifying the following options:</span></span>

-   <span data-ttu-id="f99c9-145">Le nombre d'accès, ou le nombre maximal d'occurrences d'une condition d'arrêt avant suspension de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-145">The hit count, or the maximum number of times that a break condition occurs before the execution is suspended.</span></span>

-   <span data-ttu-id="f99c9-146">Le type du nombre d'accès, ou la règle spécifiant à quel moment la condition d'arrêt déclenche le point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-146">The hit count type, or the rule that specifies when the break condition triggers the breakpoint.</span></span>

 <span data-ttu-id="f99c9-147">Les types du nombre d'accès, à l'exception du type Toujours, sont qualifiés de manière plus approfondie par le nombre d'accès.</span><span class="sxs-lookup"><span data-stu-id="f99c9-147">The hit count types, except for the Always type, are further qualified by the hit count.</span></span> <span data-ttu-id="f99c9-148">Par exemple, si le type est « Égal au nombre d'accès » et si le nombre d'accès est 5, l'exécution est suspendue à la sixième occurrence de la condition d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-148">For example, if the type is "Hit count equals" and the hit count is 5, execution is suspended on the sixth occurrence of the break condition.</span></span>

 <span data-ttu-id="f99c9-149">Le tableau suivant décrit les types de nombre d'accès.</span><span class="sxs-lookup"><span data-stu-id="f99c9-149">The following table describes the hit count types.</span></span>

|<span data-ttu-id="f99c9-150">Type du nombre d'accès</span><span class="sxs-lookup"><span data-stu-id="f99c9-150">Hit count type</span></span>|<span data-ttu-id="f99c9-151">Description</span><span class="sxs-lookup"><span data-stu-id="f99c9-151">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="f99c9-152">Toujours</span><span class="sxs-lookup"><span data-stu-id="f99c9-152">Always</span></span>|<span data-ttu-id="f99c9-153">L'exécution est toujours suspendue lorsque le point d'arrêt est atteint.</span><span class="sxs-lookup"><span data-stu-id="f99c9-153">Execution is always suspended when the breakpoint is hit.</span></span>|
|<span data-ttu-id="f99c9-154">Égal au nombre d'accès</span><span class="sxs-lookup"><span data-stu-id="f99c9-154">Hit count equals</span></span>|<span data-ttu-id="f99c9-155">L'exécution est suspendue lorsque le nombre de fois où s'est produit le point d'arrêt est égal au nombre d'accès.</span><span class="sxs-lookup"><span data-stu-id="f99c9-155">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|
|<span data-ttu-id="f99c9-156">Supérieur ou égal au nombre d'accès</span><span class="sxs-lookup"><span data-stu-id="f99c9-156">Hit count greater than or equal to</span></span>|<span data-ttu-id="f99c9-157">L'exécution est suspendue lorsque le nombre de fois où s'est produit le point d'arrêt est supérieur ou égal au nombre d'accès.</span><span class="sxs-lookup"><span data-stu-id="f99c9-157">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|
|<span data-ttu-id="f99c9-158">Multiple du nombre d'accès</span><span class="sxs-lookup"><span data-stu-id="f99c9-158">Hit count multiple</span></span>|<span data-ttu-id="f99c9-159">L'exécution est suspendue lorsqu'un multiple du nombre d'accès est atteint.</span><span class="sxs-lookup"><span data-stu-id="f99c9-159">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="f99c9-160">Par exemple, si vous définissez cette option sur 5, l'exécution est suspendue une fois toutes les cinq fois.</span><span class="sxs-lookup"><span data-stu-id="f99c9-160">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|

#### <a name="to-set-breakpoints"></a><span data-ttu-id="f99c9-161">Pour définir des points d'arrêt</span><span class="sxs-lookup"><span data-stu-id="f99c9-161">To set breakpoints</span></span>

-   [<span data-ttu-id="f99c9-162">Déboguer un package en définissant des points d’arrêt sur une tâche ou un conteneur</span><span class="sxs-lookup"><span data-stu-id="f99c9-162">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)

## <a name="progress-reporting"></a><span data-ttu-id="f99c9-163">Rapport de progression</span><span class="sxs-lookup"><span data-stu-id="f99c9-163">Progress Reporting</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="f99c9-164">Le concepteur propose deux types de rapports de progression : les codes de couleur sur l’aire de conception de l’onglet **Flux de contrôle** et les messages de progression sous l’onglet **Progression** .</span><span class="sxs-lookup"><span data-stu-id="f99c9-164">Designer includes two types of progress reporting: color-coding on the design surface of the **Control Flow** tab, and progress messages on the **Progress** tab.</span></span>

 <span data-ttu-id="f99c9-165">Lorsque vous exécutez un package, le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] indique la progression de l'exécution en affichant chaque tâche ou conteneur dans une couleur qui indique l'état de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-165">When you run a package, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer depicts execution progress by displaying each task or container using a color that indicates execution status.</span></span> <span data-ttu-id="f99c9-166">En fonction de la couleur, vous pouvez déterminer si l'élément est en attente d'exécution, s'il est en cours d'exécution, s'il s'est terminé avec succès ou s'il s'est terminé avec des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f99c9-166">You can tell by its color whether the element is waiting to run, currently running, has completed successfully, or has ended unsuccessfully.</span></span> <span data-ttu-id="f99c9-167">Les codes de couleur disparaissent dès que vous arrêtez l'exécution du package.</span><span class="sxs-lookup"><span data-stu-id="f99c9-167">After you stop package execution, the color-coding disappears.</span></span>

 <span data-ttu-id="f99c9-168">Le tableau suivant indique les couleurs utilisées pour décrire l'état de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f99c9-168">The following table describes the colors that are used to depict execution status.</span></span>

|<span data-ttu-id="f99c9-169">Couleur</span><span class="sxs-lookup"><span data-stu-id="f99c9-169">Color</span></span>|<span data-ttu-id="f99c9-170">État de l'exécution</span><span class="sxs-lookup"><span data-stu-id="f99c9-170">Execution status</span></span>|
|-----------|----------------------|
|<span data-ttu-id="f99c9-171">Gris</span><span class="sxs-lookup"><span data-stu-id="f99c9-171">Gray</span></span>|<span data-ttu-id="f99c9-172">En attente d'exécution</span><span class="sxs-lookup"><span data-stu-id="f99c9-172">Waiting to run</span></span>|
|<span data-ttu-id="f99c9-173">Jaune</span><span class="sxs-lookup"><span data-stu-id="f99c9-173">Yellow</span></span>|<span data-ttu-id="f99c9-174">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="f99c9-174">Running</span></span>|
|<span data-ttu-id="f99c9-175">Vert</span><span class="sxs-lookup"><span data-stu-id="f99c9-175">Green</span></span>|<span data-ttu-id="f99c9-176">Exécuté avec succès</span><span class="sxs-lookup"><span data-stu-id="f99c9-176">Ran successfully</span></span>|
|<span data-ttu-id="f99c9-177">mis en surbrillance</span><span class="sxs-lookup"><span data-stu-id="f99c9-177">highlighted</span></span>|<span data-ttu-id="f99c9-178">Exécuté avec des erreurs</span><span class="sxs-lookup"><span data-stu-id="f99c9-178">Ran with errors</span></span>|

 <span data-ttu-id="f99c9-179">L’onglet **Progression** énumère les tâches et les conteneurs dans l’ordre d’exécution et indique les heures de début et de fin, les avertissements et les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f99c9-179">The **Progress** tab lists tasks and containers in execution order and includes the start and finish times, warnings, and error messages.</span></span> <span data-ttu-id="f99c9-180">À la fin de l’exécution du package, les informations de progression restent disponibles sous l’onglet **Résultats d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="f99c9-180">After you stop package execution, the progress information remains available on the **Execution Results** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="f99c9-181">Pour activer ou désactiver l'affichage de messages sous l'onglet **Progression** , basculez l'option **Création de rapports de progression de débogage** dans le menu **SSIS** .</span><span class="sxs-lookup"><span data-stu-id="f99c9-181">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

 <span data-ttu-id="f99c9-182">Le diagramme qui suit représente l’onglet **Progression** .</span><span class="sxs-lookup"><span data-stu-id="f99c9-182">The following diagram shows the **Progress** tab.</span></span>

 <span data-ttu-id="f99c9-183">![Onglet Progression du Concepteur SSIS](../media/mw-dtsflow04.gif "Onglet Progression du Concepteur SSIS")</span><span class="sxs-lookup"><span data-stu-id="f99c9-183">![Progress tab of SSIS Designer](../media/mw-dtsflow04.gif "Progress tab of SSIS Designer")</span></span>

## <a name="debug-windows"></a><span data-ttu-id="f99c9-184">Fenêtres de débogage</span><span class="sxs-lookup"><span data-stu-id="f99c9-184">Debug Windows</span></span>
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f99c9-185">propose de nombreuses fenêtres que vous pouvez utiliser pour travailler avec les points d’arrêt et déboguer les packages qui contiennent des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-185">includes many windows that you can use to work with breakpoints, and to debug packages that contain breakpoints.</span></span> <span data-ttu-id="f99c9-186">Pour en savoir plus sur chacune des fenêtres, ouvrez-les et appuyez sur F1 pour afficher l'aide.</span><span class="sxs-lookup"><span data-stu-id="f99c9-186">To learn more about each window, open the window, and then press F1 to display Help for the window.</span></span>

 <span data-ttu-id="f99c9-187">Pour ouvrir ces fenêtres dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Déboguer** , pointez sur **Fenêtres**, puis cliquez sur **Points d’arrêt**, **Sortie**ou **Immédiat**.</span><span class="sxs-lookup"><span data-stu-id="f99c9-187">To open these windows in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], click the **Debug** menu, point to **Windows**, and then click **Breakpoints**, **Output**, or **Immediate**.</span></span>

 <span data-ttu-id="f99c9-188">Le tableau qui suit décrit ces fenêtres.</span><span class="sxs-lookup"><span data-stu-id="f99c9-188">The following table describes the windows.</span></span>

|<span data-ttu-id="f99c9-189">Fenêtre</span><span class="sxs-lookup"><span data-stu-id="f99c9-189">Window</span></span>|<span data-ttu-id="f99c9-190">Description</span><span class="sxs-lookup"><span data-stu-id="f99c9-190">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="f99c9-191">Points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="f99c9-191">Breakpoints</span></span>|<span data-ttu-id="f99c9-192">Énumère les points d'arrêt d'un package et donne accès aux options permettant d'activer ou de supprimer des points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="f99c9-192">Lists the breakpoints in a package and provides options to enable and delete breakpoints.</span></span>|
|<span data-ttu-id="f99c9-193">Output</span><span class="sxs-lookup"><span data-stu-id="f99c9-193">Output</span></span>|<span data-ttu-id="f99c9-194">Affiche les messages d’état relatifs aux fonctionnalités de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f99c9-194">Displays status messages for features in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|
|<span data-ttu-id="f99c9-195">Immédiat</span><span class="sxs-lookup"><span data-stu-id="f99c9-195">Immediate</span></span>|<span data-ttu-id="f99c9-196">Utilisée pour déboguer et évaluer des expressions, et imprimer des valeurs variables.</span><span class="sxs-lookup"><span data-stu-id="f99c9-196">Used to debug and evaluate expressions and print variable values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f99c9-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f99c9-197">See Also</span></span>
 [<span data-ttu-id="f99c9-198">Outils de dépannage pour le développement des packages</span><span class="sxs-lookup"><span data-stu-id="f99c9-198">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)

