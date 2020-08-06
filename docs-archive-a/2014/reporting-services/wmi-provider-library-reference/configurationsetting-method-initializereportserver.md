---
title: InitializeReportServer, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604366"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a>Méthode InitializeReportServer (WMI MSReportServer_ConfigurationSetting)
  Initialise l'instance du service de rapports spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Paramètres  
 *InstallationID*  
 Chaîne utilisée pour chiffrer la clé de chiffrement avant qu'elle soit retournée.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette méthode est appelée, la clé de chiffrement qui accède aux informations sécurisées de la base de données du serveur de rapports est chiffrée à l'aide de la clé publique du serveur de rapports identifiée par *InstallationID*.  
  
 La clé publique du serveur de rapports spécifiée doit au préalable avoir été écrite dans la base de données du serveur de rapports.  
  
 La méthode *InitializeReportServer* doit être appelée contre un serveur de rapports qui a déjà accès aux informations sécurisées, afin qu'il puisse déchiffrer la clé de chiffrement. La clé de chiffrement chiffrée résultante est ensuite stockée dans la base de données du serveur de rapports.  
  
 Si la propriété [IsInitialized](configurationsetting-property-isinitialized.md) du serveur de rapports a la valeur `true` lorsque la méthode InitializeReportServer est appelée, la méthode retourne la valeur Success sans essayer de chiffrer la clé de chiffrement.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
