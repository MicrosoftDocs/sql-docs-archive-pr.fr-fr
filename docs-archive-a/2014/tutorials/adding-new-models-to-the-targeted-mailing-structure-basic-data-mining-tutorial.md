---
title: Ajout de nouveaux modèles à la structure de publipostage ciblée (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704503"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Ajout de nouveaux modèles à la structure de publipostage ciblé (Didacticiel sur l'exploration de données de base)
  Dans cette tâche, vous allez définir deux modèles supplémentaires à l’aide de l’onglet **modèles d’exploration** de données du concepteur d’exploration de données. Vous allez utiliser l'algorithme MNB (Microsoft Naive Bayes) et l'algorithme de gestion de clusters Microsoft pour créer les modèles. Ces deux algorithmes sont sélectionnés en raison de leur capacité à prédire une valeur discrète (c.-à-d., un achat de vélo). Pour plus d’informations sur ces algorithmes, consultez [algorithme de clustering Microsoft](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) et [algorithme Microsoft Naive Bayes](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)  
  
### <a name="to-create-a-clustering-mining-model"></a>Pour créer un modèle d'exploration de données Microsoft Clustering  
  
1.  Basculez vers l’onglet **modèles d’exploration** de données du concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .  
  
     Notez que le concepteur affiche deux colonnes, une pour la structure d’exploration de données et une pour le `TM_Decision_Tree` modèle d’exploration de données que vous avez créée dans la leçon précédente.  
  
2.  Cliquez avec le bouton droit sur la colonne **structure** et sélectionnez **nouveau modèle d’exploration de données**.  
  
3.  Dans la boîte de dialogue **nouveau modèle d’exploration de données** , dans **nom du modèle**, tapez `TM_Clustering` .  
  
4.  Dans **nom de l’algorithme**, sélectionnez **clustering Microsoft**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Le nouveau modèle s’affiche maintenant sous l’onglet **modèles d’exploration** de données du concepteur d’exploration de données. Ce modèle, créé à l’aide de l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de clustering, regroupe les clients ayant des caractéristiques similaires en clusters et prédit l’achat de bicyclettes pour chaque cluster. Bien que vous puissiez modifier l’utilisation des colonnes et les propriétés du nouveau modèle, aucune modification du `TM_Clustering` modèle n’est nécessaire pour ce didacticiel.  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Pour créer un modèle d'exploration de données Naive Bayes  
  
1.  Sous l’onglet **modèles d’exploration** de données du concepteur d’exploration de données, cliquez avec le bouton droit sur la colonne de **structure** clickthe, puis sélectionnez **nouveau modèle d’exploration**de données.  
  
2.  Dans la boîte de dialogue **nouveau modèle d’exploration de données** , sous **nom du modèle**, tapez `TM_NaiveBayes` .  
  
3.  Dans **nom de l’algorithme**, sélectionnez **Microsoft Naive Bayes**, puis cliquez sur **OK**.  
  
     Un message s’affiche, indiquant que l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Naive Bayes ne prend pas en charge les colonnes **Age** et **Yearly Income** , qui sont continues.  
  
4.  Cliquez sur **Oui** pour accuser réception du message et continuer.  
  
 Un nouveau modèle apparaît sous l’onglet **modèles d’exploration** de données du concepteur d’exploration de données. Bien que vous puissiez modifier l’utilisation des colonnes et les propriétés de tous les modèles de cet onglet, aucune modification du `TM_NaiveBayes` modèle n’est nécessaire pour ce didacticiel.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Traitement des modèles dans la structure de publipostage ciblée &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des modèles d’exploration de données à une structure &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Déplacement d'objets d'exploration de données](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
