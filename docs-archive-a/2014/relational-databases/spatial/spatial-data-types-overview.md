---
title: Présentation des types de données spatiales | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c0548d974e83bfe2b1e103d4458b17078fba8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703980"
---
# <a name="spatial-data-types-overview"></a>Présentation des types de données spatiales
  Il existe deux types de données spatiales. Le type de données `geometry` prend en charge les données planaires, ou euclidiennes (monde en deux dimensions). Le type de données `geometry` se conforme à la fois à la spécification Open Geospatial Consortium (OGC) Simple Features for SQL version 1.1.0. et à la norme SQL MM (norme ISO).

 De plus, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le type de données `geography`, qui stocke des données ellipsoïdes (monde sphérique), telles que des coordonnées GPS de latitude et de longitude.

> [!IMPORTANT]
>  Pour obtenir une description détaillée et des exemples des nouvelles fonctionnalités spatiales dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], notamment les optimisations des types de données spatiales, téléchargez le livre blanc [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407)(Nouvelles fonctions spatiales dans SQL Server nom de code « Denali »).

##  <a name="spatial-data-objects"></a><a name="objects"></a> Objets de données spatiales
 Les types de données `geometry` et `geography` prennent en charge seize objets de données spatiales, ou types d'instances. Toutefois, seuls onze de ces types d’instances sont *instanciables*; vous pouvez créer et utiliser ces instances (ou les instancier) dans une base de données. Ces instances dérivent certaines propriétés de leurs types de données parents qui les distinguent comme `Points` , **LineStrings, CircularStrings**,, `CompoundCurves` `Polygons` , `CurvePolygons` ou comme `geometry` instances multiples ou `geography` dans un `GeometryCollection` . Le type `Geography` possède un type d'instance supplémentaire, `FullGlobe`.

 La figure ci-dessous représente la hiérarchie `geometry` sur laquelle les types de données `geometry` et `geography` sont basés. Les types instanciables de `geometry` et `geography` sont indiqués en bleu.

 ![Hiérarchie du type geometry](../../database-engine/media/geom-hierarchy.gif "Hiérarchie du type geometry")

 Comme l’indique la figure, les dix types instanciables `geometry` des `geography` types de données et sont `Point` , `MultiPoint` , `LineString` , `CircularString` , `MultiLineString` , `CompoundCurve` , `Polygon` ,, `CurvePolygon` `MultiPolygon` et `GeometryCollection` . Il existe un type instanciable supplémentaire pour le type de données geography : `FullGlobe`. Les `geometry` `geography` types et peuvent reconnaître une instance spécifique tant qu’il s’agit d’une instance bien formée, même si l’instance n’est pas définie explicitement. Par exemple, si vous définissez une `Point` instance explicitement à l’aide de la méthode STPointFromText (), et que vous `geometry` `geography` Identifiez l’instance comme un `Point` , tant que l’entrée de la méthode est correctement formée. Si vous définissez la même instance à l'aide de la méthode `STGeomFromText()`, les types de données `geometry` et `geography` reconnaissent l'instance comme un `Point`.

 Les sous-types des types geometry et geography sont divisés en types simples et de collection.  Certaines méthodes, telles que `STNumCurves()` , fonctionnent uniquement avec les types simples.

 Exemples de types simples :

-   [Point](../spatial/point.md)

-   [LineString](../spatial/linestring.md)

-   [CircularString](../spatial/circularstring.md)

-   [CompoundCurve](../spatial/compoundcurve.md)

-   [Polygon](../spatial/polygon.md)

-   [CurvePolygon](../spatial/curvepolygon.md)

 Exemples de types de collection :

-   [MultiPoint](../spatial/multipoint.md)

-   [MultiLineString](../spatial/multilinestring.md)

-   [MultiPolygon](../spatial/multipolygon.md)

-   [GeometryCollection](../spatial/geometrycollection.md)


##  <a name="differences-between-the-geometry-and-geography-data-types"></a><a name="differences"></a> Différences entre les types de données geometry et geography
 Les deux types de données spatiales se comportent souvent à peu près de la même façon, mais il existe des différences clés dans la façon dont les données sont stockées et manipulées.

### <a name="how-connecting-edges-are-defined"></a>Mode de définition des arêtes de connexion
 Les données de définition concernant les types `LineString` et `Polygon` sont uniquement des sommets.  L'arête reliant deux sommets dans un type geometry forme une ligne droite.  Toutefois, l'arête reliant deux sommets dans un type geography est un grand arc elliptique court entre les deux sommets.  Une grande ellipse correspond à l'intersection de l'ellipsoïde avec un plan passant par son centre tandis qu'un grand arc elliptique est un segment d'arc sur la grande ellipse.

