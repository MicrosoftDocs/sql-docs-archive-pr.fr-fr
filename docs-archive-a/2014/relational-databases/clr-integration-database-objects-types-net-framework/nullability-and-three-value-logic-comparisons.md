---
title: Possibilité de valeur null et comparaisons logiques de trois valeurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709632"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Possibilité de valeur Null et comparaisons logiques de trois valeurs
  Si vous avez une bonne connaissance des types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous trouverez une sémantique et une précision semblables dans l'espace de noms `System.Data.SqlTypes` dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Il existe toutefois certaines différences, dont les principales sont décrites dans cette rubrique.  
  
## <a name="null-values"></a>Valeurs Null  
 L'une des principales différences entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les types de données CLR (Common Language Runtime) natifs porte sur le fait que ceux-ci n'autorisent pas les valeurs Null, tandis que ceux-là fournissent une sémantique Null complète.  
  
 Les comparaisons sont affectées par les valeurs Null. Lors de la comparaison de deux valeurs x et y, si x ou y a la valeur Null, certaines comparaisons logiques évaluent à une valeur UNKNOWN plutôt que true ou false.  
  
## <a name="sqlboolean-data-type"></a>Type de données SqlBoolean  
 L'espace de noms `System.Data.SqlTypes` introduit un type `SqlBoolean` pour représenter cette logique à 3 valeurs. Les comparaisons entre des `SqlTypes` retournent un type de valeur `SqlBoolean`. La valeur UNKNOWN est représentée par la valeur Null du type `SqlBoolean`. Les propriétés `IsTrue`, `IsFalse` et `IsNull` sont fournies afin de vérifier la valeur d'un type `SqlBoolean`.  
  
## <a name="operations-functions-and-null-values"></a>Opérations, fonctions et valeurs Null  
 Tous les opérateurs arithmétiques (+,-, \* ,/,%), les opérateurs de bits (~, & et |) et la plupart des fonctions retournent Null si l’un des opérandes ou arguments de `SqlTypes` est null. La propriété `IsNull` retourne toujours une valeur true ou false.  
  
## <a name="precision"></a>Précision  
 Les types de données décimaux dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ont des valeurs maximales différentes de celles des types de données numériques et décimaux dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De plus, dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], les types de données décimaux supposent la précision maximale. Dans le CLR pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en revanche, `SqlDecimal` fournit les mêmes échelle et précision maximale, ainsi que la même sémantique que le type de données décimal dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Détection de dépassement de capacité  
 Dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], l'addition de deux très grands nombres peut ne pas lever d'exception. Au lieu de cela, si aucun opérateur de contrôle n'a été utilisé, le résultat retourné peut être « enveloppé » en tant qu'entier négatif. Dans `System.Data.SqlTypes`, des exceptions sont levées pour toutes les erreurs de dépassement de capacité et de dépassement de précision et pour les erreurs de division par zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
