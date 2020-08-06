---
title: Utilisation des données de table imbriquée comme entrée pour un graphique d’exactitude | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97d5bbd75d09b1a9e4276c4723ad6986dbabf9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600326"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a>Utilisation des données de table imbriquée comme entrée pour un graphique d'analyse de précision
  Si vous testez l'exactitude d'un modèle d'exploration de données en utilisant des données externes et que le modèle d'exploration de données contient des tables imbriquées, les données externes doivent également contenir une table de cas et une table imbriquée associée.  
  
 Cette rubrique explique comment utiliser des tables imbriquées utilisées pour le test de modèle, comment mapper des tables imbriquées et des tables de cas dans le mode et dans les données externes, et comment appliquer un filtre à une table imbriquée.  
  
 Lors de l'utilisation de tables imbriquées, gardez à l'esprit les conseils suivants :  
  
-   Si vous sélectionnez l’option **Utiliser des scénarios de test de modèle d’exploration de données** ou **Utiliser des scénarios de test de structure d’exploration de données**, il est inutile de spécifier une table de cas ou une table imbriquée. Avec ces options, la définition des données de test est stockée dans la structure d'exploration de données et les données de test sont sélectionnées automatiquement lorsque vous créez le graphique d'analyse de précision.  
  
-   Si une relation existe déjà entre la table de cas et la table imbriquée dans la source de données, les colonnes de la structure d'exploration de données sont automatiquement associées aux colonnes portant le même nom dans la table d'entrée.  
  
-   Vous ne pouvez pas sélectionner de table imbriquée tant que vous n'avez pas spécifié la table de cas. Par ailleurs, vous ne pouvez pas spécifier de table imbriquée comme entrée à moins que le modèle d'exploration de données n'utilise également une structure de table de cas et de table imbriquée.  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a>Utiliser une table imbriquée comme entrée dans un graphique d'analyse de précision  
  
1.  Double-cliquez sur la structure d'exploration de données pour l'ouvrir dans le Concepteur d'exploration de données.  
  
2.  Sélectionnez l’onglet **Graphique d’analyse de précision de l’exploration de données** puis l’onglet **Sélection d’entrée** .  
  
3.  Dans **Sélectionner le jeu de données à utiliser pour le graphique d’analyse de précision**, sélectionnez l’option **Spécifier un autre jeu de données**.  
  
4.  Cliquez sur le bouton Parcourir **(...)** pour choisir le jeu de données externes dans une liste de vues de source de données sur le serveur actuel.  
  
5.  Cliquez sur **Sélectionner la table de cas**. Dans la boîte de dialogue **Sélectionner une table** , sélectionnez la table dans la vue de source de données contenant les données de cas, puis cliquez sur **OK**.  
  
6.  Cliquez sur **Sélectionner la table imbriquée**. Dans la boîte de dialogue **Sélectionner une table** , sélectionnez la table contenant les données imbriquées, puis cliquez sur **OK**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Si vous devez modifier la relation entre la table imbriquée et la table de cas, cliquez sur **Modifier la jointure** pour ouvrir la boîte de dialogue **Créer une relation** .  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir et mapper les données de test du modèle](choose-and-map-model-testing-data.md)   
 [Appliquer des filtres aux données de test du modèle](apply-filters-to-model-testing-data.md)  
  
  
