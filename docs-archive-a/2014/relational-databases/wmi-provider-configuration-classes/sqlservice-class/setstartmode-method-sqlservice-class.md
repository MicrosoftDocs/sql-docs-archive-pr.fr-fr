---
title: Méthode setStartMode, (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a9b7310623f526d7b106485ed9681df3aa100129
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600701"
---
# <a name="setstartmode-method-sqlservice-class"></a>Méthode SetStartMode (classe SqlService)
  Modifie le mode de démarrage de l'instance de service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
#### <a name="parameters"></a>Paramètres  
 *StartMode*  
 Valeur `uint32` qui spécifie le mode de démarrage de l'instance de service.  
  
 Les valeurs valides sont les suivantes :  
  
 Valeur = 0. Boot - Le pilote de périphérique est démarré par le chargeur du système d'exploitation. Cette valeur est uniquement valide pour les services de pilote.  
  
 Valeur = 1. System - Le pilote de périphérique est démarré par la méthode `IoInitSystem`. Cette valeur est uniquement valide pour les services de pilote.  
  
 Valeur = 2 Automatic - Le service doit être démarré automatiquement par le Gestionnaire de contrôle des services lors du démarrage du système.  
  
 Valeur = 3. Manual - Le service doit être démarré par Computer Manager lorsqu'un processus appelle la méthode `StartService`.  
  
 Valeur = 4 Disabled - Le service ne peut pas être démarré.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32` égale à 0 si le service a été correctement modifié ou égale à 1 si la demande n'est pas prise en charge. Tout autre nombre indique une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
