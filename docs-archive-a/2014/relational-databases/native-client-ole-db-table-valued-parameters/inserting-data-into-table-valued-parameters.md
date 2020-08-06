---
title: Insertion de données dans des paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
ms.assetid: 9c1a3234-4675-40d3-b473-8df06208f880
author: rothja
ms.author: jroth
ms.openlocfilehash: 38e33c6e58bc2633591fa80e095ceafe46f67045
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603485"
---
# <a name="inserting-data-into-table-valued-parameters"></a><span data-ttu-id="2a688-102">Insertion de données dans des paramètres table</span><span class="sxs-lookup"><span data-stu-id="2a688-102">Inserting Data into Table-Valued Parameters</span></span>
  <span data-ttu-id="2a688-103">Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge deux modèles pour que le consommateur spécifie des données pour les lignes de paramètres table : un modèle d’émission et un modèle d’extraction.</span><span class="sxs-lookup"><span data-stu-id="2a688-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider supports two models for the consumer to specify data for table valued parameter rows: a push model and a pull model.</span></span> <span data-ttu-id="2a688-104">Pour obtenir un exemple illustrant le modèle de tirage (pull) des données, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).</span><span class="sxs-lookup"><span data-stu-id="2a688-104">A sample that demonstrates the pull model is available; see [SQL Server Data Programming Samples](https://msftdpprodsamples.codeplex.com/).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a688-105">Une colonne de paramètre table doit avoir, soit des valeurs non définies par défaut, soit des valeurs définies par défaut dans toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="2a688-105">A table-valued parameter column must have either non-default values in all rows or default values in all rows.</span></span> <span data-ttu-id="2a688-106">Il n'est pas possible d'avoir des valeurs par défaut dans certaines lignes et pas d'autres.</span><span class="sxs-lookup"><span data-stu-id="2a688-106">It is not possible to have default values in some rows but not others.</span></span> <span data-ttu-id="2a688-107">Par conséquent, dans les liaisons de paramètres table, les seules valeurs d'état autorisées pour les données de colonnes d'ensembles de lignes de paramètres table sont DBSTATUS_S_ISNULL et DBSTATUS_S_OK.</span><span class="sxs-lookup"><span data-stu-id="2a688-107">Therefore, in table-valued parameter bindings, the only status values allowed for table-valued parameter rowset column data are DBSTATUS_S_ISNULL and DBSTATUS_S_OK.</span></span> <span data-ttu-id="2a688-108">DBSTATUS_S_DEFAULT provoque un échec et la valeur d'état liée est définie à DBSTATUS_E_BADSTATUS.</span><span class="sxs-lookup"><span data-stu-id="2a688-108">DBSTATUS_S_DEFAULT will result in a failure and the bound status value will be set to DBSTATUS_E_BADSTATUS.</span></span>  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a><span data-ttu-id="2a688-109">Modèle d'émission des données (charge toutes les données de paramètres table en mémoire)</span><span class="sxs-lookup"><span data-stu-id="2a688-109">Push Model (Loads All Table-Valued Paremeter Data in Memory)</span></span>  
 <span data-ttu-id="2a688-110">Le modèle d’envoi (push) des données est semblable à l’utilisation des jeux de paramètres (c’est-à-dire le paramètre DBPARAMS dans ICommand::Execute).</span><span class="sxs-lookup"><span data-stu-id="2a688-110">The push model is similar to the use of parameter sets (that is, the DBPARAMS parameter in ICommand::Execute).</span></span> <span data-ttu-id="2a688-111">Le modèle d’envoi des données est utilisé uniquement si les objets d’ensembles de lignes de paramètres table sont utilisés sans implémentation personnalisée des interfaces IRowset.</span><span class="sxs-lookup"><span data-stu-id="2a688-111">The push model is only used if table-valued parameter rowset objects are used without a customized implementation of IRowset interfaces.</span></span> <span data-ttu-id="2a688-112">Le modèle d'émission des données est recommandé lorsque le nombre de lignes de l'ensemble de lignes de paramètres table est faible et qu'il ne risque pas d'entraîner une sollicitation excessive de la mémoire dans l'application.</span><span class="sxs-lookup"><span data-stu-id="2a688-112">The push model is recommended when the number of rows in the table-valued parameter rowset is small and is not expected to put excessive memory pressure on the application.</span></span> <span data-ttu-id="2a688-113">Il est plus simple que le modèle d'extraction des données, car les seules fonctionnalités qu'il requiert de la part de l'application du consommateur sont celles communes aux applications OLE DB classiques.</span><span class="sxs-lookup"><span data-stu-id="2a688-113">This is simpler than the pull model, because it does not require any more functionality from the consumer application than what is currently common in typical OLE DB applications.</span></span>  
  
 <span data-ttu-id="2a688-114">Le consommateur est censé fournir toutes les données de paramètres table au fournisseur avant d'exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="2a688-114">The consumer is expected to provide all the table-valued parameter data to the provider before executing a command.</span></span> <span data-ttu-id="2a688-115">Pour fournir les données, le consommateur remplit un objet d'ensemble de lignes de paramètres table pour chaque paramètre table.</span><span class="sxs-lookup"><span data-stu-id="2a688-115">To provide the data, the consumer populates a table-valued parameter rowset object for each table-valued parameter.</span></span> <span data-ttu-id="2a688-116">L'objet d'ensemble de lignes de paramètres table expose les opérations d'insertion, de définition et de suppression de l'ensemble de lignes, qui permettent au consommateur de manipuler les données de paramètres table.</span><span class="sxs-lookup"><span data-stu-id="2a688-116">The table-valued parameter rowset object exposes rowset Insert, Set, and Delete operations, which the consumer will use to manipulate the table-valued parameter data.</span></span> <span data-ttu-id="2a688-117">Le fournisseur extrait les données de cet objet d'ensemble de lignes de paramètres table au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2a688-117">The provider will fetch the data from this table-valued parameter rowset object at execution time.</span></span>  
  
 <span data-ttu-id="2a688-118">Lorsqu'un objet d'ensemble de lignes de paramètres table est fourni au consommateur, ce dernier peut le traiter comme un objet d'ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="2a688-118">When a table-valued parameter rowset object is provided to the consumer, the consumer can process it as a rowset object.</span></span> <span data-ttu-id="2a688-119">Le consommateur peut obtenir les informations de type de chaque colonne (type, longueur maximale, précision et échelle) en utilisant la méthode d'interface IColumnsInfo::GetColumnInfo ou IColumnsRowset::GetColumnsRowset.</span><span class="sxs-lookup"><span data-stu-id="2a688-119">The consumer can obtain the type information of each column (type, maximum length, precision, and scale) by using the IColumnsInfo::GetColumnInfo or IColumnsRowset::GetColumnsRowset interface method.</span></span> <span data-ttu-id="2a688-120">Le consommateur crée ensuite un accesseur pour spécifier les liaisons des données.</span><span class="sxs-lookup"><span data-stu-id="2a688-120">The consumer then creates an accessor to specify the bindings for the data.</span></span> <span data-ttu-id="2a688-121">L'étape suivante consiste à insérer des lignes de données dans l'ensemble de lignes de paramètres table.</span><span class="sxs-lookup"><span data-stu-id="2a688-121">The next step is to insert rows of data into the table-valued parameter rowset.</span></span> <span data-ttu-id="2a688-122">Pour ce faire, vous pouvez utiliser IRowsetChange::InsertRow.</span><span class="sxs-lookup"><span data-stu-id="2a688-122">This can be done by using IRowsetChange::InsertRow.</span></span> <span data-ttu-id="2a688-123">Cela est aussi possible via IRowsetChange::SetData ou IRowsetChange::DeleteRows sur l'objet d'ensemble de lignes de paramètres table si vous devez manipuler les données.</span><span class="sxs-lookup"><span data-stu-id="2a688-123">IRowsetChange::SetData or IRowsetChange::DeleteRows can also be used on the table-valued parameter rowset object if you have to manipulate the data.</span></span> <span data-ttu-id="2a688-124">Les objets d'ensembles de lignes de paramètres table ont un décompte de références, à l'instar des objets de flux.</span><span class="sxs-lookup"><span data-stu-id="2a688-124">Table-valued parameter rowset objects are reference counted, similar to stream objects.</span></span>  
  
 <span data-ttu-id="2a688-125">Si vous utilisez IColumnsRowset::GetColumnsRowset, il y aura des appels ultérieurs aux méthodes IRowset::GetNextRows, IRowset::GetData et IRowset::ReleaseRows sur l’objet d’ensemble de lignes de la colonne résultante.</span><span class="sxs-lookup"><span data-stu-id="2a688-125">If IColumnsRowset::GetColumnsRowset is used, there will be subsequent calls to IRowset::GetNextRows, IRowset::GetData, and IRowset::ReleaseRows methods on the rowset object of the resulting column.</span></span>  
  
 <span data-ttu-id="2a688-126">Une fois que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client commence à exécuter la commande, les valeurs de paramètre table sont extraites de cet objet d’ensemble de lignes de paramètre table et envoyées au serveur.</span><span class="sxs-lookup"><span data-stu-id="2a688-126">After the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider begins executing the command, the table-valued parameter values will be fetched from this table-valued parameter rowset object and sent to the server.</span></span>  
  
 <span data-ttu-id="2a688-127">Le modèle d'émission des données requiert un travail minimal de la part du consommateur ; toutefois, il utilise plus de mémoire que le modèle d'extraction des données, car toutes les données de paramètres table doivent être en mémoire au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2a688-127">The push model requires minimal work by the consumer, but uses more memory than the pull model, because all the table-valued parameter data has to be in memory at execution time.</span></span>  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a><span data-ttu-id="2a688-128">Modèle d'extraction des données (obtention de données de paramètres table sur demande, de la part du consommateur)</span><span class="sxs-lookup"><span data-stu-id="2a688-128">Pull Model (Obtaining Table-Valued Parameter Data on Demand from the Consumer)</span></span>  
 <span data-ttu-id="2a688-129">Le modèle d'extraction des données est utile pour deux scénarios :</span><span class="sxs-lookup"><span data-stu-id="2a688-129">The pull model is useful for two scenarios:</span></span>  
  
