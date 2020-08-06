---
title: Créer un graphique de courbes d’élévation, un graphique des bénéfices ou une matrice de classification | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], mining structures
ms.assetid: aa3d052f-58a9-4417-8e7a-5e6feb562af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 932138b37b36269bed86df42786bd5d684f75ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696332"
---
# <a name="create-a-lift-chart-profit-chart-or-classification-matrix"></a>Créer un graphique de courbes d'élévation, un graphique des bénéfices ou une matrice de classification
  Vous pouvez créer un graphique d'analyse de précision pour un modèle d'exploration de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en cinq étapes de base :  
  
-   Sélectionnez la structure d'exploration de données contenant les modèles d'exploration de données à comparer.  
  
-   Sélectionnez les modèles d'exploration de données à ajouter au graphique.  
  
-   Spécifiez une source de données de test à utiliser pour générer le graphique.  
  
-   Choisissez le type de graphique.  
  
-   Configurez les options du graphique.  
  
 Ces étapes de base sont les mêmes pour le graphique de courbes d'élévation, le graphique des bénéfices et la matrice de classification. Les procédures suivantes présentent les étapes à suivre pour configurer les options des graphiques de base pour ces types de graphiques. Pour plus d’informations sur la création d’un rapport de validation croisée, consultez [Mesures dans le rapport de validation croisée](measures-in-the-cross-validation-report.md).  
  
### <a name="open-the-mining-structure-in-the-accuracy-chart-designer"></a>Ouvrir la structure d'exploration de données dans le concepteur graphique d'analyse de précision  
  
1.  Ouvrez le Concepteur d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur la structure qui contient le ou les modèles d'exploration de données.  
  
3.  Cliquez sur l'onglet **Graphique d'analyse de précision de l'exploration de données** .  
  
### <a name="select-mining-models-for-inclusion-in-the-chart"></a>Sélectionner des modèles d'exploration de données à inclure dans le graphique  
  
1.  Sous l'onglet **Graphique d'analyse de précision de l'exploration de données** du Concepteur d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur l'onglet **Sélection d'entrée** .  
  
     La liste affiche tous les modèles dans la structure actuelle qui ont le même attribut prédictible.  
  
2.  Activez la case à cocher **Afficher** pour chaque modèle à inclure dans le graphique.  
  
3.  Cliquez sur la zone de texte **Nom de la colonne prédictible** et sélectionnez le nom d'une colonne prédictible dans la liste. Tous les modèles que vous incluez dans un graphique doivent avoir la même colonne prédictible.  
  
4.  Si vous comparez deux modèles et que les colonnes prédictibles ont des valeurs différentes ou des types de données différents, désactivez la case à cocher **Synchroniser les colonnes de prédiction et les valeurs** pour forcer une comparaison.  
  
    > [!NOTE]  
    >  Si la case à cocher **Synchroniser les colonnes de prédiction et les valeurs** est activée, Analysis Services analyse les données dans les colonnes prédictibles du modèle et les données de test, puis tente de trouver la meilleure correspondance. Par conséquent, ne désactivez pas la case à cocher sauf en cas d'absolue nécessité pour forcer une comparaison des colonnes.  
  
5.  Cliquez sur la zone de texte **Prédire la valeur** et sélectionnez une valeur dans la liste. Si la colonne prédictible est un type de données continu, vous devez taper une valeur dans la zone de texte.  
  
     Pour plus d’informations, consultez [Choisir la colonne à utiliser pour tester un modèle d’exploration de données](choose-the-column-to-use-for-testing-a-mining-model.md).  
  
### <a name="select-testing-data"></a>Sélectionner des données de test  
  
