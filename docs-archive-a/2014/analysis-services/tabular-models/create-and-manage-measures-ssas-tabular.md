---
title: Créer et gérer des mesures (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603659"
---
# <a name="create-and-manage-measures-ssas-tabular"></a>Créer et gérer des mesures (SSAS Tabulaire)
  Une mesure est une formule créée pour être utilisée dans un rapport ou un tableau croisé dynamique (ou un graphique croisé dynamique) Excel. Les mesures peuvent reposer sur des fonctions d'agrégation standard, comme COUNT ou SUM, ou vous pouvez définir votre propre formule à l'aide de DAX. Les tâches de cette rubrique décrivent comment créer et gérer des mesures à l’aide de la grille de mesures d’une table.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer une mesure qui utilise une formule d'agrégation standard](#bkmk_create_stand)  
  
-   [Pour créer une mesure à l’aide d’une formule personnalisée](#bkmk_create_custom)  
  
-   [Pour modifier les propriétés de mesure](#bkmk_edit)  
  
-   [Pour renommer une mesure](#bkmk_rename)  
  
-   [Pour supprimer une mesure](#bkmk_delete)  
  
## <a name="tasks"></a>Tâches  
 Pour créer et gérer des mesures, vous allez utiliser la grille de mesures d’une table. Vous pouvez afficher la grille de mesures pour une table dans le générateur de modèles dans la vue de données uniquement. Vous ne pouvez pas créer de mesures ni afficher la grille de mesures dans la vue de diagramme ; toutefois, vous pouvez afficher des mesures existantes dans la vue de diagramme. Pour afficher la grille de mesures d'une table, cliquez sur le menu **Table** , puis sur **Afficher la grille de mesures**.  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a>Pour créer une mesure à l’aide d’une formule d’agrégation standard  
  
-   Cliquez sur la colonne pour laquelle vous souhaitez créer la mesure, puis dans le menu **Colonne** , pointez sur **Somme automatique**, puis cliquez sur un type d'agrégation.  
  
     La mesure est créée automatiquement avec un nom par défaut, suivi de la formule dans la première cellule de la grille de mesures directement sous la colonne.  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a> Pour créer une mesure qui utilise une formule personnalisée  
  
-   Dans la grille de mesures, sous la colonne pour laquelle vous souhaitez créer la mesure, cliquez sur une cellule, puis dans la barre de formule, tapez un nom, suivi de deux-points (:), d’un signe égal (=) et de la formule. Appuyez sur Entrée pour accepter la formule.  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a>Pour modifier des propriétés de mesures  
  
-   Dans la grille de mesures, cliquez sur une mesure, puis dans la fenêtre **Propriétés** , tapez ou sélectionnez une valeur de propriété différente.  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a>Pour renommer une mesure  
  
-   Dans la grille de mesures, cliquez sur une mesure, puis dans la fenêtre **Propriétés** , dans **Nom de la mesure**, tapez un nouveau nom et cliquez sur ENTRÉE.  
  
     Vous pouvez également renommer une mesure dans la barre de formule. Le nom de la mesure précède la formule, suivi de deux-points.  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a>Pour supprimer une mesure  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur une mesure, puis sélectionnez **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesures &#40;&#41;tabulaire SSAS](measures-ssas-tabular.md)   
 [KPI &#40;&#41;tabulaires SSAS](kpis-ssas-tabular.md)   
 [Colonnes calculées &#40;SSAS tabulaire&#41;](ssas-calculated-columns.md)  
  
  
