---
title: Algorithmes de plug-in | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
ms.openlocfilehash: ebc5e007dcc6de7fb25d59547e21f1e892100570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703456"
---
# <a name="plugin-algorithms"></a>Algorithmes de plug-in
  Outre les algorithmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournis par, il existe de nombreux autres algorithmes que vous pouvez utiliser pour l’exploration de données. Ainsi, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un mécanisme d'ajout d'algorithmes créés par des concepteurs tiers. Tant que ces algorithmes respectent certaines normes, vous pouvez les utiliser dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de la même manière que vous utilisez les algorithmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Les algorithmes de plug-in ont toutes les fonctionnalités des algorithmes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournis par.  
  
 Pour obtenir une description complète des interfaces qu’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise pour communiquer avec les algorithmes de plug-in, consultez les exemples de création d’un algorithme personnalisé et d’une visionneuse de modèles personnalisés qui sont publiés sur le site web [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) .  
  
## <a name="algorithm-requirements"></a>Conditions préalables à l'ajout d'algorithmes  
 Pour intégrer un algorithme dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez implémenter les interfaces COM suivantes :  
  
 `IDMAlgorithm`  
 Implémente un algorithme qui produit des modèles et implémente les opérations de prédiction des modèles résultants.  
  
 `IDMAlgorithmNavigation`  
 Permet aux navigateurs d'accéder au contenu des modèles.  
  
 `IDMPersist`  
 Permet aux modèles dont l’algorithme effectue l’apprentissage d’être enregistrés et chargés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 `IDMAlgorithmMetadata`  
 Décrit les capacités et les paramètres d'entrée de l'algorithme.  
  
 `IDMAlgorithmFactory`  
 Crée des instances des objets qui implémentent l'interface de l'algorithme et fournit à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] l'accès à l'interface des métadonnées de l'algorithme.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise ces interfaces COM pour communiquer avec les algorithmes de plug-in. Les algorithmes de plug-in que vous utilisez doivent prendre en charge la spécification [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour l’exploration de données, mais ils ne doivent pas nécessairement prendre en charge l’ensemble des options d’exploration de données définies dans la spécification. Vous pouvez utiliser l’ensemble de lignes de schéma [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) pour déterminer les fonctionnalités d’un algorithme. Cet ensemble de lignes de schéma répertorie les options de prise en charge d'exploration de données pour chaque fournisseur d'algorithme de plug-in.  
  
 Vous devez enregistrer les nouveaux algorithmes avant de les utiliser avec [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour enregistrer un algorithme, ajoutez les informations suivantes dans le fichier .ini de l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle vous voulez inclure les algorithmes :  
  
-   Le nom de l'algorithme  
  
-   Le ProgID (information facultative, incluse uniquement pour les algorithmes de plug-in)  
  
-   Un indicateur qui signale si l'algorithme est activé ou non  
  
 L'exemple de code suivant illustre comment enregistrer un nouvel algorithme :  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Ensemble de lignes DMSCHEMA_MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
