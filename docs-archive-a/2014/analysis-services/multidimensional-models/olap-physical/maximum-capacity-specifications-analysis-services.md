---
title: Spécifications de capacité maximale (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0495ed563585a5b7427655428a257174673fc02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612546"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>Caractéristiques de capacité maximale (Analysis Services)
  Les tableaux suivants spécifient les tailles maximales et les nombres des différents objets définis dans les composants [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] selon des modes de déploiement de serveur différents.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Mode multidimensionnel et d'exploration de données (DeploymentMode=0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode=1)](#bkmk_sharepoint)  
  
 [Tabulaire (DeploymentMode=2)](#bkmk_vertipaq)  
  
##  <a name="multidimensional-and-data-mining-deploymentmode0"></a><a name="bkmk_OLAP"></a>Multidimensionnel et exploration de données (DeploymentMode = 0)  
 Le mode de stockage MOLAP, qui stocke des données et des métadonnées, a des limites physiques supplémentaires concernant les tailles de fichier. Les fichiers du magasin de chaînes ont par défaut une taille maximale de 4 Go. Si vous avez besoin de fichiers de plus grande taille pour les magasins de chaînes, vous pouvez spécifier une architecture de stockage de chaînes différente. Pour plus d’informations, consultez [configurer le stockage de chaînes pour les dimensions et les partitions](../configure-string-storage-for-dimensions-and-partitions.md).  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2 147 483 647|  
|Dimensions dans une base de données|2^31-1 = 2 147 483 647|  
|Attributs dans une dimension|2^31-1 = 2 147 483 647|  
|Membres dans un attribut de dimension|2^31-1 = 2 147 483 647|  
|Hiérarchies définies par l'utilisateur dans une dimension|2^31-1 = 2 147 483 647|  
|Niveaux dans une hiérarchie définie par l'utilisateur|2^31-1 = 2 147 483 647|  
|Cubes dans une base de données|2^31-1 = 2 147 483 647|  
|Groupes de mesures dans un cube|2^31-1 = 2 147 483 647|  
|Mesures dans un groupe de mesures|2^31-1 = 2 147 483 647|  
|Calculs dans un cube|2^31-1 = 2 147 483 647|  
|KPI dans un cube|2^31-1 = 2 147 483 647|  
|Actions dans un cube|2^31-1 = 2 147 483 647|  
|Partitions dans un cube|2^31-1 = 2 147 483 647|  
|Traductions dans un cube|2^31-1 = 2 147 483 647|  
|Agrégations dans une partition|2^31-1 = 2 147 483 647|  
|Cellules renvoyées par une requête|2^31-1 = 2 147 483 647|  
|Taille d’enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
|Nombre maximal d'états distincts dans une colonne d'attribut de modèle d'exploration de données|2^31-1 = 2 147 483 647|  
|Nombre maximal d'attributs pris en compte (sélection de fonctionnalité)|2^31-1 = 2 147 483 647|  
  
 Pour plus d’informations sur les règles d’affectation des noms d’objets, consultez [objets ASSL et caractéristiques des](../scripting-language-assl/assl-objects-and-object-characteristics.md)objets.  
  
 Pour plus d’informations sur les limitations de source de données pour le traitement analytique en ligne (OLAP) et l’exploration de données, consultez [sources de données prises en charge &#40;&#41;multidimensionnels SSAS ](../supported-data-sources-ssas-multidimensional.md), [sources de données prises en charge &#40;&#41;multidimensionnels SSAS ](../supported-data-sources-ssas-multidimensional.md), [objets ASSL et caractéristiques de l’objet](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
##  <a name="sharepoint-deploymentmode1"></a><a name="bkmk_sharepoint"></a>SharePoint (DeploymentMode = 1)  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2 147 483 647|  
|Tables dans une base de données|2^31-1 = 2 147 483 647|  
|Colonnes dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de colonnes dans une table dépend du nombre total de mesures et de colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Lignes dans une table|**Avertissement illimité :** avec une restriction, aucune colonne ne peut contenir plus de 1 999 999 997 valeurs distinctes.|  
|Hiérarchies dans une table|2^31-1 = 2 147 483 647|  
|Niveaux dans une hiérarchie|2^31-1 = 2 147 483 647|  
|Relations|2^31-1 = 2 147 483 647|  
|Colonnes clés dans une table|2^31-1 = 2 147 483 647|  
|Mesures dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de mesures dans une table dépend du nombre total de colonnes et de colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Colonnes calculées dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de colonnes calculées dans une table dépend du nombre total de colonnes et de mesures associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Cellules renvoyées par une requête|2^31-1 = 2 147 483 647|  
|Taille d’enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
  
##  <a name="tabular-deploymentmode2"></a><a name="bkmk_vertipaq"></a>Tabulaire (DeploymentMode = 2)  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2 147 483 647|  
|Tables dans une base de données|2^31-1 = 2 147 483 647|  
|Colonnes dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de colonnes dans une table dépend du nombre total de mesures et de colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Lignes dans une table|**Avertissement illimité :** avec la restriction, aucune colonne unique de la table ne peut avoir plus de 1 999 999 997 valeurs distinctes.|  
|Hiérarchies dans une table|2^31-1 = 2 147 483 647|  
|Niveaux dans une hiérarchie|2^31-1 = 2 147 483 647|  
|Relations|2^31-1 = 2 147 483 647|  
|Colonnes clés dans une table|2^31-1 = 2 147 483 647|  
|Mesures dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de mesures dans une table dépend du nombre total de colonnes et de colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Colonnes calculées dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :** le nombre total de colonnes calculées dans une table dépend du nombre total de colonnes et de mesures associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Cellules renvoyées par une requête|2^31-1 = 2 147 483 647|  
|Taille d’enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
  
## <a name="see-also"></a>Voir aussi  
 [Déterminer le mode serveur d’une instance de Analysis Services](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Propriétés générales](../../server-properties/general-properties.md)  
  
  
