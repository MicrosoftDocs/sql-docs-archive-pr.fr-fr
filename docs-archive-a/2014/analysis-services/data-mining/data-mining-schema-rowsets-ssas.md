---
title: Interrogation des ensembles de lignes de schéma d’exploration de données (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612632"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a>Interrogation des ensembles de lignes de schéma d'exploration de données (Analysis Services - Exploration de données)
  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la plupart des ensembles de lignes de schéma d'exploration de données OLE DB existants sont exposés sous forme d'un jeu de tables système que vous pouvez interroger à l'aide d'instructions DMX (Data Mining Extensions). En créant des requêtes sur l'ensemble de lignes de schéma d'exploration de données, vous pouvez identifier les services qui sont disponibles, obtenir des mises à jour sur l'état de vos modèles et de vos structures, et obtenir des détails sur le contenu ou les paramètres du modèle. Pour obtenir une description des ensembles de lignes de schéma d’exploration de données, consultez [Ensembles de lignes de schéma d’exploration de données](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
> [!NOTE]  
>  Vous pouvez également interroger les ensembles de lignes de schéma d'exploration de données à l'aide de XMLA. Pour plus d’informations sur la procédure à suivre dans SQL Server Management Studio, consultez [Créer une requête d’exploration de données en utilisant XMLA](create-a-data-mining-query-by-using-xmla.md).  
  
## <a name="list-of-data-mining-schema-rowsets"></a>Liste des ensembles de lignes de schéma d'exploration de données  
 Le tableau suivant répertorie les ensembles de lignes de schéma d'exploration de données qui peuvent s'avérer utiles pour l'interrogation et l'analyse.  
  
|Nom de l'ensemble de lignes|Description|  
|-----------------|-----------------|  
|DMSCHEMA_MINING_MODELS|Répertorie tous les modèles d'exploration de données dans le contexte actuel.<br /><br /> Inclut des informations telles que la date de création, les paramètres utilisés pour créer le modèle et la taille du jeu d'apprentissage.|  
|DMSCHEMA_MINING_COLUMNS|Répertorie toutes les colonnes utilisées dans les modèles d'exploration de données dans le contexte actuel.<br /><br /> Les informations incluent le mappage à la colonne source de la structure d'exploration de données, le type de données, la précision et les fonctions de prédiction pouvant être utilisées avec la colonne.|  
|DMSCHEMA_MINING_STRUCTURES|Répertorie toute la structure d'exploration de données dans le contexte actuel.<br /><br /> Les informations contenues indiquent notamment si la structure est remplie, la date à laquelle la structure a été traitée pour la dernière fois et, le cas échéant, la définition du jeu de données d'exclusion pour la structure.|  
|DMSCHEMA_MINING_STRUCTURE_COLUMNS|Répertorie toutes les colonnes utilisées dans les structures d'exploration de données dans le contexte actuel.<br /><br /> Les informations indiquent notamment le type de contenu et le type de données, la possibilité de valeur NULL et si la colonne contient ou non des données de table imbriquées.|  
|DMSCHEMA_MINING_SERVICES|Répertorie tous les services d'exploration de données, ou algorithmes, qui sont disponibles sur le serveur spécifié.<br /><br /> Les informations indiquent notamment les indicateurs de modélisation pris en charge, les types d'entrée et les types de source de données pris en charge.|  
|DMSCHEMA_MINING_SERVICE_PARAMETERS|Répertorie tous les paramètres pour les services d'exploration de données qui sont disponibles sur l'instance actuelle.<br /><br /> Les informations indiquent notamment le type de données pour chaque paramètre, les valeurs par défaut et les limites supérieures et inférieures.|  
|DMSCHEMA_MODEL_CONTENT|Retourne le contenu du modèle si le modèle a été traité.<br /><br /> Pour plus d’informations, consultez [Contenu du modèle d’exploration &#40;Analysis Services - Exploration de données&#41;](mining-model-content-analysis-services-data-mining.md).|  
|DBSCHEMA_CATALOGS|Répertorie toutes les bases de données (catalogues) dans l'instance actuelle d'Analysis Services.|  
|MDSCHEMA_INPUT_DATASOURCES|Répertorie toutes les sources de données dans l'instance actuelle d'Analysis Services.|  
  
> [!NOTE]  
>  La liste dans la table n'est pas complète ; elle affiche uniquement les ensembles de lignes les plus intéressants pour le dépannage.  
  
## <a name="examples"></a>Exemples  
 La section suivante fournit quelques exemples de requêtes sur les ensembles de lignes de schéma d'exploration de données.  
  
### <a name="example-1-list-data-mining-services"></a>Exemple 1 : Répertorier les services d'exploration de données  
 La requête suivante retourne une liste des services d'exploration de données qui sont disponibles sur le serveur actuel, c'est-à-dire les algorithmes qui sont activés. Les colonnes fournies pour chaque service d'exploration de données comprennent notamment les indicateurs de modélisation et les types de contenu qui peuvent être utilisés par chaque algorithme, le GUID pour chaque service et toute limite de prédiction ayant pu être ajoutée pour chaque service.  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a>Exemple 2 : Répertorier les paramètres du modèle d'exploration de données  
 L'exemple suivant retourne les paramètres utilisés pour créer un modèle d'exploration de données spécifique :  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a>Exemple 3 : Répertorier tous les ensembles de lignes  
 L'exemple suivant retourne une liste complète des ensembles de lignes disponibles sur le serveur actuel :  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de dépannage (Analysis Services - Exploration de données)](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
