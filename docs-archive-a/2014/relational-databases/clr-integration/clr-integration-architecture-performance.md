---
title: Performances de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], performance
- common language runtime [SQL Server], compilation process
- performance [CLR integration]
ms.assetid: 7ce2dfc0-4b1f-4dcb-a979-2c4f95b4cb15
author: rothja
ms.author: jroth
ms.openlocfilehash: 33e45039ed98ea3df607df1714b3c6108ec17c35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704155"
---
# <a name="performance-of-clr-integration"></a><span data-ttu-id="c0533-102">Performances de l'intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="c0533-102">Performance of CLR Integration</span></span>
  <span data-ttu-id="c0533-103">Cette rubrique décrit quelques-uns des choix de conception qui améliorent les performances de l' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intégration avec le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c0533-103">This topic discusses some of the design choices that enhance the performance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework common language runtime (CLR).</span></span>  
  
## <a name="the-compilation-process"></a><span data-ttu-id="c0533-104">Processus de compilation</span><span class="sxs-lookup"><span data-stu-id="c0533-104">The Compilation Process</span></span>  
 <span data-ttu-id="c0533-105">Pendant la compilation d'expressions SQL, en cas de référence à une routine managée, un stub MSIL ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Intermediate Language) est généré.</span><span class="sxs-lookup"><span data-stu-id="c0533-105">During compilation of SQL expressions, when a reference to a managed routine is encountered, a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] intermediate language (MSIL) stub is generated.</span></span> <span data-ttu-id="c0533-106">Ce stub inclut le code pour marshaler les paramètres de routine à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers le CLR, appeler la fonction et retourner le résultat.</span><span class="sxs-lookup"><span data-stu-id="c0533-106">This stub includes code to marshal the routine parameters from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the CLR, invoke the function, and return the result.</span></span> <span data-ttu-id="c0533-107">Ce code de type glue est basé sur le type de paramètre et sur la direction du paramètre (in, out ou reference).</span><span class="sxs-lookup"><span data-stu-id="c0533-107">This "glue" code is based on the type of parameter and on parameter direction (in, out, or reference).</span></span>  
  
 <span data-ttu-id="c0533-108">Le code de type glue active les optimisations spécifiques au type et garantit une application efficace de la sémantique [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], telle que la possibilité de valeur NULL, les facettes de contrainte et la gestion des exceptions par valeur et standard.</span><span class="sxs-lookup"><span data-stu-id="c0533-108">The glue code enables type-specific optimizations and ensures efficient enforcement of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] semantics, such as nullability, constraining facets, by-value, and standard exception handling.</span></span> <span data-ttu-id="c0533-109">En générant le code pour les types exacts des arguments, vous évitez le conflit de types ou les coûts de création d'objet de wrapper (ou « conversion boxing ») à travers la limite d'appel.</span><span class="sxs-lookup"><span data-stu-id="c0533-109">By generating code for the exact types of the arguments, you avoid type coercion or wrapper object creation costs (called "boxing") across the invocation boundary.</span></span>  
  
 <span data-ttu-id="c0533-110">Le stub généré est ensuite compilé en code natif et optimisé pour l'architecture matérielle particulière sur laquelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute, à l'aide des services de compilation JIT (juste-à-temps) du CLR.</span><span class="sxs-lookup"><span data-stu-id="c0533-110">The generated stub is then compiled to native code and optimized for the particular hardware architecture on which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] executes, using the JIT (just-in-time) compilation services of the CLR.</span></span> <span data-ttu-id="c0533-111">Les services JIT sont appelés au niveau de la méthode et permettent à l'environnement d'hébergement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de créer une seule unité de compilation qui couvre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et l'exécution du CLR.</span><span class="sxs-lookup"><span data-stu-id="c0533-111">The JIT services are invoked at the method level and allow the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosting environment to create a single compilation unit that spans both [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and CLR execution.</span></span> <span data-ttu-id="c0533-112">Une fois le stub compilé, le pointeur fonction résultant devient l'implémentation à l'exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c0533-112">Once the stub is compiled, the resulting function pointer becomes the run-time implementation of the function.</span></span> <span data-ttu-id="c0533-113">Cette solution de génération du code garantit qu'il n'existe pas de coûts d'appel supplémentaires en rapport avec la réflexion ou l'accès aux métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c0533-113">This code generation approach ensures that there are no additional invocation costs related to reflection or metadata access at run time.</span></span>  
  
