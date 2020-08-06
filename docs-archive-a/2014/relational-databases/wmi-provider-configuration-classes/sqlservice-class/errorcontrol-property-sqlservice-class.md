---
title: Propriété ErrorControl (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706312"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Propriété ErrorControl (classe SqlService)
  Obtient ou définit la gravité de l'erreur si le service ne peut pas démarrer au démarrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur de chaîne qui spécifie la gravité de l'erreur signalée si le service échoue au démarrage. Le tableau suivant répertorie les valeurs possibles.  
  
 Ignorer  
 L'utilisateur n'est pas notifié.  
  
 Normal  
 L'utilisateur est notifié.  
  
 Severe  
 Le système est redémarré avec la dernière bonne configuration connue.  
  
 Critique  
 Le système tente de redémarrer avec une bonne configuration.  
  
 Unknown  
 La gravité est inconnue.  
  
## <a name="remarks"></a>Notes  
 La valeur indique l'action prise par le programme de démarrage en cas d'échec. Toutes les erreurs sont journalisées par le système informatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
