---
title: Éditeur de liste de propriétés de recherche | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c68ec986e2c6f4f53dfec7f188ba2a120532ae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604119"
---
# <a name="search-property-list-editor"></a>Éditeur de listes de propriétés de recherche
  Utilisez cette boîte de dialogue pour ajouter ou supprimer des propriétés de recherche dans une liste de propriétés de recherche.  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>Pour utiliser SQL Server Management Studio pour gérer des listes de propriétés de recherche  
 Pour plus d’informations sur la création, l’affichage ou la suppression d’une liste de propriétés de recherche, ainsi que sur la configuration d’un index de recherche en texte intégral pour la recherche de propriétés, consultez [Rechercher des propriétés de document avec des listes de propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="options"></a>Options  
 **Nom de la propriété**  
 Spécifiez le nom à utiliser pour identifier la propriété dans les requêtes de texte intégral. Un nom de propriété peut contenir des espaces internes. La longueur maximale de **Property Name** est de 256 caractères. Ce nom peut être un nom convivial, tel que « Auteur » ou « Domicile », ou ce peut être le nom canonique Windows de la propriété, tel que `System.Author` ou `System.Contact.HomeAddress`. **Property Name** doit identifier la propriété de manière unique dans le jeu de propriétés.  
  
 Les développeurs utilisent le nom de la propriété pour identifier la propriété dans le prédicat [CONTAINS](/sql/t-sql/queries/contains-transact-sql) . Par conséquent, lors de l'ajout d'une propriété, il est important de spécifier une valeur qui représente la propriété de manière significative.  
  
 **GUID du jeu de propriétés**  
 Spécifiez l'identificateur du jeu de propriétés auquel appartient la propriété. Il s'agit d'un identificateur global unique (GUID). Un jeu de propriétés est un groupe de propriétés connexes du point du vue logique. Pour plus d'informations sur l'obtention de cette valeur, consultez les « Notes », dans la suite de cette rubrique.  
  
 **ID entier de propriété**  
 Spécifiez l'identificateur entier de la propriété. Cette valeur pré-assignée est un entier positif qui est unique dans le jeu de propriétés. Pour plus d'informations sur l'obtention de cette valeur, consultez les « Notes », dans la suite de cette rubrique.  
  
> [!NOTE]  
>  Les propriétés du document qui utilisent des identificateurs de chaîne ne sont pas prises en charge par la recherche en texte intégral.  
  
 **Description de la propriété**  
 Éventuellement, spécifiez une description de la propriété. Il s'agit d'une chaîne comprenant 512 caractères maximum. Par exemple, une description peut contenir des informations relatives au jeu de propriétés de la propriété ou des informations à propos d'une propriété dont le nom n'est pas très explicite.  
  
## <a name="remarks"></a>Notes  
 Pour ajouter une propriété de recherche à une liste de propriétés de recherche, vous devez spécifier l'identificateur global unique (GUID) du jeu de propriétés auquel la propriété appartient, ainsi que l'identificateur entier de la propriété. Une combinaison donnée de ces informations doit être unique dans une liste de propriétés de recherche donnée. Si vous essayez d'ajouter une combinaison existante, l'opération échoue et génère une erreur. Cela signifie que vous ne pouvez configurer qu'un seul nom pour une propriété donnée.  
  
 La description de la propriété est facultative.  
  
 **Pour configurer une liste de propriétés de recherche pour un index de recherche en texte intégral**  
  
-   [Rechercher les propriétés du document à l’aide des listes des propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a>Autorisations  
 Consultez la page [ALTER Search Property LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)   
 [Rechercher des propriétés de document avec des listes de propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
