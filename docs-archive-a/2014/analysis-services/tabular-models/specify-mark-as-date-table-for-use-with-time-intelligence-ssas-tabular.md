---
title: Spécifier la marque comme table de dates pour l’utiliser avec Time Intelligence (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81038369b8cb8636a2aa216f1c26783a96d5f7ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694720"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular"></a>Spécifier la marque comme table de dates pour l'utiliser avec Time Intelligence (SSAS - Tabulaire)
  Pour utiliser des fonctions Time Intelligence dans les formules DAX, vous devez spécifier une table de dates et une colonne (datetime) d'identification unique pour le type de données Date. Une fois qu'une colonne dans la table de dates est spécifiée comme identificateur unique, vous pouvez créer des relations entre les colonnes de cette table et de toutes les tables de faits.  
  
 Lorsque vous utilisez les fonctions Time Intelligence, les règles suivantes s'appliquent :  
  
-   Lorsque vous utilisez les fonctions Time Intelligence DAX, ne spécifiez jamais une colonne datetime à partir d'une table de faits. Créez toujours une table de dates distincte dans votre modèle, avec au moins une colonne datetime de type de données Date et avec des valeurs uniques.  
  
-   Vérifiez que votre table de dates a une plage de dates continue.  
  
-   La colonne datetime dans la table de dates doit avoir une granularité de jour (sans fractions d'un jour).  
  
-   Vous devez spécifier une table de dates et une colonne d'identificateur unique à l'aide de la boîte de dialogue **Marquez la table de dates** .  
  
-   Créez des relations entre les tables de faits et les colonnes de type de données Date dans la table de dates.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>Pour spécifier une table de dates et un identificateur unique  
  
1.  Dans le concepteur de modèles, cliquez sur la table de dates.  
  
2.  Cliquez sur le menu **Table** , cliquez sur **Date**, puis cliquez sur **Marquer en tant que table de dates**  
  
3.  Dans la boîte de dialogue **Marquer en tant que table de dates** , dans la zone de liste **Date** , sélectionnez une colonne à utiliser comme identificateur unique. Cette colonne doit contenir des valeurs uniques et doit avoir le type de données Date. Par exemple :  
  
    |Date|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  Si nécessaire, créez les relations entre les tables de faits et la table de dates.  
  
## <a name="see-also"></a>Voir aussi  
 [Calculs &#40;&#41;tabulaire SSAS](calculations-ssas-tabular.md)   
 [Fonctions Time Intelligence &#40;&#41;DAX](/dax/time-intelligence-functions-dax)  
  
  
