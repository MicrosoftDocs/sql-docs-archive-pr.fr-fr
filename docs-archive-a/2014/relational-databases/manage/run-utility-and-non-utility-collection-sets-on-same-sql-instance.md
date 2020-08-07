---
title: Considérations relatives à l’exécution de jeux d’éléments de collecte de l’utilitaire et non-utilitaire sur la même instance de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67df2d65cc9da4026377e77c152c0d78f3749932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611066"
---
# <a name="considerations-for-running-utility-and-non-utility-collection-sets-on-the-same-instance-of-sql-server"></a>Considérations sur l'exécution de jeux d'éléments de collecte de l'utilitaire et non-utilitaire sur la même instance de SQL Server
  Le jeu d'éléments de collecte de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est pris en charge côte à côte avec les jeux d'éléments de collecte d'utilitaires non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Autrement dit, une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être surveillée par d'autres jeux d'éléments de collecte bien qu'elle soit membre d'un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, vous devez désactiver les fonctionnalités du jeu d'éléments de collecte de l'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrite dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Une fois l'instance inscrite avec l'UCP, vous pouvez redémarrer le jeu d'éléments de collecte de l'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Notez, toutefois, que tous les jeux d'éléments de collecte sur l'instance gérée téléchargeront leurs données dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Pour exécuter des jeux d'éléments de collecte d'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte avec des jeux d'éléments de collecte d'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , prenez en considération les points suivants :  
  
-   Les jeux d'éléments de collecte côte à côte sont pris en charge.  
  
-   Vous devez désactiver les collecteurs de données existants en inscrivant des instances dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour satisfaire aux exigences de validation, vous devez exécuter les procédures stockées suivantes sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de créer un UCP, et sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de l'inscrire dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Si vous n'exécutez pas ces procédures stockées avant de lancer l'Assistant Créer un UCP ou l'Assistant Ajouter une instance gérée, l'opération échouera.  
  
-   Vous devez utiliser l'UMDW (sysutility_mdw) de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour tous les jeux d'éléments de collecte sur une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](sql-server-utility-features-and-tasks.md)   
 [Configurer votre entrepôt de données de point de contrôle de l’utilitaire &#40;utilitaire SQL Server&#41;](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
