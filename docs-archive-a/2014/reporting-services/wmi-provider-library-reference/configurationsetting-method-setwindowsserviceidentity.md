---
title: SetWindowsServiceIdentity, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706032"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a>Méthode SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Fait en sorte que le service Windows Report Server s'exécute en tant qu'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *UseBuiltInAccount*  
 Indique si le compte spécifié est un compte Windows intégré.  
  
 *Compte*  
 Compte Windows à utiliser pour exécuter le service Windows, au format « DOMAINE\alias ».  
  
 *Mot de passe*  
 Mot de passe du compte.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque le paramètre *UseBuiltInAccount a* a la `true` valeur et que le serveur de rapports s’exécute sur Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] ou Windows XP, la valeur des paramètres *Name*, *Domain*et *Password* est ignorée et le compte système local est utilisé.  
  
 Lorsque le paramètre *UseBuiltInAccount a* a la valeur `true` et que le serveur de rapports s’exécute sur Windows Server 2003, les propriétés *Domain* et *Password* sont ignorées, et le champ Name doit contenir « Builtin\System » ou « , » ou « Builtin\LocalService ».  
  
 La méthode SetWindowsServiceIdentity définit des autorisations d’accès aux fichiers sur les fichiers et les dossiers dans le répertoire d’installation du serveur de rapports.  
  
 Le compte spécifié dans le paramètre de *compte* requiert `LogonAsService` des droits dans Windows. La méthode accorde ce droit au compte spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
