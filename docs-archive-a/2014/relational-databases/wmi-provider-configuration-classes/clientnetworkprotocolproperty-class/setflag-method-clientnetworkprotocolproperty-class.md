---
title: Méthode SetFlag (classe ClientNetworkProtocolProperty) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1c83a1d647b62f0e5c5acf0659d54bf787bf0c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706335"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="cc8fa-102">Méthode SetFlag (classe ClientNetworkProtocolProperty)</span><span class="sxs-lookup"><span data-stu-id="cc8fa-102">SetFlag Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="cc8fa-103">Définit l'indicateur de la propriété actuelle référencée par la valeur de la [propriété PropertyIdx (classe ClientNetworkProtocolProperty)](clientnetworkprotocolproperty-class.md) .</span><span class="sxs-lookup"><span data-stu-id="cc8fa-103">Sets the flag of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc8fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc8fa-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
) [=]  
```  
  
## <a name="parts"></a><span data-ttu-id="cc8fa-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="cc8fa-105">Parts</span></span>  
 <span data-ttu-id="cc8fa-106">*object*</span><span class="sxs-lookup"><span data-stu-id="cc8fa-106">*object*</span></span>  
 <span data-ttu-id="cc8fa-107">A [classe ClientNetworkProtocolProperty](clientnetworkprotocolproperty-class.md) qui représente un attribut du protocole réseau utilisé par le client [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cc8fa-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="cc8fa-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc8fa-108">Parameters</span></span>  
  
|<span data-ttu-id="cc8fa-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cc8fa-109">Parameter</span></span>|<span data-ttu-id="cc8fa-110">Description</span><span class="sxs-lookup"><span data-stu-id="cc8fa-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc8fa-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="cc8fa-111">*BoolValue*</span></span>|<span data-ttu-id="cc8fa-112">Valeur booléenne qui spécifie la nouvelle valeur de l'indicateur.</span><span class="sxs-lookup"><span data-stu-id="cc8fa-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="cc8fa-113">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cc8fa-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="cc8fa-114">Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="cc8fa-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc8fa-115">Notes</span><span class="sxs-lookup"><span data-stu-id="cc8fa-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc8fa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc8fa-116">See Also</span></span>  
 [<span data-ttu-id="cc8fa-117">Configurer des protocoles clients</span><span class="sxs-lookup"><span data-stu-id="cc8fa-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  