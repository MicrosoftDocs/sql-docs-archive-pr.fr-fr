---
title: 'Leçon 4 : ajout d’une table au rapport (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52694168bd60b8e3807db6204f33a89815573093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601967"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a>Leçon 4 : Ajout d'une table au rapport (Reporting Services)
  Une fois le dataset défini, vous pouvez commencer à concevoir le rapport. Pour créer une mise en page de rapport, faites glisser les régions de données, les zones de texte, les images et autres éléments que vous souhaitez inclure dans un rapport vers l'aire de conception.  
  
 Les éléments qui contiennent des lignes de données répétées de datasets sous-jacents sont appelés *régions de données*. Un rapport de base possède une seule région de données, mais vous pouvez en ajouter davantage (pour ajouter un graphique à un rapport tabulaire, par exemple). Une fois que vous avez ajouté une région de données, vous pouvez y ajouter des champs.  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a>Pour ajouter une région de données de table et des champs à une mise en page de rapport  
  
1.  Dans la **Boîte à outils**, cliquez sur **Table**, puis sur l’aire de conception et faites glisser la souris. Le Concepteur de rapports trace une région de donnée de table composée de trois colonnes au centre de l'aire de conception.  
  
    > [!NOTE]  
    >  La **Boîte à outils** peut s’afficher sous la forme d’un onglet situé à gauche du volet **Données du rapport** . Pour ouvrir la **boîte à outils**, déplacez le pointeur sur l’onglet **boîte à outils** . Si la **boîte à outils** n’est pas visible, dans le menu **affichage** , cliquez sur **boîte à outils**.  
  
2.  Dans le volet **données du rapport** , développez le jeu de données **AdventureWorksDataSet** pour afficher les champs.  
  
3.  Faites glisser le champ Date du volet **Données du rapport** vers la première colonne de la table.  
  
     Lorsque vous déposez ce champ dans la première colonne, deux événements se produisent. En premier lieu, la cellule de données affiche le nom du champ, appelé *expression de champ*, entre crochets : `[Date]`. En second lieu, une valeur d'en-tête de colonne est automatiquement ajoutée à la ligne d'en-tête, immédiatement au-dessus de l'expression de champ. Par défaut, la colonne porte le nom du champ. Vous pouvez sélectionner le texte de la ligne d'en-tête et taper un nouveau nom.  
  
4.  Faites glisser le champ Order du volet **Données du rapport** vers la deuxième colonne de la table.  
  
5.  Faites glisser le champ Product du volet **Données du rapport** vers la troisième colonne de la table.  
  
6.  Faites glisser le champ Qty vers le bord droit de la troisième colonne jusqu'à ce que vous obteniez un curseur vertical et que le pointeur de la souris prennent la forme d'un signe plus [+]. Lorsque vous relâchez le bouton de la souris, une quatrième colonne est créée pour `[Qty]`.  
  
7.  Ajoutez le champ LineTotal de la même façon, en créant une cinquième colonne.  
  
    > [!NOTE]  
    >  L'en-tête de colonne est Line Total. Le Concepteur de rapports crée automatiquement un nom convivial pour la colonne en fractionnant LineTotal en deux mots.  
  
     Le diagramme suivant représente une région de données de table qui a été remplie avec les champs suivants : Date, Order, Product, Qty et Line Total.  
  
     ![Conception, table avec ligne d'en-tête et ligne de détails](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Conception, table avec ligne d'en-tête et ligne de détails")  
  
## <a name="preview-your-report"></a>Affichage d'un aperçu d'un rapport  
 L'affichage d'un aperçu d'un rapport vous permet de visualiser le rapport rendu sans avoir à le publier au préalable sur un serveur de rapports. Vous souhaiterez probablement afficher fréquemment des aperçus du rapport pendant sa conception. Afficher un aperçu du rapport entraîne également l'exécution de la validation au niveau de la conception et des connexions de données pour vous permettre de corriger les erreurs et les problèmes avant la publication sur un serveur de rapports.  
  
#### <a name="to-preview-a-report"></a>Pour afficher l'aperçu d'un rapport  
  
-   Cliquez sur l’onglet **Aperçu** . concepteur de rapports exécute le rapport et l’affiche en mode aperçu.  
  
     Le diagramme suivant représente une partie du rapport en mode Aperçu.  
  
     ![Aperçu, lignes de détails de table avec 5 colonnes](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Aperçu, lignes de détails de table avec 5 colonnes")  
  
     Remarquez que la devise (dans la colonne Line Total) possède six décimales après la virgule et que la date comporte un horodatage. Vous allez reprendre cette mise en forme dans la leçon suivante.  
  
> [!NOTE]  
>  Dans le menu **Fichier** , cliquez sur **Enregistrer tout** pour enregistrer le rapport.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez ajouté avec succès une région de données de table à votre rapport, ajouté des champs à la région de données et affiché un aperçu du rapport. Vous allez ensuite mettre en forme des en-têtes de colonnes et des valeurs de devise et de date. Consultez [Leçon 5 : mise en forme d’un rapport &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tables &#40;Générateur de rapports et SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
