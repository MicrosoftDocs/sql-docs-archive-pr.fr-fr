---
title: Traductions de dimensions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f31773ad871ef7e3fc8f99d57e7a9099335b899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706888"
---
# <a name="dimension-translations"></a>Traductions de dimension
  Une traduction est un mécanisme simple permettant de modifier les étiquettes et les légendes affichées d'une langue à une autre. Chaque traduction est définie comme une paire de valeurs : une chaîne avec le texte traduit et un nombre avec l'ID de langue. Les traductions sont disponibles pour tous les objets dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les valeurs d'attribut peuvent également être traduites pour les dimensions. L'application cliente est chargée de rechercher le paramètre de langue que l'utilisateur a défini et bascule pour afficher toutes les légendes et les étiquettes dans cette langue. Un objet peut avoir autant de traductions que vous le souhaitez.  
  
 Un objet <xref:Microsoft.AnalysisServices.Translation> simple est composé d'un numéro d'ID de langue et de la légende traduite. Le numéro d'ID de langue est un `Integer` avec l'ID de langue. La légende traduite est le texte traduit.  
  
 Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , une traduction de dimension est une représentation spécifique au langage du nom d’une dimension, le nom d’un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet ou l’un de ses membres, par exemple une légende, un membre ou un niveau de hiérarchie. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]prend également en charge les traductions d’objets de cube.  
  
 Les traductions permettent au serveur de prendre en charge les applications clientes qui autorisent l'emploi de plusieurs langues. Souvent, des utilisateurs de différents pays affichent un cube et ses dimensions. Il est utile de pouvoir traduire divers éléments d'un cube et ses dimensions dans une langue différente, de sorte que ces utilisateurs puissent afficher et comprendre le cube. Par exemple, un utilisateur professionnel en France peut accéder à un cube à partir d’une station de travail avec des paramètres régionaux français et voir les valeurs des propriétés de l’objet en français. En revanche, un utilisateur d'une entreprise en Allemagne qui accède au même cube depuis une station de travail avec les paramètres régionaux allemands peut voir les mêmes valeurs des propriétés des objets en allemand.  
  
 Les informations de classement et de langue pour l'ordinateur client sont stockées sous la forme d'un identificateur local (LCID). Lors de la connexion, le client envoie cet identificateur à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cette instance utilise ensuite l'identificateur LCID pour déterminer quel jeu de traductions utiliser en fournissant les métadonnées pour des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Si un objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne contient pas la traduction spécifiée, la langue par défaut est utilisée pour retourner le contenu au client.  
  
## <a name="see-also"></a>Voir aussi  
 [Traductions de cube](../multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Traductions &#40;Analysis Services&#41;](../translations-analysis-services.md)   
 [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