### <a name="how-circular-arc-segments-are-defined"></a>Mode de définition des segments d'arc de cercle
 Les segments d'arc de cercle pour les types geography sont définis sur le plan des coordonnées cartésiennes XY (les valeurs Z sont ignorées). Les segments d'arc de cercle pour les types geography sont définis par des segments de courbe sur une sphère de référence. Toute parallèle sur la sphère de référence peut être définie par deux arcs de cercle complémentaires où les points des deux arcs ont un angle de latitude constant.

### <a name="measurements-in-spatial-data-types"></a>Mesures dans les types de données spatiales
 Dans le système planaire, ou monde en deux dimensions, les mesures de distances et de surfaces sont données dans la même unité de mesure que les coordonnées. Avec le type de données `geometry`, la distance entre (2, 2) et (5, 6) est 5 unités, quelles que soient les unités utilisées.

 Dans le système ellipsoïdal, ou monde sphérique, les coordonnées sont données en degrés de latitude et de longitude. Toutefois, les longueurs et surfaces sont généralement mesurées en mètres et en mètres carrés, bien que la mesure puisse dépendre de l'identificateur de référence spatiale (SRID) de l'instance `geography`. L'unité de mesure la plus courante pour le type de données `geography` est le mètre.

### <a name="orientation-of-spatial-data"></a>Orientation des données spatiales
 Dans le système planaire, l'orientation d'anneau d'un polygone n'est pas un facteur important. Par exemple, un polygone décrit par ((0, 0), (10, 0), (0, 20), (0, 0)) est le même qu'un polygone décrit par ((0, 0), (0, 20), (10, 0), (0, 0)). La spécification OGC Simple Features for SQL ne stipule pas d'ordonnancement d'anneau et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'applique pas d'ordonnancement d'anneau.

 Dans un système ellipsoïdal, un polygone n'a aucune signification, ou est ambigu, sans orientation. Par exemple, un anneau autour de l'équateur décrit-il l'hémisphère Nord ou Sud ? Si nous utilisons le type de données `geography` pour stocker l'instance spatiale, nous devons spécifier l'orientation de l'anneau et décrire précisément l'emplacement de l'instance. L'intérieur du polygone dans un système ellipsoïdal est défini par la règle gauche.

 Lorsque le niveau de compatibilité est 100 ou inférieur dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , le `geography` type de données présente les restrictions suivantes :

-   Chaque instance `geography` doit être contenue à l'intérieur d'un seul hémisphère. Aucun objet spatial plus grand qu'un hémisphère ne peut être stocké.

-   Toute instance `geography` d'une représentation WKB (Well-Known Binary) ou WKT (Well-Known Text) OGC (Open Geospatial Consortium) qui produit un objet plus grand qu'un hémisphère lève une `ArgumentException`.

