---
title: Impossible de charger le fichier ou l’assembly &#39;Microsoft. AnalysisServices. SharePoint. Integration&#39; | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612540"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>Impossible de charger le fichier ou l’assembly &#39;Microsoft. AnalysisServices. SharePoint. Integration&#39;
  Dans les environnements SharePoint 2010 qui disposent de PowerPivot pour SharePoint, cette erreur se produira si la solution au niveau de l'application pour PowerPivot n'a pas été déployée correctement.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S’applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|La solution Powerpivotwebapp n'est pas déployée ou n'a pas été déployée correctement.|  
|Texte du message|Impossible de charger le fichier ou l'assembly 'Microsoft.AnalysisServices.SharePoint.Integration'|  
  
## <a name="explanation"></a>Explication  
 PowerPivot pour SharePoint utilise des packages de solution pour déployer ses fonctionnalités sur un serveur SharePoint. L'une des solutions n'est pas déployée correctement. Par conséquent, cette erreur s'affiche chaque fois que vous essayez d'ouvrir la Galerie PowerPivot ou d'autres pages d'application PowerPivot sur un site SharePoint.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Déployez le package de solution.  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les solutions de la batterie**.  
  
2.  Cliquez sur **Powerpivotwebapp**.  
  
3.  Cliquez sur **Déployer la solution**.  
  
4.  Choisissez l'application Web pour laquelle cette erreur se produit. S'il y a plusieurs applications Web, redéployez la solution pour chacune d'entre elles.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des solutions PowerPivot sur SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
