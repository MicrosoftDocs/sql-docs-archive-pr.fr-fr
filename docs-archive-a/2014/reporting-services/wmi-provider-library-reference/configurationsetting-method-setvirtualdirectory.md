---
title: SetVirtualDirectory, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7f45181f3f6a791f5cb64a7519285b6d2a87dd36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706040"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a>Méthode SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)
  Définit le nom du répertoire virtuel pour une application donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Application*  
 Nom de l'application pour laquelle définir le répertoire virtuel.  
  
 *VirtualDirectory*  
 Nom du répertoire virtuel.  
  
 *lcid*  
 ID de paramètres régionaux du répertoire virtuel.  
  
 *Error*  
 [out] Description de l'erreur qui s'est produite.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
 Une application ne peut avoir qu'un seul nom de répertoire virtuel pour toutes les réservations d'URL.  
  
 VirtualDirectory doit être conforme aux conventions d'affectation des noms pour les répertoires virtuels. VirtualDirectory ne doit pas être une chaîne vide ou contenant uniquement un espace.  
  
 Met à jour la valeur de l'élément \Configuration\URLReservations\Application\VirtualDirectory. Réussit même si aucune réservation d'URL n'a encore été créée.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
