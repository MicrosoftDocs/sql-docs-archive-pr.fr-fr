---
title: 'Didacticiel : création d’un rapport de matrice (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9ee19c2e-2a8c-4bb0-9274-04a5812c2e96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3df32098d9e6400931ba2a88b2ffd22d6e015a62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706123"
---
# <a name="tutorial-creating-a-matrix-report-report-builder"></a>Didacticiel : création d'un rapport de matrice (Générateur de rapports)
  Ce didacticiel vous apprend comment créer un rapport de matrice de base reposant sur des exemples de données de vente. La matrice comporte des groupes de lignes et de colonnes imbriqués, ainsi qu'un groupe de colonnes adjacent. Vous apprendrez également comment mettre en forme les colonnes et faire pivoter le texte. L'illustration suivante montre un rapport similaire à celui que vous allez créer.  
  
 ![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")  
  
 Une version améliorée du rapport créé dans ce didacticiel est disponible sous forme d'exemple de rapport du Générateur de rapports de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations sur le téléchargement de cet exemple de rapport et d’autres, consultez [Générateur de rapports exemples de rapports](https://go.microsoft.com/fwlink/?LinkId=184851).  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à :  
  
1.  [Créer un rapport de matrice et un dataset à partir de l'Assistant Nouveau tableau ou nouvelle matrice](#CreateMatrix)  
  
2.  [Organiser les données et choisir la mise en page et le style à partir de l'Assistant Nouveau tableau ou nouvelle matrice](#Groups)  
  
3.  [Mettre en forme les données](#FormatData)  
  
4.  [Ajouter un groupe de colonnes adjacent](#AdjacentGroup)  
  
5.  [Modifier la largeur des colonnes](#Width)  
  
6.  [Fusionner des cellules de matrice](#MergeCells)  
  
7.  [Ajouter un en-tête de rapport et un titre de rapport](#HeaderTitle)  
  
8.  [Enregistrer le rapport](#Save)  
  
### <a name="other-optional-step"></a>Autre étape facultative  
  
1.  [Faire pivoter la zone de texte de 270 degrés](#RotateTextBox)  
  
 Durée estimée pour effectuer le didacticiel : 20 minutes.  
  
## <a name="requirements"></a>Spécifications  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-new-table-or-matrix-wizard"></a><a name="CreateMatrix"></a>1. créer un rapport de matrice et un DataSet à partir de l’Assistant Nouveau tableau ou nouvelle matrice  
 À partir de la boîte de dialogue **prise en main** dans générateur de rapports, choisissez une source de données partagée, créez un dataset incorporé, puis affichez les données dans une matrice.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient déjà les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-matrix"></a>Pour créer une nouvelle matrice  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
    > [!NOTE]  
    >  La boîte de dialogue **Mise en route** s'affiche. Si ce n’est pas le cas, à partir du bouton Générateur de rapports, cliquez sur **nouveau**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Tableau ou matrice**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **choisir une connexion à une source de données** , sélectionnez une source de données existante ou accédez au serveur de rapports, puis sélectionnez une source de données. Si aucune source de données n'est disponible ou si vous n'avez pas accès à un serveur de rapports, vous pouvez utiliser une source de données incorporée à la place. Pour plus d’informations sur la création d’une source de données incorporée, consultez [Didacticiel : création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
9. Copiez et collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
10. Cliquez sur **Suivant**.  
  
##  <a name="2-organize-data-and-choose-layout-and-style-from-the-new-table-or-matrix-wizard"></a><a name="Groups"></a>2. organiser les données et choisir la mise en page et le style à partir de l’Assistant Nouveau tableau ou nouvelle matrice  
 Utilisez l'Assistant pour obtenir une conception initiale dans laquelle afficher les données. Le volet de visualisation de l'Assistant vous aide à visualiser le résultat du regroupement des données avant de terminer la conception de la matrice.  
  
#### <a name="to-organize-data-into-groups-and-choose-a-layout-and-style"></a>Pour organiser les données en groupes et choisir une mise en page et un style  
  
1.  Dans la page **Organiser les champs** , faites glisser Territory de **Champs disponibles** vers **Groupes de lignes**.  
  
2.  Faites glisser SalesDate vers **Groupes de lignes** et placez-le sous Territory.  
  
     L’ordre dans lequel les champs sont répertoriés dans **Groupes de lignes** définit la hiérarchie des groupes. Les étapes 1 et 2 organisent les valeurs des champs par secteur de vente (Territory), puis par date de vente (SalesDate).  
  
3.  Faites glisser Subcategory vers **Groupes de colonnes**.  
  
4.  Faites glisser Product vers **groupes de colonnes,** puis placez sous sous-catégorie.  
  
     L’ordre dans lequel les champs sont répertoriés dans **groupes de colonnes** définit la hiérarchie des groupes.  
  
     Les étapes 3 et 4 organisent les valeurs des champs par sous-catégorie (SubCategory), puis par produit (Product).  
  
5.  Faites glisser Sales vers **Valeurs**.  
  
     Sales est synthétisé à l'aide de la fonction Sum, la fonction de synthèse par défaut des champs numériques.  
  
6.  Faites glisser Quantity vers **Valeurs**.  
  
     Quantity est synthétisé à l'aide de la fonction Sum.  
  
     Les étapes 5 et 6 spécifient les données à afficher dans les cellules de données de la matrice.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page choisir la disposition, sous **options**, vérifiez que **afficher les sous-totaux et les totaux généraux** est sélectionné.  
  
9. Vérifiez que **Bloqué, sous-total ci-dessous** est sélectionné.  
  
10. Vérifiez que l’option **Développer/Réduire les groupes** est sélectionnée.  
  
11. Cliquez sur **Suivant**.  
  
12. Dans la page Choisir un style , dans le volet Styles , sélectionnez **Ardoise**.  
  
13. Cliquez sur **Terminer**.  
  
     La matrice est ajoutée à l'aire de conception. Le volet Groupes de lignes affiche deux groupes de lignes : Territory et SalesDate. Le volet Groupes de colonnes affiche deux groupes de colonnes : Subcategory et Product. Les données de détail sont toutes les données récupérées par la requête de dataset.  
  
14. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Pour chaque produit vendu à une date spécifique, la matrice affiche la sous-catégorie à laquelle le produit appartient et le secteur des ventes.  
  
##  <a name="3-format-data"></a><a name="FormatData"></a>3. mettre en forme les données  
 Par défaut, les données de synthèse du champ Sales affichent un nombre général et le champ SalesDate affiche des informations de date et d'heure. Mettez en forme le champ Sales de manière à afficher le nombre sous forme de devise et le champ SalesDate afin qu'il n'affiche que la date. Activez/désactivez **Styles des espaces réservés** pour afficher les zones de texte mises en forme et le texte de l’espace réservé en tant qu’exemples de valeurs.  
  
#### <a name="to-format-fields"></a>Pour mettre en forme les champs  
  
1.  Cliquez sur **Conception** pour basculer en mode Conception.  
  
2.  Appuyez sur la touche Ctrl, puis sélectionnez les neuf cellules contenant `[Sum(Sales)]`.  
  
3.  Sous l’onglet **Accueil** , dans le groupe **Nombre** , cliquez sur **Devise**. Le contenu des cellules est maintenant au format de devise.  
  
     Si votre paramètre régional est Anglais (États-Unis), le texte d’exemple par défaut est [**$12,345.00**]. Si vous ne voyez pas d’exemple de valeur monétaire, cliquez sur **styles des espaces réservés** dans le groupe **nombres** , puis cliquez sur **exemples de valeurs**.  
  
4.  Cliquez sur la cellule qui contient `[SalesDate]`.  
  
5.  Dans le groupe **nombre** , dans la liste déroulante, sélectionnez **Date**.  
  
     La cellule affiche l’exemple de date **[1/31/2000]**. Si vous ne voyez pas s’afficher d’exemple de date, cliquez sur **Styles des espaces réservés** dans le groupe **Nombres** , puis cliquez sur **Valeurs d’aperçu**.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Les valeurs de date affichent uniquement les dates et les valeurs de ventes sont affichées sous forme de valeurs monétaires.  
  
##  <a name="4-add-adjacent-column-group"></a><a name="AdjacentGroup"></a>4. Ajouter un groupe de colonnes adjacent  
 Vous pouvez imbriquer des groupes de lignes et de colonnes dans des relations parent-enfant ou définir des groupes adjacents dans des relations de frère.  
  
 Ajoutez un groupe de colonnes adjacent au groupe de colonnes Subcategory, copiez les cellules pour remplir le nouveau groupe de colonnes, puis utilisez une expression pour créer la valeur de l'en-tête de groupe de colonnes.  
  
#### <a name="to-add-an-adjacent-column-group"></a>Pour ajouter un groupe de colonnes adjacent  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez avec le bouton droit sur la cellule qui contient `[Subcategory]`, pointez sur **Ajouter un groupe**, puis cliquez sur **Adjacent à droite**.  
  
     La boîte de dialogue **Groupe de tableaux matriciels** s'affiche.  
  
3.  Dans la liste **Regrouper par** , sélectionnez SalesDate, puis cliquez sur **OK**.  
  
     Un nouveau groupe de colonnes est ajouté à gauche du groupe de colonnes Subcategory.  
  
4.  Cliquez avec le bouton droit sur la cellule du nouveau groupe de colonnes qui contient `[SalesDate],` , puis cliquez sur **Expression**.  
  
5.  Copiez l'expression suivante dans la zone d'expression.  
  
    ```  
    =WeekdayName(DatePart("w",Fields!SalesDate.Value))  
    ```  
  
     Cette expression extrait le nom de jour de la semaine de la date de vente. Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).  
  
6.  Cliquez avec le bouton droit sur la cellule du groupe de colonnes Subcategory qui contient Total, puis cliquez sur **Copier**.  
  
7.  Cliquez avec le bouton droit immédiatement en-dessous de la cellule qui contient l’expression créée à l’étape 5, puis cliquez sur **Coller**.  
  
8.  Appuyez sur la touche Ctrl.  
  
9. Dans le groupe Subcategory, cliquez avec le bouton droit sur l’en-tête de colonne Sales et sur les trois cellules en dessous, puis cliquez sur **Copier**.  
  
10. Collez les quatre cellules dans les quatre cellules vides du nouveau groupe de colonnes.  
  
11. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport inclut des colonnes nommées Monday et Tuesday. Le dataset contient uniquement des données pour ces deux jours.  
  
> [!NOTE]  
>  Si les données avaient inclus d'autres jours, le rapport aurait également inclus des colonnes pour ces jours. Chaque colonne a l’en-tête de colonne, `Sales` et les totaux des ventes par secteur.  
  
##  <a name="5-change-column-widths"></a><a name="Width"></a>5. modifier la largeur des colonnes  
 Un rapport qui inclut une matrice s'étend généralement horizontalement et verticalement lorsqu'il s'exécute. Le contrôle de l'expansion horizontale est particulièrement important si vous projetez d'exporter le rapport vers des formats tels que Microsoft Word ou Adobe PDF qui sont utilisés pour imprimer les rapports. Si le rapport s'étend horizontalement sur plusieurs pages, le rapport imprimé est difficile à comprendre. Pour réduire l'expansion horizontale, vous pouvez redimensionner les colonnes afin qu'elles ne soient pas plus larges que nécessaire pour afficher les données sans renvoi à la ligne. Vous pouvez également renommer les colonnes afin que leur titre soit ajusté à la largeur nécessaire pour afficher les données.  
  
#### <a name="to-rename-and-resize-the-columns"></a>Pour renommer et redimensionner les colonnes  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Sélectionnez le texte dans la colonne Quantity la plus à gauche, puis tapez **QTY**.  
  
     Le titre de la colonne est maintenant QTY.  
  
3.  Répétez l'étape 2 pour les autres colonnes nommées Quantity. Il y en a deux.  
  
4.  Cliquez sur la matrice pour que les poignées de ligne et de colonne apparaissent au-dessus et à côté de la matrice.  
  
     Les barres grises le long du haut et du côté de la table sont les poignées de colonne et de ligne.  
  
5.  Pour redimensionner la colonne QTY la plus à gauche, pointez sur la ligne entre les poignées de colonne afin que le curseur se transforme en flèche à deux pointes. Faites glisser la colonne vers la gauche jusqu'à ce qu'elle fasse 0,5 pouce de large.  
  
     Une largeur de colonne de 0,5 pouce est parfaite pour afficher la quantité.  
  
6.  Répétez l'étape 5 pour les autres colonnes nommées QTY.  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Les colonnes du rapport qui contiennent des quantités sont désormais nommées QTY et sont plus étroites.  
  
##  <a name="6-merge-matrix-cells"></a><a name="MergeCells"></a>6. fusionner des cellules de matrice  
 La zone d'angle se trouve dans le coin supérieur gauche de la matrice. Selon le nombre de groupes de lignes et de colonnes dans la matrice, le nombre de cellules de la zone d'angle varie. La matrice générée dans ce didacticiel comporte quatre cellules dans sa zone d'angle. Les cellules sont disposées en deux lignes et deux colonnes, ce qui reflète la profondeur des hiérarchies de groupes de lignes et de colonnes. Les quatre cellules ne sont pas utilisées dans ce rapport et vous allez les fusionner en une seule.  
  
#### <a name="to-merge-matrix-cells"></a>Pour fusionner des cellules de matrice  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la matrice pour que les poignées de ligne et de colonne apparaissent au-dessus et à côté de la matrice.  
  
3.  Appuyez sur la touche Ctrl, puis sélectionnez les quatre cellules d'angle.  
  
4.  Cliquez avec le bouton droit sur les cellules, puis cliquez sur **fusionner les cellules**.  
  
5.  Cliquez avec le bouton droit sur la cellule d’angle, puis cliquez sur **Propriétés de la zone de texte**.  
  
6.  Cliquez sur l'onglet **Remplissage** .  
  
7.  Cliquez sur le bouton (***FX***) pour **couleur de remplissage**.  
  
8.  Copiez et collez l'expression suivante dans la zone d'expression.  
  
    ```  
    #96a4b2  
    ```  
  
     Il s'agit de la valeur RVB pour une couleur bleu gris utilisée dans le style Ardoise.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 La matrice de l'angle supérieur est une cellule unique de la même couleur que les cellules des groupes de colonnes et des groupes de lignes.  
  
##  <a name="7-add-a-report-header-and-report-title"></a><a name="HeaderTitle"></a>7. Ajouter un en-tête de rapport et un titre de rapport  
 Un titre de rapport s'affiche dans la partie supérieure du rapport. Vous pouvez placer le titre du rapport dans un en-tête de rapport, ou si le rapport n'en utilise pas, dans une zone de texte située en haut du corps du rapport. Dans ce didacticiel, vous allez supprimer la zone de texte au haut du rapport et ajouter un titre à l'en-tête.  
  
#### <a name="to-add-a-report-header-and-report-title"></a>Pour ajouter un en-tête de rapport et un titre de rapport  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la zone de texte en haut du corps du rapport qui contient **cliquez pour ajouter un titre**, puis appuyez sur la touche Suppr.  
  
3.  Sous l’onglet **Insérer** du ruban, cliquez sur **en-tête** , puis sur **Ajouter un en-tête**.  
  
     Un en-tête est ajouté en haut du corps du rapport.  
  
4.  Sous l’onglet **Insérer** , cliquez sur **Zone de texte**, puis faites glisser une zone de texte à l’intérieur de l’en-tête du rapport. Définissez sa taille sur environ 6 pouces de long et 0,75 pouce de haut et placez-la sur le côté gauche de l'en-tête de rapport.  
  
5.  Dans la zone de texte, tapez **Sales by Territory, Subcategory, and Day**.  
  
6.  Sélectionnez le texte que vous avez tapé, cliquez dessus avec le bouton droit, puis cliquez sur **Propriétés du texte**.  
  
    > [!NOTE]  
    >  Pour mettre en forme les caractères en même temps, ils doivent être contigus.  
  
7.  Dans la boîte de dialogue **Propriétés du texte** , cliquez sur **police**.  
  
8.  Dans la liste **police** , sélectionnez **Times New Roman**; dans **taille** , sélectionnez **24 PT**, **dans couleur** , sélectionnez **marron**, puis dans **style** , sélectionnez **italique**.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport inclut un titre de rapport dans l'en-tête de rapport.  
  
##  <a name="8-save-the-report"></a><a name="Save"></a>8. enregistrer le rapport  
 Vous pouvez enregistrer les rapports sur un serveur de rapports, dans une bibliothèque SharePoint ou sur l'ordinateur.  
  
 Dans ce didacticiel, enregistrez le rapport sur un serveur de rapports. Si vous n'avez pas accès à un serveur de rapports, enregistrez le rapport sur votre ordinateur.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l’administrateur du serveur de rapports s’affiche comme emplacement par défaut des rapports.  
  
4.  Dans **Nom**, remplacez le nom par défaut par **SalesByTerritorySubcategory**.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Bureau**, **Mes documents**ou **Poste de travail**, puis naviguez jusqu'au dossier où vous souhaitez enregistrer le rapport.  
  
3.  Dans **Nom**, remplacez le nom par défaut par **SalesByTerritorySubcategory**.  
  
4.  Cliquez sur **Enregistrer**.  
  
##  <a name="9-optional-rotate-text-box-270-degrees"></a><a name="RotateTextBox"></a>9. (facultatif) faire pivoter la zone de texte de 270 degrés  
 Un rapport avec des matrices peut s'étendre horizontalement et verticalement lorsqu'il s'exécute. En faisant pivoter les zones de texte verticalement, ou de 270 degrés, vous pouvez gagner de l'espace horizontal. Le rapport rendu sera alors plus étroit, et s'il est exporté dans un format tel que Microsoft Word, il rentrera plus facilement sur une page imprimée.  
  
 Une zone de texte peut également afficher du texte horizontal dans le sens vertical (de haut en bas). Pour plus d’informations, consultez [Zones de texte &#40;Générateur de rapports et SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md).  
  
#### <a name="to-rotate-text-box-270-degrees"></a>Pour faire pivoter la zone de texte de 270 degrés  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la cellule qui contient `[Territory].`  
  
3.  Dans le volet Propriétés, recherchez la propriété WritingMode et, dans sa liste déroulante, sélectionnez **Rotate270**.  
  
     Si le volet Propriétés n’est pas ouvert, cliquez sur l’onglet **Affichage** du ruban et sélectionnez **Propriétés**.  
  
4.  Vérifiez que la propriété CanGrow a la valeur `True` .  
  
5.  Redimensionnez la colonne Territory afin qu'elle fasse à 0,5 pouce de large et supprimez le titre de la colonne.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le nom du secteur est écrit verticalement, de bas en haut. La hauteur du groupe de lignes Territory varie en fonction de la longueur du nom du secteur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ainsi s'achève le didacticiel de création d'un rapport de matrice. Pour plus d’informations sur les matrices, consultez [tables, matrices et listes &#40;générateur de rapports et ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [matrices &#40;Générateur de rapports et SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), zones de région de données de tableau [matriciel &#40;générateur de rapports et SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)et [cellules, lignes et colonnes de région de données de tableau matriciel &#40;générateur de rapports&#41; et SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
