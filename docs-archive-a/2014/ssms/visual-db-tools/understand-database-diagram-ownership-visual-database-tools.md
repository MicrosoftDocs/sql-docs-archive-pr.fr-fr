---
title: Comprendre la propriété du diagramme de base de données (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21d0f6f006328d8843bbbe12ee066a8564fb722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703672"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Comprendre la propriété du diagramme de base de données (Visual Database Tools)
  Pour utiliser le Concepteur de diagrammes de base de données, il doit d’abord être installé par un membre du rôle db_owner (rôle de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) pour contrôler l’accès aux diagrammes. Chaque schéma a un seul propriétaire : l'utilisateur qui l'a créé. Pour plus d’informations sur la configuration de la création de diagrammes, consultez [configurer le concepteur de schémas de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Voici quelques points à retenir au sujet de la propriété des schémas :  
  
-   Même si tout utilisateur ayant accès à une base de données peut créer un schéma, lorsque ce dernier est créé, les seuls utilisateurs autorisés à le consulter sont son créateur et tout membre du rôle db_owner.  
  
-   La propriété de schémas ne peut être transférée qu'à des membres du rôle db_owner. Cela n'est possible que si l'ancien propriétaire du schéma a été supprimé de la base de données.  
  
-   Si le propriétaire d'un schéma a été supprimé de la base de données, le schéma reste dans la base de données jusqu'à ce qu'un membre du rôle db_owner tente de l'ouvrir. À ce stade, le membre du rôle db_owner peut choisir de prendre possession du schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des schémas de base de données &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [Configurer le Concepteur de diagrammes de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
