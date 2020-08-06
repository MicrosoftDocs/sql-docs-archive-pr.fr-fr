---
title: Définition et utilisation d’une action d’extraction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ea19a9721d87936bc88b5401c71ee550a47bc1ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698724"
---
# <a name="defining-and-using-a-drillthrough-action"></a>Définition et utilisation d'une action d'extraction
  Le dimensionnement des données de fait par une dimension de fait sans filtrage correct des données retournées par la requête peut ralentir les performances des requêtes. Pour éviter ceci, vous pouvez définir une action d'extraction qui restreint le nombre total de lignes retournées. Cela améliorera considérablement les performances des requêtes.  
  
 Dans les tâches de cette rubrique, vous définissez une action d'extraction pour retourner des informations détaillées sur les commandes pour les ventes à des clients via Internet.  
  
## <a name="defining-the-drillthrough-action-properties"></a>Définition des propriétés d'une action d'extraction  
  
1.  Ouvrez le Concepteur de cube pour le cube du didacticiel de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur l’onglet **Actions** .  
  
     L’onglet **Actions** comporte plusieurs volets. Sur le côté gauche de l’onglet se trouvent le volet **Organisateur d’action** et le volet **Outils de calcul** . À droite de ces deux volets se trouve le volet de **visualisation** , qui contient les détails de l’action qui est sélectionnée dans le volet **Organisateur d’action** .  
  
     L’image suivante montre l’onglet **Actions** du Concepteur de cube.  
  
     ![Onglet Actions du Concepteur de cube](../../2014/tutorials/media/l8-action1.gif "Onglet Actions du Concepteur de cube")  
  
2.  Dans la barre d’outils de l’onglet **Actions** , cliquez sur le bouton **Nouvelle action d’extraction** .  
  
     Un modèle d'action vide apparaît dans le volet de visualisation.  
  
     ![Modèle d'action vide dans le volet d'informations](../../2014/tutorials/media/l8-action2.gif "Modèle d'action vide dans le volet d'informations")  
  
3.  Dans la zone **nom** , remplacez le nom de cette action par `Internet Sales Details Drillthrough Action` .  
  
4.  Dans la liste **Membres de groupe de mesures** , sélectionnez **Internet Sales**.  
  
5.  Dans la zone **Colonnes d’extraction** , sélectionnez **Internet Sales Order Details** dans la liste **Dimensions** .  
  
