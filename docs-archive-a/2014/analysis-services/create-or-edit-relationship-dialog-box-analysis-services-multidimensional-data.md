---
title: Boîte de dialogue créer ou modifier une relation (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603727"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Créer/Modifier une relation (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Créer/Modifier une relation** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir ou modifier une relation dans une vue de source de données. Pour afficher la boîte de dialogue **Créer/Modifier une relation** , vous pouvez :  
  
-   cliquer sur **Nouvelle relation** dans le volet **Barre d’outils** du **Concepteur de vues de source de données**;  
  
-   cliquer avec le bouton droit sur une table dans le volet **Tables** ou **Diagramme** du **Concepteur de vues de source de données** et sélectionner **Nouvelle relation**;  
  
-   cliquer avec le bouton droit sur une relation dans le volet **Diagramme** du **Concepteur de vues de source de données** et sélectionner **Modifier la relation**.  
  
> [!NOTE]  
>  Vous pouvez créer des relations dans le **Concepteur de vues de source de données** , qui n’existent pas dans la source de données sous-jacente, et supprimer des relations créées par le **Concepteur de vues de source de données** à partir de relations de clé étrangère existantes dans la source de données sous-jacente.  
  
## <a name="options"></a>Options  
 **Table source (clé étrangère)**  
 Sélectionnez la table ou la requête nommée qui contient la référence à une ou plusieurs colonnes de la table de destination.  
  
 **Table de destination (clé primaire)**  
 Sélectionnez la table qui contient une ou plusieurs colonnes référencées par la table source. Pour les jointures réflexives, sélectionnez la même table que celle sélectionnée dans **Table source (clé étrangère)**.  
  
 **Colonnes source**  
 Sélectionnez les colonnes qui font référence à des colonnes de la table de destination.  
  
 **Colonnes de destination**  
 Sélectionnez les colonnes qui sont référencées par des colonnes de la table source.  
  
 **TVA**  
 Inverse le sens de la relation.  
  
 **Description**  
 Tapez une description facultative de la relation.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Concepteur de vue de source de données &#40;Analysis Services - Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
