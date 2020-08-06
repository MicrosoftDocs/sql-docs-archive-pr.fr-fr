---
title: Programmation de l’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696291"
---
# <a name="data-mining-programming"></a>Programmation de l'exploration de données
  Si vous estimez que les outils et composants intégrés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne répondent pas à vos besoins, vous pouvez étendre la puissance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en codant vos propres extensions. Dans cette optique, deux options sont à votre disposition :  
  
-   **XMLA**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]prend en charge XML for Analysis (XMLA) comme protocole pour la communication avec les applications clientes. Des commandes supplémentaires qui étendent la spécification XML for Analysis sont prises en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Dans la mesure où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise XMLA pour la définition, la manipulation et le contrôle de données, vous pouvez créer des structures et des modèles d'exploration de données à l'aide des outils visuels fournis par [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], puis étendre les objets d'exploration de données que vous avez créés en utilisant des scripts DMX (Data Mining Extensions) et ASSL (Analysis Services Scripting Language).  
  
     Vous pouvez créer et modifier des objets d'exploration de données entièrement dans des scripts XMLA et exécuter par programme des requêtes de prédiction sur les modèles à partir de vos propres applications.  
  
-   **Objets AMO (Analysis Management Objects)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] propose également une infrastructure complète permettant aux fournisseurs d'exploration de données tiers d'intégrer les objets d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Créez des structures et des modèles d'exploration de données à l'aide d'AMO. Consultez les exemples suivants dans CodePlex :  
  
    -   Navigateur d'indicateur de performance clé (AMO)  
  
         Se connecte à l'instance SSAS spécifiée et répertorie tous les objets serveur et leurs propriétés, notamment la structure d'exploration de données et les modèles d'exploration de données.  
  
    -   Exemple AMO simple  
  
         L'exemple AS simple couvre l'accès par programme à la plupart des objets principaux et illustre la navigation dans les métadonnées et l'accès aux valeurs des objets.  
  
         L'exemple illustre également la création et le traitement d'une structure et d'un modèle d'exploration de données, et la navigation dans un modèle d'exploration de données existant.  
  
-   **DMR**  
  
     Vous pouvez utiliser DMX pour encapsuler des instructions de commande, des requêtes de prédiction et des requêtes de métadonnées, et retourner les résultats dans un format tabulaire, si vous avez créé une connexion à un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [OLE DB pour l'exploration de données](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 Décrit les ajouts possibles à la spécification de manière à prendre en charge l'exploration de données et les données multidimensionnelles : nouveaux ensembles de lignes et nouvelles colonnes pour les schémas, langage DMX (Data Mining Extension) pour la création et la gestion des structures d'exploration de données.  
  
## <a name="related-reference"></a>Référence connexe  
 [Développement avec ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 Présente les objets de programmation du client et du serveur ADOMD.NET.  
  
 [Développement avec AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 Présente la bibliothèque de programmation AMO.  
  
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Présente XML for Analysis (XMLA) et ses extensions.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide du développeur &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [Référence DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
