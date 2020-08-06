---
title: Modifications importantes apportées aux fonctionnalités des outils d’administration de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0487b6ab0958e0b83d4e8e34be507b5b3211ac87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611334"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Dernières modifications apportées aux fonctionnalités des outils d'administration dans SQL Server 2014
  Cette rubrique décrit les dernières modifications apportées aux fonctionnalités des outils d'administration. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-sssql14"></a>Modifications avec rupture dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informations qui seront fournies par la suite.  
  
## <a name="breaking-changes-in-sssql11"></a>Modifications avec rupture dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a>Vous ne pouvez pas utiliser les outils de gestion de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] de SQL Server  
 Pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], utilisez les outils de gestion de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a>SMO a changé de version dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Le code développé avec SMO depuis [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ou les versions antérieures peut ne pas convenir sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] à mois d'y apporter des changements mineurs. Pour plus d’informations, consultez [Compatibilité descendante dans SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a>Modifications avec rupture dans SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
 [En savoir plus sur les modifications importantes apportées aux fonctionnalités des outils d’administration de SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
