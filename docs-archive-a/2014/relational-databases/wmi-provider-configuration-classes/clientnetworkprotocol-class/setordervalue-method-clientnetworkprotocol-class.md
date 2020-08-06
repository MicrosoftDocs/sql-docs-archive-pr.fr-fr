---
title: Méthode SetOrderValue (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6839e85b6131c54e233d980c84a8727eeda2202a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614449"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a>Méthode SetOrderValue (classe ClientNetworkProtocol)
  Sélectionne le protocole avec la valeur d'ordre spécifiée dans la liste de protocoles du client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetOrderValue(  
OrderValue  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*OrderValue*|Valeur u`int32` qui définit la valeur d'ordre.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de protocoles clients (onglet Ordre)](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