6.  Dans la liste **Colonnes de retour** , cochez les cases **Item Description** et **Order Number** , puis cliquez sur **OK**. L'image suivante montre le modèle d'action tel qu'il doit se présenter à ce stade de la procédure.  
  
     ![Zone Colonnes d'extraction](../../2014/tutorials/media/l8-action3.gif "Zone Colonnes d'extraction")  
  
7.  Développez la zone **Propriétés supplémentaires** , comme le montre l’image suivante.  
  
     ![Zone Propriétés supplémentaires](../../2014/tutorials/media/l8-action4.gif "Zone Propriétés supplémentaires")  
  
8.  Dans la zone **nombre maximal de lignes** , tapez `10` .  
  
9. Dans la zone **légende** , tapez `Drillthrough to Order Details...` .  
  
     Ces paramètres limitent le nombre de lignes retournées et spécifient la légende qui apparaît dans le menu de l'application cliente. L’image suivante montre ces paramètres dans la zone **Propriétés supplémentaires** .  
  
     ![Zone Propriétés supplémentaires](../../2014/tutorials/media/l8-action5.gif "Zone Propriétés supplémentaires")  
  
## <a name="using-the-drillthrough-action"></a>Utilisation de l'action d'extraction  
  
1.  Dans le menu **Générer** , cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Une fois le déploiement terminé, cliquez sur l’onglet **Navigateur** dans le Concepteur de cube pour le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Reconnexion** .  
  
3.  Démarrez Excel.  
  
4.  Ajoutez la mesure **Internet Sales-Sales Amount** à la zone Valeurs.  
  
5.  Ajoutez la hiérarchie définie par l’utilisateur **Customer Geography** à partir du dossier **Location** de la dimension **Customer** à la zone **Filtre de rapport** .  
  
6.  Dans le tableau croisé dynamique, dans **Customer Geography**, ajoutez un filtre qui sélectionne un seul client. Développez successivement **All Customers**, **Australia**, **Queensland**, **Brisbane**et **4000**, cochez la case **Adam Powell**, puis cliquez sur **OK**.  
  
     Les ventes totales de produits par [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] à Adam Powell sont affichées dans la zone de données.  
  
7.  Cliquez avec le bouton droit sur le montant des ventes, pointez sur **Actions supplémentaires**, puis cliquez sur **Drillthrough to Order Details**.  
  
     Les détails des commandes qui ont été expédiées à Adam Powell sont affichés dans la **Visionneuse des données d’exemple**, comme le montre l’image suivante. Cependant, certains détails supplémentaires pourraient être utiles, par exemple la date de la commande, la date de livraison prévue et la date d'expédition. Dans la procédure suivante, vous allez ajouter ces détails supplémentaires.  
  
     ![Commandes expédiées à Adam Powell](../../2014/tutorials/media/l8-action6.gif "Commandes expédiées à Adam Powell")  
  
8.  Fermez Excel.  
  
## <a name="modifying-the-drillthrough-action"></a>Modification de l'action d'extraction  
  
1.  Ouvrez le Concepteur de dimensions pour la dimension **Internet Sales Order Details** .  
  
     Observez que trois attributs seulement ont été définis pour cette dimension.  
  
2.  Dans le volet **Vue de source de données** , cliquez avec le bouton droit dans une zone ouverte, puis cliquez sur **Afficher toutes les tables**.  
  
3.  Dans le menu **Format** , pointez sur **Disposition automatique** , puis cliquez sur **Diagramme**.  
  
4.  Localisez la table **InternetSales (dbo.FactInternetSales)** en cliquant avec le bouton droit dans une zone ouverte du volet **Vue de source de données** . Puis, cliquez sur **Rechercher une table** , cliquez sur **InternetSales** et cliquez sur **OK**.  
  
5.  Créez les nouveaux attributs basés sur les colonnes suivantes :  
  
    -   OrderDateKey  
  
    -   DueDateKey  
  
    -   ShipDateKey  
  
6.  Affectez à la propriété **nom** de l’attribut **Order Date Key** la valeur `Order Date` , cliquez sur le bouton Parcourir pour la propriété **colonne de nom** , et dans la boîte de dialogue **colonne de nom** , sélectionnez **Date** comme table source et sélectionnez SimpleDate comme colonne source. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Modifiez la propriété de **nom** de l’attribut de **clé de date d’échéance** sur, puis `Due Date` , en utilisant la même méthode que l’attribut **Order Date Key** , remplacez la valeur de la propriété **Name Column** de cet attribut par **date. SimpleDate (WCHAR)**.  
  
8.  Remplacez la propriété **Name** de l’attribut **Ship Date Key** par `Ship Date` , puis remplacez la propriété **Name Column** de cet attribut par **date. SimpleDate (WCHAR)**.  
  
9. Sélectionnez l’onglet **Actions** du Concepteur de cube pour le cube du didacticiel de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
10. Dans la zone **Colonnes d’extraction** , cochez les cases pour ajouter les colonnes suivantes à la liste **Colonnes de retour** , puis cliquez sur **OK**:  
  
    -   Order Date  
  
    -   Due Date  
  
    -   Ship Date  
  
     L'image suivante montre ces colonnes sélectionnées.  
  
     ![Zone Colonnes d'extraction](../../2014/tutorials/media/l8-action7.gif "Zone Colonnes d'extraction")  
  
## <a name="reviewing-the-modified-drillthrough-action"></a>Vérification de l'action d'extraction modifiée  
  
1.  Dans le menu **Générer** , cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Une fois le déploiement terminé, cliquez sur l’onglet **Navigateur** dans le Concepteur de cube pour le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Reconnexion** .  
  
3.  Démarrez Excel.  
  
4.  Recréez le tableau croisé dynamique à l’aide de **Internet Sales-Sales Amount** dans la zone Valeurs et **Customer Geography** dans le Filtre de rapport.  
  
     Ajoutez un filtre qui sélectionne **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**et **Adam Powell**.  
  
5.  Cliquez sur la cellule de données **Internet Sales-Sales Amount** , pointez sur **Actions supplémentaires**, puis cliquez **Drillthrough to Order Details**.  
  
     Les détails des commandes expédiées à Adam Powell sont affichés dans la feuille de calcul temporaire. Cela inclut une description de l'article, le numéro de commande, la date de commande, la date d'échéance et la date de livraison, comme illustré dans l'image suivante.  
  
     ![Commandes expédiées à Adam Powell](../../2014/tutorials/media/l8-action8.gif "Commandes expédiées à Adam Powell")  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 9 : Définition de perspectives et de traductions](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Actions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)   
 [Actions dans les modèles multidimensionnels](multidimensional-models/actions-in-multidimensional-models.md)   
 [Relations de dimension](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Définition d’une relation de faits](lesson-5-2-defining-a-fact-relationship.md)   
 [Définir une relation de fait et des propriétés de relation de fait](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
