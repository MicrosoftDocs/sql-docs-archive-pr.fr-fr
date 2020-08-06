---
title: Obtenir les champs pour tous les événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 01d98e827121a0c47111dd601c6e1772f796849d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701579"
---
# <a name="get-the-fields-for-all-events"></a>Obtenir les champs pour tous les événements
  Pour accomplir cette tâche, vous devez utiliser l'éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Une fois que les instructions de cette procédure sont exécutées, l’onglet **Résultats** de l’éditeur de requêtes affiche les colonnes suivantes :  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 Vous pouvez utiliser les informations précédentes lors de la configuration des sessions d'événement qui utilisent la cible de création de compartiments. Pour plus d'informations, consultez [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Avant de créer une session des événements étendus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , il est utile d'obtenir des informations à propos des champs associés aux événements.  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a>Pour obtenir les champs de tous les événements à l'aide de l'éditeur de requête  
  
-   Dans l'éditeur de requêtes, émettez les instructions suivantes.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
