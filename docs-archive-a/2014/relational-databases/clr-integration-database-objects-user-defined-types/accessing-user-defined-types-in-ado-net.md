---
title: Accès aux types définis par l’utilisateur dans ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612400"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accès aux types définis par l'utilisateur dans ADO.NET
  Les types définis par l’utilisateur (UDT) sont écrits à l’aide de l’un des langages pris en charge par le [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Common Language Runtime (CLR) qui produit un code vérifiable. notamment [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Les types définis par l'utilisateur permettent de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les données sont exposées en tant que membres publics d'une classe ou d'une structure .NET Framework, et les comportements sont définis par des méthodes de la classe ou de la structure. Un type UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un lot [!INCLUDE[tsql](../../includes/tsql-md.md)] ou en tant qu’argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Dans ADO.NET, le fournisseur `System.Data.SqlClient` expose les types définis par l'utilisateur des manières suivantes :  
  
-   Par le biais du `System.Data.SqlClient.SqlDataReader` en tant qu'objet.  
  
-   Par le biais du `SqlDataReader` en tant qu'octets bruts.  
  
-   En tant que paramètre d'un objet `System.Data.SqlClient.SqlParameter`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extraction de données UDT](accessing-user-defined-types-retrieving-udt-data.md)  
 Décrit comment récupérer les données UDT et comment spécifier des paramètres.  
  
 [Mise à jour de colonnes UDT avec DataAdapters](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Décrit comment utiliser les types définis par l'utilisateur dans `DataSets` et comment mettre à jour les données UDT à l'aide de `DataAdapters`.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l'utilisateur](clr-user-defined-types.md)  
  
  
