---
title: Méthode SetDefaults (classe SInstance) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c581834d3c97bed622d16fbb35e48704f8679531
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696591"
---
# <a name="setdefaults-method-sinstance-class"></a>Méthode SetDefaults (classe SInstance)
  Définit toutes les valeurs par défaut de l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l’option permettant de remplacer les données existantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SInstance](sinstance-class.md) qui représente une instance de serveur.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Valeur booléenne qui spécifie s'il faut remplacer la valeur existante sur l'instance du client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : `true` si les données existantes sont remplacées ou `false` si les données existantes ne sont pas remplacées.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
