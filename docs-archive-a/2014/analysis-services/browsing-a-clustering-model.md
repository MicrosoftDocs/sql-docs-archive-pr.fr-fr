---
title: Exploration d’un modèle de clustering | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d508603acd29fde981bddc5642b54ca9413f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602581"
---
# <a name="browsing-a-clustering-model"></a>Exploration d'un modèle de clustering
  Lorsque vous ouvrez un modèle de clustering à l’aide de l’outil **Parcourir**, le modèle est affiché dans une visionneuse interactive, similaire à la visionneuse de clustering dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Cette visionneuse vous aide à explorer les clusters qui ont été créés et à comprendre les caractéristiques de cluster. Vous pouvez également comparer des segments individuels avec d'autres segments ou avec la population, et mettre en évidence les différences.  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a>Explorer le modèle  
 La fenêtre **Parcourir** comprend les outils suivants pour vous aider à comprendre votre modèle de clustering et à explorer les attributs des groupes de données sous-jacents :  
  
-   [Diagramme de cluster](#BKMK_ClusterDiagram)  
  
-   [Profils du cluster](#BKMK_ClusterProfiles)  
  
-   [Caractéristiques du cluster](#BKMK_ClusterCharacteristics)  
  
-   [Discrimination de cluster](#BKMK_ClusterDiscrimination)  
  
 Pour expérimenter un modèle de clustering, vous pouvez utiliser les exemples de données de l’onglet formation du classeur d’exemples de données et créer un modèle de clustering à l’aide de l' [Assistant cluster &#40;compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) et toutes les valeurs par défaut.  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a>Diagramme de cluster  
 L’onglet **diagramme de cluster** affiche tous les clusters qui se trouvent dans un modèle d’exploration de données. Vous pouvez voir ici le nombre important de regroupements différents qui ont été détectés dans votre jeu de données, ainsi que leur proximité les uns par rapport aux autres.  
  
##### <a name="explore-the-cluster-diagram"></a>Explorer le diagramme de cluster  
  
1.  Cliquez sur Cluster 1 dans le diagramme.  
  
     Notez comment les lignes grises reliant tous les clusters changent pour mettre en surbrillance en bleu vif les lignes menant au cluster sélectionné.  
  
     ![introduction du diagramme de cluster](media/dm13-cluster-diagram-intro.gif "introduction du diagramme de cluster")  
  
     L'intensité de la ligne reliant un cluster à un autre représente le niveau de similarité des clusters. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires. Plus la ligne est sombre, plus la similarité entre les deux clusters est importante.  
  
2.  Cliquez et faites glisser le curseur à gauche du diagramme de cluster pour modifier le nombre de lignes affichées par la visionneuse.  
  
     Lorsque vous faites glisser le curseur vers le bas, seuls les liens les plus forts entre les clusters sont affichés. Cela vous aide à vous concentrer sur les groupes associés.  
  
3.  Notez le contrôle de **variable d’ombrage** dans l’angle supérieur droit de la fenêtre du **diagramme de cluster** .  
  
     Par défaut, il est défini sur **remplissage**. Cela signifie que les clusters les plus foncés bénéficient d'une meilleure prise en charge.  
  
4.  Placez le curseur de la souris au niveau d'un cluster.  
  
     Une info-bulle est affichée pour indiquer la population de ce cluster.  
  
5.  Maintenant, cliquez sur la liste déroulante **variable d’ombrage** et choisissez la variable **Age** . Dans ce cas, une liste de valeurs apparaît dans la zone de texte **État** .  
  
     La colonne d'âge utilisée comme entrée de ce modèle contient des valeurs numériques continues, mais pour les besoins du clustering, l'algorithme discrétise toujours les nombres. Ici, vous pouvez voir les emplacements ou les groupes créés par l’algorithme, par exemple « très faible ( \<=27)" and "Very High (> = 63) ».  
  
6.  Dans les listes déroulantes **État** , sélectionnez **très élevé** pour voir comment le diagramme change.  
  
     En modifiant la variable d'ombrage, vous pouvez voir d'un coup d'œil les clusters qui contiennent une plus grande part de cette catégorie d'âge cible, ainsi que les clusters qui contiennent très peu de clients dans cette catégorie d'âge.  
  
     ![Modifier le diagramme de cluster pour afficher l'âge](media/dm13-cluster-diagramshadebyage.gif "Modifier le diagramme de cluster pour afficher l'âge")  
  
     Plus l'ombrage est foncé, plus la proportion de l'attribut cible et la distribution de valeurs sont importantes pour ce cluster.  
  
7.  Recherchez le cluster ombré le plus foncé lorsque la **variable d’ombrage** est définie sur Age >65.  
  
     Pointez le curseur de la souris sur le cluster.  
  
     La valeur affichée dans l'info-bulle indique maintenant la population de clients de ce cluster qui ont plus de 65 ans.  
  
8.  Cliquez avec le bouton droit sur le cluster et sélectionnez **Renommer le cluster**. Tapez un nouveau nom descriptif, par exemple plus de **65**. Le nouveau nom est enregistré avec le modèle sur le serveur et peut être utilisé pour identifier le cluster dans les autres vues de clustering.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a>Profils de cluster  
 L’onglet **profils du cluster** vous permet de comparer la composition de tous les clusters en un clin d’œil. C'est le point de départ idéal pour vous familiariser avec le modèle. Cette vue sera également utile ultérieurement, si vous avez exploré un cluster particulier et que vous devez déterminer ceux qui y sont associés.  
  
 Les **profils de cluster** vous donnent également une bonne vue d’ensemble de la façon dont les clusters sont différents. Par conséquent, vous apprécierez peut-être le côté pratique de cette vue pour donner à chaque cluster un nom descriptif.  
  
##### <a name="explore-the-cluster-profiles"></a>Explorer les profils de cluster  
  
1.  Cliquez sur la cellule relative aux occupations, dans la colonne **États** , pour afficher la liste de toutes les valeurs pour profession.  
  
2.  Déplacez maintenant le curseur sur la profession dans les profils de cluster.  
  
     L'info-bulle affiche la distribution des professions dans ce cluster.  
  
     ![Afficher les valeurs détaillées dans les info-bulles ou la légende](media/dm13-cluster-profile-age-tooltip.gif "Afficher les valeurs détaillées dans les info-bulles ou la légende")  
  
     Notez que, dans certains clusters (tels que celui du graphique), la liste des professions n’est pas complète et que certaines professions sont remplacées par l’étiquette **autre**.  
  
     Cela est inhérent à la conception ; en effet, il peut être difficile de faire la différence entre plusieurs barres de petite taille dans un histogramme. Par défaut, seules les barres de la plus grande importance sont conservées et les barres restantes sont regroupées dans un **autre** compartiment gris.  
  
     Pour modifier le nombre de barres visibles dans un histogramme, utilisez l’option barres de l' **histogramme**.  
  
3.  Notez que la colonne **Age** est différente des autres. Cliquez sur le losange dans le graphique utilisé pour représenter l'âge.  
  
     La colonne Age (Âge) contenait à l'origine uniquement des nombres continus. L'algorithme de clustering requiert des valeurs discrètes ; il a donc regroupé les valeurs numériques de la colonne d'âge dans un nombre limité de tranches d'âges, en fonction de la distribution de valeurs.  
  
4.  Cliquez sur l'un des graphiques en losange dans un profil de cluster.  
  
     Ces graphiques en losange sont affichés uniquement lorsque les données sources utilisent des valeurs numériques continues. Les graphiques en losange fournissent des statistiques descriptives utiles, y compris la moyenne et l'écart type pour cette valeur dans chaque cluster :  
  
    -   La ligne dans le graphique en losange représente la plage de valeurs pour l'attribut. Les valeurs s’affichent également dans la colonne **États** à gauche du graphique **profils** .  
  
    -   Le centre du losange est positionné à la moyenne du nœud.  
  
    -   La largeur du losange représente la variance de l'attribut à ce nœud. Par conséquent, un losange plus étroit indique que le nœud peut créer une prédiction plus précise.  
  
5.  Pour libérer de l’espace dans le graphique, cliquez avec le bouton droit sur un cluster que vous n’avez pas besoin d’afficher immédiatement, puis sélectionnez **masquer la colonne**. Cela ne le supprime pas du modèle, il suffit de réduire temporairement la colonne.  
  
     Pour afficher les clusters que vous avez masqués, vous pouvez cliquer et faire glisser le bord de la colonne, ou sélectionner le nom du cluster dans la liste, **plus de clusters**.  
  
6.  Faites défiler la liste des attributs vers le bas jusqu'à ce que vous trouviez Bike Buyer, puis recherchez le cluster présentant le pourcentage le plus élevé de valeurs Oui.  
  
     Cliquez avec le bouton droit sur l’en-tête de la colonne pour le cluster que vous souhaitez renommer, sélectionnez **Renommer le cluster**et tapez **Bike**Buyers.  
  
     Le nouveau nom de cluster est persistant dans toutes les vues, et sur le serveur, jusqu'à ce que vous traitiez une nouvelle fois le modèle.  
  
     ![Renommer les clusters pour faciliter l'utilisation d'un graphique](media/dm13-cluster-rename.gif "Renommer les clusters pour faciliter l'utilisation d'un graphique")  
  
 **Conseils**  
  
-   Cliquez sur un en-tête de colonne pour trier les attributs par ordre d'importance pour ce cluster.  
  
-   Faites glisser les colonnes pour les réorganiser dans la visionneuse.  
  
-   Cliquez sur une cellule du graphique profils pour afficher des statistiques détaillées dans la **légende d’exploration de données**.  
  
-   Cliquez avec le bouton droit sur une cellule et sélectionnez **colonnes du modèle d’extraction** pour copier les données sous-jacentes dans une nouvelle feuille de calcul Excel.  
  
-   Cliquez avec le bouton droit sur l’en-tête de colonne du cluster et sélectionnez **extraction pour structurer les données** pour obtenir des informations détaillées sur les membres du cluster qui n’étaient pas inclus dans le modèle.  
  
     Par exemple, si vous profilez des clients, vous pouvez conserver les informations de contact dans les données sous-jacentes (la structure d’exploration de données) mais ne pas les inclure dans le modèle, car elles ne sont pas utiles pour l’analyse. Cependant, une fois que les clients ont été attribués à des clusters, vous pouvez afficher les informations détaillées à l'aide de l'extraction.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a>Caractéristiques du cluster  
 La vue Caractéristiques du cluster vous permet de vraiment explorer un cluster unique, afin de rechercher les attributs qui caractérisent le plus fortement ce groupe de données.  
  
##### <a name="explore-the-cluster-characteristics"></a>Explorer les caractéristiques du cluster  
  
1.  Sélectionnez le cluster **supérieur à 65** dans la liste des **clusters** .  
  
     Après avoir sélectionné un cluster, vous pouvez examiner en détail les caractéristiques qui composent ce cluster spécifique.  
  
     Les attributs contenus dans le cluster sont répertoriés dans les colonnes **Variables** et l'état de l'attribut répertorié est répertorié dans la colonne **Valeurs** .  
  
     Les États d’attribut sont répertoriés par ordre d’importance, accompagnés de leur probabilité dans ce cluster, représentés sous la forme d’une barre de couleur dans la colonne **probabilité** .  
  
     ![Caractéristiques d'un modèle de clustering](media/dm13-cluster-characteristics.gif "Caractéristiques d'un modèle de clustering")  
  
2.  Cliquez sur la colonne **variables** pour trier par attribut.  
  
     En modifiant la variable de tri, vous pouvez voir plus facilement comment les valeurs des variables telles que le revenu ou le fait d'être propriétaire d'une voiture, sont distribuées dans le groupe.  
  
3.  Cliquez sur **copier dans Excel**.  
  
     Une nouvelle feuille de calcul est ajoutée à votre classeur ; elle contient les caractéristiques du cluster sélectionné.  
  
4.  Choisissez maintenant un autre cluster dans la liste, **Bike**Buyers.  
  
5.  Cliquez sur **copier dans Excel**.  
  
     Notez que le nouveau graphique des caractéristiques du cluster est ajouté sur sa propre feuille de calcul. Vous pouvez le déplacer sur la même feuille de calcul que l’autre profil pour faciliter sa comparaison, ce que vous ferez à l’étape suivante.  
  
 **Conseils**  
  
-   Notez que la caractéristique principale du client dans le cluster plus de 65 est qu’il n’achète pas votre produit. Si vous souhaitez en connaître la raison, vous pouvez parcourir les clusters et comparer les groupes, ou vous pouvez créer un modèle associé à l'aide d'un algorithme qui se prête à l'exploration des causes et des résultats, par exemple un modèle d'arbre de décision ou un modèle Naïve Bayes.  
  
-   Si vous voulez obtenir la liste complète des attributs et des probabilités pour ce cluster (ou l'ensemble des clusters), vous pouvez créer une requête. Pour obtenir des exemples de requêtes sur des modèles de clustering, consultez [exemples de requêtes de modèle de clustering](data-mining/clustering-model-query-examples.md).  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a>Discrimination de cluster  
 Vous utilisez l’onglet **discrimination de cluster** pour comparer les attributs entre deux clusters, ou entre un cluster et tous les autres cas du jeu de données.  
  
 Pour mettre en évidence les fonctionnalités de cette visionneuse, nous allons la comparer aux tables côte à côte dans Excel que vous avez créées en fonction de la vue des **caractéristiques du cluster** .  
  
##### <a name="explore-cluster-discrimination"></a>Explorer la discrimination de cluster  
  
1.  Utilisez les listes **Cluster 1** et **Cluster 2** pour sélectionner les clusters à comparer.  
  
    -   Pour Cluster 1, sélectionnez les plus de 65 ans.  
  
    -   Pour Cluster 2, sélectionnez Bike Buyers.  
  
     La comparaison doit ressembler au graphique suivant.  
  
     ![comparaison de clusters dans un modèle](media/dm13-cluster-compareclusters.gif "comparaison de clusters dans un modèle")  
  
     Notez que, en arrière-plan, la visionneuse de **discrimination de cluster** envoie des requêtes complexes au serveur d’exploration de données, afin d’extraire les attributs les plus importants en distinguant les deux groupes, ce qui facilite la comparaison de deux ensembles de clients.  
  
2.  Cliquez sur l’une des colonnes **favorables..** ..  
  
     La barre à la droite de l'attribut et de la liste des valeurs montre les fonctionnalités ou les valeurs qui sont les plus importantes en tant que caractéristique du cluster sélectionné.  
  
3.  Comparez maintenant les listes dans Excel.  
  
     ![Diagramme de réseau de dépendances pour un modèle d'association](media/dm13-comparing-profiles-in-excel.gif "Diagramme de réseau de dépendances pour un modèle d'association")  
  
     Comme les statistiques sous-jacentes qui étaient utilisées pour créer l'image dans la visionneuse sont enregistrées dans Excel sous forme de tableaux, vous pouvez filtrer et trier, ou encore afficher les valeurs réelles de probabilité.  
  
     En plus d'utiliser Excel, nous vous recommandons d'essayer la visionneuse de cluster pour Visio, qui vous permet également non seulement d'afficher des points de données, mais aussi de modifier en profondeur et d'améliorer le graphique. Pour plus d’informations, consultez la [procédure pas à pas relative au diagramme de Cluster &#40;compléments d’exploration de données&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).  
  
 **Conseils**  
  
 Après avoir obtenu des informations sur les groupes de clients, essayez d’utiliser le [scénario de simulation &#40;les outils d’analyse de table pour excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) ou le scénario de recherche de l' [objectif &#40;les outils d’analyse de table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) Tools, afin d’explorer les facteurs du modèle qui peuvent être modifiés pour affecter le résultat.  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [Assistant de cluster &#40;des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
