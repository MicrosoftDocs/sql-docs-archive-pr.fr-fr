---
title: Extraction de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
author: rothja
ms.author: jroth
ms.openlocfilehash: 435e1d705091814b2544c75772f20882caddf942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602117"
---
# <a name="fetching-rows"></a><span data-ttu-id="90117-102">Extraction de lignes</span><span class="sxs-lookup"><span data-stu-id="90117-102">Fetching Rows</span></span>
  <span data-ttu-id="90117-103">L’interface **IRowset** est l’interface de base des ensembles de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-103">The **IRowset** interface is the base rowset interface.</span></span> <span data-ttu-id="90117-104">L’interface **IRowset** fournit des méthodes pour récupérer (fetch) les lignes séquentiellement, obtenir les données de ces lignes et gérer les lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-104">The **IRowset** interface provides methods for fetching rows sequentially, getting the data from those rows, and managing rows.</span></span> <span data-ttu-id="90117-105">Les consommateurs utilisent les méthodes de l’interface **IRowset** pour toutes les opérations de base des ensembles de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-105">Consumers use the methods in **IRowset** for all basic rowset operations.</span></span> <span data-ttu-id="90117-106">Ces opérations incluent l'extraction et la libération des lignes, ainsi que l'obtention des valeurs des colonnes.</span><span class="sxs-lookup"><span data-stu-id="90117-106">This includes fetching and releasing rows and getting column values.</span></span>  
  
 <span data-ttu-id="90117-107">Quand un consommateur obtient un pointeur d’interface sur un ensemble de lignes, la première étape consiste ordinairement à déterminer les fonctions de l’ensemble de lignes à l’aide de la méthode **IRowsetInfo::GetProperties**.</span><span class="sxs-lookup"><span data-stu-id="90117-107">When a consumer obtains an interface pointer on a rowset, the first step is ordinarily to determine the capabilities of the rowset by using the **IRowsetInfo::GetProperties** method.</span></span> <span data-ttu-id="90117-108">Cette opération retourne les informations sur les interfaces exposées par l'ensemble de lignes, ainsi que les fonctions de l'ensemble de lignes n'apparaissant pas comme interfaces distinctes, telles que le nombre maximal de lignes actives et le nombre de lignes qui peuvent avoir simultanément des mises à jour en attente.</span><span class="sxs-lookup"><span data-stu-id="90117-108">This returns information about the interfaces exposed by the rowset and also capabilities of the rowset that do not show up as distinct interfaces, such as the maximum number of active rows and the number of rows that can have pending updates at the same time.</span></span>  
  
 <span data-ttu-id="90117-109">L'étape suivante pour les consommateurs consiste à déterminer les caractéristiques, ou métadonnées, des colonnes de l'ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-109">The next step for consumers is to determine the characteristics, or metadata, of the columns in the rowset.</span></span> <span data-ttu-id="90117-110">À cette fin, ils utilisent la méthode **IColumnsInfo** pour les informations de colonnes simples ou la méthode **IColumnsRowset** pour les informations de colonnes étendues.</span><span class="sxs-lookup"><span data-stu-id="90117-110">For this they use the **IColumnsInfo** method for simple column information or the **IColumnsRowset** method for extended column information.</span></span> <span data-ttu-id="90117-111">La méthode **GetColumnInfo** retourne les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="90117-111">The **GetColumnInfo** method returns the following information:</span></span>  
  
-   <span data-ttu-id="90117-112">Nombre de colonnes de l'ensemble de résultats.</span><span class="sxs-lookup"><span data-stu-id="90117-112">The number of columns in the result set.</span></span>  
  
-   <span data-ttu-id="90117-113">Tableau de structures DBCOLUMNINFO, une par colonne.</span><span class="sxs-lookup"><span data-stu-id="90117-113">An array of DBCOLUMNINFO structures, one per column.</span></span>  
  
     <span data-ttu-id="90117-114">L'ordre des structures désigne l'ordre dans lequel les colonnes apparaissent dans l'ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-114">The order of the structures is the order in which the columns appear in the rowset.</span></span> <span data-ttu-id="90117-115">Chaque structure DBCOLUMNINFO inclut les métadonnées des colonnes, telles que le nom de colonne, le numéro ordinal de la colonne, la longueur maximale d'une valeur de la colonne, le type de données de la colonne, la précision et la longueur.</span><span class="sxs-lookup"><span data-stu-id="90117-115">Each DBCOLUMNINFO structure includes column metadata, such as column name, ordinal of the column, maximum possible length of a value in the column, data type of the column, precision, and length.</span></span>  
  
