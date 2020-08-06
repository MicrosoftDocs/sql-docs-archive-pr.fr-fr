---
title: Choisir un programme de résolution | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602077"
---
# <a name="choose-a-resolver"></a><span data-ttu-id="a7088-102">Choisir un résolveur</span><span class="sxs-lookup"><span data-stu-id="a7088-102">Choose a Resolver</span></span>
  <span data-ttu-id="a7088-103">Lors du choix d'un résolveur, considérez l'importance de la résolution des conflits dans votre application et si vous pouvez utiliser l'outil de résolution des conflits par défaut basé sur les priorités ou si vous devez utiliser un résolveur d'articles.</span><span class="sxs-lookup"><span data-stu-id="a7088-103">When choosing a resolver, consider the importance of conflict resolution in your application and whether you can use the default priority-based conflict resolver or need to use an article resolver.</span></span>  
  
 <span data-ttu-id="a7088-104">Si vos données sont partitionnées sans que plusieurs utilisateurs écrivent dans les mêmes partitions, et que votre topologie de réplication est relativement simple (un éditeur et quelques abonnés), les conflits seront rares ou inexistants.</span><span class="sxs-lookup"><span data-stu-id="a7088-104">If your data is partitioned without multiple users writing to the same partitions, and your replication topology is relatively basic (one Publisher and a few Subscribers), conflicts should be rare or nonexistent.</span></span> <span data-ttu-id="a7088-105">Dans ce type d'environnement, vous n'avez probablement pas besoin d'une stratégie complexe de résolution des conflits.</span><span class="sxs-lookup"><span data-stu-id="a7088-105">In these environments, you probably do not need a complex conflict resolution strategy.</span></span> <span data-ttu-id="a7088-106">Une stratégie utilisant les paramètres par défaut de résolution de conflits, des abonnements clients et une règle du type « la première modification l'emporte », est recommandée.</span><span class="sxs-lookup"><span data-stu-id="a7088-106">A strategy using the default settings for conflict resolution, using client subscriptions and a first change in wins policy, is recommended.</span></span> <span data-ttu-id="a7088-107">Si la topologie est plus complexe (utilisant par exemple des Abonnés de réédition), des abonnements serveur avec des priorités spécifiques peuvent être plus appropriés.</span><span class="sxs-lookup"><span data-stu-id="a7088-107">If the topology is more complex (using republishing Subscribers, for example), server subscriptions with specific priorities might be more appropriate.</span></span>  
  
 <span data-ttu-id="a7088-108">Un résolveur d'articles est recommandé si votre entreprise requiert une solution plus avancée que celle qui est disponible avec le résolveur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7088-108">An article resolver is recommended if your business needs require a more finely tuned solution than is available with the default resolver.</span></span> <span data-ttu-id="a7088-109">Si vous choisissez d'utiliser un résolveur d'articles, il est recommandé d'utiliser un gestionnaire de logique métier.</span><span class="sxs-lookup"><span data-stu-id="a7088-109">If you choose to use an article resolver, it is recommended that you use a business logic handler.</span></span> <span data-ttu-id="a7088-110">Pour plus d’informations, consultez [Exécuter la logique métier lors de la synchronisation de fusion](execute-business-logic-during-merge-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="a7088-110">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="a7088-111">Enfin, le choix entre utiliser le résolveur par défaut et utiliser un résolveur d'articles doit être basé sur les besoins de l'application en termes de données et de logique métier.</span><span class="sxs-lookup"><span data-stu-id="a7088-111">Ultimately, choosing whether to use the default resolver or an article resolver should be based on the data and the business logic needs of the application.</span></span> <span data-ttu-id="a7088-112">Par exemple, considérez des employés entrant des données sur le classement des clients dans un ensemble de tables non partitionnées au niveau de différents abonnés. Ces employés sont répartis en plusieurs catégories professionnelles (directeurs de filiale, directeurs de gamme de produits, personnel des ventes), et la catégorie professionnelle détermine les données prioritaires.</span><span class="sxs-lookup"><span data-stu-id="a7088-112">For example, consider employees who enter customer ranking data into a set of non-partitioned tables at different Subscribers; the employees span various job categories (branch managers, line managers, sales staff), and job category determines whose data should be given priority.</span></span> <span data-ttu-id="a7088-113">Dans ce cas, il est possible de créer un résolveur d'articles qui utilise les données de la catégorie professionnelle de l'article pour déterminer celui qui l'emporte en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="a7088-113">In this case, an article resolver can be built that uses job category data from the article to determine the winner if a conflict occurs.</span></span>  
  
 <span data-ttu-id="a7088-114">Lorsque des conflits sont susceptibles de se produire assez fréquemment, voici les décisions les plus importantes à prendre en considération lors de la mise en œuvre d'une stratégie de résolution de conflits.</span><span class="sxs-lookup"><span data-stu-id="a7088-114">If conflicts are likely to occur with some frequency, here are the most important decisions you should consider when implementing a conflict resolution strategy.</span></span>  
  
|<span data-ttu-id="a7088-115">Problème de résolution de conflits</span><span class="sxs-lookup"><span data-stu-id="a7088-115">Conflict resolution issue</span></span>|<span data-ttu-id="a7088-116">Recommandation</span><span class="sxs-lookup"><span data-stu-id="a7088-116">Recommendation</span></span>|  
|-------------------------------|--------------------|  
|<span data-ttu-id="a7088-117">Différentes catégories d'utilisateurs nécessitent des valeurs de priorité différentes.</span><span class="sxs-lookup"><span data-stu-id="a7088-117">Different categories of users require different priority values.</span></span>|<span data-ttu-id="a7088-118">Utilisez le résolveur par défaut et créez des abonnements serveur avec des valeurs de priorité différentes.</span><span class="sxs-lookup"><span data-stu-id="a7088-118">Use the default resolver and create server subscriptions with different priority values.</span></span><br /><br /> <span data-ttu-id="a7088-119">-Ou-</span><span class="sxs-lookup"><span data-stu-id="a7088-119">-Or-</span></span><br /><br /> <span data-ttu-id="a7088-120">Utilisez un résolveur d'article qui reconnaît une colonne de valeur d'autorité dans l'article pour contribuer à résoudre tout conflit.</span><span class="sxs-lookup"><span data-stu-id="a7088-120">Use an article resolver that recognizes an authority value column in the article to help resolve a conflict.</span></span>|  
|<span data-ttu-id="a7088-121">Nécessité d'une solution de résolution de conflit du type “ le premier l'emporte ”.</span><span class="sxs-lookup"><span data-stu-id="a7088-121">First change in wins conflict solution wanted.</span></span>|<span data-ttu-id="a7088-122">Utilisez le résolveur par défaut et créez des abonnements clients.</span><span class="sxs-lookup"><span data-stu-id="a7088-122">Use the default resolver and create client subscriptions.</span></span>|  
|<span data-ttu-id="a7088-123">La modification d'une même ligne de données par plusieurs utilisateurs est acceptable, du moment qu'aucune modification conflictuelle n'est apportée à la même colonne.</span><span class="sxs-lookup"><span data-stu-id="a7088-123">Multiple users changing the same data row is acceptable, as long as no conflicting changes are made to the same column.</span></span>|<span data-ttu-id="a7088-124">Utilisez soit le résolveur par défaut soit un résolveur d'articles où le suivi au niveau des colonnes est activé.</span><span class="sxs-lookup"><span data-stu-id="a7088-124">Use either the default resolver or an article resolver with column-level tracking enabled.</span></span>|  
|<span data-ttu-id="a7088-125">Les multiples modifications de valeurs dans une ligne doivent être signalées comme un conflit.</span><span class="sxs-lookup"><span data-stu-id="a7088-125">Flag multiple changes to any value in a row as a conflict.</span></span>|<span data-ttu-id="a7088-126">Utilisez soit le résolveur par défaut soit un résolveur d'articles où le suivi au niveau des lignes est activé.</span><span class="sxs-lookup"><span data-stu-id="a7088-126">Use either the default resolver or an article resolver with row-level tracking.</span></span>|  
|<span data-ttu-id="a7088-127">De multiples modifications de valeurs dans un enregistrement logique doivent être signalées comme un conflit.</span><span class="sxs-lookup"><span data-stu-id="a7088-127">Flag multiple changes to any value in a logical record as a conflict.</span></span>|<span data-ttu-id="a7088-128">Utilisez le résolveur par défaut avec un suivi au niveau des enregistrements logiques (les enregistrements logiques ne prennent pas en charge les résolveurs personnalisés ni les gestionnaires de logique métier).</span><span class="sxs-lookup"><span data-stu-id="a7088-128">Use the default resolver with logical record-level tracking (the logical records feature does not support custom resolvers or business logic handlers).</span></span>|  
|<span data-ttu-id="a7088-129">Les données de résultat d'un conflit doivent être différentes des données de conflit originales.</span><span class="sxs-lookup"><span data-stu-id="a7088-129">Conflict outcome data needs to be different from original conflict data.</span></span>|<span data-ttu-id="a7088-130">Utilisez un résolveur d'articles qui calcule les nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="a7088-130">Use an article resolver that calculates new values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7088-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7088-131">See Also</span></span>  
 <span data-ttu-id="a7088-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span><span class="sxs-lookup"><span data-stu-id="a7088-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span></span>  
 <span data-ttu-id="a7088-133">[Détection et résolution des conflits de réplication de fusion avancée](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="a7088-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="a7088-134">Republier des données</span><span class="sxs-lookup"><span data-stu-id="a7088-134">Republish Data</span></span>](../republish-data.md)  
  
  