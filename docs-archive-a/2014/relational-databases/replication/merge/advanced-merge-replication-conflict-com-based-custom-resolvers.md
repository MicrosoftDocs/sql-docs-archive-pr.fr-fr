---
title: Programmes de résolution personnalisés COM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b28795c1a7d43bcd4e8cb3f18723e05f9e76966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702820"
---
# <a name="com-based-custom-resolvers"></a><span data-ttu-id="ff916-102">COM-Based Custom Resolvers</span><span class="sxs-lookup"><span data-stu-id="ff916-102">COM-Based Custom Resolvers</span></span>
  <span data-ttu-id="ff916-103">Les programmes de résolution personnalisés offrent une plus grande souplesse que le mécanisme de résolution par défaut et ils peuvent implémenter la logique métier requise par les applications utilisant les données répliquées.</span><span class="sxs-lookup"><span data-stu-id="ff916-103">Custom resolvers provide more flexibility than the default resolution mechanism, and they can implement business logic required by applications using the replicated data.</span></span> <span data-ttu-id="ff916-104">Un programme de résolution personnalisé COM est une bibliothèque de liens dynamiques (DLL) qui implémente l'interface **ICustomResolver** , ses méthodes et ses propriétés, ainsi que d'autres interfaces de prise en charge et définitions de types conçues spécifiquement pour la résolution de conflits.</span><span class="sxs-lookup"><span data-stu-id="ff916-104">A COM-based custom resolver is a dynamic-link library (DLL) that implements the **ICustomResolver** COM interface, its methods and properties, and other supporting interfaces and type definitions designed specifically for conflict resolution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff916-105">Il est recommandé d'utiliser si possible un gestionnaire de logique métier au lieu d'un programme de résolution personnalisé COM.</span><span class="sxs-lookup"><span data-stu-id="ff916-105">It is recommended to use a business logic handler rather than a COM-based custom resolver if possible.</span></span> <span data-ttu-id="ff916-106">Pour plus d’informations sur les gestionnaires de logique métier, consultez [Exécuter la logique métier lors de la synchronisation de fusion](execute-business-logic-during-merge-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="ff916-106">For more information on business logic handlers, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="ff916-107">Pour créer un programme de résolution personnalisé COM, vous pouvez utiliser la bibliothèque de types fournie dans le fichier replrec.dll. Cette bibliothèque est installée par défaut dans [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span><span class="sxs-lookup"><span data-stu-id="ff916-107">To build a custom COM resolver, you can use the type library that is provided in the replrec.dll; by default, this library is installed at [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
 <span data-ttu-id="ff916-108">Avant d'écrire un programme de résolution personnalisé COM, vous devez décider des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ff916-108">Before writing a custom COM resolver, you need to decide:</span></span>  
  
-   <span data-ttu-id="ff916-109">Types des modifications de ligne à résoudre, tels que les mises à jour, insertions et suppressions ainsi que l'appel ou non du programme de résolution au cours du chargement des modifications de fusion, leur téléchargement, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="ff916-109">The types of row changes you want to resolve, such as updates, inserts, and deletes, and whether the resolver should be invoked during the upload of merge changes, the download of merge changes, or both.</span></span> <span data-ttu-id="ff916-110">Vous pouvez spécifier un type de modification, toutes les modifications ou n'importe quelle combinaison.</span><span class="sxs-lookup"><span data-stu-id="ff916-110">You can specify one type of change, all changes, or any combination.</span></span> <span data-ttu-id="ff916-111">Le programme de résolution de conflits de fusion par défaut gère tous les conflits non pris en charge par un programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ff916-111">The default merge conflict resolver handles any conflicts not covered by a custom resolver.</span></span>  
  
-   <span data-ttu-id="ff916-112">Utilisation du suivi des colonnes lors de la résolution du conflit.</span><span class="sxs-lookup"><span data-stu-id="ff916-112">Whether to use column tracking when resolving the conflict.</span></span> <span data-ttu-id="ff916-113">Lorsque le suivi au niveau des colonnes est activé, seules les données des colonnes présentant un conflit sont signalées en tant que tel, dans le cas contraire, les données sont fusionnées.</span><span class="sxs-lookup"><span data-stu-id="ff916-113">When column-level tracking is on, only data in those columns where a conflict exists are flagged as a conflict, otherwise the data is merged.</span></span> <span data-ttu-id="ff916-114">Cependant, les conflits sont résolus de la même façon qu'avec le suivi au niveau des lignes : la ligne prioritaire remplace toute la ligne de données (mais ces données peuvent être un mélange entre les valeurs du serveur de publication, des Abonnés, ou certaines valeurs modifiées qui n'appartiennent ni au serveur de publication ni aux Abonnés).</span><span class="sxs-lookup"><span data-stu-id="ff916-114">However, conflicts are resolved in the same way as row-level tracking: the priority winner overwrites the entire row of data (but the data can be a mix of values from the Publisher, Subscribers, or some altered values that were from neither Publisher nor Subscribers).</span></span> <span data-ttu-id="ff916-115">Pour plus d’informations, consulter [Détecter et résoudre des conflits de réplication de fusion](advanced-merge-replication-conflict-detection-and-resolution.md).</span><span class="sxs-lookup"><span data-stu-id="ff916-115">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
 <span data-ttu-id="ff916-116">Pour implémenter un outil de résolution des conflits personnalisé COM, consultez [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span><span class="sxs-lookup"><span data-stu-id="ff916-116">To implement a COM-based custom conflict resolver, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
 <span data-ttu-id="ff916-117">Un programme de résolution personnalisé est spécifié pour un article mais pas pour l'intégralité d'une publication.</span><span class="sxs-lookup"><span data-stu-id="ff916-117">A custom resolver is specified for an article, not an entire publication.</span></span> <span data-ttu-id="ff916-118">Le même programme de résolution peut être spécifié avec plusieurs articles mais la logique des programmes de résolution personnalisés est souvent propre à une table donnée.</span><span class="sxs-lookup"><span data-stu-id="ff916-118">The same resolver can be used with more than one article, but the logic in custom resolvers is often specific to a particular table.</span></span> <span data-ttu-id="ff916-119">Si la table utilisée dans l'article est modifiée après la création d'un programme de résolution (par exemple, attribution d'un nouveau nom à une colonne intervenant dans la résolution du conflit), il se peut que le programme de résolution personnalisé doive être modifié et recompilé.</span><span class="sxs-lookup"><span data-stu-id="ff916-119">If the table used in the article is modified after the resolver is created (for example, renaming the column name that is used in conflict resolution), the custom resolver might need to be modified and recompiled.</span></span>  
  
 <span data-ttu-id="ff916-120">Pour spécifier un programme de résolution personnalisé, consultez [Spécifier un programme de résolution d'articles de fusion](../publish/specify-a-merge-article-resolver.md).</span><span class="sxs-lookup"><span data-stu-id="ff916-120">To specify a custom resolver, see [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff916-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff916-121">See Also</span></span>  
 <span data-ttu-id="ff916-122">[Détection et résolution des conflits de réplication de fusion avancée](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="ff916-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="ff916-123">Microsoft-programmes de résolution COM</span><span class="sxs-lookup"><span data-stu-id="ff916-123">Microsoft COM-Based Resolvers</span></span>](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  