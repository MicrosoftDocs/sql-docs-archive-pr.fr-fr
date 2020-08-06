---
title: Propriétés personnalisées de la destination SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a4ad136319e4ec6bd42c9da8dd8e99ab00cddadc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613064"
---
# <a name="sql-server-destination-custom-properties"></a><span data-ttu-id="d5adf-102">Propriétés personnalisées de la destination SQL Server</span><span class="sxs-lookup"><span data-stu-id="d5adf-102">SQL Server Destination Custom Properties</span></span>
  <span data-ttu-id="d5adf-103">La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispose à la fois de propriétés personnalisées et des propriétés communes à tous les composants de flux de données.</span><span class="sxs-lookup"><span data-stu-id="d5adf-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="d5adf-104">Le tableau suivant décrit les propriétés personnalisées de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d5adf-104">The following table describes the custom properties of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination.</span></span> <span data-ttu-id="d5adf-105">Toutes les propriétés sont en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="d5adf-105">All properties are read/write.</span></span>  
  
|<span data-ttu-id="d5adf-106">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="d5adf-106">Property name</span></span>|<span data-ttu-id="d5adf-107">Type de données</span><span class="sxs-lookup"><span data-stu-id="d5adf-107">Data Type</span></span>|<span data-ttu-id="d5adf-108">Description</span><span class="sxs-lookup"><span data-stu-id="d5adf-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="d5adf-109">AlwaysUseDefaultCodePage</span><span class="sxs-lookup"><span data-stu-id="d5adf-109">AlwaysUseDefaultCodePage</span></span>|<span data-ttu-id="d5adf-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-110">Boolean</span></span>|<span data-ttu-id="d5adf-111">Impose l’utilisation de la valeur de propriété DefaultCodePage.</span><span class="sxs-lookup"><span data-stu-id="d5adf-111">Forces the use of the DefaultCodePage property value.</span></span> <span data-ttu-id="d5adf-112">La valeur par défaut de cette propriété est `False`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-112">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="d5adf-113">BulkInsertCheckConstraints</span><span class="sxs-lookup"><span data-stu-id="d5adf-113">BulkInsertCheckConstraints</span></span>|<span data-ttu-id="d5adf-114">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-114">Boolean</span></span>|<span data-ttu-id="d5adf-115">Valeur qui spécifie si l'insertion en bloc vérifie les contraintes.</span><span class="sxs-lookup"><span data-stu-id="d5adf-115">A value that specifies whether the bulk insert checks constraints.</span></span> <span data-ttu-id="d5adf-116">La valeur par défaut de cette propriété est `True`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-116">The default value of this property is `True`.</span></span>|  
|<span data-ttu-id="d5adf-117">BulkInsertFireTriggers</span><span class="sxs-lookup"><span data-stu-id="d5adf-117">BulkInsertFireTriggers</span></span>|<span data-ttu-id="d5adf-118">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-118">Boolean</span></span>|<span data-ttu-id="d5adf-119">Valeur qui spécifie si l'insertion en bloc exécute des déclencheurs dans les tables.</span><span class="sxs-lookup"><span data-stu-id="d5adf-119">A value that specifies whether the bulk insert fires triggers on tables.</span></span> <span data-ttu-id="d5adf-120">La valeur par défaut de cette propriété est `False`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-120">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="d5adf-121">BulkInsertFirstRow</span><span class="sxs-lookup"><span data-stu-id="d5adf-121">BulkInsertFirstRow</span></span>|<span data-ttu-id="d5adf-122">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-122">Integer</span></span>|<span data-ttu-id="d5adf-123">Valeur qui spécifie la première ligne à insérer.</span><span class="sxs-lookup"><span data-stu-id="d5adf-123">A value that specifies the first row to insert.</span></span> <span data-ttu-id="d5adf-124">La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée</span><span class="sxs-lookup"><span data-stu-id="d5adf-124">The default value of this property is **-1**, which indicates that no value has been assigned</span></span>|  
|<span data-ttu-id="d5adf-125">BulkInsertKeepIdentity</span><span class="sxs-lookup"><span data-stu-id="d5adf-125">BulkInsertKeepIdentity</span></span>|<span data-ttu-id="d5adf-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-126">Boolean</span></span>|<span data-ttu-id="d5adf-127">Valeur qui spécifie si les valeurs peuvent être insérées dans des colonnes d'identité.</span><span class="sxs-lookup"><span data-stu-id="d5adf-127">A value that specifies whether values can be inserted into identity columns.</span></span> <span data-ttu-id="d5adf-128">La valeur par défaut de cette propriété est `False`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-128">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="d5adf-129">BulkInsertKeepNulls</span><span class="sxs-lookup"><span data-stu-id="d5adf-129">BulkInsertKeepNulls</span></span>|<span data-ttu-id="d5adf-130">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-130">Boolean</span></span>|<span data-ttu-id="d5adf-131">Valeur qui spécifie si l'insertion en bloc conserve les valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="d5adf-131">A value that specifies whether the bulk insert keeps Null values.</span></span> <span data-ttu-id="d5adf-132">La valeur par défaut de cette propriété est `False`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-132">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="d5adf-133">BulkInsertLastRow</span><span class="sxs-lookup"><span data-stu-id="d5adf-133">BulkInsertLastRow</span></span>|<span data-ttu-id="d5adf-134">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-134">Integer</span></span>|<span data-ttu-id="d5adf-135">Valeur qui spécifie la dernière ligne à insérer.</span><span class="sxs-lookup"><span data-stu-id="d5adf-135">A value that specifies the last row to insert.</span></span> <span data-ttu-id="d5adf-136">La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.</span><span class="sxs-lookup"><span data-stu-id="d5adf-136">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>|  
|<span data-ttu-id="d5adf-137">BulkInsertMaxErrors</span><span class="sxs-lookup"><span data-stu-id="d5adf-137">BulkInsertMaxErrors</span></span>|<span data-ttu-id="d5adf-138">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-138">Integer</span></span>|<span data-ttu-id="d5adf-139">Valeur qui spécifie le nombre d'erreurs au-delà duquel l'insertion en bloc s'arrête.</span><span class="sxs-lookup"><span data-stu-id="d5adf-139">A value that specifies the number of errors that can occur before the bulk insert stops.</span></span> <span data-ttu-id="d5adf-140">La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.</span><span class="sxs-lookup"><span data-stu-id="d5adf-140">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>|  
|<span data-ttu-id="d5adf-141">BulkInsertOrder</span><span class="sxs-lookup"><span data-stu-id="d5adf-141">BulkInsertOrder</span></span>|<span data-ttu-id="d5adf-142">String</span><span class="sxs-lookup"><span data-stu-id="d5adf-142">String</span></span>|<span data-ttu-id="d5adf-143">Noms des colonnes de tri.</span><span class="sxs-lookup"><span data-stu-id="d5adf-143">The names of the sort columns.</span></span> <span data-ttu-id="d5adf-144">Chaque colonne peut être triée par ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="d5adf-144">Each column can be sorted in ascending or descending order.</span></span> <span data-ttu-id="d5adf-145">En cas d'utilisation de plusieurs colonnes de tri, les noms des colonnes sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d5adf-145">If multiple sort columns are used, the column names are separated by commas.</span></span>|  
|<span data-ttu-id="d5adf-146">BulkInsertTableName</span><span class="sxs-lookup"><span data-stu-id="d5adf-146">BulkInsertTableName</span></span>|<span data-ttu-id="d5adf-147">String</span><span class="sxs-lookup"><span data-stu-id="d5adf-147">String</span></span>|<span data-ttu-id="d5adf-148">Table ou vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données dans laquelle les données sont copiées.</span><span class="sxs-lookup"><span data-stu-id="d5adf-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view in the database to which the data is copied.</span></span>|  
|<span data-ttu-id="d5adf-149">BulkInsertTablock</span><span class="sxs-lookup"><span data-stu-id="d5adf-149">BulkInsertTablock</span></span>|<span data-ttu-id="d5adf-150">Boolean</span><span class="sxs-lookup"><span data-stu-id="d5adf-150">Boolean</span></span>|<span data-ttu-id="d5adf-151">Valeur qui spécifie si la table est verrouillée lors de l'insertion en bloc.</span><span class="sxs-lookup"><span data-stu-id="d5adf-151">A value that specifies whether the table is locked during the bulk insert.</span></span> <span data-ttu-id="d5adf-152">La valeur par défaut de cette propriété est `True`.</span><span class="sxs-lookup"><span data-stu-id="d5adf-152">The default value of this property is `True`.</span></span>|  
|<span data-ttu-id="d5adf-153">DefaultCodePage</span><span class="sxs-lookup"><span data-stu-id="d5adf-153">DefaultCodePage</span></span>|<span data-ttu-id="d5adf-154">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-154">Integer</span></span>|<span data-ttu-id="d5adf-155">Page de codes à utiliser lorsque les informations de page de codes ne sont pas disponibles à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="d5adf-155">The code page to use when code page information is not available from the data source.</span></span>|  
|<span data-ttu-id="d5adf-156">MaxInsertCommitSize</span><span class="sxs-lookup"><span data-stu-id="d5adf-156">MaxInsertCommitSize</span></span>|<span data-ttu-id="d5adf-157">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-157">Integer</span></span>|<span data-ttu-id="d5adf-158">Valeur qui spécifie le nombre maximal de lignes à insérer dans un lot.</span><span class="sxs-lookup"><span data-stu-id="d5adf-158">A value that specifies the maximum number of rows to insert in a batch.</span></span> <span data-ttu-id="d5adf-159">Lorsque la valeur est nulle, toutes les lignes sont insérées dans un lot unique.</span><span class="sxs-lookup"><span data-stu-id="d5adf-159">When the value is zero, all rows are inserted in a single batch.</span></span>|  
|<span data-ttu-id="d5adf-160">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="d5adf-160">Timeout</span></span>|<span data-ttu-id="d5adf-161">Integer</span><span class="sxs-lookup"><span data-stu-id="d5adf-161">Integer</span></span>|<span data-ttu-id="d5adf-162">Valeur qui spécifie le nombre de secondes pendant lesquelles la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] patiente avant de s'arrêter si aucune donnée disponible ne peut être insérée.</span><span class="sxs-lookup"><span data-stu-id="d5adf-162">A value that specifies the number of seconds the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination waits before termination if there is no data available for insertion.</span></span> <span data-ttu-id="d5adf-163">Une valeur égale à 0 signifie que la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’expire pas. La valeur par défaut de cette propriété est 30.</span><span class="sxs-lookup"><span data-stu-id="d5adf-163">A value of 0 means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination will not time out. The default value of this property is 30.</span></span>|  
  
 <span data-ttu-id="d5adf-164">Les entrées et les colonnes d’entrée de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’ont pas de propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d5adf-164">The input and the input columns of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination have no custom properties.</span></span>  
  
 <span data-ttu-id="d5adf-165">Pour plus d’informations, consultez [Destination SQL Server](sql-server-destination.md).</span><span class="sxs-lookup"><span data-stu-id="d5adf-165">For more information, see [SQL Server Destination](sql-server-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5adf-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5adf-166">See Also</span></span>  
 [<span data-ttu-id="d5adf-167">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="d5adf-167">Common Properties</span></span>](../common-properties.md)  
  
  