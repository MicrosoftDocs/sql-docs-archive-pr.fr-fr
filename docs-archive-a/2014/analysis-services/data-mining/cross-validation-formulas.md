---
title: Formules de validation croisée | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 878d88f695b2cdbf3c999c54568304accc54e3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604296"
---
# <a name="cross-validation-formulas"></a>Formules de validation croisée
  Lorsque vous créez un rapport de validation croisée, il contient des mesures de précision pour chaque modèle, selon le type du modèle d'exploration de données (autrement dit, l'algorithme utilisé pour créer le modèle), le type de données de l'attribut prédictible et la valeur de l'attribut prédictible, le cas échéant.  
  
 Cette section répertorie les mesures utilisées dans le rapport de validation croisée et décrit la méthode de calcul.  
  
 Pour une décomposition des mesures de précision par type de modèle, consultez [Mesures dans le rapport de validation croisée](measures-in-the-cross-validation-report.md).  
  
## <a name="formulas-used-for-cross-validation-measures"></a>Formules utilisées pour les mesures de validation croisée  
  
> [!NOTE]  
>  **Important :** ces mesures de précision sont calculées pour chaque attribut cible. Pour chaque attribut, vous pouvez spécifier ou omettre une valeur cible. Si un cas dans le jeu de données n'a pas de valeur pour l'attribut cible, le cas est traité comme faisant appel à une valeur spéciale appelée *valeur manquante*. Les lignes qui ont des valeurs manquantes ne sont pas comptées lors du calcul de la mesure de précision pour un attribut cible particulier. Notez que, dans la mesure où les scores sont calculés individuellement pour chaque attribut, si des valeurs sont présentes pour l'attribut cible mais manquantes pour d'autres attributs, cela n'affecte pas le score pour l'attribut cible.  
  
|Measure|S'applique à|Implémentation|  
|-------------|----------------|--------------------|  
|**Vrai positif**|Attribut discret, valeur spécifiée|Nombre de cas qui remplissent ces conditions :<br /><br /> Le cas contient la valeur cible.<br /><br /> Le modèle a prédit que le cas contient la valeur cible.|  
|**Vrai négatif**|Attribut discret, valeur spécifiée|Nombre de cas qui remplissent ces conditions :<br /><br /> Le cas ne contient pas la valeur cible.<br /><br /> Le modèle a prédit que le cas ne contient pas la valeur cible.|  
|**Faux positif**|Attribut discret, valeur spécifiée|Nombre de cas qui remplissent ces conditions :<br /><br /> La valeur réelle est égale à la valeur cible.<br /><br /> Le modèle a prédit que le cas contient la valeur cible.|  
|**Faux négatif**|Attribut discret, valeur spécifiée|Nombre de cas qui remplissent ces conditions :<br /><br /> La valeur réelle n'est pas égale à la valeur cible.<br /><br /> Le modèle a prédit que le cas ne contient pas la valeur cible.|  
|**Réussite/échec**|Attribut discret, cible non spécifiée|Nombre de cas qui remplissent ces conditions :<br /><br /> Succès si l'état prédit avec la probabilité la plus élevée est identique à l'état d'entrée et la probabilité est supérieure à la valeur de **Seuil d'état**.<br /><br /> Sinon, Échec.|  
|**Lâche**|Attribut discret. La valeur cible peut être spécifiée, mais elle n'est pas requise.|La vraisemblance logarithmique moyenne pour toutes les lignes avec des valeurs pour l’attribut cible, où la vraisemblance logarithmique de chaque cas est calculée par Log(ActualProbability/MarginalProbability). Pour calculer la moyenne, la somme des valeurs de la vraisemblance du journal est divisée par le nombre de lignes dans le dataset d'entrée, à l'exclusion des lignes avec les valeurs manquantes pour l'attribut cible.<br /><br /> La courbe d'élévation peut être une valeur négative ou positive. Une valeur positive signifie un modèle efficace qui devance l'estimation aléatoire.|  
|**Score du journal**|Attribut discret. La valeur cible peut être spécifiée, mais elle n'est pas requise.|Journal des valeurs de probabilité réelle pour chaque cas, additionnées, puis divisées par le nombre de lignes dans le jeu de données d'entrée, en excluant les lignes avec des valeurs manquantes pour l'attribut cible.<br /><br /> Étant donné que la probabilité est représentée comme une fraction décimale, les scores du journal sont toujours un nombre négatif. Un score plus proche de 0 représente un meilleur score.|  
|**Probabilité de cas**|Cluster|Somme des scores de vraisemblance de cluster pour tous les cas de la partition, divisée par le nombre de cas dans la partition, en excluant les lignes avec des valeurs manquantes pour l'attribut cible.|  
|**Erreur d'absolue moyenne**|Attribut continu|Somme de l'erreur absolue pour tous les cas de la partition, divisée par le nombre de cas dans la partition.|  
|**Erreur du carré moyen racine**|Attribut continu|Racine carrée de l'erreur-type pour la partition.|  
|**Racine de l’erreur quadratique moyenne**|Attribut discret. La valeur cible peut être spécifiée, mais elle n'est pas requise.|Racine carrée de la moyenne des carrés du complément du score de probabilité, divisée par le nombre de cas dans la partition, en excluant les lignes avec des valeurs manquantes pour l'attribut cible.|  
|**Racine de l’erreur quadratique moyenne**|Attribut discret, cible non spécifiée|Racine carrée de la moyenne des carrés du complément du score de probabilité, divisée par le nombre de cas dans la partition, en excluant les cas avec des valeurs manquantes pour l'attribut cible.|  
  
## <a name="see-also"></a>Voir aussi  
 [Test et validation &#40;l’exploration de données&#41;](testing-and-validation-data-mining.md)   
 [Validation croisée &#40;Analysis Services - Exploration de données&#41;](cross-validation-analysis-services-data-mining.md)  
  
  
