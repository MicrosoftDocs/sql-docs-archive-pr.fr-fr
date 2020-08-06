---
title: Extraction d’une seule ligne avec IRow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612784"
---
# <a name="fetching-a-single-row-with-irow"></a><span data-ttu-id="9e1e2-102">Extraction d'une ligne unique avec IRow</span><span class="sxs-lookup"><span data-stu-id="9e1e2-102">Fetching a Single Row with IRow</span></span>
  <span data-ttu-id="9e1e2-103">L’implémentation de l’interface **IRow** dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client est simplifiée pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-103">The **IRow** interface implementation in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is simplified to increase performance.</span></span> <span data-ttu-id="9e1e2-104">**IRow** autorise l’accès direct aux colonnes d’un objet ligne unique.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-104">**IRow** allows direct access to columns of a single row object.</span></span> <span data-ttu-id="9e1e2-105">Si vous savez à l’avance que le résultat d’une exécution de commande produira une ligne exactement, **IRow** récupèrera les colonnes de cette ligne.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-105">If you know beforehand that the result of a command execution will produce exactly one row, **IRow** will retrieve the columns of that row.</span></span> <span data-ttu-id="9e1e2-106">Si le jeu de résultats comprend plusieurs lignes, **IRow** exposera uniquement la première ligne.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-106">If the result set includes multiple rows, **IRow** will expose only the first row.</span></span>  
  
 <span data-ttu-id="9e1e2-107">L’implémentation **IRow** ne permet aucune navigation de la ligne.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-107">The **IRow** implementation does not allow any navigation of the row.</span></span> <span data-ttu-id="9e1e2-108">Chaque colonne dans la ligne est accédée une seule fois, à une exception près : une colonne peut être accédée une fois pour rechercher la taille de colonne et une autre fois pour extraire les données.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-108">Each column in the row is accessed only one time with one exception: A column can be accessed one time to find the column size and again to fetch the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e1e2-109">**IRow::Open** prend uniquement en charge l’ouverture des types d’objets DBGUID_STREAM et DBGUID_NULL.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-109">**IRow::Open** supports only DBGUID_STREAM and DBGUID_NULL type of objects to be opened.</span></span>  
  
 <span data-ttu-id="9e1e2-110">Pour obtenir un objet ligne à l’aide de la méthode **ICommand::Execute**, IID_IRow doit être passé.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-110">To obtain a row object using **ICommand::Execute** method, IID_IRow must be passed.</span></span> <span data-ttu-id="9e1e2-111">L’interface **IMultipleResults** doit être utilisée pour gérer plusieurs jeux de résultats.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-111">The **IMultipleResults** interface must be used to handle multiple result sets.</span></span> <span data-ttu-id="9e1e2-112">**IMultipleResults** prend en charge **IRow** et **IRowset**.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-112">**IMultipleResults** supports **IRow** and **IRowset**.</span></span> <span data-ttu-id="9e1e2-113">**IRowset** est utilisé pour les opérations en bloc.</span><span class="sxs-lookup"><span data-stu-id="9e1e2-113">**IRowset** is used for bulk operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e1e2-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9e1e2-114">In This Section</span></span>  
  
-   [<span data-ttu-id="9e1e2-115">Utilisation d'IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="9e1e2-115">Using IRow::GetColumns</span></span>](using-irow-getcolumns.md)  
  
-   [<span data-ttu-id="9e1e2-116">Extraction de données BLOB à l'aide d'IRow</span><span class="sxs-lookup"><span data-stu-id="9e1e2-116">Fetching BLOB Data Using IRow</span></span>](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e1e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e1e2-117">See Also</span></span>  
 [<span data-ttu-id="9e1e2-118">Ensembles de lignes</span><span class="sxs-lookup"><span data-stu-id="9e1e2-118">Rowsets</span></span>](rowsets.md)  
  
  