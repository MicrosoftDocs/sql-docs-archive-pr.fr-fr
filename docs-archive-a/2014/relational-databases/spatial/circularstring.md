---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601313"
---
# <a name="circularstring"></a>CircularString
  Un `CircularString` est une collection de zéro ou plusieurs segments d'arc de cercle continus. Un segment d'arc de cercle est un segment courbé défini par trois points dans un plan à deux dimensions ; le premier point doit être différent du troisième point. Si les trois points d'un segment d'arc de cercle sont colinéaires, le segment d'arc est traité comme un segment de ligne.

> [!IMPORTANT]
>  Pour obtenir une description détaillée et des exemples des nouvelles fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , y compris le `CircularString` sous-type, téléchargez le livre blanc [nouvelles fonctionnalités spatiales dans SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).

## <a name="circularstring-instances"></a>Instances CircularString
 Le dessin suivant montre des instances `CircularString` valides :

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a>Instances acceptées
 Une `CircularString` instance est acceptée si elle est vide ou si elle contient un nombre impair de points, n, où n > 1. Les instances `CircularString` suivantes sont acceptées.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 `@g3` montre que l'instance `CircularString` peut être acceptée, mais pas valide. La déclaration suivante d'instance de CircularString n'est pas acceptée. Cette déclaration lève une `System.FormatException`.

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a>Instances valides
 Une instance `CircularString` valide doit être vide ou avoir les attributs suivants :

-   Elle doit contenir au moins un segment d'arc de cercle (autrement dit, voir un minimum de trois points).

-   Le dernier point de terminaison de chaque segment d'arc de cercle de la séquence, à l'exception du dernier segment, doit correspondre au premier point de terminaison du segment suivant dans la séquence.

-   Elle doit comporter un nombre impair de points.

-   Elle ne peut pas se chevaucher sur un intervalle.

-   Bien que les instances `CircularString` puissent contenir des segments de ligne, ces segments de ligne doivent être définis par trois points colinéaires.

 L'exemple suivant montre des instances `CircularString` valides.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 Une instance `CircularString` doit contenir au moins deux segments d'arc de cercle pour définir un cercle complet. Une instance `CircularString` ne peut pas utiliser un seul segment d'arc de cercle (tel que (1 1, 3 1, 1 1)) pour définir un cercle complet. Utilisez (1 1, 2 2, 3 1, 2 0, 1 1) pour définir le cercle.

 L'exemple suivant montre des instances CircularString qui ne sont pas valides.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a>Instances avec des points colinéaires
 Dans les cas suivants un segment d'arc de cercle sera traité comme un segment de ligne :

-   lorsque les trois points sont colinéaires (par exemple, (1 3, 4 4, 7 5)) ;

-   lorsque le premier point et le point central sont les mêmes, mais que le troisième point est différent (par exemple, (1 3, 1 3, 7 5)) ;

-   lorsque le point central et le dernier point sont les mêmes, mais que le premier point est différent (par exemple, (1 3, 4 4, 4 4)).

## <a name="examples"></a>Exemples

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>R. Instanciation d'une instance géométrique à l'aide d'un CircularString vide
 Cet exemple indique comment créer une instance `CircularString` vide :

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. Instanciation d'une instance géométrique à l'aide d'un CircularString avec un segment d'arc de cercle
 L'exemple suivant indique comment créer une instance `CircularString` avec un segment d'arc de cercle unique (demi-cercle) :

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. Instanciation d'une instance géométrique à l'aide d'un CircularString avec plusieurs segments d'arc de cercle
 L'exemple suivant indique comment créer une instance `CircularString` avec plusieurs segments d'arc de cercle (cercle complet) :

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 Ce code produit la sortie suivante :

```
Circumference = 6.28319
```

 Comparez la sortie lorsque `LineString` est utilisé à la place de `CircularString` :

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 Ce code produit la sortie suivante :

```
Perimeter = 5.65685
```

 Notez que la valeur de l' `CircularString` exemple est proche de 2&#x03c0; (2 * pi), qui est la circonférence réelle du cercle.

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. Déclaration et instanciation d'une instance géométrique avec un CircularString dans la même instruction
 Cet extrait de code indique comment déclarer et instancier une instance `geometry` avec un `CircularString` dans la même instruction :

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. Instanciation d'une instance géographique avec un CircularString
 L'exemple suivant indique comment déclarer et instancier une instance `geography` avec un `CircularString` :

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. Instanciation d'une instance géométrique avec un CircularString qui est une ligne droite
 L'exemple suivant indique comment créer une instance `CircularString` qui est une ligne droite :

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble des types de données spatiales](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry type de données&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;Geometry type](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) de données&#41;STIsValid &#40;type de données [Geography&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) &#40;type de données geometry [&#41;STStartPoint](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [&#40;STEndPoint&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [type de](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) données geometry &#40;[STPointN&#41;type](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) de données geometry [&#40;STNumPoints](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [&#41;type de](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) données geometry STIsRing [&#40;STIsClosed](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md)


