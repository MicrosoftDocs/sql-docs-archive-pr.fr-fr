---
title: Méthode SetStringValue (classe ServerNetworkProtocolProperty) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8eb4a27d700d801e3ca94362663c6d7feaa7dc86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696623"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="789ef-102">Méthode SetStringValue (classe ServerNetworkProtocolProperty)</span><span class="sxs-lookup"><span data-stu-id="789ef-102">SetStringValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="789ef-103">Définit la valeur de chaîne de la propriété référencée.</span><span class="sxs-lookup"><span data-stu-id="789ef-103">Sets the string value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="789ef-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="789ef-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="789ef-105">Parts</span></span>  
 <span data-ttu-id="789ef-106">*object*</span><span class="sxs-lookup"><span data-stu-id="789ef-106">*object*</span></span>  
 <span data-ttu-id="789ef-107">A [classe ServerNetworkProtocolProperty](servernetworkprotocolproperty-class.md) qui représente un attribut du protocole réseau sur l'instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="789ef-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="789ef-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="789ef-108">Parameters</span></span>  
  
|<span data-ttu-id="789ef-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="789ef-109">Parameter</span></span>|<span data-ttu-id="789ef-110">Description</span><span class="sxs-lookup"><span data-stu-id="789ef-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="789ef-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="789ef-111">*StrValue*</span></span>|<span data-ttu-id="789ef-112">Valeur de chaîne qui spécifie la nouvelle valeur de la propriété actuelle.</span><span class="sxs-lookup"><span data-stu-id="789ef-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="789ef-113">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="789ef-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="789ef-114">Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="789ef-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="789ef-115">Notes</span><span class="sxs-lookup"><span data-stu-id="789ef-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="789ef-116">See Also</span></span>  
 <span data-ttu-id="789ef-117">[Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="789ef-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  