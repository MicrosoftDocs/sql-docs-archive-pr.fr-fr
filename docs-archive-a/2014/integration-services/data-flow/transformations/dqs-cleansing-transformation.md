---
title: Nettoyage DQS, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e980497905b8fa96a73516916af17f934221992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601015"
---
# <a name="dqs-cleansing-transformation"></a>Transformation de nettoyage DQS
  La transformation de nettoyage DQS utilise les services Data Quality Services (DQS) pour corriger des données provenant d'une source de données connectée en appliquant des règles approuvées créées pour la source de données connectée ou une source de données similaire. Pour plus d'informations sur les règles de correction des données, consultez [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md). Pour plus d'informations sur DQS, consultez [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Pour déterminer si les données doivent être corrigée, la transformation de nettoyage DQS traite les données d'une colonne d'entrée lorsque les conditions suivantes sont remplies :  
  
-   La colonne est sélectionnée pour la correction des données.  
  
-   Le type de données de la colonne est pris en charge pour la correction des données.  
  
-   La colonne est mappée à un domaine dont le type de données est compatible.  
  
 La transformation inclut également une sortie d'erreur que vous configurez pour gérer les erreurs au niveau des lignes. Pour configurer la sortie d'erreur, utilisez l' **Éditeur de transformation de nettoyage DQS**.  
  
 Vous pouvez inclure la [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) dans le flux de données pour identifier les lignes de données susceptibles d'être en double.  
  
## <a name="data-quality-projects-and-values"></a>Projets de qualité des données et valeurs  
 Lorsque vous traitez des données avec la transformation de nettoyage DQS, un projet de nettoyage est créé sur le serveur de qualité des données. Vous utilisez le client de qualité des données pour gérer le projet. En outre, vous pouvez utiliser le client de qualité des données pour importer les valeurs du projet dans un domaine de base de connaissances DQS. Vous pouvez importer les valeurs uniquement vers un domaine (ou un domaine lié) configuré pour être utilisé par la transformation de nettoyage DQS.  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Ouvrir des projets Integration Services dans Data Quality Client](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Importer des valeurs de projet de nettoyage dans un domaine](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Appliquer des règles de qualité des données à la source de données](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Gérer &#40;ouvrir, déverrouiller, renommer et supprimer des&#41; un projet de qualité des données](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   Article [Nettoyage de données complexes à l'aide des domaines composites](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), sur social.technet.microsoft.com.  
  
  
