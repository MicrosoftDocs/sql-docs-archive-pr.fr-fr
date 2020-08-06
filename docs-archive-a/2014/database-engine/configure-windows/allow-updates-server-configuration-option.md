---
title: allow updates (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7e3ede317509a2044be90635db46e30a932af66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611301"
---
# <a name="allow-updates-server-configuration-option"></a><span data-ttu-id="4023d-102">allow updates (option de configuration de serveur)</span><span class="sxs-lookup"><span data-stu-id="4023d-102">allow updates Server Configuration Option</span></span>
  <span data-ttu-id="4023d-103">Cette option est toujours présente dans la procédure stockée **sp_configure** , bien que ses fonctionnalités ne soient pas disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4023d-103">This option is still present in the **sp_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4023d-104">Le paramètre n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="4023d-104">The setting has no effect.</span></span> <span data-ttu-id="4023d-105">Les mises à jour directes des tables système ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="4023d-105">Direct updates to the system tables are not supported.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="4023d-106">La modification de l'option **allow updates** provoquera l'échec de l'instruction RECONFIGURE.</span><span class="sxs-lookup"><span data-stu-id="4023d-106">Changing the **allow updates** option will cause the RECONFIGURE statement to fail.</span></span> <span data-ttu-id="4023d-107">Les modifications de l'option **allow updates** doivent être supprimées de tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="4023d-107">Changes to the **allow updates** option should be removed from all scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4023d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4023d-108">See Also</span></span>  
 [<span data-ttu-id="4023d-109">Options de configuration de serveur &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4023d-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  