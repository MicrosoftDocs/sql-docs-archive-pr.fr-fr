---
title: Créer, construire et interroger des instances geography | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d744457cc517a6172cca96b27eae1f456deca24e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601309"
---
# <a name="create-construct-and-query-geography-instances"></a>Créer, construire et interroger des instances geography
  Le type de données spatiales géographiques, `geography`, représente des données dans un système de coordonnées de monde sphérique. Ce type est implémenté en tant que type de données CLR (Common Language Runtime) .NET dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` qui stocke des données ellipsoïdales, telles que des coordonnées de latitude et de longitude GPS.  
  
 Le type `geography` est prédéfini et disponible dans chaque base de données. Vous pouvez créer des colonnes de table de type `geography` et opérer sur les données `geography` comme vous le feriez avec d'autres types fournis par le système.  
  
##  <a name="creating-or-constructing-a-new-geography-instance"></a><a name="creating"></a> Création ou construction d'une nouvelle instance geography  
  
###  <a name="creating-a-new-geography-instance-from-an-existing-instance"></a><a name="existing"></a> Création d'une nouvelle instance geography à partir d'une instance existante  
 Le type de données `geography` fournit de nombreuses méthodes intégrées que vous pouvez utiliser pour créer des instances `geography` basées sur des instances existantes.  
  
 **Pour créer une mémoire tampon autour d'une géographie**  
 [STBuffer &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **Pour créer une mémoire tampon autour d'une géographie, en tenant compte d'une tolérance**  
 [BufferWithTolerance &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **Pour créer une géographie à partir de l'intersection de deux instances géographiques**  
 [STIntersection &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Pour créer une géographie à partir de l'union de deux instances géographiques**  
 [STUnion &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **Pour créer une géographie à partir des points où une géographie n'en chevauche pas une autre**  
 [STDifference &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-text-input"></a><a name="wkt"></a> Construction d'une instance geography à partir d'une entrée WKT (Well-Known Text)  
 Le type de données `geography` fournit plusieurs méthodes intégrées qui génèrent une géographie à partir de la représentation WKT OGC (Open Geospatial Consortium). La norme WKT est une chaîne de texte qui autorise l'échange de données geography sous forme textuelle.  
  
 **Pour construire tout type d'instance geography à partir d'une entrée WKT**  
 [STGeomFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [Parse &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **Pour construire une instance Point geography à partir d'une entrée WKT**  
 [STPointFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **Pour construire une instance MultiPoint geography à partir d'une entrée WKT**  
 [STMPointFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **Pour construire une instance LineString geography à partir d'une entrée WKT**  
 STLineFromText (type de données geography)  
  
 **Pour construire une instance MultiLineString geography à partir d'une entrée WKT**  
 [STMLineFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **Pour construire une instance Polygon geography à partir d'une entrée WKT**  
 [STPolyFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **Pour construire une instance MultiPolygon geography à partir d'une entrée WKT**  
 [STMPolyFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **Pour construire une instance GeometryCollection geography à partir d'une entrée WKT**  
 [STGeomCollFromText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-binary-input"></a><a name="wkb"></a> Construction d'une instance geography à partir d'une entrée WKB (Well-Known Binary)  
 WKB est un format binaire spécifié par l'OGC qui autorise l'échange de données de `Geography` entre une application cliente et une base de données SQL. Les fonctions suivantes acceptent l'entrée WKB pour construire des instances geography :  
  
 **Pour construire tout type d'instance geography à partir d'une entrée WKB**  
 [STGeomFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **Pour construire une instance Point geography à partir d'une entrée WKB**  
 [STPointFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **Pour construire une instance MultiPoint geography à partir d'une entrée WKB**  
 [STMPointFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **Pour construire une instance LineString geography à partir d'une entrée WKB**  
 [STLineFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **Pour construire une instance MultiLineString geography à partir d'une entrée WKB**  
 [STMLineFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **Pour construire une instance Polygon geography à partir d'une entrée WKB**  
 [STPolyFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **Pour construire une instance MultiPolygon geography à partir d'une entrée WKB**  
 [STMPolyFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **Pour construire une instance GeometryCollection geography à partir d'une entrée WKB**  
 [STGeomCollFromWKB &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (type de données geography)  
  
###  <a name="constructing-a-geography-instance-from-gml-text-input"></a><a name="gml"></a> Construction d'une instance geography à partir d'une entrée texte GML  
 Le `geography` type de données fournit une méthode qui génère une `geography` instance à partir de GML, une représentation XML d’une `geography` instance. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge un sous-ensemble de GML.  
  
 Pour plus d’informations sur le langage GML (Geography Markup Language), consultez la spécification OGC : [OGC Specifications, Geography Markup Language (en anglais)](https://go.microsoft.com/fwlink/?LinkId=93629).  
  
 **Pour construire tout type d'instance geography à partir d'une entrée GML**  
 [GeomFromGML &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geography-instance"></a><a name="returning"></a> Renvoi de données WKT et WKB à partir d'une instance geography  
 Vous pouvez utiliser les méthodes suivantes pour retourner le format WKT ou WKB d'une instance `geography` :  
  
 **Pour retourner la représentation WKT d'une instance geography**  
 [STAsText &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [ToString &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **Pour retourner la représentation WKT d'une instance geography incluant des valeurs Z et M**  
 [AsTextZM &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **Pour retourner la représentation WKB d'une instance geography**  
 [STAsBinary &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **Pour retourner une représentation GML d'une instance geography**  
 [AsGml &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="querying-the-properties-and-behaviors-of-geography-instances"></a><a name="query"></a> Interrogation des propriétés et des comportements des instances geography  
 Toutes les `geography` instances ont un certain nombre de propriétés qui peuvent être récupérées par le biais des méthodes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournies par. Les rubriques suivantes définissent les propriétés et comportements de types géographiques et les méthodes permettant de les interroger.  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> Informations sur la validité, le type d'instance et GeometryCollection  
 Une fois qu’une `geography` instance est construite, vous pouvez utiliser les méthodes suivantes pour retourner le type d’instance ou, s’il s’agit d’une `GeometryCollection` instance, retourner une `geography` instance spécifique.  
  
 **Pour retourner le type d'instance d'une géographie**  
 [STGeometryType &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **Pour déterminer si une géographie est un type d'instance donné**  
 [InstanceOf &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **Pour déterminer si une instance géographique est de forme correcte pour son type d'instance**  
 [STNumGeometries &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **Pour retourner une géographie spécifique dans une instance GeometryCollection**  
 [STGeometryN &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (type de données geography)  
  
###  <a name="number-of-points"></a><a name="number"></a> Nombre de points  
 Toutes les instances non vides `geography` sont constituées de *points*. Ces points représentent les coordonnées de latitude et de longitude du monde sur lequel les instances `geography` sont dessinées. Le type de données `geography` fournit de nombreuses méthodes intégrées pour interroger les points d'une instance.  
  
 **Pour retourner le nombre de points qui composent une instance**  
 [STNumPoints &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **Pour retourner un point spécifique dans une instance**  
 [STPointN &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **Pour retourner le point de départ d'une instance**  
 [STStartPoint &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **Pour retourner le point de terminaison d'une instance**  
 [STEndpoint &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a><a name="dimension"></a> Dimension  
 Une instance `geography` non vide peut avoir 0, 1 ou 2 dimensions. Les instances de dimension zéro `geography` , telles que `Point` et `MultiPoint` , n’ont pas de longueur ou de zone. Les objets unidimensionnels, tels que `LineString, CircularString`, `CompoundCurve` et `MultiLineString`, ont une longueur. Les instances à deux dimensions, telles que `Polygon, CurvePolygon` , et `MultiPolygon` , ont une surface et une longueur. Les instances vides indiquent une dimension de -1 et une `GeometryCollection` indique la dimension maximale de son contenu.  
  
 **Pour retourner la dimension d'une instance**  
 [STDimension &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **Pour retourner la longueur d'une instance**  
 [STLength &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **Pour retourner la surface d'une instance**  
 [STArea &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a><a name="empty"></a> Vide  
 Une instance *vide* `geography` n’a aucun point. La longueur des instances `LineString, CircularString`, `CompoundCurve` et `MultiLineString` vides est 0. La surface des instances `Polygon, CurvePolygon` et `MultiPolygon` vides est 0.  
  
 **Pour déterminer si une instance est vide**  
 [STIsEmpty &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a><a name="closure"></a> Fermeture  
 Une instance *fermée* `geography` est une figure dont les points de début et de fin sont identiques. Les instances `Polygon` sont considérées comme fermées. Les instances `Point` ne sont pas fermées.  
  
 Un anneau est une instance `LineString` simple et fermée.  
  
 **Pour déterminer si une instance est fermée**  
 [STIsClosed &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **Pour retourner le nombre d'anneaux dans une instance Polygon**  
 [NumRings &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **Pour retourner un anneau spécifié d'une instance géographique**  
 [RingN &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> ID de référence spatial (SRID)  
 L'ID de référence spatial (SRID) est un identificateur spécifiant dans quel système de coordonnées ellipsoïde l'instance `geography` est représentée. Deux instances `geography` avec différents SRID ne peuvent pas être comparées.  
  
 **Pour définir ou retourner le SRID d'une instance**  
 [STSrid &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 Cette propriété peut être modifiée.  
  
##  <a name="determining-relationships-between-geography-instances"></a><a name="rel"></a> Détermination de relations entre des instances geography  
 Le type de données `geography` fournit de nombreuses méthodes intégrées que vous pouvez utiliser pour déterminer les relations entre deux instances `geography`.  
  
 **Pour déterminer si deux instances comprennent le même ensemble de points**  
 [STEquals &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **Pour déterminer si deux instances sont disjointes**  
 [STDisjoint &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **Pour déterminer si deux instances se croisent**  
 [STIntersects &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **Pour déterminer le ou les points où deux instances se croisent**  
 [STIntersection &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Pour déterminer la distance la plus courte entre des points dans deux instances géographiques**  
 [STDistance &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **Pour déterminer la différence en points entre deux instances géographiques**  
 [STDifference &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **Pour dériver la différence symétrique, ou points uniques, d'une instance geography comparée à une autre instance**  
 [STSymDifference &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="geography-instances-must-use-supported-srid"></a><a name="supportedsrid"></a> Les instances geography doivent utiliser un SRID pris en charge  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les SRID basés sur les normes EPSG. Un SRID [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pris en charge pour les instances `geography` doit être utilisé lors de l'exécution de calculs ou de l'utilisation de méthodes avec des données spatiales géographiques. Le SRID doit correspondre à l’un des SRID présents dans l’affichage catalogue **sys.spatial_reference_systems** . Comme mentionné précédemment, lorsque vous effectuez des calculs sur vos données spatiales à l'aide du type de données `geography`, vos résultats dépendront de l'ellipsoïde utilisée dans la création de vos données, car un identificateur de référence spatiale (SRID) spécifique est assigné à chaque ellipsoïde.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le SRID par défaut de 4326, qui mappe au système de référence spatiale WGS 84, lors de l'utilisation de méthodes sur des instances `geography`. Si vous utilisez des données d'un système de référence spatiale autre que WGS 84 (ou SRID 4326), vous devrez déterminer le SRID spécifique pour vos données spatiales geography.  
  
##  <a name="examples"></a><a name="examples"></a> Exemples  
 Les exemples suivants montrent comment ajouter et interroger des données géographiques.  
  
-   Le premier exemple crée une table avec une colonne d'identité et une colonne `geography``GeogCol1`. Une troisième colonne restitue la colonne `geography` dans sa représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) et utilise la méthode `STAsText()` . Deux lignes sont ensuite insérées : une ligne contient une instance `LineString` de `geography`et une ligne contient une instance `Polygon` .  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   Le deuxième exemple utilise la méthode `STIntersection()` pour retourner les points où les deux instances `geography` précédemment insérées se croisent.  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Données spatiales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
