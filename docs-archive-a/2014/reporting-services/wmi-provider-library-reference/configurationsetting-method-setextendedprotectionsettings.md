---
title: SetExtendedProtectionSettings, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee937747b74bcf8d53012721b4be5bfca04185df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706060"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a>Méthode SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)
  La méthode SetExtendedProtectionSettings sert à définir les propriétés RSWindowsExtendedProtectionLevel et RSWindowsExtendedProtectionScenario dans le fichier de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (RSReportServer.config).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ExtendedProtectionLevel*  
 Définit RSWindowsExtendedProtectionLevel dans le fichier RSRreportserver.config. La valeur est obligatoire et ne respecte pas la casse.  
  
 La liste suivante affiche les valeurs valides :  
  
 `"Off | Allow | Require"`  
  
 *ExtendedProtectionScenario*  
 Définit RSWindowsExtendedProtectionScenario dans le fichier RSReportserver.config. La valeur est obligatoire et ne respecte pas la casse.  
  
 La liste suivante affiche les valeurs valides :  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a>Notes  
 Les propriétés RSWindowsExtendedProtectionLevel et RSWindowsExtendedProtectionScenario s'appliquent lorsque AuthenticationTypes dans le fichier RSReportServer.config inclut RSWindowNTLM, RSWindowsNegotiate ou RSWindowsKerberos. La définition de ces propriétés change la manière dont les utilisateurs et le logiciel client sont authentifiés au niveau du serveur de rapports. Nosu vous conseillons de lire la documentation relative à la protection étendue avant de définir la propriété ExtendedProtectionLevel sur `Allow` ou `Require`.  
  
 Pour définir la propriété ExtendedProtectionLevel, l'utilisateur doit être un membre du groupe BUILTIN\Administrators sur le serveur de rapports.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Propriété RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Protection étendue de l’authentification avec Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