-   <span data-ttu-id="2a688-130">flux de lignes ;</span><span class="sxs-lookup"><span data-stu-id="2a688-130">To stream rows.</span></span>  
  
-   <span data-ttu-id="2a688-131">utilisation d'un ensemble de lignes d'un autre fournisseur comme valeur de paramètre table.</span><span class="sxs-lookup"><span data-stu-id="2a688-131">If a rowset from another provider is being used as the table-valued parameter value.</span></span>  
  
 <span data-ttu-id="2a688-132">Dans le modèle d'extraction des données, le consommateur fournit des données au fournisseur à la demande.</span><span class="sxs-lookup"><span data-stu-id="2a688-132">In the pull model, the consumer provides data on demand to the provider.</span></span> <span data-ttu-id="2a688-133">Utilisez cette approche si votre application comporte de nombreuses insertions de données et si les données d'ensembles de lignes de paramètres table en mémoire peuvent entraîner une sollicitation excessive de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2a688-133">Use this approach if your application has many data insertions, and table-valued parameter rowset data in memory would result in excessive memory access.</span></span> <span data-ttu-id="2a688-134">Si plusieurs fournisseurs OLE DB sont utilisés, le modèle d'extraction des données du consommateur permet à ce dernier de fournir n'importe quel objet d'ensemble de lignes en tant que valeur de paramètre table.</span><span class="sxs-lookup"><span data-stu-id="2a688-134">If multiple OLE DB providers are used, the consumer pull model enables the consumer to provide any rowset object as the table-valued parameter value.</span></span>  
  
 <span data-ttu-id="2a688-135">Pour utiliser le modèle d'extraction des données, les consommateurs doivent fournir leur propre implémentation d'un objet d'ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="2a688-135">To use the pull model, consumers have to provide their own implementation of a rowset object.</span></span> <span data-ttu-id="2a688-136">Lors de l'utilisation du modèle d'extraction des données avec les ensembles de lignes de paramètres table (CLSID_ROWSET_TVP), le consommateur doit agréger l'objet d'ensemble de lignes de paramètres table que le fournisseur expose via la méthode ITableDefinitionWithConstraints::CreateTableWithConstraints ou IOpenRowset::OpenRowset.</span><span class="sxs-lookup"><span data-stu-id="2a688-136">When using the pull model with table-valued parameter rowsets (CLSID_ROWSET_TVP), the consumer is required to aggregate the table-valued parameter rowset object that the provider exposes through the ITableDefinitionWithConstraints::CreateTableWithConstraints method or the IOpenRowset::OpenRowset method.</span></span> <span data-ttu-id="2a688-137">L'objet du consommateur est uniquement supposé substituer l'implémentation de l'interface IRowset.</span><span class="sxs-lookup"><span data-stu-id="2a688-137">The consumer object is only expected to override the IRowset interface implementation.</span></span> <span data-ttu-id="2a688-138">Vous devez substituer les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a688-138">You must override the following functions:</span></span>  
  
