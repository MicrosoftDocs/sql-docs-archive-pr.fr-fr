---
title: Actualisation des données PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605779"
---
# <a name="powerpivot-data-refresh"></a>Actualisation des données PowerPivot
  Une fois que vous avez créé un classeur contenant des données PowerPivot, vous pouvez actualiser périodiquement les données en réexécutant une requête ou une commande afin d'obtenir les informations mises à jour des sources utilisées initialement pour créer le classeur. Ce processus est appelé `data refresh`, et vous pouvez actualiser les données à la demande dans [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], ou de manière planifiée avec un processus [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui s'exécute sur un serveur d'applications dans une batterie de serveurs SharePoint. Pour plus d'informations, consultez les pages suivantes :  
  
-   [Actualisation des données PowerPivot avec SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Configurez le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Configurez les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Afficher l’historique d’actualisation des données &#40;PowerPivot pour SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et SharePoint Server 2013 Excel Services utilisent une architecture différente pour l'actualisation des données des modèles de données PowerPivot. L'architecture prise en charge par SharePoint 2013 utilise Excel Services en tant que composant principal pour charger les modèles de données PowerPivot. L'architecture d'actualisation des données précédente reposait sur un serveur exécutant le service système PowerPivot et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint afin de charger les modèles de données. Pour plus d’informations, consultez les rubriques suivantes :  
> 
>  -   [Actualisation des données PowerPivot avec SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Mettre à niveau les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