### <a name="fast-transitions-between-sql-server-and-clr"></a><span data-ttu-id="c0533-114">Transitions rapides entre SQL Server et CLR</span><span class="sxs-lookup"><span data-stu-id="c0533-114">Fast Transitions Between SQL Server and CLR</span></span>  
 <span data-ttu-id="c0533-115">Le processus de compilation génère une fonction pointeur qui peut être appelée au moment de l'exécution à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="c0533-115">The compilation process yields a function pointer that can be called at run time from native code.</span></span> <span data-ttu-id="c0533-116">Dans le cas de fonctions scalaires définies par l'utilisateur, cet appel de fonction se produit ligne par ligne.</span><span class="sxs-lookup"><span data-stu-id="c0533-116">In the case of scalar-valued user-defined functions, this function invocation happens on a per-row basis.</span></span> <span data-ttu-id="c0533-117">Pour réduire le coût de la transition entre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et le CLR, les instructions qui contiennent un appel managé possèdent une étape de démarrage pour identifier le domaine d'application cible.</span><span class="sxs-lookup"><span data-stu-id="c0533-117">To minimize the cost of transitioning between [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and the CLR, statements that contain any managed invocation have a startup step to identify the target application domain.</span></span> <span data-ttu-id="c0533-118">Cette étape d'identification réduit le coût de la transition pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="c0533-118">This identification step reduces the cost of transitioning for each row.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="c0533-119">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="c0533-119">Performance Considerations</span></span>  
 <span data-ttu-id="c0533-120">Les éléments suivants résument les considérations sur les performances spécifiques à l'intégration du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0533-120">The following summarizes performance considerations specific to CLR integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0533-121">Pour plus d’informations, consultez «[utilisation de l’intégration du CLR dans SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=50332)» sur le site Web MSDN.</span><span class="sxs-lookup"><span data-stu-id="c0533-121">More detailed information can be found in "[Using CLR Integration in SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=50332)" on the MSDN Web site.</span></span> <span data-ttu-id="c0533-122">Vous trouverez des informations générales sur les performances du code managé dans la rubrique «[amélioration des performances et de l’évolutivité des applications .net](https://go.microsoft.com/fwlink/?LinkId=50333)» sur le site Web MSDN.</span><span class="sxs-lookup"><span data-stu-id="c0533-122">General information regarding managed code performance can be found in "[Improving .NET Application Performance and Scalability](https://go.microsoft.com/fwlink/?LinkId=50333)" on the MSDN Web site.</span></span>  
  
### <a name="user-defined-functions"></a><span data-ttu-id="c0533-123">Fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0533-123">User-Defined Functions</span></span>  
 <span data-ttu-id="c0533-124">Les fonctions CLR tirent parti d'un chemin d'accès d'appel plus rapide que celui des fonctions [!INCLUDE[tsql](../../../includes/tsql-md.md)] définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c0533-124">CLR functions benefit from a quicker invocation path than that of [!INCLUDE[tsql](../../../includes/tsql-md.md)] user-defined functions.</span></span> <span data-ttu-id="c0533-125">En outre, le code managé possède un avantage décisif en termes de performances par rapport à [!INCLUDE[tsql](../../../includes/tsql-md.md)] quant au code procédural, au calcul et à la manipulation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c0533-125">Additionally, managed code has a decisive performance advantage over [!INCLUDE[tsql](../../../includes/tsql-md.md)] in terms of procedural code, computation, and string manipulation.</span></span> <span data-ttu-id="c0533-126">Les fonctions CLR gourmandes en calculs et n'effectuant pas d'accès aux données sont mieux écrites en code managé.</span><span class="sxs-lookup"><span data-stu-id="c0533-126">CLR functions that are computing-intensive and that do not perform data access are better written in managed code.</span></span> <span data-ttu-id="c0533-127">Toutefois, les fonctions [!INCLUDE[tsql](../../../includes/tsql-md.md)] exécutent l'accès aux données plus efficacement que l'intégration du CLR.</span><span class="sxs-lookup"><span data-stu-id="c0533-127">[!INCLUDE[tsql](../../../includes/tsql-md.md)] functions do, however, perform data access more efficiently than CLR integration.</span></span>  
  
