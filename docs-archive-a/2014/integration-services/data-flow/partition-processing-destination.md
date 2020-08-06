---
title: Destination de traitement de partition | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602922"
---
# <a name="partition-processing-destination"></a>Destination de traitement de partition
  La destination de traitement de partition charge et traite une partition [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les partitions, consultez [Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).  
  
 La destination de traitement de partition regroupe les fonctionnalités suivantes :  
  
-   options permettant de choisir entre un traitement incrémentiel, un traitement complet ou un traitement de mise à jour ;  
  
-   configuration d'erreur permettant de spécifier si le traitement ignore les erreurs ou s'arrête après un nombre spécifique d'erreurs ;  
  
-   mappage des colonnes d'entrée aux colonnes de partition.  
  
 Pour plus d’informations sur le traitement des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).  
  
> [!NOTE]  
>  Les tâches décrites ici ne s’appliquent pas aux modèles tabulaires Analysis Services.  Vous ne pouvez pas mapper des colonnes d’entrée aux colonnes de partition pour les modèles tabulaires. Vous pouvez en revanche utiliser la tâche DDL d'exécution [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) d'Analysis Services pour traiter la partition.  
  
## <a name="configuration-of-the-partition-processing-destination"></a>Configuration de la destination de traitement de partition  
 La destination de traitement de partition utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à l’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient les cubes et partitions traités par la destination. Pour plus d'informations, consultez [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Cette destination comporte une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés pouvant être définies dans la boîte de dialogue **Éditeur de destination de traitement de partition** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de traitement de partition &#40;page Gestionnaire de connexions&#41;](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de traitement de partition &#40;page Mappages&#41;](../partition-processing-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination de traitement de partition &#40;page Avancé&#41;](../partition-processing-destination-editor-advanced-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées de la destination de traitement de partition](partition-processing-destination-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
  
