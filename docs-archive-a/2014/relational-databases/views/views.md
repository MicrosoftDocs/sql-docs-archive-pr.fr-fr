---
title: Vues | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], about views
ms.assetid: ada83c28-e8b7-45d9-b53c-b3d67c8820c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: c7332506666b11e96255c2b903d70b232ae4efa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599841"
---
# <a name="views"></a>Les vues
  Une vue est une table virtuelle dont le contenu est défini par une requête. À l'instar d'une table, une vue est un ensemble de colonnes et de lignes nommées de données. À moins d'être indexée, elle n'existe pas en tant qu'ensemble de valeurs de données stocké dans une base de données. Les lignes et les colonnes de données proviennent de tables référencées dans la requête qui définit la vue et sont produites dynamiquement lorsque la vue est référencée.  
  
 Une vue fait office de filtre sur les tables sous-jacentes qui y sont référencées. La requête qui définit la vue peut émaner d'une ou de plusieurs tables ou d'autres vues de la base de données en cours ou d'autres bases de données. Les requêtes distribuées peuvent également être employées pour définir des vues qui utilisent des données provenant de plusieurs sources hétérogènes. Cela est particulièrement utile si vous souhaitez combiner des données de structure similaire issues de différents serveurs, chacun hébergeant des données relatives à une région différente de votre organisation.  
  
 Vous pouvez recourir aux vues pour affiner, simplifier et personnaliser la perception de la base de données par chaque utilisateur. Les vues peuvent être utilisées comme mécanismes de sécurité en permettant aux utilisateurs d'accéder aux données par le biais de la vue, sans leur accorder d'autorisations qui leur permettraient d'accéder directement aux tables de base sous-jacentes de la vue. Les vues peuvent servir à fournir une interface de compatibilité descendante afin d'émuler une table qui existait mais dont le schéma a changé. Cependant, vous pouvez aussi y recourir pour copier des données vers et à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d'améliorer les performances et de partitionner les données.  
  
## <a name="types-of-views"></a>Types de vues  
 Outre le rôle standard des vues de base définies par l'utilisateur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] met à votre disposition les types de vues suivants, qui remplissent une fonction particulière dans une base de données.  
  
 Vues indexées  
 Une vue indexée est une vue qui a été matérialisée, Cela signifie que la définition de la vue a été calculée et que les données résultantes sont stockées comme dans une table. Vous indexez une vue en créant un index cluster unique sur celle-ci. Les vues indexées peuvent améliorer considérablement les performances de certains types de requêtes. Les vues indexées sont les plus efficaces pour les requêtes qui agrègent de nombreuses lignes. Elles ne conviennent pas à des datasets sous-jacents qui sont fréquemment mis à jour.  
  
 Vues partitionnées  
 Une vue partitionnée joint horizontalement les données partitionnées d'un ensemble de tables membres sur un ou plusieurs serveurs. Les données sont ainsi affichées comme si elles provenaient d'une seule table. Une vue qui joint des tables membres sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est une vue partitionnée locale.  
  
 Vues système  
 Les vues système exposent les métadonnées de catalogue. Vous pouvez utiliser des vues système pour retourner des informations sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les objets définis dans l'instance. Par exemple, vous pouvez interroger la vue de catalogue sys.databases pour retourner des informations sur les bases de données définies par l’utilisateur disponibles dans l’instance. Pour plus d’informations, consultez [Vues système &#40;Transact-SQL&#41;](/sql/t-sql/language-reference)  
  
## <a name="common-view-tasks"></a>Tâches courantes associées aux vues  
 Le tableau suivant fournit des liens vers les tâches couramment associées à la création ou à la modification d'une vue.  
  
|Tâches associées aux vues|Rubrique|  
|----------------|-----------|  
|Explique comment créer une vue.|[Créer des vues](../views/views.md)|  
|Explique comment créer une vue indexée.|[Créer des vues indexées](../views/create-indexed-views.md)|  
|Explique comment modifier la définition de la vue.|[Modifier des vues](../views/modify-views.md)|  
|Explique comment modifier des données par le biais d'une vue.|[Modifier les données par l’intermédiaire d’une vue](../views/modify-data-through-a-view.md)|  
|Explique comment supprimer une vue.|[Supprimer des vues](../views/delete-views.md)|  
|Explique comment retourner des informations sur une vue comme la définition de la vue.|[Obtenir des informations au sujet d’une vue](../views/get-information-about-a-view.md)|  
|Explique comment renommer une vue.|[Renommer des vues](../views/rename-views.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des vues sur les colonnes XML](../xml/create-views-over-xml-columns.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)  
  
  
