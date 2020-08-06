---
title: Créer une requête singleton de prédiction à partir d’un modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80e853875cce349dd8623fab3c30f1ad09bfbf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601783"
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a>Créer une requête singleton de prédiction à partir d'un modèle
  Une requête singleton est utile lorsque vous avez un modèle que vous souhaitez utiliser pour la prédiction, mais que vous ne souhaitez pas le mapper à un jeu de données d’entrée externe ou effectuer des prédictions en bloc. Avec une requête singleton, vous pouvez fournir une ou plusieurs valeurs au modèle et immédiatement consulter la valeur prédite.  
  
 Par exemple, la requête DMX suivante représente une requête singleton sur le modèle de publipostage ciblé TM_Decision_Tree.  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 La procédure qui suit explique comment utiliser l'Explorateur de modèles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer rapidement cette requête.  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a>Pour ouvrir les modèles Analysis Services dans SQL Server Management Studio  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Cliquez sur l’icône du cube pour ouvrir les modèles **Analysis Server**.  
  
### <a name="to-open-a-prediction-query-template"></a>Pour ouvrir un modèle de requête de prédiction  
  
1.  Dans la liste de modèles Analysis Server de **l’Explorateur de modèles**, développez **DMX**, puis **Requêtes de prédiction**.  
  
2.  Double-cliquez sur **Prédiction singleton**.  
  
3.  Dans la boîte de dialogue **Se connecter à Analysis Services** , tapez le nom du serveur qui dispose de l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenant le modèle d'exploration de données à interroger.  
  
4.  Cliquez sur **Connecter**.  
  
5.  Le modèle s'ouvre dans la base de données spécifiée, avec un modèle d'exploration de données Explorateur d'objets qui contient des fonctions d'exploration de données et une liste de structures d'exploration de données et de modèles connexes.  
  
### <a name="to-customize-the-singleton-query-template"></a>Pour personnaliser le modèle de requête singleton  
  
1.  Dans le modèle, cliquez sur la liste déroulante **Bases de données disponibles** , puis sélectionnez une instance d’Analysis Service dans la liste.  
  
2.  Dans la liste **Modèle d'exploration de données** , sélectionnez le modèle d'exploration de données à interroger.  
  
     La liste des colonnes dans le modèle d'exploration de données s'affiche dans le volet **Métadonnées** de l'Explorateur d'objets.  
  
3.  Dans le menu **Requête** , sélectionnez **Spécifier les valeurs des paramètres du modèle**.  
  
4.  Dans la ligne **liste de sélection** , tapez * pour retourner toutes les colonnes, ou tapez une liste de colonnes et d’expressions délimitée par des virgules pour retourner des colonnes spécifiques.  
  
     Si vous tapez *, la colonne prédictible est retournée, ainsi que toutes les colonnes auxquelles vous fournissez de nouvelles valeurs à l'étape 6.  
  
     Pour l’exemple de code présenté au début de cette rubrique, la ligne de **liste de sélection** a la valeur *.  
  
5.  Dans la ligne **modèle d'exploration de données** , tapez le nom du modèle d'exploration de données extrait de la liste des modèles d'exploration de données qui apparaissent dans l' **Explorateur d'objets**.  
  
     Pour l’exemple de code présenté au début de cette rubrique, la ligne du **modèle d’exploration de données** a été définie sur le nom, `TM_Decision_Tree` .  
  
6.  Dans la ligne **valeur** , tapez la nouvelle valeur des données pour lesquelles vous souhaitez effectuer une prédiction.  
  
     Pour l’exemple de code présenté au début de cette rubrique, la ligne **valeur** a été définie sur `2` pour prédire le comportement d’achat de vélo en fonction du nombre d’enfants à la base.  
  
7.  Dans la ligne **colonne** , tapez le nom de la colonne du modèle d'exploration de données à laquelle les nouvelles données doivent être mappées.  
  
     Pour l’exemple de code présenté au début de cette rubrique, la ligne de la **colonne** a la valeur `Number Children at Home` .  
  
    > [!NOTE]  
    >  Lorsque vous utilisez la boîte de dialogue **Spécifier les valeurs des paramètres du modèle** , vous n'avez pas besoin de mettre le nom de colonne entre crochets. Les crochets seront ajoutés automatiquement.  
  
8.  Laissez l' **alias d’entrée** sous la forme `t` .  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Dans le volet de texte de requête, recherchez le tilde rouge sous la virgule et les points de suspension qui indiquent une erreur de syntaxe. Supprimez les points de suspension et ajoutez une condition de requête supplémentaire de votre choix. Si vous n'ajoutez pas d'autres conditions, supprimez la virgule.  
  
     Dans l’exemple de code présenté au début de cette rubrique, la condition de requête supplémentaire a la valeur `'45' as [Age]`.  
  
11. Cliquez sur **Exécuter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de prédictions &#40;Didacticiel sur l’exploration de données de base&#41;](../../tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
  
