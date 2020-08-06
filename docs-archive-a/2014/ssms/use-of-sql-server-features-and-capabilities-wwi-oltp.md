---
title: Arguments pour outils externes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71a7fb99eee3286d21a405e9564d046847406a1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613762"
---
# <a name="arguments-for-external-tools"></a>Arguments pour outils externes
  Les arguments sont des variables pour lesquelles l'environnement Studio fournit des valeurs lorsque vous lancez un outil externe à partir du menu **Outils** . Des outils externes, tels que le Bloc-notes, peuvent être ajoutés au menu **Outils** via la boîte de dialogue **Outils externes** .  
  
 Le tableau ci-dessous répertorie les arguments pour les outils externes.  
  
|Name|Argument|Description|  
|----------|--------------|-----------------|  
|**Chemin d'accès de l'élément**|$(ItemPath)|Nom complet du fichier source en cours (sous la forme lecteur + chemin d'accès + nom du fichier) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Répertoire de l'élément**|$(ItemDir)|Répertoire de la source en cours (sous la forme lecteur + chemin d'accès) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Nom de fichier de l'élément**|$(ItemFilename)|Nom de fichier de la source en cours (sous la forme nom de fichier) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Extension de l'élément**|$(ItemExt)|Extension du nom de fichier de la source en cours.|  
|**Ligne active** <sup>1</sup>|$(CurLine)|Position de ligne active du curseur de l'éditeur.|  
|**Colonne active**1|$(CurCol)|Position de colonne active du curseur de l'éditeur.|  
|**Texte actif**1|$(CurText)|Texte actif (mot se trouvant à la position actuelle du curseur, ou sélection d'une seule ligne, s'il y en a une).|  
|**Chemin d'accès de la cible**|$(TargetPath)|Nom de fichier complet de la cible (sous la forme lecteur + chemin d'accès + nom du fichier).|  
|**Répertoire cible**|$(TargetDir)|Répertoire de la cible.|  
|**Nom de la cible**|$(TargetName)|Nom de fichier de la cible.|  
|**Extension de la cible**|$(TargetExt)|Extension du nom de fichier de la cible.|  
|**Répertoire du projet**|$(ProjDir)|Répertoire du projet en cours (sous la forme lecteur + chemin d'accès).|  
|**Nom du fichier projet**|$(ProjFileName)|Nom de fichier du projet en cours (sous la forme lecteur + chemin d'accès + nom du fichier).|  
|**Répertoire de la solution**|$(SolutionDir)|Répertoire de la solution en cours (sous la forme lecteur + chemin d'accès).|  
|**Nom du fichier solution**|$(SolutionFileName)|Nom de fichier de la solution en cours (sous la forme lecteur + chemin d'accès + nom du fichier).|  
  
 <sup>1</sup> la ligne active, la colonne Active ou le texte actif est basé sur la position du curseur dans l’éditeur de texte, comme indiqué dans la barre d’État.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils externes, boîte de dialogue](external-tools-dialog-box.md)   
 [Éléments généraux de l’interface utilisateur](general-user-interface-elements.md)  
  
  