1.  Sous l'onglet **Sélection d'entrée** de l'onglet **Graphique d'analyse de précision de l'exploration de données** , spécifiez la source des données à utiliser pour générer le graphique en sélectionnant l'une des options dans le groupe, **Sélectionner le jeu de données à utiliser pour le graphique d'analyse de précision**.  
  
    -   Sélectionnez l'option **Utiliser des scénarios de test de modèle d'exploration de données**, si vous souhaitez utiliser le sous-ensemble de scénarios défini par l'intersection des scénarios de test de la structure d'exploration de données et les filtres qui ont pu être appliqués lors de la création du modèle.  
  
    -   Sélectionnez l'option **Utiliser des scénarios de test de structure d'exploration de données**, pour utiliser le jeu complet de scénarios de test définis dans le jeu de données d'exclusion des structures d'exploration de données.  
  
    -   Sélectionnez l’option **Spécifier un autre jeu de données**si vous souhaitez utiliser des données externes.  Le jeu de données doit être disponible comme vue de source de données.   Cliquez sur le bouton Parcourir (**...**) pour choisir les tables de données à utiliser pour le graphique d’exactitude. Pour plus d’informations, consultez [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md).  
  
         Si vous utilisez un jeu de données externes, vous pouvez éventuellement filtrer le jeu de données d'entrée. Pour plus d’informations, consultez [Appliquer des filtres aux données de test du modèle](apply-filters-to-model-testing-data.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas créer de filtre sur les cas de test de modèle ou les cas de test de la structure d’exploration de données sous l’onglet **sélection d’entrée** . Pour créer un filtre sur le modèle d’exploration de données, modifiez la propriété Filter du modèle. Pour plus d’informations, consultez [Appliquer un filtre à un modèle d’exploration de données](apply-a-filter-to-a-mining-model.md).  
  
### <a name="configure-chart-settings-and-generate-the-chart"></a>Configurer les paramètres du graphique et générer le graphique  
  
1.  Sous l'onglet **Graphique d'analyse de précision de l'exploration de données** , cliquez sur l'onglet correspondant au graphique à créer.  
  
2.  Pour un **graphique de courbes d’élévation**, cliquez sur l’onglet **graphique de courbes d’élévation** . Le graphique est automatiquement généré en fonction du modèle, des attributs prévisibles et des données d’entrée que vous venez de sélectionner.  
  
3.  Pour une **matrice de classification**, cliquez sur l’onglet **matrice de classification** . Aucun autre paramètre n’est nécessaire. le graphique est automatiquement généré en fonction des données d’entrée et du modèle que vous avez sélectionnés.  
  
4.  Pour un **graphique des bénéfices**, cliquez d’abord sur l’onglet **graphique de courbes d’élévation** . Ensuite, dans la liste déroulante **type de graphique** , sélectionnez **graphique des bénéfices**.  
  
     Entrez les paramètres suivants dans la boîte de dialogue **Paramètres du graphique des bénéfices** .  
  
     **Habitants**  
     Nombre de cas du jeu de données que vous voulez utiliser lors de la création du graphique de courbes d'élévation.  
  
     Le modèle choisit toujours les cas par ordre décroissant de probabilité ; en d'autres termes, si vous évaluez des clients potentiels et que vous choisissez un nombre qui représente uniquement la moitié des enregistrements de votre base de données de clients, le modèle mesurera la précision sur le sous-ensemble des cas les mieux adaptés à votre modèle.  
  
     En effet, lorsque vous utilisez le modèle pour générer un publipostage ou créer une campagne, vous utiliserez la probabilité de prédiction associée à chaque cas pour cibler uniquement les clients qui ont la probabilité la plus élevée de faire une réponse positive.  
  
     **Coût fixe**  
     Coût fixe associé au problème professionnel.  
  
     S'il s'agit d'une solution de publipostage ciblé, le coût fixe peut représenter des frais de configuration de l'imprimante qui couvrent le coût initial de préparation du publipostage promotionnel.  
  
     Ce coût s'applique une fois à l'ensemble de la population cible.  
  
     **Coût individuel**  
     Coûts s'ajoutant au coût fixe, qui peuvent être associés à chaque client contacté. Par exemple, vous pouvez entrer le coût d'affranchissement pour un publipostage promotionnel ou le coût des appels téléphoniques.  
  
     Ce coût doit être le même pour l'ensemble de la population cible. Chaque valeur est multipliée par le nombre de cas ciblés.  
  
     **Revenu par personne**  
     Revenu associé à chaque vente réussie.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de courbes d’élévation &#40;Analysis Services d’exploration de données&#41;](lift-chart-analysis-services-data-mining.md)   
 [Matrice de classification &#40;Analysis Services - Exploration de données&#41;](classification-matrix-analysis-services-data-mining.md)  
  
  
