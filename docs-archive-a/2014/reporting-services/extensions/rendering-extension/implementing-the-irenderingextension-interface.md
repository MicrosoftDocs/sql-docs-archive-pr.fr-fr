---
title: Implémentation de l’interface IRenderingExtension | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f57c4aa41ccfed165b69581cbf3917e4dfbb4960
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610485"
---
# <a name="implementing-the-irenderingextension-interface"></a>Implémentation de l'interface IRenderingExtension
  L'extension de rendu prend les résultats d'une définition de rapport qui est combinée aux données réelles et restitue les données résultantes dans un format utilisable. La transformation de la combinaison des données et de la mise en forme s'effectue par le biais d'une classe CLR (Common Language Runtime) qui implémente <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>. Cela transforme le modèle objet en un format de sortie qui est consommable par une visionneuse, une imprimante ou une autre cible de sortie.  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> a trois méthodes qui doivent être codées :  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> : effectue le rendu du rapport.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> : effectue le rendu d'un flux spécifique à partir du rapport.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> :  obtient des informations supplémentaires, telles que des icônes, nécessaires pour le rapport.  
  
 Ces méthodes sont traitées en détail dans les sections suivantes.  
  
## <a name="render-method"></a>Méthode Render  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> contient des arguments qui représentent les objets suivants :  
  
-   L’objet *report* lui-même que vous souhaitez restituer. Cet objet contient des informations sur les propriétés, les données et la disposition du rapport. Le rapport est la racine de l'arborescence du modèle objet de rapport.  
  
-   Le paramètre *ServerParameters* qui contient l’objet dictionnaire de chaînes ainsi que les paramètres du serveur de rapports, le cas échéant.  
  
-   Le paramètre *deviceInfo* qui contient les paramètres de périphérique. Pour plus d’informations, consultez [Passage de paramètres d’informations sur les appareils aux extensions de rendu](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   Le paramètre *clientCapabilities* qui contient un objet dictionnaire <xref:System.Collections.Specialized.NameValueCollection> qui a des informations relatives au client destinataire du rendu.  
  
-   Le paramètre *RenderProperties* qui contient les informations relatives au résultat de rendu.  
  
-   La fonction *createAndRegisterStream* est une fonction de délégué à appeler pour obtenir un flux de données de rendu.  
  
### <a name="deviceinfo-parameter"></a>Paramètre deviceInfo  
 Le paramètre *deviceInfo* contient des paramètres de rendu, pas des paramètres de rapport. Ces paramètres de rendu sont passés à l'extension de rendu. Les valeurs *deviceInfo* sont converties en un objet <xref:System.Collections.Specialized.NameValueCollection> par le serveur de rapports. Les éléments dans le paramètre *deviceInfo* sont traités comme des valeurs non sensibles à la casse. Si la demande de rendu résulte d’un accès URL, les paramètres d’URL de type `rc:key=value` sont convertis en paires clé/valeur dans l’objet dictionnaire *deviceInfo*. Le code de détection du navigateur fournit également les éléments suivants dans le dictionnaire *clientCapabilities* : EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type et AcceptLanguage. Toute paire nom/valeur dans *deviceInfo* qui n’est pas interprétée par l’extension de rendu est ignorée. L'exemple de code suivant montre un exemple de méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> qui extrait des icônes :  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>Méthode RenderStream  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> restitue un flux particulier à partir du rapport. Tous les flux sont créés pendant l'appel <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> initial, mais les flux ne sont pas renvoyés initialement au client. Cette méthode est utilisée pour des flux secondaires (par exemple, des images dans le rendu HTML) ou des pages supplémentaires d'une extension de rendu multi-page (par exemple, Image/EMF).  
  
## <a name="getrenderingresource-method"></a>Méthode GetRenderingResource  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> extrait les informations sans exécuter un rendu entier du rapport. Il arrive que le rapport requière des informations qui ne nécessitent pas le rendu du rapport lui-même. Par exemple, si vous avez besoin de l’icône associée à l’extension de rendu, utilisez le paramètre *DeviceInfo* contenant la balise unique **\<Icon>** . Utilisez, dans ce cas, la méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de rendu](implementing-a-rendering-extension.md)   
 [Vue d'ensemble des extensions de rendu](rendering-extensions-overview.md)  
  
  