-   <span data-ttu-id="90117-116">Pointeur vers un stockage de toutes les valeurs de chaîne au sein d'un bloc d'allocation unique.</span><span class="sxs-lookup"><span data-stu-id="90117-116">The pointer to a storage for all string values within a single allocation block.</span></span>  
  
 <span data-ttu-id="90117-117">Le consommateur détermine s'il a besoin des colonnes des métadonnées ou de celles fondées sur la commande de texte ayant généré l'ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-117">The consumer determines which columns it needs either from the metadata or based on the text command that generated the rowset.</span></span> <span data-ttu-id="90117-118">Il détermine les ordinaux des colonnes nécessaires à partir du classement des informations sur les colonnes retournées par **IColumnsInfo** ou à partir des ordinaux de l’ensemble de lignes des métadonnées des colonnes retournées par **IColumnsRowset**.</span><span class="sxs-lookup"><span data-stu-id="90117-118">It determines the ordinals of the needed columns from the ordering of the column information returned by **IColumnsInfo** or from the ordinals in the column metadata rowset returned by **IColumnsRowset**.</span></span>  
  
 <span data-ttu-id="90117-119">Les interfaces **IColumnsInfo** et **IColumnsRowset** sont utilisées pour extraire des informations sur les colonnes de l’ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-119">The **IColumnsInfo** and **IColumnsRowset** interfaces are used to extract information about the columns in the rowset.</span></span> <span data-ttu-id="90117-120">L’interface **IColumnsInfo** retourne un ensemble limité d’informations, alors que l’interface **IColumnsRowset** fournit toutes les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="90117-120">The **IColumnsInfo** interface returns a limited set of information, whereas **IColumnsRowset** provides all the metadata.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90117-121">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 et antérieure, la colonne de métadonnées facultative DBCOLUMN_COMPUTEMODE retournée par **IColumnsInfo::GetColumnsInfo** retourne DBSTATUS_S_ISNULL (au lieu des valeurs indiquant si la colonne est calculée), parce qu’il n’est pas possible de déterminer si la colonne sous-jacente est calculée.</span><span class="sxs-lookup"><span data-stu-id="90117-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and earlier, the optional metadata column DBCOLUMN_COMPUTEMODE returned by **IColumnsInfo::GetColumnsInfo** returns DBSTATUS_S_ISNULL (instead of the values describing whether the column is computed) because it cannot be determined whether the underlying column is computed.</span></span>  
  
 <span data-ttu-id="90117-122">Les ordinaux sont utilisés pour spécifier une liaison à une colonne.</span><span class="sxs-lookup"><span data-stu-id="90117-122">The ordinals are used to specify a binding to a column.</span></span> <span data-ttu-id="90117-123">Une liaison est une structure qui associe un élément de la structure du consommateur et une colonne.</span><span class="sxs-lookup"><span data-stu-id="90117-123">A binding is a structure that associates an element of the consumer's structure with a column.</span></span> <span data-ttu-id="90117-124">La liaison peut lier la valeur des données, la longueur et la valeur d'état de la colonne.</span><span class="sxs-lookup"><span data-stu-id="90117-124">The binding can bind the data value, length, and status value of the column.</span></span>  
  
 <span data-ttu-id="90117-125">Un jeu de liaisons est regroupé dans un accesseur.</span><span class="sxs-lookup"><span data-stu-id="90117-125">A set of bindings is gathered together in an accessor.</span></span> <span data-ttu-id="90117-126">Celui-ci est créé à l’aide de la méthode **IAccessor::CreateAccessor**.</span><span class="sxs-lookup"><span data-stu-id="90117-126">This is created by using the **IAccessor::CreateAccessor** method.</span></span> <span data-ttu-id="90117-127">Un accesseur peut contenir plusieurs liaisons afin que les données de plusieurs colonnes puissent être extraites ou définies en un seul appel.</span><span class="sxs-lookup"><span data-stu-id="90117-127">An accessor can contain multiple bindings so that the data for multiple columns can be retrieved or set in a single call.</span></span> <span data-ttu-id="90117-128">Le consommateur peut créer plusieurs accesseurs pour correspondre aux divers modèles d'utilisation des différentes parties de l'application.</span><span class="sxs-lookup"><span data-stu-id="90117-128">The consumer can create several accessors to match different usage patterns in different parts of the application.</span></span> <span data-ttu-id="90117-129">Il peut créer et libérer des accesseurs tandis que l'ensemble de lignes continue à exister.</span><span class="sxs-lookup"><span data-stu-id="90117-129">It can create and release accessors while the rowset remains in existence.</span></span>  
  
 <span data-ttu-id="90117-130">Pour récupérer (fetch) les lignes de la base de données, le consommateur appelle une méthode, telle que **IRowset::GetNextRows** ou **IRowsetLocate::GetRowsAt**.</span><span class="sxs-lookup"><span data-stu-id="90117-130">To fetch rows from the database, the consumer calls a method, such as **IRowset::GetNextRows** or **IRowsetLocate::GetRowsAt**.</span></span> <span data-ttu-id="90117-131">Ces opérations d'extraction placent les données de ligne du serveur dans le tampon de ligne du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="90117-131">These fetch operations put row data from the server into the row buffer of the provider.</span></span> <span data-ttu-id="90117-132">Le consommateur ne peut pas accéder directement au tampon de ligne du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="90117-132">The consumer does not have direct access to the row buffer of the provider.</span></span> <span data-ttu-id="90117-133">Le consommateur utilise **IRowset::GetData** pour copier les données de la mémoire tampon du fournisseur vers la mémoire tampon du consommateur, et **IRowsetChange::SetData** pour copier les modifications de données de la mémoire tampon du consommateur vers la mémoire tampon de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="90117-133">The consumer uses **IRowset::GetData** to copy data from the buffer of the provider to the consumer buffer and **IRowsetChange::SetData** to copy data changes from the consumer buffer to the provider buffer.</span></span>  
  
 <span data-ttu-id="90117-134">Le consommateur appelle la méthode **GetData** et passe le descripteur à une ligne, le descripteur à un accesseur et un pointeur vers une mémoire tampon allouée par le consommateur.</span><span class="sxs-lookup"><span data-stu-id="90117-134">The consumer calls the **GetData** method and passes the handle to a row, the handle to an accessor, and a pointer to a consumer-allocated buffer.</span></span> <span data-ttu-id="90117-135">**GetData** convertit les données et retourne les colonnes comme spécifié dans les liaisons utilisées pour créer l’accesseur.</span><span class="sxs-lookup"><span data-stu-id="90117-135">**GetData** converts the data and returns the columns as specified in the bindings used to create the accessor.</span></span> <span data-ttu-id="90117-136">Le consommateur peut appeler **GetData** plusieurs fois pour une même ligne, à l’aide de différents accesseurs et mémoires tampon. Par conséquent, le consommateur peut obtenir plusieurs copies des mêmes données.</span><span class="sxs-lookup"><span data-stu-id="90117-136">The consumer can call **GetData** more than one time for a row, using different accessors and buffers and therefore the consumer can obtain multiple copies of the same data.</span></span>  
  
 <span data-ttu-id="90117-137">Les données de colonnes de longueur variable peuvent être traitées de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="90117-137">Data from variable-length columns can be treated several ways.</span></span> <span data-ttu-id="90117-138">En premier lieu, ces colonnes peuvent être liées à une section limitée de la structure du consommateur.</span><span class="sxs-lookup"><span data-stu-id="90117-138">First, such columns can be bound to a finite section of the consumer's structure.</span></span> <span data-ttu-id="90117-139">Il s'ensuit une troncation quand la longueur des données dépasse la longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="90117-139">This causes truncation when the length of the data exceeds the length of the buffer.</span></span> <span data-ttu-id="90117-140">Le consommateur peut déterminer que la troncation a eu lieu en vérifiant l'état DBSTATUS_S_TRUNCATED.</span><span class="sxs-lookup"><span data-stu-id="90117-140">The consumer can determine that truncation has occurred by checking for the status DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="90117-141">La longueur retournée est toujours la véritable longueur en octets, afin que le consommateur puisse également déterminer la quantité de données tronquées.</span><span class="sxs-lookup"><span data-stu-id="90117-141">The returned length is always the true length in bytes, so that the consumer also can determine how much data was truncated.</span></span>  
  
 <span data-ttu-id="90117-142">Quand le consommateur a fini de récupérer ou de mettre à jour les lignes, il les libère avec la méthode **ReleaseRows**.</span><span class="sxs-lookup"><span data-stu-id="90117-142">When the consumer has finished fetching or updating rows, it releases them with the **ReleaseRows** method.</span></span> <span data-ttu-id="90117-143">Cela libère les ressources de la copie des lignes de l'ensemble de lignes et crée de la place pour les nouvelles lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-143">This releases resources from the copy of the rows in the rowset and makes room for new rows.</span></span> <span data-ttu-id="90117-144">Le consommateur peut ensuite répéter son cycle d'extraction ou de création de lignes et d'accès à leurs données.</span><span class="sxs-lookup"><span data-stu-id="90117-144">The consumer can then repeat its cycle of fetching or creating rows and accessing the data in them.</span></span>  
  
 <span data-ttu-id="90117-145">Lorsque le consommateur en a fini avec l’ensemble de lignes, il appelle la méthode **IAccessor::ReleaseAccessor** pour libérer un accesseur éventuel.</span><span class="sxs-lookup"><span data-stu-id="90117-145">When the consumer is finished with the rowset, it calls the **IAccessor::ReleaseAccessor** method to release any accessor.</span></span> <span data-ttu-id="90117-146">Il appelle la méthode **IUnknown::Release** sur toutes les interfaces exposées par l’ensemble de lignes pour libérer l’ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="90117-146">It calls the **IUnknown::Release** method on all interfaces exposed by the rowset to release the rowset.</span></span> <span data-ttu-id="90117-147">Lorsque l'ensemble de lignes est libéré, il force la libération des lignes ou accesseurs restants que le consommateur peut détenir.</span><span class="sxs-lookup"><span data-stu-id="90117-147">When the rowset is released, it forces the release of any remaining rows or accessors the consumer may hold.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90117-148">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="90117-148">In This Section</span></span>  
  
-   [<span data-ttu-id="90117-149">Prochaine position d'extraction</span><span class="sxs-lookup"><span data-stu-id="90117-149">Next Fetch Position</span></span>](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a><span data-ttu-id="90117-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90117-150">See Also</span></span>  
 [<span data-ttu-id="90117-151">Ensembles de lignes</span><span class="sxs-lookup"><span data-stu-id="90117-151">Rowsets</span></span>](rowsets.md)  
  
  