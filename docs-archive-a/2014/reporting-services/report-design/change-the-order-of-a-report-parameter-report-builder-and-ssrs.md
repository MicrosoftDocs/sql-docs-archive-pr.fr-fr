---
title: Modifier l’ordre d’un paramètre de rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad9dd25be7a87fee089a48849fcc716e682e4c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706199"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Modifier l'ordre d'un paramètre de rapport (Générateur de rapports et SSRS)
  Modifiez l'ordre des paramètres de rapport lorsqu'un paramètre dépendant figure dans la liste avant le paramètre dont il dépend. L'ordre des paramètres est important lorsque vous avez des paramètres en cascade ou lorsque vous souhaitez montrer aux utilisateurs la valeur par défaut d'un paramètre avant qu'ils ne choisissent des valeurs pour d'autres paramètres. Un paramètre de rapport dépendant contient une référence, dans sa requête de valeurs par défaut ou de valeurs valides, à un paramètre de requête qui pointe vers un autre paramètre du rapport situé plus loin dans la liste des paramètres du volet Données du rapport.  
  
 L'ordre d'affichage des paramètres dans la barre d'outils de la visionneuse de rapports dépend de l'ordre des paramètres dans le volet Données du rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>Pour modifier l'ordre des paramètres d'un rapport  
  
1.  Dans le volet Données du rapport, développez le nœud Paramètres.  
  
2.  Cliquez sur un paramètre et utilisez les flèches de direction Haut et Bas de la barre d'outils du volet des données de rapportpour faire monter ou descendre le paramètre dans la liste. L'illustration suivante montre le volet des données de rapport du Générateur de rapports.  
  
     ![Volet des données de rapport](../media/reportdatapane.png "Volet des données de rapport")  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et de Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Aide Générateur de rapports pour les boîtes de dialogue, les volets et les assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : ajouter un paramètre à votre rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupe &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Références à la collection Parameters &#40;Générateur de rapports et SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