-   <span data-ttu-id="2a688-139">IRowset::GetNextRows</span><span class="sxs-lookup"><span data-stu-id="2a688-139">IRowset::GetNextRows</span></span>  
  
-   <span data-ttu-id="2a688-140">IRowset::AddRefRows</span><span class="sxs-lookup"><span data-stu-id="2a688-140">IRowset::AddRefRows</span></span>  
  
-   <span data-ttu-id="2a688-141">IRowset::GetData</span><span class="sxs-lookup"><span data-stu-id="2a688-141">IRowset::GetData</span></span>  
  
-   <span data-ttu-id="2a688-142">IRowset::ReleaseRows</span><span class="sxs-lookup"><span data-stu-id="2a688-142">IRowset::ReleaseRows</span></span>  
  
-   <span data-ttu-id="2a688-143">IRowset::RestartPosition</span><span class="sxs-lookup"><span data-stu-id="2a688-143">IRowset::RestartPosition</span></span>  
  
 <span data-ttu-id="2a688-144">Le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client lit une ou plusieurs lignes à la fois à partir de l'objet d'ensemble de lignes du consommateur afin de prendre en charge l'accès en continu dans les paramètres table.</span><span class="sxs-lookup"><span data-stu-id="2a688-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider will read one or more rows at a time from the consumer rowset object to support streaming behavior in table-valued parameters.</span></span> <span data-ttu-id="2a688-145">Par exemple, l'utilisateur peut disposer des données d'ensembles de lignes de paramètres table sur disque (et non en mémoire) et peut implémenter les fonctionnalités de lecture des données à partir du disque lorsque cela est requis par le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span><span class="sxs-lookup"><span data-stu-id="2a688-145">For example, the user might have the table-valued parameter rowset data on disk (not in memory) and might implement the functionality to read data from the disk when required by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider.</span></span>  
  
 <span data-ttu-id="2a688-146">Le consommateur communique son format de données au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client à l’aide de IAccessor :: CreateAccessor sur l’objet d’ensemble de lignes de paramètre table.</span><span class="sxs-lookup"><span data-stu-id="2a688-146">The consumer will communicate its data format to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider by using IAccessor::CreateAccessor on the table-valued parameter rowset object.</span></span> <span data-ttu-id="2a688-147">Lors de la lecture des données à partir de la mémoire tampon du consommateur, le fournisseur s'assure que toutes les colonnes accessibles en écriture et non définies par défaut sont disponibles à travers au moins un handle d'accesseur, et utilise les handles correspondants pour lire les données des colonnes.</span><span class="sxs-lookup"><span data-stu-id="2a688-147">When reading data from the consumer buffer, the provider verifies that all the writable and non-default columns are available through at least one accessor handle, and uses the corresponding handles to read columns data.</span></span> <span data-ttu-id="2a688-148">Pour éviter toute ambiguïté, il doit exister une correspondance unique entre une colonne d’ensemble de lignes de paramètres table et une liaison.</span><span class="sxs-lookup"><span data-stu-id="2a688-148">To avoid ambiguity, there should be a one-to-one correspondence between a table-valued parameter rowset column and a binding.</span></span> <span data-ttu-id="2a688-149">Les liaisons en double à la même colonne génèrent une erreur.</span><span class="sxs-lookup"><span data-stu-id="2a688-149">Duplicate bindings to the same column will result in an error.</span></span> <span data-ttu-id="2a688-150">Par ailleurs, chaque accesseur est supposé avoir le membre *iOrdinal* de DBBindings en séquence.</span><span class="sxs-lookup"><span data-stu-id="2a688-150">Also, each accessor is expected to have the *iOrdinal* member of DBBindings in sequence.</span></span> <span data-ttu-id="2a688-151">Il y a autant d’appels à IRowset::GetData que d’accesseurs par ligne. En outre, l’ordre des appels est basé sur l’ordre de la valeur *iOrdinal*, du plus petit au plus grand.</span><span class="sxs-lookup"><span data-stu-id="2a688-151">There will be as many calls to IRowset::GetData as the number of accessors per row, and the order of calls will be based on the order of *iOrdinal* value from lower to higher values.</span></span>  
  
 <span data-ttu-id="2a688-152">Le fournisseur est supposé implémenter la plupart des interfaces exposées par l'objet d'ensemble de lignes de paramètres table.</span><span class="sxs-lookup"><span data-stu-id="2a688-152">The provider is expected to implement most of the interfaces exposed by the table-valued parameter rowset object.</span></span> <span data-ttu-id="2a688-153">Le consommateur implémente un objet d’ensemble de lignes avec des interfaces minimales (IRowset).</span><span class="sxs-lookup"><span data-stu-id="2a688-153">The consumer will implement a rowset object with minimal interfaces (IRowset).</span></span> <span data-ttu-id="2a688-154">Avec une agrégation indifférenciée, les interfaces d'objets d'ensembles de lignes obligatoires restantes sont implémentées par l'objet d'ensemble de lignes de paramètres table.</span><span class="sxs-lookup"><span data-stu-id="2a688-154">Because of blind aggregation, the remaining mandatory rowset object interfaces will be implemented by the table-valued parameter rowset object.</span></span>  
  
 <span data-ttu-id="2a688-155">Pour tout autre objet d'ensemble de lignes, par exemple les objets d'ensembles de lignes obtenus pour n'importe quel fournisseur OLE DB, l'ensemble de lignes fourni par le consommateur doit implémenter toutes les interfaces d'objets d'ensembles de lignes obligatoires conformément à la spécification OLE DB.</span><span class="sxs-lookup"><span data-stu-id="2a688-155">For any other rowset object, such as rowset objects obtained for any OLE DB provider, the consumer-provided rowset must implement all the mandatory rowset object interfaces as specified in the OLE DB specification.</span></span>  
  
 <span data-ttu-id="2a688-156">Au moment de l'exécution, le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rappelle l'objet d'ensemble de lignes pour extraire les lignes et lire les données de colonne.</span><span class="sxs-lookup"><span data-stu-id="2a688-156">At the time of execution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider will call back to the rowset object to fetch rows and read column data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a688-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a688-157">See Also</span></span>  
 <span data-ttu-id="2a688-158">[Paramètres table &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="2a688-158">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="2a688-159">Utiliser les paramètres table &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="2a688-159">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  