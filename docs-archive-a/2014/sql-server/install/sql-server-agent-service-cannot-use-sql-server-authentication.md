---
title: Le service SQL Server Agent ne peut pas utiliser l’authentification SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611509"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a><span data-ttu-id="7b099-102">Le service SQL Server Agent ne peut pas utiliser l'authentification SQL Server</span><span class="sxs-lookup"><span data-stu-id="7b099-102">SQL Server Agent Service cannot use SQL Server Authentication</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b099-103">Agent prend en charge uniquement l'authentification Windows lorsque le service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se connecte à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b099-103">Agent only supports Windows Authentication when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="7b099-104">Composant</span><span class="sxs-lookup"><span data-stu-id="7b099-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b099-105">Agent</span><span class="sxs-lookup"><span data-stu-id="7b099-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="7b099-106">Description</span><span class="sxs-lookup"><span data-stu-id="7b099-106">Description</span></span>  
 <span data-ttu-id="7b099-107">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut uniquement se connecter à la base de données en utilisant l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="7b099-107">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can only log on to the database using Windows Authentication.</span></span> <span data-ttu-id="7b099-108">Cela signifie que le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b099-108">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="7b099-109">Pour plus d'informations, consultez les rubriques « Sécurité pour l'administration automatique » et « Implémentation de la sécurité de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b099-109">For more information, see the topics "Security for Automatic Administration" and "Implementing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Security" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b099-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b099-110">See Also</span></span>  
 [<span data-ttu-id="7b099-111">Problèmes de mise à niveau de l'Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="7b099-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  