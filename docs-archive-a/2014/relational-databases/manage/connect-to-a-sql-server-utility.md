---
title: Se connecter à un utilitaire SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602136"
---
# <a name="connect-to-a-sql-server-utility"></a>Se connecter à un utilitaire SQL Server
  Avant de vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez créer un point de contrôle de l’utilitaire (UCP). Pour plus d’informations, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](sql-server-utility-features-and-tasks.md).

 Pour afficher et gérer l’intégrité des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) pour vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

 Pour vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via SSMS :

1.  Lancez SSMS.

2.  Dans SSMS, connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

3.  Cliquez sur **Affichage** , puis **Explorateur de l’utilitaire**.

4.  Dans le volet Navigation de l’Explorateur de l’utilitaire, cliquez sur ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Se connecter à l’utilitaire**.

5.  Dans la boîte de dialogue **Se connecter au serveur** , spécifiez le nom de l’instance de l’UCP, puis cliquez **Se connecter**.

6.  Affichez le volet Navigation de l’Explorateur de l’utilitaire pour consulter une arborescence des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’UCP.

 La création d’un UCP vous connecte également à l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Créer un point de contrôle de l’utilitaire SQL Server &#40;utilitaire SQL Server&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)

## <a name="see-also"></a>Voir aussi
 [Utilitaire SQL Server affichage des fonctionnalités et des tâches Resource Health les résultats de](sql-server-utility-features-and-tasks.md) la [stratégie &#40;utilitaire SQL Server&#41;](view-resource-health-policy-results-sql-server-utility.md)


