---
title: IsSharePointIntegrated, propriété (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604344"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a>Propriété IsSharePointIntegrated (WMI MSReportServer_Instance)
  Spécifie si le serveur de rapports s'exécute en mode intégré SharePoint. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette propriété retourne toujours `False`, car en mode SharePoint, les instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont des services partagés SharePoint et ne sont pas contrôlées par les fournisseurs WMI.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Valeur `Boolean` qui indique si le serveur de rapports fonctionne en mode intégré SharePoint.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_Instance](msreportserver-instance-members.md)   
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  
