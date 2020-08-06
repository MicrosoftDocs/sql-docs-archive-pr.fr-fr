---
title: Configurer un serveur de rapports pour la remise par messagerie (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611518"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a>Configurer un serveur de rapports pour la remise par messagerie (Gestionnaire de configuration de SSRS)


  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de la remise du courrier électronique que vous pouvez utiliser pour distribuer les rapports par courrier électronique. Selon la façon dont vous définissez l'abonnement de messagerie électronique, une remise peut consister en une notification, un lien, une pièce jointe ou un rapport incorporé. L'extension de remise de courrier électronique fonctionne avec votre technologie de serveur de messagerie existante. Le serveur de messagerie doit être un serveur SMTP ou redirecteur. Le serveur de rapports se connecte à un serveur SMTP par le biais de bibliothèques CDO (Collaboration Data Objects) (cdosys.dll) fournies par le système d'exploitation.  
  
 L'extension de remise du courrier électronique par le serveur de rapports n'est pas configurée par défaut. Vous devez utiliser le Gestionnaire de configuration de Reporting Services pour effectuer une configuration minimale de l'extension. Pour définir des propriétés avancées, vous devez modifier le fichier `RSReportServer.config` . Si vous ne pouvez pas configurer le serveur de rapports afin qu'il utilise cette extension, vous pouvez remettre les rapports dans un dossier partagé à la place. Pour plus d'informations, consultez [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a>Configuration requise  
  
-   La remise du courrier électronique par le serveur de rapports est implémentée sur des objets de données de collaboration (CDO) et nécessite un serveur SMTP (Simple Mail Transfer Protocol) local ou distant, ou encore un redirecteur SMTP. Le protocole SMTP n'est pas pris en charge sur tous les systèmes d'exploitation Windows. Si vous utilisez l'édition Itanium de Windows Server 2008, le protocole SMTP n'est pas pris en charge. Pour plus d'informations sur les options de configuration fournies par le biais des objets CDO, consultez [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) sur MSDN.  
  
-   Le compte de service Report Server doit être autorisé à envoyer du courrier sur le serveur SMTP.  
  
-   L'extension de remise du courrier électronique utilise l'encodage UTF-8 dans les pièces jointes électroniques. Vous ne pouvez pas modifier cet encodage ; l'extension de rendu HTML prend en charge UTF-8 uniquement.  
  
> [!NOTE]  
>  L'extension par défaut de la remise du courrier électronique ne prend pas en charge la signature numérique et le chiffrement des messages sortants.  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a>Configuration d’un serveur de rapports pour un service SMTP local ou distant  
 Vous pouvez utiliser un service SMTP local ou un serveur ou un redirecteur SMTP distant pour la prise en charge de la remise du courrier électronique. Si vous pouvez accéder à un serveur SMTP existant à distance, pensez à l'utiliser. Si aucun serveur SMTP n'est disponible ou si vous rencontrez par la suite des erreurs liées à la remise des rapports attribuables aux pannes de connexion de l'ordinateur, nous vous recommandons d'utiliser plutôt un service SMTP local. Cette rubrique couvre plus en détail le mode de configuration d'un serveur de rapports pour un service local ou distant.  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a>Définition des options de configuration pour la remise par messagerie  
 Avant d'utiliser la remise du courrier électronique par le serveur de rapports, vous devez définir les valeurs de configuration fournissant des informations sur le mode d'utilisation du serveur SMTP.  
  
 Pour configurer un serveur de rapports pour la remise par messagerie, procédez comme suit :  
  
-   Utilisez le Gestionnaire de configuration de Reporting Services si vous spécifiez simplement un serveur SMTP et un compte d'utilisateur ayant l'autorisation d'envoyer des messages électroniques. Ce sont les paramètres minimum requis pour configurer l'extension de remise du courrier électronique par le serveur de rapports. Pour plus d’informations, consultez [paramètres de messagerie électronique-Configuration Manager &#40;mode natif SSRS&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) et [remise par courrier électronique dans Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   (Facultatif) Utilisez un éditeur de texte pour spécifier les paramètres supplémentaires dans le fichier RSreportserver.config. Ce fichier contient tous les paramètres de configuration pour la remise du courrier électronique par le serveur de rapports. La spécification de paramètres supplémentaires dans ces fichiers est obligatoire si vous utilisez un serveur SMTP local ou si vous limitez la remise par messagerie à des hôtes spécifiques. Pour plus d’informations sur la recherche et la modification des fichiers de configuration, consultez [modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) dans documentation en ligne de SQL Server.  
  
> [!NOTE]  
>  Les paramètres du courrier électronique pour le serveur de rapports dépendent du CDO. Si vous souhaitez obtenir plus de détails sur des paramètres spécifiques, reportez-vous à la documentation de production CDO.  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a>Exemple de configuration de la messagerie du serveur de rapports  
 L'exemple suivant illustre les paramètres dans le fichier RSreportserver.config pour un serveur SMTP distant. Pour plus d'dans la documentation en ligne deformations sur les descriptions et les valeurs valides de paramètres, consultez [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onldans la documentation en ligne dee or the CDO product documentation.  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a>Options de configuration pour la définition du champ à : dans un message  
 Les abonnements définis par l’utilisateur qui sont créés en fonction des autorisations accordées par la tâche **gérer les abonnements individuels** contiennent un nom d’utilisateur prédéfini basé sur le compte d’utilisateur de domaine. Quand l’utilisateur crée l’abonnement, le nom du destinataire dans le champ **À :** est configuré automatiquement à l’adresse de la personne qui crée l’abonnement, au moyen du compte d’utilisateur de domaine.  
  
 Si vous utilisez un redirecteur ou un serveur SMTP qui utilise des comptes de messagerie différents du compte d'utilisateur de domaine, la remise des rapports échouera lorsque le serveur SMTP tentera de remettre le rapport à cet utilisateur.  
  
 Pour contourner ce problème, vous pouvez modifier les paramètres de configuration qui permettent aux utilisateurs d'entrer un nom dans le champ **À :** .  
  
1.  Ouvrez le fichier RSReportServer.config avec un éditeur de texte.  
  
2.  Définissez `SendEmailToUserAlias` sur `False`.  
  
3.  Définissez `DefaultHostName` au nom DNS (Domain Name System) ou à l'adresse IP du redirecteur ou du serveur SMTP.  
  
4.  Enregistrez le fichier .  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a>Options de configuration pour le service SMTP distant  
 La connexion entre le serveur de rapports et le serveur ou redirecteur SMTP est déterminée par les paramètres de configuration suivants :  
  
-   `SendUsing` spécifie une méthode pour l’envoi de messages. Vous pouvez choisir entre un service SMTP réseau ou un répertoire de collecte du service SMTP local. Pour utiliser un service SMTP distant, cette valeur doit être définie sur **2** dans le fichier RSReportServer.config.  
  
-   `SMTPServer` spécifie le serveur ou le redirecteur SMTP distant. Cette valeur est obligatoire si vous utilisez un serveur ou un redirecteur SMTP distant.  
  
-   `From`définit la valeur qui s’affiche dans la ligne de **:** d’un message électronique. Cette valeur est obligatoire si vous utilisez un serveur ou un redirecteur SMTP distant.  
  
 D'autres valeurs utilisées pour le service SMTP distant comprennent ce qui suit (notez que vous n'avez pas besoin de les spécifier à moins de vouloir remplacer les valeurs par défaut).  
  
-   **SMTPServerPort** est configuré pour le port 25.  
  
-   **SMTPAuthenticate** spécifie le mode de connexion du serveur de rapports au serveur SMTP distant. La valeur par défaut est 0 (ou aucune authentification). Dans ce cas, la connexion est effectuée par un accès anonyme. En fonction de la configuration de votre domaine, il est possible que le serveur de rapports et le serveur SMTP soient obligés d'être des membres du même domaine.  
  
     Pour envoyer du courrier électronique aux listes de distribution limitée (par exemple, les listes de distribution qui acceptent des messages entrants uniquement à partir de comptes authentifiés), définissez **SMTPAuthenticate** sur la valeur **2**.  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a>Options de configuration pour le service SMTP local  
 La configuration d'un service SMTP local est pratique si vous testez ou dépannez la remise du courrier électronique par le serveur de rapports. Par défaut, le service SMTP local n'est pas activé. Pour obtenir des instructions sur la façon de l’activer, consultez [configurer un serveur de rapports pour la remise par messagerie (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) et [paramètres de messagerie-Configuration Manager &#40;le Mode natif SSRS&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 La connexion entre le serveur de rapports et le serveur ou le redirecteur SMTP local est déterminée par les paramètres de configuration suivants :  
  
-   `SendUsing` est défini sur **1**.  
  
-   **SMTPServerPickupDirectory** est défini sur un dossier de lecteur local.  
  
    > [!NOTE]  
    >  Veillez à ne pas définir `SMTPServer` si vous utilisez un serveur SMTP local.  
  
-   `From`définit la valeur qui s’affiche dans la ligne de **:** d’un message électronique. Cette valeur est requise.  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a>Pour configurer la messagerie électronique du serveur de rapports à l’aide de l’Gestionnaire de configuration de Reporting Services  
  
1.  Vérifiez que le service Report Server Windows a des autorisations `Send As` sur le serveur SMTP.  
  
2.  Démarrez le Gestionnaire de configuration de Reporting Services, puis connectez-vous à l'instance du serveur de rapports.  
  
3.  Sur la page Paramètres de messagerie, entrez le nom du serveur SMTP. Il peut s'agir d'une adresse IP, du nom UNC d'un ordinateur sur l'intranet de votre entreprise ou d'un nom de domaine complet.  
  
4.  Dans **Adresse de l'expéditeur**, tapez le nom d'un compte qui a l'autorisation d'envoyer des messages électroniques à partir du serveur SMTP.  
  
5.  Cliquez sur **Appliquer**.  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a>Pour configurer un service SMTP distant pour le serveur de rapports  
  
1.  Vérifiez que le service Report Server Windows a des autorisations `Send As` sur le serveur SMTP.  
  
2.  Ouvrez le fichier RSReportServer.config dans un éditeur de texte.  
  
3.  Vérifiez que <`UrlRoot`> est définie sur l’adresse URL du serveur de rapports. Cette valeur est définie lorsque vous configurez le serveur de rapports et elle devrait normalement être déjà définie. Si elle n'est pas définie, tapez l'adresse URL du serveur de rapports.  
  
4.  Dans la section remise, recherchez <`ReportServerEmail`>.  
  
5.  Dans <`SMTPServer`>, tapez le nom du serveur SMTP. Il peut s'agir d'une adresse IP, du nom UNC d'un ordinateur sur l'intranet de votre entreprise ou d'un nom de domaine complet.  
  
6.  Vérifiez que <`SendUsing`> a la valeur 2. Si la valeur est différente, le serveur de rapports n'est pas configuré pour utiliser un service SMTP distant.  
  
7.  Dans <`From`>, tapez le nom d’un compte qui a l’autorisation d’envoyer du courrier électronique à partir du serveur SMTP.  
  
8.  Enregistrez le fichier .  
  
     Le serveur de rapports utilise automatiquement les nouveaux paramètres ; il n'est pas nécessaire de redémarrer le service. Vous pouvez spécifier des paramètres SMTP supplémentaires pour configurer comment le serveur SMTP est utilisé pour la remise par messagerie du serveur de rapports. Pour plus d'dans la documentation en ligne deformations, consultez [Configurdans la documentation en ligne deg a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) et [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onldans la documentation en ligne dee.  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a>Pour configurer un service SMTP local pour le serveur de rapports  
  
1.  Dans le Panneau de configuration, cliquez sur **Ajout/Suppression de programmes**.  
  
2.  Cliquez sur **Ajouter/Supprimer des composants Windows** pour démarrer l'Assistant Composants Windows.  
  
3.  Sélectionnez **Serveur d'applications** et cliquez sur **Détails**.  
  
4.  Sélectionnez **Services Internet (IIS)** , puis cliquez sur **Détails**.  
  
5.  Activez la case à cocher **Service SMTP** , puis cliquez sur **OK**.  
  
6.  Dans l'Assistant Composants Windows, cliquez sur **Suivant**. Cliquez sur **Terminer**.  
  
7.  Vérifiez que le service s'exécute dans la console **Services** .  
  
8.  Ouvrez le fichier **RSReportServer.config** dans un éditeur de texte.  
  
9. Vérifiez que `<UrlRoot>` est paramétré à l'adresse URL du serveur de rapports. Cette valeur est définie lorsque vous configurez le serveur de rapports et elle devrait normalement être déjà définie. Si elle n'est pas définie, tapez l'adresse URL du serveur de rapports.  
  
10. Dans la section Remise, recherchez `<ReportServerEmail>.`.  
  
11. Dans `<SMTPServer>`, effacez les valeurs pour ce paramètre, mais ne supprimez pas les balises.  
  
12. Affectez à `<SendUsing>` la valeur 1. Si la valeur est différente, le serveur de rapports n'est pas configuré pour utiliser un service SMTP local.  
  
13. Définissez `<SMTPServerPickupDirectory>` sur un dossier de lecteur local.  
  
14. Définissez `<From>` sur un compte qui a l'autorisation d'envoyer des messages électroniques à partir du serveur SMTP.  
  
15. Enregistrez le fichier .  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
