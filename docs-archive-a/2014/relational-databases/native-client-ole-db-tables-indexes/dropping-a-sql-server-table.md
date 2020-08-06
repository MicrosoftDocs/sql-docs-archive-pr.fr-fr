---
title: Suppression d'une table SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d7bea98a3afcd0022f66117b6bde2d968a866b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611038"
---
# <a name="dropping-a-sql-server-table"></a><span data-ttu-id="9b7d2-102">Suppression d'une table SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b7d2-102">Dropping a SQL Server Table</span></span>
  <span data-ttu-id="9b7d2-103">Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client expose la fonction **ITableDefinition ::D roptable** .</span><span class="sxs-lookup"><span data-stu-id="9b7d2-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropTable** function.</span></span> <span data-ttu-id="9b7d2-104">Cela permet aux consommateurs de supprimer une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="9b7d2-104">This allows consumers to remove a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from a database.</span></span>  
  
 <span data-ttu-id="9b7d2-105">Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*.</span><span class="sxs-lookup"><span data-stu-id="9b7d2-105">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="9b7d2-106">Le membre *eKind* de *pTableID* doit être DBKIND_NAME.</span><span class="sxs-lookup"><span data-stu-id="9b7d2-106">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7d2-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b7d2-107">See Also</span></span>  
 [<span data-ttu-id="9b7d2-108">Tables et index</span><span class="sxs-lookup"><span data-stu-id="9b7d2-108">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  