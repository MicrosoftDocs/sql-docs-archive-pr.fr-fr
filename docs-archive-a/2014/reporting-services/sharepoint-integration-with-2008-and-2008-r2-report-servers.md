---
title: Intégration de SharePoint avec les serveurs de rapports 2008 et 2008 R2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9f51c37-b071-45d0-baec-f82fa6db366f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0b12429a520a674f4bc3ec7626bb3885fc33c814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696379"
---
# <a name="sharepoint-integration-with-2008-and-2008-r2--report-servers"></a>Intégration de SharePoint aux serveurs de rapports 2008 et 2008 R2
  La version [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] a introduit une architecture où le mode SharePoint est désormais basé sur un service partagé SharePoint. La gestion de la nouvelle fonctionnalité est effectuée dans l’administration centrale de SharePoint dans les pages **gérer les services** et **applications du service gestionnaire** . L' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] architecture précédente de l’intégration SharePoint est toujours prise en charge avec le [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] complément pour les produits SharePoint 2010. vous pouvez ainsi intégrer SharePoint 2010 avec les versions précédentes d’un serveur de rapports.  
  
 Les pages de l'Administration centrale de SharePoint que utilisez pour administrer l'ancienne architecture se trouvent dans les éléments suivants :  
  
1.  Dans l’administration centrale de SharePoint, cliquez sur **paramètres généraux**de l’application.  
  
2.  Le groupe **SQL Server Reporting Services (2008 et 2008 R2)** contient les liens et les pages de gestion de l’ancienne architecture  
  
## <a name="server-integration-architecture"></a>Architecture d'intégration de serveur  
 Lorsque vous intégrez un serveur de rapports à une instance d'un produit SharePoint, les éléments et les propriétés sont stockés dans les bases de données de contenu SharePoint. Cela fournit un niveau d'intégration plus élevé entre les technologies serveur, qui affecte la manière dont le contenu est stocké, sécurisé et accessible.  
  
 Le stockage des éléments et des propriétés des rapports dans les bases de données de contenu SharePoint vous permet de rechercher des types de contenu de serveur de rapports dans les bibliothèques SharePoint, de sécuriser des éléments en utilisant les mêmes niveaux d'autorisation et fournisseur d'authentification pour contrôler l'accès aux autres documents professionnels hébergés sur un site SharePoint, d'utiliser les fonctionnalités de collaboration et de gestion de documents pour archiver et extraire des rapports afin de les modifier, d'utiliser des alertes pour déterminer si un élément a changé, ainsi que d'incorporer ou de personnaliser le composant WebPart de visionneuse de rapports sur les pages et les sites au sein de l'application. Si vous disposer des autorisations suffisantes dans un site SharePoint, vous pouvez également générer des modèles de rapport à partir de sources de données partagées et utiliser le Générateur de rapports pour créer des rapports.  
  
 Le serveur de rapports continue à assurer toutes les opérations de traitement de données, de rendu et de remise. Il prend également en charge toutes les opérations de traitement de rapport planifiées pour les instantanés et l'historique de rapport. Lorsque vous ouvrez un rapport à partir d'un site SharePoint, le point de terminaison du serveur de rapports se connecte à un serveur de rapports, crée une session, prépare le traitement du rapport, récupère les données, fusionne le rapport dans la mise en page de rapport et l'affiche dans le composant WebPart Visionneuse de rapports. Lorsque le rapport est ouvert, vous pouvez l'exporter vers différents formats d'application ou interagir avec les données en extrayant les valeurs sous-jacentes ou en cliquant jusqu'à obtenir un rapport lié. Les opérations d'exportation et d'interaction dans les rapports sont exécutées sur le serveur de rapports.  
  
 Le serveur de rapports synchronise les opérations et les données à l'aide de SharePoint et effectue le suivi des informations sur les fichiers qu'il traite. Lorsque vous modifiez des propriétés ou des paramètres pour un élément de serveur de rapports quelconque, la modification est stockée dans une base de données SharePoint, puis copiée dans une base de données du serveur de rapports qui assure le stockage interne d'un serveur de rapports.  
  
## <a name="related-content"></a>Contenu associé  
 [Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
 activer la fonctionnalité Serveur de rapports exigée pour l'intégration avec les serveurs de rapports des versions précédentes.  
  
  
