---
title: Éditeur de transformation d’échantillonnage par pourcentage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4dbd96ab952b6c88bdaa7bf56a0a2f1b3585c57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601542"
---
# <a name="percentage-sampling-transformation-editor"></a>Éditeur de transformation de l'échantillonnage du pourcentage
  La boîte de dialogue **Éditeur de transformation de l'échantillonnage du pourcentage** permet de fractionner une partie d'une entrée en un exemple par le biais d'un certain pourcentage de lignes. Cette transformation divise l'entrée en deux sorties distinctes.  
  
 Pour en savoir plus sur la transformation d'échantillonnage par pourcentage, consultez [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="options"></a>Options  
 **Pourcentage de lignes**  
 Permet d'indiquer le pourcentage de lignes de l'entrée à utiliser comme exemple.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Nom de sortie de l'exemple**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes échantillonnées. Le nom fourni s'affichera dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Nom de sortie non sélectionnée**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes exclues de l'échantillonnage. Le nom fourni s'affichera dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Utiliser la valeur de départ aléatoire suivante**  
 Définissez la valeur de départ d'échantillonnage du générateur de nombres aléatoires qu'utilise la transformation pour créer un échantillon. Ceci est recommandé uniquement pour le développement et les tests. La fonctionnalité de transformation utilise le nombre de cycles de Microsoft Windows si aucune valeur de départ aléatoire n'est mentionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation d'échantillonnage de lignes](data-flow/transformations/row-sampling-transformation.md)  
  
  
