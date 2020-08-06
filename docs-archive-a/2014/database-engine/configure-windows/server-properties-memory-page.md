---
title: Propriétés du serveur (page Mémoire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.memory.f1
ms.assetid: 46a77d4e-ab92-49d3-a14b-423462e50715
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a000a4c670b36b08a34fd544cc5ff5e61c7bab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610852"
---
# <a name="server-properties-memory-page"></a><span data-ttu-id="50e20-102">Propriétés du serveur (page Mémoire)</span><span class="sxs-lookup"><span data-stu-id="50e20-102">Server Properties (Memory Page)</span></span>
  <span data-ttu-id="50e20-103">Cette page vous permet d'afficher et de modifier les options de mémoire de votre serveur.</span><span class="sxs-lookup"><span data-stu-id="50e20-103">Use this page to view or modify your server memory options.</span></span> <span data-ttu-id="50e20-104">Lorsque **Mémoire minimale du serveur (en Mo)** a la valeur 0 et que **Mémoire maximale du serveur** a la valeur 2 147 483 647 Mo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut bénéficier d'un volume optimal de mémoire à tout moment, selon la quantité de mémoire que le système d'exploitation et les autres applications utilisent simultanément.</span><span class="sxs-lookup"><span data-stu-id="50e20-104">When **Minimum server memory** is set to 0 and **Maximum server memory** is set to 2147483647 MB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can take advantage of the optimum amount of memory at any given time, subject to how much memory the operating system and other applications are currently using.</span></span> <span data-ttu-id="50e20-105">La mémoire est allouée au fur et à mesure des modifications de la charge de l'ordinateur et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="50e20-105">As the load on the computer and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes, so does the memory allocated.</span></span> <span data-ttu-id="50e20-106">Vous pouvez également limiter l'allocation de cette mémoire dynamique aux valeurs minimale et maximale spécifiées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="50e20-106">You can further limit this dynamic memory allocation to the minimum and maximum values specified below.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50e20-107">Options</span><span class="sxs-lookup"><span data-stu-id="50e20-107">Options</span></span>  
 <span data-ttu-id="50e20-108">**Mémoire minimale du serveur (en Mo)**</span><span class="sxs-lookup"><span data-stu-id="50e20-108">**Minimum server memory (in MB)**</span></span>  
 <span data-ttu-id="50e20-109">Spécifie que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit démarrer avec au moins la quantité minimale de mémoire allouée et ne doit pas libérer de mémoire en dessous de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="50e20-109">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should start with at least the minimum amount of allocated memory and not release memory below this value.</span></span> <span data-ttu-id="50e20-110">Spécifiez cette valeur en fonction de la taille et de l'activité de votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50e20-110">Set this value based on the size and activity of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50e20-111">Spécifiez toujours une valeur raisonnable pour cette option, afin de garantir que le système d'exploitation ne demande pas trop de mémoire à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ce qui affecterait les performances de Windows.</span><span class="sxs-lookup"><span data-stu-id="50e20-111">Always set the option to a reasonable value to ensure that the operating system does not request too much memory from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and inhibit Windows performance.</span></span>  
  
 <span data-ttu-id="50e20-112">**Mémoire maximale du serveur (en Mo)**</span><span class="sxs-lookup"><span data-stu-id="50e20-112">**Maximum server memory (in MB)**</span></span>  
 <span data-ttu-id="50e20-113">Indique la quantité maximale de mémoire que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut allouer lors de son démarrage et de son exécution.</span><span class="sxs-lookup"><span data-stu-id="50e20-113">Specifies the maximum amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can allocate when it starts and while it runs.</span></span> <span data-ttu-id="50e20-114">Il est possible d'affecter une valeur spécifique à cette option de configuration si vous savez que plusieurs applications fonctionnent en même temps que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que vous voulez garantir que ces applications disposent d'une mémoire suffisante pour s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="50e20-114">This configuration option can be set to a specific value if you know there are multiple applications running at the same time as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and you want to guarantee that these applications have sufficient memory to run.</span></span> <span data-ttu-id="50e20-115">Si ces applications, telles que des serveurs Web ou de messagerie, n'exigent de mémoire que ponctuellement, n'intervenez pas sur l'option, car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se chargera de libérer de la mémoire en fonction de leurs besoins.</span><span class="sxs-lookup"><span data-stu-id="50e20-115">If these other applications, such as Web or e-mail servers, request memory only as needed, then do not set the option, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will release memory to them as needed.</span></span> <span data-ttu-id="50e20-116">Cependant, les applications utilisent généralement toute la mémoire disponible au moment du démarrage et n'en demandent pas plus même en cas de besoin.</span><span class="sxs-lookup"><span data-stu-id="50e20-116">However, applications often use whatever memory is available when they start and do not request more if needed.</span></span> <span data-ttu-id="50e20-117">Si une application qui se comporte de cette façon s'exécute sur le même ordinateur et en même temps que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], affectez à l'option une valeur qui garantit que la mémoire requise par l'application n'est pas allouée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50e20-117">If an application that behaves in this manner runs on the same computer at the same time as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], set the option to a value that guarantees that the memory required by the application is not allocated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50e20-118">Les quantités minimales de mémoire que vous pouvez spécifier pour **max server memory** sont de 64 mégaoctets (Mo) pour les systèmes 32 bits et de 128 Mo pour les systèmes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="50e20-118">The minimum amounts of memory you can specify for **max server memory** are 64 megabytes (MB) for 32-bit systems and 128 MB for 64-bit systems.</span></span>  
  
 <span data-ttu-id="50e20-119">**Mémoire de création de l'index (en Ko, 0 = mémoire dynamique)**</span><span class="sxs-lookup"><span data-stu-id="50e20-119">**Index creation memory (in KB, 0 = dynamic memory)**</span></span>  
 <span data-ttu-id="50e20-120">Spécifie la quantité de mémoire (en Ko) utilisée pendant les tris de création d'index.</span><span class="sxs-lookup"><span data-stu-id="50e20-120">Specifies the amount of memory (in KB) to use during index creation sorts.</span></span> <span data-ttu-id="50e20-121">La valeur par défaut de zéro permet d'activer l'allocation dynamique et doit fonctionner dans la plupart des cas sans réglage supplémentaire ; toutefois, l'utilisateur peut entrer une valeur différente, comprise entre 704 et 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="50e20-121">The default value of zero enables dynamic allocation and should work in most cases without additional adjustment; however, the user can enter a different value from 704 to 2147483647.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50e20-122">Les valeurs comprises entre 1 et 703 ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="50e20-122">Values from 1 to 703 are not allowed.</span></span> <span data-ttu-id="50e20-123">Si une valeur incluse dans cette plage est entrée, cette valeur est remplacée par la valeur 704.</span><span class="sxs-lookup"><span data-stu-id="50e20-123">If a value in this range is entered, the field overrides the entered value with 704.</span></span>  
  
 <span data-ttu-id="50e20-124">**Mémoire minimale par requête (en Ko)**</span><span class="sxs-lookup"><span data-stu-id="50e20-124">**Minimum memory per query (in KB)**</span></span>  
 <span data-ttu-id="50e20-125">Spécifie la quantité de mémoire (en Ko) à allouer pour l'exécution d'une requête.</span><span class="sxs-lookup"><span data-stu-id="50e20-125">Specifies the amount of memory (in KB) to allocate for the execution of a query.</span></span> <span data-ttu-id="50e20-126">L'utilisateur peut spécifier une valeur comprise entre 512 et 2 147 483 647 Ko.</span><span class="sxs-lookup"><span data-stu-id="50e20-126">The user can set the value from 512 to 2147483647 KB.</span></span> <span data-ttu-id="50e20-127">La valeur par défaut est 1 024 Ko.</span><span class="sxs-lookup"><span data-stu-id="50e20-127">The default value is 1024 KB.</span></span>  
  
 <span data-ttu-id="50e20-128">**Valeurs configurées**</span><span class="sxs-lookup"><span data-stu-id="50e20-128">**Configured Values**</span></span>  
 <span data-ttu-id="50e20-129">Affiche les valeurs configurées pour les options de ce volet.</span><span class="sxs-lookup"><span data-stu-id="50e20-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="50e20-130">Si vous modifiez ces valeurs, cliquez sur **Valeurs en cours d’exécution** pour vérifier si les modifications ont été prises en compte.</span><span class="sxs-lookup"><span data-stu-id="50e20-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="50e20-131">Si ce n'est pas le cas, l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être d'abord redémarrée.</span><span class="sxs-lookup"><span data-stu-id="50e20-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="50e20-132">**Valeurs en cours d’exécution**</span><span class="sxs-lookup"><span data-stu-id="50e20-132">**Running Values**</span></span>  
 <span data-ttu-id="50e20-133">Affiche les valeurs en cours d'exécution pour les options de ce volet.</span><span class="sxs-lookup"><span data-stu-id="50e20-133">Shows the currently running values for the options on this pane.</span></span> <span data-ttu-id="50e20-134">Ces valeurs sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="50e20-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e20-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50e20-135">See Also</span></span>  
 <span data-ttu-id="50e20-136">[Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="50e20-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="50e20-137">server memory (options de configuration de serveur)</span><span class="sxs-lookup"><span data-stu-id="50e20-137">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  