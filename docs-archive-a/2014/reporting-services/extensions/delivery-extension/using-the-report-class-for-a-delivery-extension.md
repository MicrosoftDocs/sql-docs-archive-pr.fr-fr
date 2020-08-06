---
title: Utilisation de la classe Rapport pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615026"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Utilisation de la classe Report pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.Report> représente un rapport dans la base de données du serveur de rapports. Tout abonnement est associé à un rapport spécifique. Le rapport est contenu dans la notification. Votre extension de remise peut utiliser l'objet <xref:Microsoft.ReportingServices.Interfaces.Report> qui fait partie de la notification pour effectuer le rendu du rapport. L'objet <xref:Microsoft.ReportingServices.Interfaces.Report> contient également des propriétés spécifiques au rapport, telles que l'URL au rapport sur le serveur de rapports et le nom du rapport. Toutes ces propriétés peuvent être utilisées dans le cadre de votre fournisseur de remise.  
  
 La méthode <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> de la classe <xref:Microsoft.ReportingServices.Interfaces.Report> peut être utilisée pour effectuer le rendu d'un rapport. La méthode <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> retourne un tableau d'un ou plusieurs objets <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> qui constituent un rapport rendu unique. Le premier objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> est le rapport rendu. Les autres objets <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sont des ressources qui doivent être remises avec les données du rapport (par exemple, un fichier HTML et les images associées). Les extensions de rendu qui sont des extensions de rendu de flux unique (IMAGE, PDF, MHTML et Excel) retournent un seul objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> dans le tableau.  
  
 L'objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, qui contient le flux du rapport, peut être inclus dans le cadre d'une remise.  
  
 Pour un exemple d’utilisation de la classe <xref:Microsoft.ReportingServices.Interfaces.Report>, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d’extensions Reporting Services](../reporting-services-extension-library.md)   
 [Utilisation de la classe RenderedOutputFile pour une extension de remise](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
