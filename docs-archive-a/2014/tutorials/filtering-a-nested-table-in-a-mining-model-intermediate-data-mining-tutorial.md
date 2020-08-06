---
title: Filtrage d’une table imbriquée dans un modèle d’exploration de données (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1e6ce2936a3c6763ea41999b2724c0fe8c79301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706919"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>Filtrage d'une table imbriquée dans un modèle d'exploration de données (Didacticiel sur l'exploration de données intermédiaire)
  Après avoir créé et exploré le modèle, vous décidez de vous concentrer sur un sous-ensemble des données des clients. Par exemple, vous pouvez souhaiter analyser uniquement les paniers qui contiennent un article spécifique ou les caractéristiques démographiques des clients qui n'ont rien acheté pendant une certaine période.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] permet de filtrer les données utilisées dans un modèle d'exploration de données. Cette fonctionnalité est utile, car vous n’avez pas besoin de configurer une nouvelle vue de source de données pour utiliser des données différentes. Dans le didacticiel sur l'exploration de données de base, vous avez appris à filtrer des données provenant d'une table plate en appliquant des conditions à la table de cas. Au cours de cette tâche, vous allez créer un filtre qui s'applique à une table imbriquée.  
  
## <a name="filters-on-nested-vs-case-tables"></a>Filtres sur des tables imbriquées ou des tables de cas  
 Si votre vue de source de données contient une table de cas et une table imbriquée, à l'instar de la vue de source de données utilisée dans le modèle Association, vous pouvez effectuer un filtrage sur les valeurs de la table de cas, sur la présence ou l'absence d'une valeur dans la table imbriquée ou sur une combinaison des deux.  
  
 Au cours de cette tâche, vous allez d'abord effectuer une copie du modèle Association, puis ajouter les attributs IncomeGroup et Region au nouveau modèle associé, afin de pouvoir filtrer ces attributs dans la table de cas.  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>Pour créer et modifier une copie du modèle Association  
  
1.  Sous l’onglet **modèles d’exploration de données** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , cliquez avec le bouton droit sur le `Association` modèle, puis sélectionnez **nouveau modèle d’exploration de données**.  
  
2.  Pour le **nom du modèle**, tapez `Association Filtered` . Pour **nom de l’algorithme**, sélectionnez **règles d’association Microsoft**. Cliquez sur **OK**.  
  
3.  Dans la colonne du modèle Association filtrée, cliquez sur la ligne IncomeGroup et remplacez la valeur **Ignorer** par **entrée**.  
  
 Ensuite, vous allez créer un filtre sur la table de cas dans le nouveau modèle Association. Le filtre va passer au modèle uniquement les clients inclus dans la région cible ou possédant le niveau de revenu cible. Ensuite, vous allez ajouter un deuxième jeu de conditions de filtre pour spécifier que le modèle utilise uniquement les clients dont les paniers ont contenu au moins un article.  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>Pour ajouter un filtre à un modèle d'exploration de données  
  
1.  Dans l’onglet **modèles d’exploration de données** , cliquez avec le bouton droit sur l’Association de modèle filtrée, puis sélectionnez définir le filtre de **modèle**.  
  
2.  Dans la boîte de dialogue **Filtre de modèle** , cliquez sur la ligne supérieure dans la grille, dans la zone de texte **Colonne de la structure d'exploration de données** .  
  
3.  Dans la zone de texte colonne de la **structure d’exploration de données** , sélectionnez IncomeGroup.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est une colonne.  
  
4.  Cliquez sur la zone de texte **opérateur** et sélectionnez l' **=** opérateur dans la liste.  
  
5.  Cliquez sur la zone de texte **valeur** , puis tapez `High` dans la zone.  
  
6.  Cliquez sur la ligne suivante dans la grille.  
  
7.  Cliquez sur la zone de texte **and/or** dans la ligne suivante de la grille, puis sélectionnez **ou**.  
  
8.  Dans la zone de texte colonne de la **structure d’exploration de données** , sélectionnez IncomeGroup. Dans la zone de texte **valeur** , tapez `Moderate` .  
  
     La condition de filtre que vous avez créée est automatiquement ajoutée à la zone de texte de l' **expression** et doit apparaître comme suit :  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. Cliquez sur la ligne suivante dans la grille, en laissant l’opérateur comme valeur par défaut **et**.  
  
10. Pour **opérateur**, laissez la valeur par défaut, **contient**. Cliquez sur la zone de texte **valeur** .  
  
11. Dans la boîte de dialogue **filtre** , dans la première ligne sous colonne de la **structure d’exploration de données**, sélectionnez `Model` .  
  
12. Pour l' **opérateur**, SELECT **n’a pas la valeur null**. Laissez la zone de texte **valeur** vide. Cliquez sur **OK**.  
  
     La condition de filtre dans la zone de texte **expression** de la boîte de dialogue **filtre de modèle** est automatiquement mise à jour pour inclure la nouvelle condition sur la table imbriquée. L'expression complétée se présente comme suit :  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>Pour activer l'extraction et traiter le modèle filtré  
  
1.  Dans l’onglet **modèles d’exploration de données** , cliquez avec le bouton droit sur le `Association Filtered` modèle, puis sélectionnez **Propriétés**.  
  
2.  Remplacez la valeur de la propriété **AllowDrillThrough** par **true**.  
  
3.  Cliquez avec le bouton droit sur le `Association Filtered` modèle d’exploration de données, puis sélectionnez **traiter le modèle**.  
  
4.  Cliquez sur **Oui** dans le message d’erreur pour déployer le nouveau modèle dans la [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
5.  Dans la boîte de dialogue **traiter la structure d’exploration de données** , cliquez sur **exécuter**.  
  
6.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d’avancement** du traitement, puis cliquez de nouveau sur **Fermer** pour quitter la boîte de dialogue traiter la structure d' **exploration de données** .  
  
 Vous pouvez vérifier que le modèle filtré contient moins de cas que le modèle d'origine en utilisant la visionneuse de l'arborescence de contenu générique Microsoft et en recherchant la valeur de NODE_SUPPORT.  
  
## <a name="remarks"></a>Notes  
 Le filtre de table imbriquée que vous venez de créer recherche uniquement la présence d'au moins une ligne dans la table imbriquée ; toutefois, vous pouvez également créer des conditions de filtre qui permettent de rechercher la présence de produits spécifiques.  Par exemple, vous pouvez créer le filtre suivant :  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 Cette instruction signifie que vous restreignez les clients figurant dans la table de cas à uniquement ceux qui ont acheté une bouteille d'eau. Toutefois, puisque le nombre d'attributs de table imbriquée est potentiellement illimité, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne fournit pas de liste de valeurs possibles à sélectionner. Vous devez alors taper la valeur exacte.  
  
 Vous pouvez cliquer sur **modifier la requête** pour modifier manuellement l’expression de filtre. Toutefois, si vous modifiez manuellement quelque partie que ce soit d'une expression de filtre, la grille est alors désactivée et vous devez utiliser l'expression de filtre en mode édition de texte uniquement. Pour restaurer le mode de modification de grille, vous devez effacer l'expression de filtre et recommencer.  
  
> [!WARNING]  
>  Vous ne pouvez pas utiliser l'opérateur LIKE dans un filtre de table imbriquée.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Prédiction d’associations &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de filtre de modèle et exemples &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
