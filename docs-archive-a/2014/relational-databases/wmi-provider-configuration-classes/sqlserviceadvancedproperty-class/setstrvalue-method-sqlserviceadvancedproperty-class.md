---
title: Méthode SetStrValue (classe SqlServiceAdvancedProperty) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStrValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStrValue method
ms.assetid: 1fededc3-81ba-4b08-83f9-189b96140799
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d977eb9845c820c4128d1d60337151eeb3893eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702520"
---
# <a name="setstrvalue-method-sqlserviceadvancedproperty-class"></a>Méthode SetStrValue (classe SqlServiceAdvancedProperty)
  Définit la valeur de chaîne d'une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetStrValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlServiceAdvancedProperty](sqlserviceadvancedproperty-class.md) qui représente une propriété avancée.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*StrValue*|Valeur de chaîne qui spécifie la valeur de la propriété avancée.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
 Le type de valeur de la propriété doit être *string* pour permettre l'attribution d'une valeur de chaîne à la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
