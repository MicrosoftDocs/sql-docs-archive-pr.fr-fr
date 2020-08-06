---
title: Méthode GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604368"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a>Méthode GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting)
  Génère un script SQL qui peut être utilisé pour créer une base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Databasename*  
 Chaîne contenant le nom de la base de données du serveur de rapports à créer.  
  
 *Lcid*  
 Valeur utilisée pour la localisation des noms de rôles.  
  
 *IsSharePointMode*  
 Indique s'il convient de créer la base de données en mode natif ou mode SharePoint.  
  
> [!IMPORTANT]  
>  À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , *IsSharePointMode* = `True` n’est pas pris en charge, car en mode SharePoint, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est un service partagé SharePoint et n’est pas contrôlé par le fournisseur WMI. Ce paramètre doit toujours avoir la valeur `False`.  
  
 *Script*  
 [out] Chaîne contenant le script SQL généré.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Cette méthode génère un script SQL qui crée des bases de données du serveur de rapports pour la version du serveur de rapports actuellement connecté.  
  
 La valeur fournie dans le paramètre *DatabaseName* doit être conforme aux conventions d’affectation des noms de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La méthode ne vérifie pas l'existence de la base de données lors de la génération du script.  
  
 Cette méthode ne vérifie pas l'existence de la base de données du serveur de rapports lors de la génération du script.  
  
 Le script généré prend en charge [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
