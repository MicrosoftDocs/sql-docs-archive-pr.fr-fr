---
title: Sélectionner des tables et des vues (Assistant vue de source de données) (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac7159255ef526d871ed8906fc873d9f16d2eb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706832"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a>Sélectionner des tables et des vues (Assistant Vue de source de données) (Analysis Services)
  Utilisez la page **Sélectionner des tables et des vues** pour sélectionner des tables ou des vues dans la source de données que vous voulez inclure dans la vue de la source des données.  
  
## <a name="options"></a>Options  
 **Objets disponibles**  
 Affiche la liste des tables et des vues dans le schéma de la source des données. Le nom du schéma précède le nom de chaque objet si plusieurs schémas figurent dans la liste. Si un seul schéma est affiché, son nom ne précède pas les noms des objets.  
  
 Pour afficher la liste en ordre croissant ou décroissant, cliquez sur **Nom** ou sur **Type**.  
  
 **Objets inclus**  
 Affiche la liste des tables et des vues à inclure dans la vue de la source des données.  
  
 Pour afficher la liste en ordre croissant ou décroissant, cliquez sur **Nom** ou sur **Type**.  
  
 **Filter**  
 Filtre les objets répertoriés sous **Objets disponibles**. Tapez une chaîne, puis cliquez sur **Filtre** pour afficher uniquement les noms qui contiennent une chaîne de caractères donnée. Pour rechercher une chaîne précise, placez-la entre guillemets. Le filtre ne respecte pas la casse.  
  
 Vous pouvez inclure n'importe où dans la chaîne de caractères les caractères génériques indiqués dans la liste ci-dessous.  
  
|Caractère générique|Valeur|  
|------------------------|-----------|  
|**\***|N'importe quelle chaîne de caractères|  
|**%**|N'importe quelle chaîne de caractères|  
|**?**|Un seul caractère|  
|**«** *chaîne* **»**|Chaîne de caractères littérale. Ce caractère générique correspond à toute sous-chaîne figurant dans le nom de l'objet.|  
  
 **Afficher les objets système**  
 Affiche les objets système dans **Objets disponibles**. Cette option est disponible uniquement si le fournisseur de la source des données expose les objets système. La suppression d’un objet système de la liste **Objets inclus** sélectionne automatiquement cette option.  
  
 **Ajouter des tables associées**  
 Ajoute toutes les tables associées à celles figurant dans la liste **Objets inclus**. Cette option n'ajoute pas de vues. Néanmoins, elle ajoute des tables partitionnées. Si vous sélectionnez des critères de correspondance des noms dans la page **Correspondance de noms** de l’Assistant, cette option inclut également les tables logiquement selon les critères sélectionnés. Les tables sont également incluses si elles sont associées à des tables récemment ajoutées et si leur structure est identique à celle de la table d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant vue de source de données &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md)   
 [Vues de sources de données dans les modèles multidimensionnels](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
