---
title: State, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702543"
---
# <a name="state-property-sqlservice-class"></a>Propriété State (classe SqlService)
  Obtient ou définit l'état actuel du service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 qui spécifie l'état du service.  
  
 Il peut s'agir de l'une des valeurs suivantes.  
  
 1  
 Arrêté. Le service est arrêté.  
  
 2  
 Démarrage en attente. Le service est en attente de démarrage.  
  
 3  
 Arrêt en attente. Le service est en attente d'arrêt.  
  
 4  
 En cours d'exécution. Le service est en cours d'exécution.  
  
 5  
 Continuation en attente. Le service est en attente de continuation.  
  
 6  
 Pause en attente. Le service est en attente de pause.  
  
 7  
 Suspendu. Le service est suspendu.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
