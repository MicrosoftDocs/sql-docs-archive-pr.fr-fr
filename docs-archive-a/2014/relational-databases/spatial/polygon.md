---
title: Polygon | Microsoft Docs
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 040bb8a2558cc57b1b99a3ce984bec3c8925bc0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613912"
---
# <a name="polygon"></a>Polygone
  Un `Polygon` est une surface à deux dimensions stockée en tant que séquence de points définissant un anneau englobant extérieur et zéro ou plusieurs anneaux intérieurs.

## <a name="polygon-instances"></a>Instances Polygon
 Une instance `Polygon` peut être formée à partir d'un anneau qui possède au moins trois points distincts. Une instance `Polygon` peut également être vide.

 Les anneaux extérieurs et intérieurs d'un `Polygon` définissent sa limite. L'espace dans les anneaux définit l'intérieur du `Polygon`.

 L'illustration suivante montre des exemples d'instances `Polygon`.

 ![Exemples d'instances Polygon géométriques](../../database-engine/media/polygon.gif "Exemples d'instances Polygon géométriques")

 Comme indiqué par l'illustration :

1.  La Figure 1 est une instance `Polygon` dont la limite est définie par un anneau extérieur.

2.  La Figure 2 est une instance `Polygon` dont la limite est définie par un anneau extérieur et deux anneaux intérieurs. La zone à l'intérieur des anneaux intérieurs fait partie de l'extérieur de l'instance `Polygon`.

3.  La Figure 3 est une instance `Polygon` valide car ses anneaux intérieurs se croisent à un point tangent unique.

### <a name="accepted-instances"></a>Instances acceptées
 Les instances `Polygon` acceptées sont des instances qui peuvent être stockées dans une variable `geometry` ou `geography` sans lever d'exception. Les instances `Polygon` suivantes sont acceptées :

-   Instance `Polygon` vide

-   Instance `Polygon` qui a un anneau extérieur acceptable et zéro ou plusieurs anneaux intérieurs acceptables

 Les critères suivants sont nécessaires pour qu'un anneau soit acceptable.

-   L'instance `LineString` doit être acceptée.

-   L'instance `LineString` doit avoir au moins quatre points.

-   Les points de début et de fin de l'instance `LineString` doivent être les mêmes.

 L'exemple suivant illustre des instances `Polygon` acceptées.

```
DECLARE @g1 geometry = 'POLYGON EMPTY';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
```

 Comme le montrent `@g4` and `@g5`, une instance `Polygon` acceptée peut ne pas être une instance `Polygon` valide. `@g5` montre également qu’une instance Polygon doit contenir uniquement un anneau avec quatre points quelconques à accepter.

 Les exemples suivants lèvent une `System.FormatException` parce que les instances `Polygon` ne sont pas acceptées.

```
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';
```

 `@g1` n'est pas accepté parce que l'instance `LineString` pour l'anneau extérieur ne contient pas assez de points. `@g2` n'est pas accepté car le point de départ de l'instance `LineString` de l'anneau extérieur n'est pas identique au point de fin. L'exemple suivant a un anneau extérieur acceptable, mais l'anneau intérieur n'est pas acceptable. Cela lève également une `System.FormatException`.

```
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';
```

### <a name="valid-instances"></a>Instances valides
 Les anneaux intérieurs d'un `Polygon` peuvent se toucher eux-mêmes et l'un l'autre à des points tangents uniques, mais si les anneaux intérieurs d'un `Polygon` se croisent, l'instance n'est pas valide.

 L'exemple suivant montre des instances `Polygon` valides.

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 `@g3` est valide parce que les deux anneaux intérieurs se touchent à un point unique et ne se croisent pas l’un l’autre. L'exemple suivant montre des instances `Polygon` qui ne sont pas valides.

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();
```

 `@g1` n’est pas valide, car la boucle interne touche l’anneau intérieur à deux endroits. `@g2` n’est pas valide, car le deuxième anneau intérieur est à l’intérieur du premier anneau intérieur. `@g3` n’est pas valide, car les deux anneaux intérieurs se touchent au niveau de plusieurs points consécutifs. `@g4` n’est pas valide, car les parties intérieures des deux anneaux intérieurs se chevauchent. `@g5` n’est pas valide, car l’anneau extérieur n’est pas le premier anneau. `@g6` n’est pas valide, car la boucle n’a pas au moins trois points distincts.

## <a name="examples"></a>Exemples
 L’exemple suivant crée une instance `geometry``Polygon` simple avec un trou et un SRID 10.

```
DECLARE @g geometry;
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);
```

 Une instance non valide peut être entrée et convertie en une instance `geometry` valide. Dans l'exemple suivant d'un `Polygon`, les anneaux intérieurs et extérieurs se chevauchent et l'instance n'est pas valide.

```
DECLARE @g geometry;
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');
```

 Dans l'exemple suivant, l'instance non valide est rendue valide avec `MakeValid()`.

```
SET @g = @g.MakeValid();
SELECT @g.ToString();
```

 L'instance `geometry` retournée par l'exemple ci-dessus est un `MultiPolygon`.

```
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```

 Voici un autre exemple de conversion d'une instance non valide en instance geometry valide. Dans l'exemple suivant, l'instance `Polygon` a été créée à l'aide de trois points qui sont exactement les mêmes :

```sql
DECLARE @g geometry
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');
SET @g = @g.MakeValid();
SELECT @g.ToString()
```

 L'instance geometry retourné ci-dessus est un `Point(1 3)`.  Si le `Polygon` donné est `POLYGON((1 3, 1 5, 1 3, 1 3))` , alors `MakeValid()` retourne `LINESTRING(1 3, 1 5)`.

## <a name="see-also"></a>Voir aussi
 [STArea &#40;Geometry type de données&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;Geometry type de données&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry type de données&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;geometry type de données&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) type [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [de données](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) Geometry&#41;[STPointOnSurface &#40;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [&#41;type de](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) données geometry [&#40;](../spatial/polygon.md)


