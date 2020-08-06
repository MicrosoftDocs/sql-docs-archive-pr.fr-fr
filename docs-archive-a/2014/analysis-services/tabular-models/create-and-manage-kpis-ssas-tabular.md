---
title: Créer et gérer des indicateurs de performance clés (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603660"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a>Créer et gérer les indicateurs de performance clés (SSAS Tabulaire)
  Cette rubrique décrit comment créer, modifier ou supprimer un indicateur de performance clé (KPI) dans un modèle tabulaire. Pour créer un indicateur de performance clé, vous sélectionnez une mesure qui correspond à la valeur de base de l’indicateur de performance clé. Utilisez ensuite la boîte de dialogue Indicateur de performance clé pour sélectionner une seconde mesure ou une valeur absolue qui prend une valeur cible. Vous pourrez ensuite définir des seuils d'état qui mesurent les performances entre les mesures de base et cible.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer un KPI](#bkmk_create_KPI)  
  
-   [Pour modifier un KPI](#bkmk_edit_KPI)  
  
-   [Pour supprimer un KPI et la mesure de base](#bkmk_delete)  
  
-   [Pour supprimer un KPI, mais conserver la mesure de base](#bkmk_delete_KPI)  
  
## <a name="tasks"></a>Tâches  
  
> [!IMPORTANT]  
>  Avant de créer un KPI, vous devez d'abord créer une mesure de base qui retourne une valeur. La mesure de base doit ensuite être étendue à un KPI. Pour savoir comment créer des mesures, consultez la rubrique [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](measures-ssas-tabular.md). Un KPI nécessite également une valeur cible. Cette valeur peut être obtenue à partir d'une autre valeur prédéfinie ou d'une valeur absolue. Une fois que vous avez étendu une mesure de base à un KPI, vous pouvez sélectionner la valeur cible et définir les seuils d’état dans la boîte de dialogue Indicateur de performance clé.  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a>Pour créer un indicateur de performance clé  
  
1.  Dans la Grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur), puis cliquez sur **Créer un KPI**.  
  
2.  Dans la boîte de dialogue **Indicateur de performance clé** , dans **Définir la valeur cible**, sélectionnez l’une des options suivantes :  
  
     Sélectionnez **Mesure**, puis sélectionnez une mesure cible dans la zone de liste.  
  
     Sélectionnez **Valeur absolue**, puis entrez une valeur numérique.  
  
3.  Dans **Définir les seuils d’état**, cliquez sur les valeurs des seuils et faites-les glisser.  
  
4.  Dans **Sélectionner le style d’icône**, cliquez sur un type d’image.  
  
5.  Cliquez sur **Descriptions**, puis tapez une description du KPI, de la valeur, de l’état et de la cible.  
  
> [!TIP]  
>  Vous pouvez utiliser la fonctionnalité Analyser dans Excel pour tester votre indicateur de performance clé. Pour plus d'informations, consultez la section [Analyser dans Excel &#40;SSAS Tabulaire&#41;](analyze-in-excel-ssas-tabular.md).  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a>Pour modifier un KPI  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Modifier les paramètres du KPI**.  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a>Pour supprimer un KPI et la mesure de base  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Supprimer**.  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a>Pour supprimer un KPI, mais conserver la mesure de base  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Supprimer le KPI**.  
  
## <a name="alt-shortcuts"></a>Raccourcis Alt  
  
|Section de l'interface utilisateur|Combinaison de touches|  
|----------------|-----------------|  
|Mesure de base du KPI|Alt+B|  
|État du KPI|Alt+S|  
|Measure|Alt+M|  
|Valeur absolue|ALT + A|  
|Définir les seuils d’état|Alt+U|  
|Sélectionner le style d’icône|Alt+I|  
|Tendance|Alt+T|  
|Descriptions|Alt+D|  
|Tendance|Alt+T|  
  
## <a name="see-also"></a>Voir aussi  
 [KPI &#40;&#41;tabulaires SSAS](kpis-ssas-tabular.md)   
 [Mesures &#40;&#41;tabulaire SSAS](measures-ssas-tabular.md)   
 [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](create-and-manage-measures-ssas-tabular.md)  
  
  
