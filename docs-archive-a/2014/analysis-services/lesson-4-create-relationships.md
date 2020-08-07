---
title: 'Leçon 5 : créer des relations | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
author: minewiskan
ms.author: owend
ms.openlocfilehash: f622f88d4d400fedf24e99059eda94882b1bcc3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703383"
---
# <a name="lesson-5-create-relationships"></a>Leçon 5 : Créer des relations
  Dans cette leçon, vous allez vérifier les relations qui ont été créées automatiquement lorsque vous avez importé des données, et vous allez ajouter de nouvelles relations entre les tables. Une relation est une connexion entre deux tables qui établit le mode de corrélation des données dans les deux tables. Par exemple, la table Product et la table Product Subcategory ont une relation basée sur le fait que chaque produit appartient à une sous-catégorie. Pour en savoir plus, consultez [Relations &#40;SSAS Tabulaire&#41;](tabular-models/relationships-ssas-tabular.md).  
  
 Durée estimée pour suivre cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Examiner les relations existantes et ajouter de nouvelles relations  
 Lorsque vous avez importé des données à l'aide de l'Assistant Importation de table, vous avez importé sept tables de la base de données AdventureWorksDW. En général, si vous importez des données d'une source relationnelle, les relations existantes sont importées automatiquement avec les données. Toutefois, avant de poursuivre avec la création de votre modèle, vous devez vérifier que les relations entre les tables ont été créées correctement. Pour ce didacticiel, vous allez également ajouter trois relations.  
  
#### <a name="to-review-existing-relationships"></a>Pour vérifier les relations existantes  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis pointez sur **Vue du modèle**et sur **Vue de diagramme**.  
  
     Le concepteur de modèles apparaît maintenant dans la vue de diagramme, c'est un format graphique affichant toutes les tables que vous avez importées et les lignes les reliant. Les lignes entre les tables indiquent les relations qui ont été créées automatiquement lorsque vous avez importé les données.  
  
     Utilisez les contrôles de la minicarte dans l'angle supérieur droit du concepteur de modèles pour ajuster la vue et inclure autant de tables que possible. Vous pouvez également cliquer et faire glisser des tables à différents emplacements, en rapprochant les tables autant que possible, ou en les plaçant dans un ordre précis. Le déplacement des tables n'affecte pas les relations qui existent déjà entre elles. Pour afficher toutes les colonnes d'une table donnée, cliquez et faites glisser le bord de la table pour l'agrandir ou la réduire.  
  
2.  Cliquez sur la ligne pleine entre la table **Customer** et la table **Geography** . La ligne pleine entre ces deux tables indique que cette relation est active, c.-à-d. qu'elle est utilisée par défaut lors du calcul des formules DAX.  
  
     Notez que la colonne **Geography Id** dans la table **Customer** et la colonne **Geography Id** dans la table **Geography** apparaissent maintenant chacune dans une zone. Cela indique que ce sont les colonnes utilisées dans la relation. Les propriétés de la relation apparaissent maintenant aussi dans la fenêtre **Propriétés** .  
  
    > [!TIP]  
    >  Outre l’utilisation du concepteur de modèles dans la vue de diagramme, vous pouvez également utiliser la boîte de dialogue **Gérer les relations** pour afficher les relations entre toutes les tables dans un format tabulaire. Cliquez sur le menu **Table** , puis sur **Gérer les relations**. La boîte de dialogue **Gérer les relations** affiche les relations qui ont été créées automatiquement quand vous avez importé des données.  
  
3.  Utilisez le concepteur de modèles dans la vue de diagramme, ou la boîte de dialogue **Gérer les relations** , pour vérifier que les relations suivantes ont été créées quand chacune des tables a été importée à partir de la base de données AdventureWorksDW :  
  
    |Actif|Table|Table de recherche associée|  
    |------------|-----------|--------------------------|  
    |Oui|**Customer [Geography Id]**|**Geography [Geography Id]**|  
    |Oui|**Product [Product Subcategory Id]**|**Product Subcategory [Product Subcategory Id]**|  
    |Oui|**Product Subcategory [Product Category Id]**|**Product Category [Product Category Id]**|  
    |Oui|**Internet Sales [Customer Id]**|**Customer [Customer Id]**|  
    |Oui|**Internet Sales [Product Id]**|**Product [Product Id]**|  
  
 Si l'une des relations dans la table ci-dessus est manquante, vérifiez que votre modèle inclut les tables suivantes : Customer, Date, Geography, Product, Product Category, Product Subcategory et Internet Sales. Si vous importez des tables provenant de la même connexion de source de données à des moments différents, les relations entre ces tables ne sont pas créées et doivent être créées manuellement.  
  
 Dans certains cas, vous devrez peut-être créer des relations supplémentaires entre les tables de votre modèle pour répondre aux besoins d’une certaine logique métier. Pour ce didacticiel, vous devez créer trois relations supplémentaires entre la table Internet sales et la table Date.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Pour ajouter de nouvelles relations entre des tables  
  
1.  Dans le concepteur de modèles, dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Order Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne pleine apparaît et indique que vous avez créé une relation active entre la colonne **Order Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** .  
  
    > [!NOTE]  
    >  Lorsque vous créez des relations, l'ordre entre la table primaire et la table de recherche associée est automatiquement classifié correctement.  
  
2.  Dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Due Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne en pointillés apparaît et indique que vous avez créé une relation inactive entre la colonne **Due Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** . Vous pouvez avoir plusieurs relations entre les tables, mais une seule relation peut être active à la fois.  
  
3.  Enfin, créez une relation supplémentaire : dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Ship Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne en pointillés apparaît et indique que vous avez créé une relation inactive entre la colonne **Ship Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** .  
  
## <a name="next-step"></a>étape suivante  
 Pour continuer cette leçon, passez à la [Leçon 6 : Créer des colonnes calculées](lesson-5-create-calculated-columns.md).  
  
  
