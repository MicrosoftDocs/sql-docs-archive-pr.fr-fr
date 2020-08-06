---
title: Modifier l’extension de remise par défaut de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703752"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a>Modification de l’extension de remise par défaut de Reporting Services
  Vous pouvez modifier les paramètres de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] pour modifier l’extension de remise par défaut qui s’affiche dans la liste **Remis par** d’une page de définition d’abonnement. Par exemple, vous pouvez modifier la configuration afin que, lorsque les utilisateurs créent un nouvel abonnement, la remise par partage de fichiers soit activée par défaut, plutôt que la remise par messagerie électronique. Vous pouvez également modifier l'ordre selon lequel les extensions de remise sont répertoriées dans l'interface utilisateur.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode natif | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode SharePoint

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] comprend les extensions de remise par messagerie électronique et de remise par partage de fichiers Windows. Il se peut que votre serveur de rapports possède des extensions de remise supplémentaires si vous avez déployé des extensions personnalisées ou tierces pour la prise en charge d'une remise personnalisée. La disponibilité d'une extension de remise varie selon qu'elle est déployée sur un serveur de rapports.

## <a name="default-native-mode-report-server-configuration"></a>Configuration de serveur de rapports en mode natif par défaut
 L’ordre d’une extension de remise dans la liste **Remis par** du Gestionnaire de rapports dépend de l’ordre des entrées d’extension de remise dans le fichier **RSReportServer.config** . Par exemple, l'image suivante présente la messagerie au début de la liste et elle est sélectionnée par défaut.

 ![liste par défaut des extensions de remise](../media/ssrs-default-delivery.png "liste par défaut des extensions de remise")

 Voici la section par défaut de **RSReportServer.config** qui contrôle l’extension de remise par défaut et l’ordre d’apparition dans le Gestionnaire de rapports. Notez que la messagerie électronique apparaît en premier dans le fichier, elle est définie comme valeur par défaut.

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a>Configuration de la remise par partage de fichiers comme extension de remise par défaut dans le Gestionnaire de rapports

1.  Les étapes de cette procédure modifient la configuration afin que la remise par partage de fichiers soit répertoriée comme la première option dans l'interface utilisateur et soit la sélection par défaut.

     Ouvrez le fichier RSReportServer.config dans un éditeur de texte. Pour plus d'informations sur le fichier de configuration, consultez [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md). Une fois la configuration modifiée, l'interface utilisateur doit ressembler à l'image suivante :

     ![liste modifiée des extensions de remise](../media/ssrs-modified-delivery.png "liste modifiée des extensions de remise")

2.  Modifiez la section DeliveryUI pour qu’elle ressemble à l'exemple suivant et notez les changements principaux :

    1.  L'extension de partage de fichiers se trouve avant l'extension de messagerie. Cela modifie l'ordre selon lequel les extensions sont répertoriées dans le Gestionnaire de rapports.

    2.  L’extension de partage de fichiers contient la balise DefaultExtension `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` et `</Extension>`a été ajouté à la balise de fin d’extension.

    3.  L'extension de messagerie n'est plus configurée comme celle par défaut. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  Enregistrez le fichier de configuration.

4.  En quelques minutes, le serveur de rapports recharge le fichier de configuration et les nouveaux paramètres prennent effet. Vous pouvez redémarrer le service de serveur de rapports pour forcer le chargement du fichier de configuration.

     Lors de la lecture de la configuration, l'événement suivant est écrit dans le journal des événements Windows.

     **ID d’événement :** 109

     **Source :** Service Windows Serveur de rapports (nom de l'instance)

     Le fichier RSReportServer.config a été modifié.

## <a name="sharepoint-mode-report-servers"></a>Serveurs de rapports en mode SharePoint
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Le mode SharePoint stocke les informations d’extensions dans les bases de données d’application de service SharePoint et non dans le fichier RsrReportServer.config. En mode SharePoint, la configuration d'extension de remise est modifiée à l'aide de PowerShell.

#### <a name="configure-the-default-delivery-extension"></a>Configuration de l'extension de remise par défaut

1.  Ouvrez **SharePoint Management Shell**.

2.  Vous pouvez ignorer cette étape si vous connaissez déjà le nom de votre application de service [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Utilisez la commande PowerShell suivante pour dresser la liste des applications de service [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] présentes dans votre batterie de serveurs SharePoint.

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  Exécutez la commande PowerShell suivante pour vérifier l’extension de remise par défaut actuelle de l’application de service [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] « ssrsapp ».

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a>Voir aussi
 [Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md) fichier de [configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md) [remise par partage de fichiers dans Reporting Services](file-share-delivery-in-reporting-services.md) [remise par courrier électronique dans Reporting Services](e-mail-delivery-in-reporting-services.md) [configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)
