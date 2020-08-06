---
title: 'Didacticiel : ajouter un histogramme à un rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706151"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>Didacticiel : ajouter un histogramme à un rapport (Générateur de rapports)
  Un histogramme affiche une série sous la forme d'un ensemble de barres verticales regroupées par catégorie. Un histogramme s'avère utile pour :  
  
-   montrer l'évolution des données sur une période ;  
  
-   comparer la valeur relative de plusieurs séries.  
  
-   afficher une moyenne mobile pour montrer les tendances.  
  
 L'illustration suivante montre l'histogramme que vous allez créer, avec une moyenne mobile.  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un graphique à partir de l'Assistant Graphique](#Chart)  
  
2.  [Choisir le type de graphique](#ChartType)  
  
3.  [Mettre en forme et étiqueter l'axe horizontal](#Horizontal)  
  
4.  [Déplacer la légende](#Legend)  
  
5.  [Intituler le graphique](#ChartTitle)  
  
6.  [Mettre en forme et étiqueter l'axe vertical](#Vertical)  
  
7.  [Ajouter une moyenne mobile](#Average)  
  
8.  [Ajouter un titre de rapport](#Title)  
  
9. [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en une seule procédure. Pour obtenir des instructions pas à pas sur l’accès à un serveur de rapports, le choix d’une source de données et la création d’un dataset, consultez le premier didacticiel de cette série : [Didacticiel : création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 15 minutes.  
  
## <a name="requirements"></a>Spécifications  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. créer un rapport de graphique à partir de l’Assistant graphique  
 À partir de la boîte de dialogue **prise en main** , utilisez l’Assistant graphique pour créer un dataset incorporé, choisir une source de données partagée et créer un histogramme.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-chart-report"></a>Pour créer un rapport de graphique  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue **prise en main** s’affiche.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue **prise en main** n’apparaît pas, à partir du bouton **Générateur de rapports** , cliquez sur **nouveau**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**.  
  
4.  Dans la page **Choisir un dataset**, cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu’au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, consultez [Autres manières d’obtenir une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter (**!**) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquez sur **Suivant**.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. choisir le type de graphique  
 Vous avez le choix entre plusieurs types de graphiques prédéfinis.  
  
#### <a name="to-add-a-column-chart"></a>Pour ajouter un histogramme  
  
1.  Dans la page **Choisir un type de graphique** , l’histogramme est le type de graphique par défaut. Cliquez sur **Suivant**.  
  
2.  Dans la page **Organiser les champs du graphique** , faites glisser le champ SalesDate vers **Catégories**. Les catégories s'affichent sur l'axe horizontal.  
  
3.  Faites glisser le champ Sales vers **Valeurs**. La zone **Valeurs** affiche Sum(Sales), car la somme de la valeur totale des ventes est agrégée pour chaque date. Les valeurs s'affichent sur l'axe vertical.  
  
4.  Cliquez sur **Suivant**.  
  
5.  Dans la page **choisir un style** , dans la zone styles, sélectionnez un style.  
  
     Un style spécifie un style de police, un jeu de couleurs et un style de bordure. Lorsque vous sélectionnez un style, le volet Aperçu affiche un aperçu du graphique avec ce style.  
  
6.  Cliquez sur **Terminer**.  
  
     Le graphique est ajouté à l'aire de conception.  
  
7.  Cliquez sur le graphique pour afficher ses poignées. Faites glisser l'angle inférieur droit du graphique pour augmenter sa taille. Notez que la taille de l'aire de conception du rapport augmente pour s'adapter à la taille du graphique.  
  
8.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>3. mettre en forme et étiqueter l’axe horizontal  
 Par défaut, l'axe horizontal affiche les valeurs dans un format général qui est mis à l'échelle automatiquement pour s'ajuster à la taille du graphique.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>Pour mettre en forme une date sur l'axe horizontal  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez avec le bouton droit sur l’axe horizontal, puis cliquez sur Propriétés de l' **axe horizontal**.  
  
3.  Cliquez sur **Nombre**.  
  
4.  Dans **catégorie**, sélectionnez **Date**.  
  
5.  Dans la zone **Type** , sélectionnez **31 Jan 2000**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Sous l’onglet Accueil, cliquez sur **Exécuter** pour afficher l’aperçu du rapport.  
  
 La date s'affiche dans le format de date que vous avez sélectionné. Notez que le graphique ne répertorie pas chaque catégorie sur l'axe horizontal. Par défaut, seules sont incluses les étiquettes qui n'empiètent pas sur l'axe.  
  
 Vous pouvez personnaliser l'affichage des étiquettes en les faisant pivoter et en spécifiant l'intervalle.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>Pour faire pivoter les étiquettes sur l'axe horizontal et modifier l'intervalle qui les sépare  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez avec le bouton droit sur le titre de l’axe horizontal, puis cliquez sur **afficher le titre** de l’axe pour supprimer le titre. Étant donné que l'axe horizontal indique les dates, le titre n'est pas nécessaire.  
  
3.  Cliquez avec le bouton droit sur l’axe horizontal, puis cliquez sur Propriétés de l' **axe horizontal**.  
  
4.  Dans la page **options** de l’axe sous **plage et intervalle**de l’axe, tapez **3** pour **intervalle**. Le graphique affiche les dates selon un intervalle de trois.  
  
5.  Cliquez sur **Étiquettes**.  
  
6.  Dans **modifier les options d’ajustement automatique des étiquettes d’axe**, sélectionnez **désactiver l’ajustement automatique**.  
  
7.  Dans **Angle de rotation des étiquettes**, sélectionnez **-90**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     L'exemple de texte de l'axe horizontal pivote de 90 degrés.  
  
9. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Sur le graphique, les étiquettes pivotent et sont affichées à raison d'une date sur trois.  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a>4. déplacer la légende  
 La légende est créée automatiquement à partir des données de catégories et de séries.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>Pour déplacer la légende sous la zone de graphique d'un histogramme  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez avec le bouton droit sur la légende du graphique, puis cliquez sur Propriétés de la **légende**.  
  
3.  Pour **disposition et position**, sélectionnez une autre position. Par exemple, choisissez de positionner le graphique en bas au centre.  
  
     Lorsque la légende est placée en haut ou en bas d'un graphique, la disposition de la légende change de vertical à horizontal. Vous pouvez sélectionner une autre disposition dans la liste déroulante **Disposition** .  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (Facultatif) Étant donné que ce didacticiel ne comprend qu'une seule catégorie, la légende n'est pas nécessaire. Pour supprimer la légende, cliquez avec le bouton droit sur la légende, puis cliquez sur **Supprimer la légende**.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a>5. titre du graphique  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>Pour modifier le titre d'un graphique au-dessus de la zone de graphique  
  
1.  Basculez en mode création de rapport.  
  
2.  Sélectionnez les mots **titre du graphique** en haut du graphique, puis tapez le texte suivant : total des **commandes client de magasin**.  
  
3.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a>6. mettre en forme et étiqueter l’axe vertical  
 Par défaut, l'axe vertical affiche les valeurs dans un format général qui est mis à l'échelle automatiquement pour s'ajuster à la taille du graphique.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>Pour appliquer le format monétaire aux chiffres figurant sur l'axe vertical  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur les étiquettes de l’axe vertical sur le côté du graphique pour les sélectionner.  
  
3.  Dans le ruban, sous l’onglet dossier de **démarrage** , dans le groupe **nombre** , cliquez sur le bouton **devise** . Les étiquettes de l'axe changent pour afficher le format monétaire.  
  
4.  Dans le ruban, sous l’onglet dossier de **démarrage** , dans le groupe **nombre** , cliquez sur le bouton **réduire la décimale** deux fois pour afficher le nombre arrondi au dollar le plus proche.  
  
5.  Cliquez avec le bouton droit sur l’axe vertical, puis cliquez sur Propriétés de l' **axe vertical**.  
  
6.  Cliquez sur **Nombre**. Notez que **devise** est déjà sélectionné dans la zone **catégorie** et que la valeur **décimale** est déjà **0** (zéro).  
  
7.  Dans la zone **afficher les valeurs dans** , cliquez sur **milliers**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Cliquez avec le bouton droit sur le titre de l’axe vertical sur le côté du graphique, puis cliquez sur **Propriétés du titre**de l’axe.  
  
10. Remplacez le texte du champ **texte du titre** par le texte suivant : **total des ventes (en milliers)**. Vous pouvez également spécifier diverses options de mise en forme du titre.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a>7. Ajouter une moyenne mobile  
  
#### <a name="to-add-a-moving-average"></a>Pour ajouter une moyenne mobile  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur le graphique pour afficher le volet **Données du graphique** .  
  
3.  Cliquez avec le bouton droit sur le champ **[Sum (Sales)]** dans la zone **valeurs** , puis cliquez sur **Ajouter une série calculée**.  
  
4.  Dans **Formule**, vérifiez que **Moyenne mobile** est sélectionné.  
  
5.  Dans **Définir les paramètres de la formule**, pour **Période**, sélectionnez **4**.  
  
6.  Cliquez sur **bordure**.  
  
7.  Dans **largeur de ligne**, sélectionnez **3 points**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le graphique présente une ligne qui indique la moyenne mobile pour le total des ventes par date. La moyenne est ici calculée toutes les quatre dates.  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a>8. Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
3.  Tapez **graphique des ventes**, appuyez sur entrée, puis tapez **janvier à décembre 2009**pour obtenir l’aspect suivant :  
  
     **Graphique sur les ventes**  
  
     **Janvier à décembre 2009**  
  
4.  Sélectionnez **graphique des ventes**, puis cliquez sur le bouton **gras** dans la section **police** de l’onglet dossier de **démarrage** du ruban.  
  
5.  Sélectionnez **janvier jusqu’au 2009 décembre**, puis dans la section **police** de l’onglet dossier de **départ** , définissez la taille de police sur **10**.  
  
6.  Facultatif Vous devrez peut-être agrandir la zone de texte du **titre** pour accueillir les deux lignes de texte en tirant sur les flèches à deux pointes lorsque vous cliquez au milieu du bord inférieur.  
  
     Ce titre s'affiche alors dans la partie supérieure du rapport. En l’absence d’en-tête de page défini, les éléments situés au-dessus du corps du rapport font office d’en-tête de rapport.  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. enregistrer le rapport  
  
#### <a name="to-save-the-report"></a>Pour enregistrer le rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  À partir du bouton Générateur de rapports , cliquez sur **Enregistrer sous**.  
  
3.  Dans **Nom**, tapez **Histogramme des commandes client**.  
  
4.  Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel Ajout d'un histogramme à un rapport. Pour en savoir plus sur les graphiques, consultez [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) et [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
