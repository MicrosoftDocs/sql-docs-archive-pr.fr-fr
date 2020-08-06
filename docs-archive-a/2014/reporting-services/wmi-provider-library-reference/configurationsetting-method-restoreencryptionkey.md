---
title: RestoreEncryptionKey, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e67478541bab615a6d441ae273ed3385a8654203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706072"
---
# <a name="restoreencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="0b06c-102">Méthode RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="0b06c-102">RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="0b06c-103">Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0b06c-103">Reapplies the specified encryption key to the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b06c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b06c-104">Syntax</span></span>  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b06c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b06c-105">Parameters</span></span>  
 <span data-ttu-id="0b06c-106">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="0b06c-106">*KeyFile[]*</span></span>  
 <span data-ttu-id="0b06c-107">[out] Tableau contenant la clé de chiffrement chiffrée.</span><span class="sxs-lookup"><span data-stu-id="0b06c-107">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="0b06c-108">*Longueur*</span><span class="sxs-lookup"><span data-stu-id="0b06c-108">*Length*</span></span>  
 <span data-ttu-id="0b06c-109">[out] Longueur du tableau retourné par la méthode.</span><span class="sxs-lookup"><span data-stu-id="0b06c-109">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="0b06c-110">*Mot de passe*</span><span class="sxs-lookup"><span data-stu-id="0b06c-110">*Password*</span></span>  
 <span data-ttu-id="0b06c-111">Chaîne utilisée pour chiffrer la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="0b06c-111">A string used to encrypt the encryption key.</span></span>  
  
 <span data-ttu-id="0b06c-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="0b06c-112">*HRESULT*</span></span>  
 <span data-ttu-id="0b06c-113">[out] Valeur indiquant si l'appel a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="0b06c-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="0b06c-114">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="0b06c-114">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="0b06c-115">[out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.</span><span class="sxs-lookup"><span data-stu-id="0b06c-115">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b06c-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0b06c-116">Return Value</span></span>  
 <span data-ttu-id="0b06c-117">Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué.</span><span class="sxs-lookup"><span data-stu-id="0b06c-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="0b06c-118">Une valeur 0 indique que l'appel de méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="0b06c-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="0b06c-119">Une valeur différente de zéro indique qu'une erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="0b06c-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b06c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0b06c-120">Remarks</span></span>  
 <span data-ttu-id="0b06c-121">S'il existe déjà une entrée pour le serveur de rapports dans la base de données du serveur de rapports, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="0b06c-121">If an entry already exists for the report server in the report server database, it is deleted.</span></span> <span data-ttu-id="0b06c-122">La nouvelle entrée est ensuite créée à l’aide de la clé de chiffrement spécifiée et de la clé publique du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="0b06c-122">The new entry is then created using the specified encryption key and the report server's public key.</span></span>  
  
 <span data-ttu-id="0b06c-123">Cette méthode est très efficace quand elle est appelée après la méthode [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) , qui efface la liste de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="0b06c-123">The method is most effective when called after the [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) method, which clears the list of encryption keys.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b06c-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0b06c-124">Requirements</span></span>  
 <span data-ttu-id="0b06c-125">**Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b06c-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b06c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b06c-126">See Also</span></span>  
 [<span data-ttu-id="0b06c-127">Membres MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="0b06c-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  