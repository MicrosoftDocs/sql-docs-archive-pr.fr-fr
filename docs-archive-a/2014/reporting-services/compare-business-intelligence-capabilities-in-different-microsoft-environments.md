---
title: Comparer les fonctionnalités décisionnelles dans différents environnements Microsoft | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 12/15/2019
ms.openlocfilehash: bfdba7ec943713da0123855ab032a560bbd9cc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604404"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Comparer les fonctionnalités de Business Intelligence dans différents environnements Microsoft

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence peut être déployé dans plusieurs environnements différents, y compris [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec SharePoint Server, SharePoint Online et Power BI pour Office 365. Cette rubrique compare les composants et les fonctionnalités pris en charge dans chaque environnement.  
  
Pour plus d'informations sur la comparaison de SharePoint Server avec SharePoint Online, consultez [Comparer les plans et les options de SharePoint](https://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Créer et gérer des rapports et des tableaux de bord BI  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online – Plan 2|Power BI pour Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Sites BI|Galerie [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]|Non|Sites Power BI|  
|Gestion des données, et partage et gestion des requêtes|Non|Non|Oui ** <sup>1</sup>**|  
|Intégration avec Master Data Services (MDS) et Data Quality Services (DQS)|Oui|Non|Non|  
|Actualisation des données de planification|Oui, mais ne prend pas en charge des classeurs contenant des données Power Query|Non|Oui|  
|Requête en langage naturel (Q&A)|Non|Non|Oui ** <sup>2</sup>**|  
|Prévision prédictive|Non|Non|Oui ** <sup>3</sup>**|  
|Intégration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Oui|Non|Non|  
|Intégration d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (multidimensionnel et tabulaire)|Oui|Non|Non|  
|Exporter un tableau de bord interactif Power View vers une présentation PowerPoint|Oui|Non|Non|  
|Création du tableau de bord dans un navigateur|Oui|Non|Non|  
|Surveillance de l'utilisation|Oui|Non|Oui|  
|Tirer parti de la sécurité de niveau ligne des cubes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Oui|Non|Non|  
|||||

 **<sup>1</sup>**  [Compréhension du rôle des gestionnaires de données dans la gestion des données](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) et [Vidéo : Gestion des informations et gestion des données de Power BI](https://www.youtube.com/watch?v=8dHOj68ts7c).  
  
 **<sup>2</sup>**  [Power bi Q&a : optimiser un classeur Power bi (modélisation Cloud)](https://powerbi.microsoft.com/nl-nl/blog/new-in-power-bi-cloud-modeling-for-q-and-a/).  
  
 **<sup>3</sup>**  [Présentation des nouvelles capacités de prévision de Power View pour Office 365](https://powerbi.microsoft.com/blog/introducing-new-forecasting-capabilities-in-power-view-for-office-365/).  
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Afficher et parcourir les données, les rapports et les tableaux de bord BI  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online – Plan 2|Power BI pour Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Afficher les classeurs Microsoft Excel dans un navigateur|Oui, si la taille du classeur est inférieure à 2 Go|Oui, si la taille du classeur est inférieure à 10 Mo|Oui, si la taille du classeur est inférieure à 250 Mo|  
|Exploration de données dans un navigateur en HTML5|Non|Non|Oui|  
|Application mobile BI pour accéder à distance à des rapports et à des tableaux de bord|Non|Non|Oui ** <sup>1</sup>**|  
|Classeur Excel avec [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] comme source de données **<sup>2</sup>**|Oui|Non|Non|  
|Possibilité d'utiliser les fonctionnalités dans différents navigateurs et versions|Oui, pour les visualisations non-Power View **<sup>3</sup>**|Oui, pour les fichiers de classeurs d'une taille inférieure à 10 Mo **<sup>3</sup>**|Oui ** <sup>3</sup>**|  
|||||

 **<sup>1</sup>**  [Microsoft Power BI](https://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).  
  
 **<sup>2</sup>**  [Classeurs PowerPivot comme source de données](https://support.office.com/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-A9C2C6E2-CC49-4976-A7D7-40896795D045)  
  
 **<sup>3</sup>**  [prise en charge mobile sur les outils décisionnels (BI)](https://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) et [planification de la prise en charge des navigateurs Reporting Services et Power View (Reporting Services 2014)](https://msdn.microsoft.com/library/ms156511.aspx).  
  
## <a name="more-information"></a>Informations complémentaires  
  
- [Fonctionnalités bi dans Excel et Office 365](https://support.office.com/article/BI-capabilities-in-Excel-and-Office-365-26c0548e-124c-4fd3-aab3-5f64568cb743).  
  
- Pour plus d’informations sur la configuration requise pour utiliser des synonymes, consultez [optimisation des Power bi Q&A avec des synonymes & formulation](https://blog.pragmaticworks.com/optimizing-power-bi-qa-with-synonyms-phrasing-using-cloud-modeling) sur pragmaticworks.com.  
  
- [Office Online, choisissez votre réseau social d'entreprise : Yammer ou Newsfeed ?](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
- [Power BI pour Office 365](https://www.microsoft.com/powerbi/default.aspx).  
  
- [Tarification Power bi](https://www.microsoft.com/powerBI/pricing.aspx).  
  
- [Analyse et création de rapports avec les outils Microsoft Business Intelligence](../reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting.md)  
  
## <a name="community-content"></a>Contenus de la Communauté