-   Les `geography` méthodes de type de données qui requièrent l’entrée de deux `geography` instances, telles que STIntersection (), STUnion (), STDifference () et STSymDifference (), retournent Null si les résultats des méthodes ne s’ajustent pas à l’intérieur d’un seul hémisphère. STBuffer() retourne également null si la sortie dépasse un seul hémisphère.

 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], `FullGlobe` est un type spécial de polygone qui couvre le globe entier. `FullGlobe` possède une zone, mais aucune bordure ni sommet.

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a>Les anneaux internes et externes ne sont pas importants dans le type de données geography
 La spécification OGC simple Features for SQL traite des anneaux externes et internes, mais cette distinction n’a que peu de sens pour le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` type de données ; tout anneau d’un polygone peut être considéré comme l’anneau externe.

 Pour plus d'informations sur les spécifications OGC, reportez-vous aux sites Web suivants :

-   [OGC Specifications, Simple Feature Access Part 1 - Common Architecture](https://go.microsoft.com/fwlink/?LinkId=93627)

-   [OGC Specifications, Simple Feature Access Part 2 - SQL Options](https://go.microsoft.com/fwlink/?LinkId=93628)


##  <a name="circular-arc-segments"></a><a name="circular"></a> Segments d'arc de cercle
 Trois types instanciables acceptent des segments d'arc de cercle : `CircularString`, `CompoundCurve` et `CurvePolygon`.  Un segment d'arc de cercle est défini par trois points dans un plan à deux dimensions ; le troisième point doit être différent du premier point.

 Les figures A et B affichent des segments d'arc de cercle types. Remarquez comment chacun des trois points se situe sur le périmètre d'un cercle.

 Les figures C et D montrent comment un segment de ligne peut être défini comme un segment d'arc de cercle.  Notez que trois points sont toujours nécessaires pour définir le segment d'arc de cercle contrairement à un segment de ligne ordinaire qui peut être défini par deux points seulement.

 Les méthodes qui fonctionnent sur les types de segment d'arc de cercle utilisent des segments de ligne droite pour se rapprocher de l'arc de cercle. Le nombre de segments de ligne utilisé pour se rapprocher de l'arc dépend de la longueur et de la courbure de l'arc. Les valeurs Z peuvent être stockées pour chacun des types de segment d'arc de cercle ; toutefois, les méthodes n'utilisent pas les valeurs Z dans leurs calculs.

> [!NOTE]
>  Si des valeurs Z sont fournies pour les segments d'arc de cercle, elles doivent être identiques pour tous les points dans le segment d'arc de cercle pour que ce dernier soit accepté comme entrée. Par exemple, `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` est autorisé, contrairement à `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` .

### <a name="linestring-and-circularstring-comparison"></a>Comparaison de LineString et de CircularString
 Le diagramme suivant montre des triangles isocèles identiques (le triangle A utilise des segments de ligne pour définir le triangle, tandis que le triangle B utilise des segments d'arc de cercle) :

 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")

 Cet exemple indique comment stocker les triangles isocèles ci-dessus à l'aide d'une instance `LineString` et d'une instance `CircularString` :

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```

 Remarquez qu'une instance `CircularString` requiert sept points pour définir le triangle, alors qu'une instance `LineString` n'en requiert que quatre. La raison est qu'une instance `CircularString` stocke des segments d'arc de cercle et non des segments de ligne. Par conséquent, les côtés du triangle stockés dans l'instance `CircularString` sont ABC, CDE et EFA, alors que les côtés du triangle stockés dans l'instance `LineString` sont AC, CE et EA.

 Prenez l'exemple de l'extrait de code suivant :

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

 Cet extrait de code produira les résultats suivants :

```
LS LengthCS Length
5.65685...6.28318...
```

 L’illustration suivante montre le mode de stockage de chaque type (la ligne rouge affiche `LineString``@g1` , la ligne bleue affiche `CircularString``@g2` ) :

 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")

 Comme le montre l'illustration ci-dessus, les instances `CircularString` utilisent moins de points pour stocker des limites de courbe avec une précision supérieure que les instances `LineString`. `CircularString`les instances sont utiles pour stocker des limites circulaires comme un rayon de recherche de vingt milles à partir d’un point spécifique. Les instances `LineString` conviennent particulièrement bien au stockage de limites qui sont linéaires comme un bloc d'agglomération carré.

### <a name="linestring-and-compoundcurve-comparison"></a>Comparaison de LineString et de CompoundCurve
 Les exemples de code suivants montrent comment stocker la même figure à l'aide des instances `LineString` et `CompoundCurve` :

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

 or

 Dans les exemples ci-dessus, une instance `LineString` ou une instance `CompoundCurve` pourrait stocker la figure.  L'exemple suivant utilise un `CompoundCurve` pour stocker un graphique en secteurs :

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');
```

 Une instance `CompoundCurve` peut stocker le segment d'arc de cercle (2 2, 1 3, 0 2) directement, alors qu'une instance `LineString` doit convertir la courbe en plusieurs segments de ligne plus petits.

### <a name="circularstring-and-compoundcurve-comparison"></a>Comparaison de CircularString et de CompoundCurve
 L'exemple de code suivant indique comment le graphique en secteurs peut être stocké dans une instance `CircularString` :

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

 Pour stocker le graphique en secteurs à l'aide d'une instance `CircularString`, il faut utiliser trois points pour chaque segment de ligne.  Si un point intermédiaire n'est pas connu, il doit être calculé ou le point de terminaison du segment de ligne doit être doublé comme le montre l'extrait de code suivant :

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

 `CompoundCurve`les instances autorisent les `LineString` composants et de `CircularString` sorte que seuls deux points des segments de ligne du graphique à secteurs soient connus.  Cet exemple de code indique comment utiliser un `CompoundCurve` pour stocker la même figure :

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a>Comparaison de Polygon et de CurvePolygon
 Les instances `CurvePolygon` peuvent utiliser des instances `CircularString` et `CompoundCurve` lors de la définition de leurs anneaux intérieurs et extérieurs.  Les instances `Polygon` ne peuvent pas utiliser les types de segment d'arc de cercle : `CircularString` et `CompoundCurve`.


## <a name="see-also"></a>Voir aussi
 [Données spatiales &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [méthode type de données geometry référence](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) à la méthode de type de données [Geography référence](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;geometry type de données&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;type de données geometry](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)&#41;[STGeomFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)


