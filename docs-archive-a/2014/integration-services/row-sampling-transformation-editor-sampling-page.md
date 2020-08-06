---
title: Éditeur de transformation d’échantillonnage de ligne (page échantillonnage) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696940"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>Éditeur de transformation d'échantillonnage de ligne (page Échantillonnage)
  Utilisez la boîte de dialogue **Éditeur de transformation d'échantillonnage de ligne** pour échantillonner une partie d'une entrée à l'aide d'un nombre de lignes spécifié. Cette transformation divise l'entrée en deux sorties distinctes.  
  
 Pour en savoir plus sur la transformation d'échantillonnage de lignes, consultez [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).  
  
## <a name="options"></a>Options  
 **Nombre de lignes**  
 Définissez le nombre de lignes de l'entrée à utiliser comme échantillon.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Nom de sortie de l'exemple**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes échantillonnées. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Nom de sortie non sélectionnée**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes exclues de l'échantillonnage. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Utiliser la valeur de départ aléatoire suivante**  
 Définissez la valeur de départ d'échantillonnage du générateur de nombres aléatoires qu'utilise la transformation pour créer un échantillon. Ceci est recommandé uniquement pour le développement et les tests. La transformation utilise le nombre de cycles Microsoft Windows comme valeur de départ si une valeur de départ aléatoire n'est pas définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation d’échantillonnage par pourcentage](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
