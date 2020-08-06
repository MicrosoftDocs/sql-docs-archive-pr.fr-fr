---
title: Élément StorageBoundInMB, (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea49b0af981b8f8d96efb087033d8f1466364c76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704584"
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB, élément (Assistant Paramétrage de base de données)
  Spécifie l'espace maximal, en mégaoctets, pouvant être consommé par la recommandation de paramétrage de l'Assistant Paramétrage du moteur de base de données (jeu d'index et de partitions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`unsignedInt`, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|facultatif. Ne peut être utilisé qu'une seule fois pour l'élément `TuningOptions`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|None|  
  
## <a name="remarks"></a>Notes  
 Lorsque plusieurs bases de données sont paramétrées, les recommandations pour toutes les bases de données sont prises en compte pour le calcul de l'espace. Par défaut, l'Assistant Paramétrage du moteur de base de données utilise la plus petite taille des tailles de stockage suivantes :  
  
-   Trois fois la taille des données brutes, qui comprend la taille totale des segments et des index cluster sur les tables.  
  
-   L'espace libre disponible sur tous les lecteurs de disques connectés, plus la taille des données brutes.  
  
 La taille de stockage par défaut ne comprend pas les index non-cluster et les vues indexées.  
  
 Si la valeur spécifiée pour l'élément `StorageBoundInMB` dépasse celle de l'espace disque, l'Assistant Paramétrage du moteur de base de données renvoie une erreur mais continue le paramétrage. Une fois le paramétrage terminé, vous pouvez ajouter de l'espace disque si vous décidez d'appliquer la recommandation.  
  
## <a name="example"></a>Exemple  
  
## <a name="description"></a>Description  
 L'exemple de code suivant montre comment définir une limite de 1500 mégaoctets comme espace disque maximal consommable par une recommandation de réglage :  
  
## <a name="code"></a>Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
