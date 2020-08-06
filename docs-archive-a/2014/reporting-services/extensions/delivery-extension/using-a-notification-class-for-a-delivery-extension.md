---
title: Utilisation d’une classe Notification pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615035"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Utilisation d'une classe Notification pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.Notification> se trouve dans l'espace de noms <xref:Microsoft.ReportingServices.Interfaces> et représente les informations d'abonnement utilisées par les extensions de remise pour la remise de rapports. La classe <xref:Microsoft.ReportingServices.Interfaces.Notification> propose différentes propriétés qui peuvent être utilisées pour effectuer le rendu des rapports à remettre, déterminer l'état de la notification et définir les données utilisateur.

 ![Processus de notification de rapport](../../media/bk-ext-03.gif "Processus de notification de rapport") La notification est l’objet central de toute remise

 Lorsqu'un événement associé à un abonnement qui utilise votre extension de remise personnalisée est déclenché, une notification contenant un objet <xref:Microsoft.ReportingServices.Interfaces.Report> est créée. L'objet <xref:Microsoft.ReportingServices.Interfaces.Report> regroupe les fonctionnalités nécessaires pour effectuer le rendu d'un rapport donné dans un format de rendu pris en charge, et contient des propriétés spécifiques au rapport, telles que l'URL d'accès au rapport sur le serveur et le nom du rapport. Pour plus d’informations sur la classe <xref:Microsoft.ReportingServices.Interfaces.Report>, consultez [Utilisation de la classe Report pour une extension de remise](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).

 L'objet <xref:Microsoft.ReportingServices.Interfaces.Notification> est passé à la méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> de votre extension de remise. Votre méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> doit contenir du code spécifique pour traiter la notification et remettre le rapport.

 Pour un exemple d’utilisation de la classe <xref:Microsoft.ReportingServices.Interfaces.Notification>, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).

## <a name="retry-functionality"></a>Fonctionnalité relative aux nouvelles tentatives de remise
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vous permet de créer une file d'attente de nouvelles tentatives pour les notifications qui ne peuvent pas être remises immédiatement. Une fois que le serveur de rapports a appelé la méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> d'une extension de remise, cette extension peut demander que le serveur de rapports effectue une nouvelle tentative de remise à un moment ultérieur. Si cela se produit, le serveur de rapports place la notification dans une file d'attente interne et effectue une nouvelle tentative de remise à l'issue d'un certain délai. Les administrateurs peuvent configurer le nombre maximal de nouvelles tentatives effectuées par le serveur de rapports, de même que le délai entre les nouvelles tentatives, dans la section relative à l’extension de remise du fichier RSReportServer.config, à l’aide des éléments XML **MaxNumberOfRetries** et **PeriodBetweenRetries**. Les notifications sont supprimées de la file d'attente des nouvelles tentatives si la remise réussit ultérieurement ou si le nombre maximal de nouvelles tentatives est atteint. Si la remise échoue après le nombre maximal de nouvelles tentatives, la notification est ignorée.

## <a name="see-also"></a>Voir aussi
 [Implémentation d’une extension de remise](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services bibliothèque d’extensions](../reporting-services-extension-library.md)


