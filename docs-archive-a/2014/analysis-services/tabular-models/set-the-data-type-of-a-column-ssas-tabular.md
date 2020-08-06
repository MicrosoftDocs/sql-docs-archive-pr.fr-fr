---
title: Définir le type de données d’une colonne (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694732"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a>Définir le type de données d'une colonne (SSAS Tabulaire)
  Lorsque vous importez ou collez des données dans un modèle, le générateur de modèles détecte et applique automatiquement les types de données. Après avoir ajouté les données au modèle, vous pouvez modifier manuellement le type de données d'une colonne afin de modifier la manière dont les données sont stockées. Si vous souhaitez simplement changer le format d'affichage des données sans modifier le mode de stockage de ces dernières, suivez plutôt la procédure ci-après.  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a>Pour modifier le type de données ou le format d'affichage d'une colonne  
  
1.  Dans le générateur de modèles, sélectionnez la colonne dont vous souhaitez modifier le type de données ou le format d'affichage.  
  
2.  Dans la fenêtre **Propriétés** de colonne, effectuez l'une des opérations suivantes :  
  
    -   Dans la propriété **Format de données** , sélectionnez un format de données différent.  
  
    -   Dans la propriété **Type de données** , sélectionnez un type de données différent.  
  
## <a name="considerations-when-changing-data-types"></a>Points à prendre en compte lors de la modification des types de données  
 Lorsque vous tentez de modifier le type de données d'une colonne ou de sélectionner une conversion de données, l'une des erreurs suivantes peut se produire :  
  
-   échec du changement de type de données ;  
  
-   échec du changement de type de données de la colonne.  
  
 Ces erreurs peuvent se produire même si le type de données est disponible en tant qu'option dans la liste déroulante Type de données. Cette section explique la cause de ces erreurs et la manière de les corriger.  
  
### <a name="understanding-automatically-determined-data-types"></a>Fonctionnement des types de données déterminés automatiquement  
 Lorsque vous ajoutez des données à un modèle, le générateur de modèles vérifie chacune des colonnes de données pour déterminer les types de données qu'elles contiennent. Si les données d'une colonne sont cohérentes, PowerPivot pour Excel affecte le type de données le plus précis à la colonne.  
  
 Toutefois, si vous ajoutez des données à partir d'Excel ou d'une autre source qui n'applique pas l'utilisation d'un type de données unique dans chaque colonne, le générateur de modèles affectera un type de données adapté à toutes les valeurs de la colonne. Par conséquent, si une colonne contient des nombres de types différents, tels que des entiers, des nombres longs et des devises, le générateur de modèles utilisera un type de données décimal. Sinon, si une colonne combine des nombres et du texte, le générateur de modèles utilise le type de données texte. Le générateur de modèles ne fournit pas de type de données semblable au type de données général disponible dans Excel.  
  
 Par conséquent, si une colonne contient à la fois des nombres et des valeurs texte, vous ne serez pas en mesure de convertir la colonne en type de données numérique.  
  
 Les types de données suivants sont disponibles dans les modèles sémantiques Business Intelligence :  
  
|Types de données de modèle|  
|----------------------|  
|Texte<br /><br /> Nombre décimal<br /><br /> Nombre entier<br /><br /> Devise<br /><br /> TRUE/FALSE<br /><br /> Date|  
  
 Si vous pensez que vos données ont un type de données incorrect, ou du moins un type différent de ce que vous souhaitiez, vous avez plusieurs options :  
  
-   Vous pouvez réimporter les données. Pour cela, ouvrez la connexion existante à la source de données, puis réimportez la colonne. Selon le type de source de données, vous avez la possibilité d'appliquer un filtre pendant l'importation pour supprimer les valeurs problématiques.  
  
-   Vous pouvez créer une formule DAX dans une colonne calculée pour créer une nouvelle valeur du type de données souhaité. Par exemple, la fonction TRUNC peut être utilisée pour changer un nombre décimal en nombre entier, ou vous pouvez combiner des fonctions d'informations et des fonctions logiques pour tester et convertir des valeurs.  
  
### <a name="understanding-data-conversion"></a>Présentation de la conversion de données  
 Si une erreur survient lorsque vous sélectionnez une option de conversion de données, cela peut indiquer que le type de données actuel de la colonne ne prend pas en charge la conversion sélectionnée. Les conversions ne sont pas toutes autorisées pour tous les types de données. Par exemple, vous pouvez changer une colonne en type de données booléen seulement si le type de données actuel de la colonne correspond à un nombre (entier ou décimal) ou à du texte. Par conséquent, vous devez choisir un type de données approprié pour les données dans la colonne.  
  
 Une fois que vous avez choisi un type de données approprié, le générateur de modèles vous signale les modifications éventuellement apportées à vos données, telles qu'une perte de précision ou une troncation. Cliquez sur OK pour accepter les modifications et convertir vos données dans le nouveau type.  
  
 Si le type de données est pris en charge, mais que le générateur de modèles détecte des valeurs non prises en charge dans le nouveau type de données, vous obtiendrez une autre erreur et devrez corriger les valeurs des données avant de continuer.  
  
 Pour obtenir des informations détaillées sur les types de données utilisés dans des modèles sémantiques Business Intelligence, sur la façon dont ils sont convertis implicitement et sur la manière d’utiliser des types de données différents dans les formules, consultez [Types de données pris en charge &#40;SSAS Tabulaire&#41;](data-types-supported-ssas-tabular.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données pris en charge &#40;SSAS Tabulaire&#41;](data-types-supported-ssas-tabular.md)  
  
  
