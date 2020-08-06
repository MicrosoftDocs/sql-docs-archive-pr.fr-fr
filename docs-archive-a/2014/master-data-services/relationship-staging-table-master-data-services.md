---
title: Table de mise en lots des relations (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 529d0521c320ff2e893a2269fe020d191a6ce284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612986"
---
# <a name="relationship-staging-table-master-data-services"></a>Table de mise en lots des relations (Master Data Services)
  Utilisez la table de mise en lots des relations (stg.name_Relationship) dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour modifier l’emplacement des membres dans une hiérarchie explicite, en fonction de la relation que les membres entretiennent les uns par rapport aux autres.  
  
##  <a name="table-columns"></a><a name="TableColumns"></a>Colonnes de table  
 Le tableau suivant explique la fonction de chacun des champs de la table de mise en lots Relation.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**Identifiant**|Identificateur automatiquement affecté. N'entrez pas de valeur dans ce champ. Si le lot n'a pas été traité, ce champ est vide.|  
|**RelationshipType**<br /><br /> Obligatoire|Type de relation défini. Les valeurs possibles sont les suivantes :<br /><br /> **1**: parent<br /><br /> **2**: frère (au même niveau)|  
|**ImportStatus_ID**<br /><br /> Obligatoire|État du processus d'importation. Les valeurs possibles sont les suivantes :<br /><br /> **0**, que vous spécifiez pour indiquer que l'enregistrement est prêt pour la mise en lots ;<br /><br /> **1**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a réussi ;<br /><br /> **2**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a échoué.|  
|**Batch_ID**<br /><br /> Requis par le service Web uniquement|Identificateur automatiquement affecté qui regroupe des enregistrements pour la mise en lots. Cet identificateur, affiché dans l'interface utilisateur [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] dans la colonne **ID** , est affecté à tous les membres du lot.<br /><br /> Si le lot n'a pas été traité, ce champ est vide.|  
|**BatchTag**<br /><br /> Requis, sauf par le service Web|Nom unique du lot, jusqu'à 50 caractères.|  
|**HierarchyName**<br /><br /> Obligatoire|Nom de hiérarchie explicite. Chaque membre consolidé ne peut appartenir qu'à une seule hiérarchie.|  
|**ParentCode**<br /><br /> Obligatoire|Pour les relations parent-enfant, code du membre consolidé qui sera le parent du membre feuille ou consolidé enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.|  
|**ChildCode**<br /><br /> Obligatoire|Pour les relations parent-enfant, code du membre consolidé ou feuille qui sera l'enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.|  
|**Ordre de tri**<br /><br /> Facultatif|Entier qui indique l'ordre du membre par rapport aux autres membres sous le parent. Chaque membre enfant doit avoir un identificateur unique.|  
|**ErrorCode**|Affiche un code d'erreur. Pour tous les enregistrements dont la valeur **ImportStatus_ID** est **2**, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacer des membres de hiérarchie explicites à l’aide du processus de site &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Affichez les erreurs qui se produisent pendant le processus de site &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