### <a name="user-defined-aggregates"></a><span data-ttu-id="c0533-128">Agrégats définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0533-128">User-Defined Aggregates</span></span>  
 <span data-ttu-id="c0533-129">Le code managé se révèle considérablement plus performant que l'agrégation à base de curseur.</span><span class="sxs-lookup"><span data-stu-id="c0533-129">Managed code can significantly outperform cursor-based aggregation.</span></span> <span data-ttu-id="c0533-130">En principe, le code managé s'exécute légèrement moins vite que les fonctions d'agrégation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intégrées.</span><span class="sxs-lookup"><span data-stu-id="c0533-130">Managed code generally performs slightly slower than built-in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aggregate functions.</span></span> <span data-ttu-id="c0533-131">S'il existe une fonction d'agrégation intégrée native, il est recommandé de l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="c0533-131">We recommend that if a native built-in aggregate function exists, you should use it.</span></span> <span data-ttu-id="c0533-132">Dans les cas où l'agrégation nécessaire n'est pas prise en charge en mode natif, choisissez, si possible, un agrégat CLR défini par l'utilisateur de préférence à une implémentation à base de curseur pour des raisons de performance.</span><span class="sxs-lookup"><span data-stu-id="c0533-132">In cases in which the needed aggregation is not natively supported, consider a CLR user-defined aggregate over a cursor-based implementation for performance reasons.</span></span>  
  
