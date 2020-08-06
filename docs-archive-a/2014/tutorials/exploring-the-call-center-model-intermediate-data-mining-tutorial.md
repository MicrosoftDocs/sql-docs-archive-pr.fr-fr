---
title: Exploration du modèle de centre d’appels (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703556"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>Exploration du modèle de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous avez généré le modèle exploratoire, vous pouvez l'utiliser pour en savoir plus sur vos données à l'aide des outils suivants fournis dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   [Visionneuse de réseau neuronal Microsoft](#bkmk_NNviewer) **:** cette visionneuse est disponible sous l’onglet **visionneuse de modèle d’exploration** de données du concepteur d’exploration de données. elle est conçue pour vous aider à expérimenter les interactions dans les données.  
  
-   [Visionneuse de l’arborescence de contenu générique Microsoft](#bkmk_genviewer) **:** cette visionneuse standard fournit des détails détaillés sur les modèles et les statistiques découverts par l’algorithme lorsqu’il a généré le modèle.  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a>Visionneuse de réseau neuronal Microsoft  
 La visionneuse comporte trois volets : **entrée**, **sortie**et **variables**.  
  
 À l’aide du volet **sortie** , vous pouvez sélectionner des valeurs différentes pour l’attribut prévisible ou la variable dépendante. Si votre modèle contient plusieurs attributs prévisibles, vous pouvez sélectionner l’attribut dans la liste **attribut de sortie** .  
  
 Le volet **variables** compare les deux résultats que vous avez choisis en termes d’attributs de contribution ou de variables. Les barres de couleur représentent visuellement dans quelle mesure la variable affecte les résultats cibles. Vous pouvez également afficher les variables sous forme de scores de finesse. Un score de finesse est calculé différemment en fonction du type de modèle d'exploration de données utilisé, mais il indique généralement l'amélioration apportée au modèle lorsque cet attribut est utilisé pour la prédiction.  
  
 Le volet **entrée** vous permet d’ajouter des influenceurs au modèle pour essayer plusieurs scénarios de simulation.  
  
### <a name="using-the-output-pane"></a>Utilisation du volet Sortie  
 Dans ce modèle initial, vous voulez voir comment divers facteurs affectent le niveau de service. Pour ce faire, vous pouvez sélectionner le niveau de service dans la liste des attributs de sortie, puis comparer différents niveaux de service en sélectionnant des plages dans les listes déroulantes pour **valeur 1** et **valeur 2**.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>Pour comparer les niveaux de service les plus bas et les plus élevés  
  
1.  Pour **valeur 1**, sélectionnez la plage avec les valeurs les plus basses. Par exemple, la plage 0-0-0.7 représente les taux d'abandon les plus bas, et par conséquent le meilleur niveau de service.  
  
    > [!NOTE]  
    >  Les valeurs exactes de cette plage peuvent varier en fonction de la façon dont vous avez configuré le modèle.  
  
2.  Pour **valeur 2**, sélectionnez la plage avec les valeurs les plus élevées. Par exemple, la plage avec la valeur >= 0,12 représente les taux d’abandon les plus élevés, et par conséquent le plus mauvais niveau de service. En d'autres termes, 12 % des clients qui ont téléphoné pendant le temps de travail de cette équipe ont raccroché avant de parler à un commercial.  
  
     Le contenu du volet **variables** est mis à jour pour comparer les attributs qui contribuent aux valeurs de résultat. Par conséquent, la colonne de gauche vous montre les attributs associés au meilleur niveau de service, et la colonne de droite vous montre ceux associés au niveau de service le moins bon.  
  
### <a name="using-the-variables-pane"></a>Utilisation du volet Variables  
 Dans ce modèle, il apparaît qu’il s' `Average Time Per Issue` agit d’un facteur important. Cette variable indique la durée moyenne nécessaire pour répondre à un appel, quel que soit le type d'appel.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>Pour afficher et copier la probabilité et les scores de finesse pour un attribut  
  
1.  Dans le volet **variables** , placez la souris sur la barre de couleur de la première ligne.  
  
     Cette barre de couleur vous indique la manière dont `Average Time Per Issue` contribue à atteindre le niveau de service. L'info-bulle affiche un score global, des probabilités et des scores de finesse pour chaque combinaison d'une variable et d'un résultat cible.  
  
2.  Dans le volet **variables** , cliquez avec le bouton droit sur une barre de couleur et sélectionnez **copier**.  
  
3.  Dans une feuille de calcul Excel, cliquez avec le bouton droit sur n’importe quelle cellule et sélectionnez **coller**.  
  
     Le rapport est collé sous forme de table HTML et affiche uniquement les scores correspondant à chaque barre.  
  
4.  Dans une autre feuille de calcul Excel, cliquez avec le bouton droit sur n’importe quelle cellule et sélectionnez **Collage spécial**.  
  
     Le rapport est collé au format texte et inclut les statistiques associées décrites dans la section suivante.  
  
### <a name="using-the-input-pane"></a>Utilisation du volet Entrée  
 Supposons que vous souhaitiez examiner l'incidence d'un facteur spécifique, tel que l'équipe ou le nombre d'opérateurs. Vous pouvez sélectionner une variable particulière à l’aide du volet **entrée** , et le volet **variables** est mis à jour automatiquement pour comparer les deux groupes précédemment sélectionnés en fonction de la variable spécifiée.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>Pour passer en revue l'incidence de la modification des attributs d'entrée sur le niveau de service  
  
1.  Dans le volet **entrée** , pour **attribut**, sélectionnez Shift.  
  
2.  Pour **valeur**, sélectionnez **am**.  
  
     Le volet **variables** est mis à jour pour afficher l’impact sur le modèle lorsque le décalage est **am**. Toutes les autres sélections restent les mêmes : vous comparez toujours les niveaux de service les plus bas et les plus élevés.  
  
3.  Pour **valeur**, sélectionnez **PM1**.  
  
     Le volet **variables** est mis à jour pour afficher l’impact sur le modèle lorsque le déplacement change.  
  
4.  Dans le volet **entrée** , cliquez sur la ligne vide suivante sous **attribut**, puis sélectionnez appels. Pour **valeur**, sélectionnez la plage qui indique le plus grand nombre d’appels.  
  
     Une nouvelle condition d'entrée est ajoutée à la liste. Le volet **variables** est mis à jour pour montrer l’impact sur le modèle pour une équipe particulière lorsque le volume d’appels est le plus élevé.  
  
5.  Continuez à modifier les valeurs de Shift (Équipe) et de Calls (Appels) afin de rechercher les corrélations intéressantes entre l'équipe, le volume d'appels et le niveau de service.  
  
    > [!NOTE]  
    >  Pour effacer le volet **entrée** afin de pouvoir utiliser des attributs différents, cliquez sur **Actualiser le contenu de la visionneuse**.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>Interprétation des statistiques fournies dans la visionneuse  
 Des temps d'attente plus longs sont un prédicteur fort d'un taux d'abandon élevé, ce qui correspond à un niveau de service médiocre. Cela peut sembler être une conclusion évidente ; toutefois, le modèle d'exploration de données vous fournit des données statistiques supplémentaires afin de vous aider à interpréter ces tendances.  
  
-   **Score**: valeur qui indique l’importance globale de cette variable pour la différenciation entre les résultats. Plus le score est élevé, plus l'incidence de la variable sur le résultat est importante.  
  
-   **Probabilité de valeur 1**: pourcentage qui représente la probabilité de cette valeur pour ce résultat.  
  
-   **Probabilité de valeur 2**: pourcentage qui représente la probabilité de cette valeur pour ce résultat.  
  
-   **Élévation pour valeur 1** et **élévation pour valeur 2**: scores qui représente l’impact de l’utilisation de cette variable particulière pour la prédiction des résultats de valeur 1 et de valeur 2. Plus le score est élevé, plus la variable est appropriée pour prédire les résultats.  
  
 Le tableau suivant contient des exemples de valeurs pour les principaux facteurs d'influence. Par exemple, la **probabilité de la valeur 1** est de 60,6% et la **probabilité de la valeur 2 est de** 8,30%, ce qui signifie que lorsque la durée moyenne par problème est comprise entre 44-70 minutes, 60,6% des cas ont été décalés avec les niveaux de service les plus élevés (valeur 1 8,30)  
  
 Vous pouvez tirer des conclusions de cette information. Un temps de réponse aux appels plus court (plage 44-70) contribue fortement à un meilleur niveau de service (plage 0.00-0.07). Le score (92.35) vous indique que cette variable est très importante.  
  
 Toutefois, lorsque vous parcourez la liste des facteurs contributeurs, vous voyez d'autres facteurs dont les effets sont plus subtils et plus difficiles à interpréter. Par exemple, l'équipe semble avoir une influence sur le service, mais les scores de finesse et les probabilités relatives indiquent que l'équipe n'est pas un facteur majeur.  
  
|Attribut|Valeur|Privilégie \< 0,07|Privilégie >= 0,12|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89,087-120,000||Score : 100<br /><br /> Probabilité de value1:4,45%<br /><br /> Probabilité de value2:51,94%<br /><br /> Finesse pour Value1 : 0.19<br /><br /> Élévation pour value2:1,94|  
|Average Time Per Issue|44,000-70,597|Score : 92.35<br /><br /> Probabilité de Value1 : 60.06 %<br /><br /> Probabilité de Value2 : 8,30 %<br /><br /> Finesse pour Value1 : 2.61<br /><br /> Finesse pour Value2 : 0.31||  
  
 [Retour au début](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a>Visionneuse de l’arborescence de contenu générique Microsoft  
 Cette visionneuse peut être utilisée pour afficher des informations encore plus détaillées créées par l'algorithme lors du traitement du modèle. La **visionneuse de l’arborescence de contenu MicrosoftGeneric** représente le modèle d’exploration de données sous la forme d’une série de nœuds, où chaque nœud représente les connaissances apprises sur les données d’apprentissage. Cette visionneuse peut être utilisée avec tous les modèles, mais le contenu des nœuds est différent en fonction du type de modèle.  
  
 Pour les modèles de réseau neuronal ou les modèles de régression logistique, vous pouvez rechercher le nœud des statistiques marginales (`marginal statistics node`), qui est particulièrement utile. Ce nœud contient des statistiques dérivées sur la distribution des valeurs dans vos données. Ces informations peuvent être utiles si vous voulez obtenir un résumé des données sans avoir à écrire de nombreuses requêtes T-SQL. Le graphique des valeurs de placement dans un conteneur dans la rubrique précédente a été dérivé du nœud des statistiques marginales.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>Pour obtenir un résumé des valeurs de données à partir du modèle d'exploration de données  
  
1.  Dans le concepteur d’exploration de données, sous l’onglet **visionneuse de modèle d’exploration** de données, sélectionnez \<mining model name> .  
  
2.  Dans la liste **visionneuse** , sélectionnez **visionneuse de l’arborescence de contenu générique Microsoft**.  
  
     La vue du modèle d'exploration de données est actualisée pour afficher une hiérarchie de nœuds dans le volet gauche et une table HTML dans le volet droit.  
  
3.  Dans le volet **légende du nœud** , cliquez sur le nœud qui porte le nom 10000000000000000.  
  
     Le nœud de niveau supérieur de tout modèle est toujours le nœud racine du modèle. Dans un modèle de réseau neuronal ou de régression logistique, le nœud situé immédiatement sous ce nœud est le nœud des statistiques marginales.  
  
4.  Dans le volet **Détails du nœud** , faites défiler vers le haut jusqu’à ce que vous trouviez la ligne, NODE_DISTRIBUTION.  
  
5.  Faites défiler le tableau NODE_DISTRIBUTION pour afficher la distribution des valeurs calculées par l’algorithme de réseau neuronal.  
  
 Pour utiliser ces données dans un rapport, vous pouvez sélectionner puis copier les informations correspondant à des lignes spécifiques, ou utiliser la requête DMX (Data Mining Extensions) suivante pour extraire le contenu complet du nœud.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 Vous pouvez également utiliser la hiérarchie de nœuds et les détails de la table NODE_DISTRIBUTION pour parcourir des chemins d'accès individuels dans le réseau neuronal et afficher des statistiques provenant de la couche masquée. Pour plus d’informations, consultez [exemples de requêtes de modèle de réseau neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 [Retour au début](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Ajout d’un modèle de régression logistique à la structure du centre d’appels &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu du modèle d’exploration de données pour les modèles de réseau neuronal &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Exemples de requêtes de modèle de réseau neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Informations techniques de référence sur l’algorithme Microsoft neuronal Network](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Modifier la discrétisation d'une colonne dans un modèle d'exploration de données](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