### <a name="streaming-table-valued-functions"></a><span data-ttu-id="c0533-133">Fonctions table en continu</span><span class="sxs-lookup"><span data-stu-id="c0533-133">Streaming Table-Valued Functions</span></span>  
 <span data-ttu-id="c0533-134">Les applications doivent souvent retourner une table comme résultat de l'appel d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="c0533-134">Applications often need to return a table as a result of invoking a function.</span></span> <span data-ttu-id="c0533-135">Les exemples incluent la lecture de données tabulaires à partir d'un fichier dans le cadre d'une opération d'importation et la conversion de valeurs séparées par des virgules dans le cas d'une représentation relationnelle.</span><span class="sxs-lookup"><span data-stu-id="c0533-135">Examples include reading tabular data from a file as part of an import operation, and converting comma-separated-values to a relational representation.</span></span> <span data-ttu-id="c0533-136">En général, vous pouvez accomplir ces actions en matérialisant la table de résultats et en la remplissant avant qu'elle ne puisse être consommée par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="c0533-136">Typically, you can accomplish this by materializing and populating the result table before it can be consumed by the caller.</span></span> <span data-ttu-id="c0533-137">L'intégration du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] introduit un nouveau mécanisme d'extensibilité appelé fonction table en continu.</span><span class="sxs-lookup"><span data-stu-id="c0533-137">The integration of the CLR into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] introduces a new extensibility mechanism called a streaming table-valued function (STVF).</span></span> <span data-ttu-id="c0533-138">Les fonctions table en continu offrent de meilleures performances que les implémentations de procédure stockée étendue comparables.</span><span class="sxs-lookup"><span data-stu-id="c0533-138">Managed STVFs perform better than comparable extended stored procedure implementations.</span></span>  
  
 <span data-ttu-id="c0533-139">Les fonctions table en continu sont des fonctions managées qui retournent une interface `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="c0533-139">STVFs are managed functions that return an `IEnumerable` interface.</span></span> <span data-ttu-id="c0533-140">`IEnumerable` possède des méthodes pour se déplacer à travers le jeu de résultats retourné par la fonction table en continu.</span><span class="sxs-lookup"><span data-stu-id="c0533-140">`IEnumerable` has methods to navigate the result set returned by the STVF.</span></span> <span data-ttu-id="c0533-141">Lorsque la fonction table en continu est appelée, l'interface `IEnumerable` retournée est directement connectée au plan de requête.</span><span class="sxs-lookup"><span data-stu-id="c0533-141">When the STVF is invoked, the returned `IEnumerable` is directly connected to the query plan.</span></span> <span data-ttu-id="c0533-142">Le plan de requête appelle les méthodes `IEnumerable` lorsqu'il doit extraire des lignes.</span><span class="sxs-lookup"><span data-stu-id="c0533-142">The query plan calls `IEnumerable` methods when it needs to fetch rows.</span></span> <span data-ttu-id="c0533-143">Ce modèle d'itération permet que les résultats soient consommés immédiatement après que la première ligne a été créée, au lieu d'attendre que la totalité de la table soit remplie.</span><span class="sxs-lookup"><span data-stu-id="c0533-143">This iteration model allows results to be consumed immediately after the first row is produced, instead of waiting until the entire table is populated.</span></span> <span data-ttu-id="c0533-144">Il réduit aussi considérablement la mémoire consommée en appelant la fonction.</span><span class="sxs-lookup"><span data-stu-id="c0533-144">It also significantly reduces the memory consumed by invoking the function.</span></span>  
  
### <a name="arrays-vs-cursors"></a><span data-ttu-id="c0533-145">Différences entre les tableaux et les curseurs</span><span class="sxs-lookup"><span data-stu-id="c0533-145">Arrays vs. Cursors</span></span>  
 <span data-ttu-id="c0533-146">Lorsque les curseurs [!INCLUDE[tsql](../../../includes/tsql-md.md)] doivent parcourir des données qui sont plus aisément exprimées en tableau, le code managé peut être utilisé avec des gains de performance significatifs.</span><span class="sxs-lookup"><span data-stu-id="c0533-146">When [!INCLUDE[tsql](../../../includes/tsql-md.md)] cursors must traverse data that is more easily expressed as an array, managed code can be used with significant performance gains.</span></span>  
  
### <a name="string-data"></a><span data-ttu-id="c0533-147">Données de type chaîne</span><span class="sxs-lookup"><span data-stu-id="c0533-147">String Data</span></span>  
 <span data-ttu-id="c0533-148">Les données caractères [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], telles que `varchar`, peuvent être du type SqlString ou SqlChars dans les fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="c0533-148">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] character data, such as `varchar`, can be of the type SqlString or SqlChars in managed functions.</span></span> <span data-ttu-id="c0533-149">Les variables SqlString créent une instance de la valeur entière en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c0533-149">SqlString variables create an instance of the entire value into memory.</span></span> <span data-ttu-id="c0533-150">Les variables SqlChars fournissent une interface multidiffusion qui peut être utilisée pour obtenir de meilleures performances et une meilleure évolutivité en ne créant pas d'instance de la totalité de la valeur en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c0533-150">SqlChars variables provide a streaming interface that can be used to achieve better performance and scalability by not creating an instance of the entire value into memory.</span></span> <span data-ttu-id="c0533-151">Ce point est particulièrement important pour les données LOB.</span><span class="sxs-lookup"><span data-stu-id="c0533-151">This becomes particularly important for large object (LOB) data.</span></span> <span data-ttu-id="c0533-152">En outre, il est possible d'accéder aux données XML du serveur via une interface de diffusion retournée par `SqlXml.CreateReader()`.</span><span class="sxs-lookup"><span data-stu-id="c0533-152">Additionally, server XML data can be accessed through a streaming interface returned by `SqlXml.CreateReader()`.</span></span>  
  
### <a name="clr-vs-extended-stored-procedures"></a><span data-ttu-id="c0533-153">Différences entre le CLR et les procédures stockées étendues</span><span class="sxs-lookup"><span data-stu-id="c0533-153">CLR vs. Extended Stored Procedures</span></span>  
 <span data-ttu-id="c0533-154">Les API Microsoft.SqlServer.Server (API) qui permettent aux procédures managées de renvoyer des jeux de résultats au client s'exécutent mieux que les API ODS (Open Data Services) utilisées par les procédures stockées étendues.</span><span class="sxs-lookup"><span data-stu-id="c0533-154">The Microsoft.SqlServer.Server application programming interfaces (APIs) that allow managed procedures to send result sets back to the client perform better than the Open Data Services (ODS) APIs used by extended stored procedures.</span></span> <span data-ttu-id="c0533-155">En outre, les API System.Data.SqlServer prennent en charge les types de données tels que `xml`, `varchar(max)`, `nvarchar(max)` et `varbinary(max)`, introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], alors que les API ODS n'ont pas été étendues pour prendre en charge les nouveaux types de données.</span><span class="sxs-lookup"><span data-stu-id="c0533-155">Furthermore, the System.Data.SqlServer APIs support data types such as `xml`, `varchar(max)`, `nvarchar(max)`, and `varbinary(max)`, introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], while the ODS APIs have not been extended to support the new data types.</span></span>  
  
 <span data-ttu-id="c0533-156">Avec le code managé, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gère l'utilisation de ressources telles que la mémoire, les threads et la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="c0533-156">With managed code, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] manages use of resources such as memory, threads, and synchronization.</span></span> <span data-ttu-id="c0533-157">La raison en est que les API managées qui exposent ces ressources sont implémentées sur le gestionnaire de ressources [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0533-157">This is because the managed APIs that expose these resources are implemented on top of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource manager.</span></span> <span data-ttu-id="c0533-158">Inversement, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'a ni vue ou contrôle sur l'utilisation des ressources de la procédure stockée étendue.</span><span class="sxs-lookup"><span data-stu-id="c0533-158">Conversely, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has no view or control over the resource usage of the extended stored procedure.</span></span> <span data-ttu-id="c0533-159">Par exemple, si une procédure stockée étendue consomme une quantité trop importante d'UC ou de ressources mémoire, il n'existe aucun moyen de le détecter ou de le contrôler avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0533-159">For example, if an extended stored procedure consumes too much CPU or memory resources, there is no way to detect or control this with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0533-160">Avec le code managé, toutefois, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut détecter qu'un thread donné n'a rien produit pendant une longue période de temps, puis forcer la tâche à être abandonnée afin qu'un autre travail puisse être planifié.</span><span class="sxs-lookup"><span data-stu-id="c0533-160">With managed code, however, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can detect that a given thread has not yielded for a long period of time, and then force the task to yield so that other work can be scheduled.</span></span> <span data-ttu-id="c0533-161">Par conséquent, l'utilisation du code managé offre une meilleure évolutivité et une meilleure utilisation des ressources système.</span><span class="sxs-lookup"><span data-stu-id="c0533-161">Consequently, using managed code provides for better scalability and system resource usage.</span></span>  
  
 <span data-ttu-id="c0533-162">Le code managé peut impliquer une charge mémoire supplémentaire nécessaire pour maintenir l'environnement d'exécution et effectuer les contrôles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c0533-162">Managed code may incur additional overhead necessary to maintain the execution environment and perform security checks.</span></span> <span data-ttu-id="c0533-163">Par exemple, tel est le cas lors de l'exécution dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que de nombreuses transitions du code managé vers le code natif sont requises (parce que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit effectuer une maintenance supplémentaire sur les paramètres spécifiques au thread lors du déplacement vers ou depuis le code natif).</span><span class="sxs-lookup"><span data-stu-id="c0533-163">This is the case, for example, when running inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and numerous transitions from managed to native code are required (because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] needs to do additional maintenance on thread-specific settings when moving out to native code and back).</span></span> <span data-ttu-id="c0533-164">Par conséquent, les procédures stockées étendues peuvent offrir de bien meilleures performances que l'exécution du code managé à l'intérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans les cas où il existe de fréquentes transitions entre le code managé et le code natif.</span><span class="sxs-lookup"><span data-stu-id="c0533-164">Consequently, extended stored procedures can significantly outperform managed code running inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cases in which there are frequent transitions between managed and native code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0533-165">Il est recommandé de ne pas développer de nouvelles procédures stockées étendues, parce que cette fonctionnalité a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c0533-165">It is recommended that you do not develop new extended stored procedures, because this feature has been deprecated.</span></span>  
  
### <a name="native-serialization-for-user-defined-types"></a><span data-ttu-id="c0533-166">Sérialisation native pour les types définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0533-166">Native Serialization for User-Defined Types</span></span>  
 <span data-ttu-id="c0533-167">Les types définis par l'utilisateur (UDT) sont conçus comme mécanisme d'extensibilité du système de types scalaires.</span><span class="sxs-lookup"><span data-stu-id="c0533-167">User-defined types (UDTs) are designed as an extensibility mechanism for the scalar type system.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c0533-168">implémente un format de sérialisation pour les UDT appelé `Format.Native`.</span><span class="sxs-lookup"><span data-stu-id="c0533-168">implements a serialization format for UDTs called `Format.Native`.</span></span> <span data-ttu-id="c0533-169">Pendant la compilation, la structure du type est examinée pour générer un langage MSIL personnalisé pour cette définition de type particulière.</span><span class="sxs-lookup"><span data-stu-id="c0533-169">During compilation, the structure of the type is examined to generate MSIL that is customized for that particular type definition.</span></span>  
  
 <span data-ttu-id="c0533-170">La sérialisation native est l'implémentation par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0533-170">Native serialization is the default implementation for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0533-171">La sérialisation définie par l'utilisateur appelle une méthode définie par le créateur du type pour effectuer la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="c0533-171">User-defined serialization invokes a method defined by the type author to do the serialization.</span></span> <span data-ttu-id="c0533-172">La sérialisation `Format.Native` doit être utilisée si possible pour de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="c0533-172">`Format.Native` serialization should be used when possible for best performance.</span></span>  
  
### <a name="normalization-of-comparable-udts"></a><span data-ttu-id="c0533-173">Normalisation d'UDT comparables</span><span class="sxs-lookup"><span data-stu-id="c0533-173">Normalization of Comparable UDTs</span></span>  
 <span data-ttu-id="c0533-174">Les opérations relationnelles, telles que le tri et la comparaison d'UDT, fonctionnent directement sur la représentation binaire de la valeur.</span><span class="sxs-lookup"><span data-stu-id="c0533-174">Relational operations, such as sorting and comparing UDTs, operate directly on the binary representation of the value.</span></span> <span data-ttu-id="c0533-175">Cette tâche s'effectue en stockant une représentation normalisée (classement binaire) de l'état de l'UDT sur le disque.</span><span class="sxs-lookup"><span data-stu-id="c0533-175">This is accomplished by storing a normalized (binary ordered) representation of the state of the UDT on disk.</span></span>  
  
 <span data-ttu-id="c0533-176">La normalisation présente deux avantages : elle rend la comparaison considérablement moins onéreuse en évitant la construction de l'instance du type et les charges mémoire liées à l'appel de méthode ; de plus, elle crée un domaine binaire pour l'UDT, en permettant la construction d'histogrammes, d'index et d'histogrammes pour les valeurs du type.</span><span class="sxs-lookup"><span data-stu-id="c0533-176">Normalization has two benefits: it makes the comparison operation considerably less expensive by avoiding the construction of the type instance and the method invocation overhead; and it creates a binary domain for the UDT, enabling the construction of histograms, indexes, and histograms for values of the type.</span></span> <span data-ttu-id="c0533-177">Par conséquent, les UDT normalisés offrent un profil de performance très similaire aux types intégrés natifs pour les opérations qui n'impliquent pas d'appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="c0533-177">Consequently, normalized UDTs have a very similar performance profile to the native built-in types for operations that do not involve method invocation.</span></span>  
  
### <a name="scalable-memory-usage"></a><span data-ttu-id="c0533-178">Utilisation de la mémoire évolutive</span><span class="sxs-lookup"><span data-stu-id="c0533-178">Scalable Memory Usage</span></span>  
 <span data-ttu-id="c0533-179">Pour que le garbage collection managé s'effectue et évolue correctement dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], évitez une allocation importante et unique.</span><span class="sxs-lookup"><span data-stu-id="c0533-179">In order for managed garbage collection to perform and scale well in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], avoid large, single allocation.</span></span> <span data-ttu-id="c0533-180">Les allocations d'une taille supérieure à 88 Ko sont placées sur le tas des objets volumineux, ce qui provoque une exécution du garbage collection et une évolution bien moins performantes que nombre d'allocations plus réduites.</span><span class="sxs-lookup"><span data-stu-id="c0533-180">Allocations greater than 88 kilobytes (KB) in size will be placed on the Large Object Heap, which will cause garbage collection to perform and scale much worse than many smaller allocations.</span></span> <span data-ttu-id="c0533-181">Par exemple, si vous devez allouer un grand tableau multidimensionnel, il est préférable d'allouer un tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="c0533-181">For example, if you need to allocate a large multi-dimensional array, it is better to allocate a jagged (scattered) array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0533-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0533-182">See Also</span></span>  
 [<span data-ttu-id="c0533-183">Types CLR définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0533-183">CLR User-Defined Types</span></span>](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  