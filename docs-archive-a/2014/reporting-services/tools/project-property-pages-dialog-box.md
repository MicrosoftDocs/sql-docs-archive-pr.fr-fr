---
title: Pages de propriétés du projet, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700679"
---
# <a name="project-property-pages-dialog-box"></a>Pages de propriétés du projet, boîte de dialogue
  Utilisez les pages de propriétés du projet pour configurer les propriétés de déploiement d'un projet Report Server. Pour ouvrir cette boîte de dialogue, dans le menu **projet** , cliquez sur _\<Report Project Name>_ **Propriétés**.  
  
 Après avoir défini les propriétés de configuration, sélectionnez une configuration dans la liste déroulante **Configurations de solutions** de la barre d’outils.  
  
## <a name="options"></a>Options  
 **Configuration**  
 Sélectionnez la configuration à modifier. Initialement, les configurations suivantes sont disponibles : **Debug**, **DebugLocal**et **Release**. La configuration active apparaît d’abord, par exemple, **Active(Débogage)**.  
  
 Pour consulter simultanément les propriétés de plusieurs configurations, sélectionnez **Toutes les configurations** ou **Configurations multiples**.  
  
 Pour créer d’autres configurations, cliquez sur **Gestionnaire de configurations** dans la barre d’outils.  
  
 **Gestionnaire de configuration**  
 Gérer les configurations de l'ensemble de la solution ou ajouter des configurations supplémentaires. Pour plus d’informations, consultez la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.  
  
 **OutputPath**  
 Tapez ou collez le chemin d'accès pour stocker la définition de rapport utilisée dans la vérification de la génération, le déploiement et l'aperçu de rapports. Le chemin d'accès doit être différent de celui que vous utilisez pour le projet et un chemin d'accès relatif qui est un dossier enfant sous le chemin d'accès du projet.  
  
> [!NOTE]  
>  Vous pouvez utiliser plusieurs configurations pour passer d'un chemin d'accès à un autre selon la tâche que vous effectuez.  
  
 **Appuie**  
 Tapez la gravité des problèmes de génération signalés comme erreurs. Les problèmes avec des niveaux de gravité inférieurs ou égaux à la valeur **ErrorLevel** sont signalés comme des erreurs. Sinon, les problèmes sont signalés comme des avertissements. Toute erreur provoquera l'échec de la tâche de génération. Les niveaux de gravité valides sont compris entre 0 et 4. La valeur par défaut est 2.  
  
 **StartItem**  
 Sélectionnez le rapport qui est affiché dans le navigateur Web une fois le projet publié sur le serveur de rapports ou dans la fenêtre d'aperçu lorsque le projet est exécuté localement. Un élément de départ est requis pour les configurations qui créent le projet sans le déployer et pour utiliser la commande **Debug** (**F5**). Il est nécessaire pour les configurations qui déploient le projet.  
  
 **OverwriteDataSources**  
 Sélectionnez **True** pour remplacer la source de données du serveur par celle du projet lorsque les rapports sont publiés. Sélectionnez **False** pour conserver la source de données existante sur le serveur.  
  
 **TargetServerVersion**  
 Sélectionnez la [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] version ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] de, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou sélectionnez **détecter la version** pour déterminer automatiquement la version installée sur le serveur identifié par la propriété **URL de TargetServer** . La valeur par défaut est **SQL Server 2008 R2**.  
  
 **TargetDataSourceFolder**  
 Nom du dossier dans lequel les sources de données partagées publiées sont stockées. Si vous ne spécifiez pas de dossier, la source de données est publiée dans le même dossier que le rapport. Si le dossier n'existe pas sur le serveur de rapports, le Générateur de rapports le crée lors de la publication des rapports.  
  
 Lors de la publication sur un serveur de rapports s'exécutant en mode natif, spécifiez le chemin complet de la hiérarchie des dossiers à partir de la racines. Par exemple, Dossier1/Dossier2/Dossier3.  
  
 Lors de la publication sur un serveur de rapports s’exécutant en mode intégré SharePoint, utilisez une URL de la bibliothèque SharePoint. Par exemple, http:// *\<servername>/\<site>* /documents/mondossier.  
  
 **TargetReportFolder**  
 Nom du dossier dans lequel stocker les rapports publiés. Par défaut, il s'agit du nom du projet de rapport. Si le dossier n'existe pas sur le serveur de rapports, le Générateur de rapports le crée lors de la publication des rapports.  
  
 Lors de la publication sur un serveur de rapports s'exécutant en mode natif, spécifiez le chemin complet de la hiérarchie des dossiers à partir de la racines. Si un dossier se trouve dans un autre dossier, incluez un chemin d'accès vers le dossier à partir de la racine, par exemple Folder1/Folder2/Folder3.  
  
 Lors de la publication sur un serveur de rapports s'exécutant en mode intégré SharePoint, utilisez une URL de la bibliothèque SharePoint. Par exemple, http:// *\<servername>* / *\<site>* /documents/mondossier.  
  
 **TargetServerURL**  
 URL du serveur de rapports cible. Avant de publier un rapport, vous devez affecter à cette propriété une URL de serveur de rapports valide.  
  
 Lors de la publication sur un serveur de rapports s’exécutant en mode natif, utilisez l’URL du répertoire virtuel du serveur de rapports. Par exemple, http:// \<server> /reportserver. Il s'agit du répertoire virtuel du serveur de rapports et non du Gestionnaire de rapports. Par défaut, le serveur de rapports est installé dans un répertoire virtuel nommé « reportserver ».  
  
 Lors de la publication sur un serveur de rapports s'exécutant en mode intégré SharePoint, utilisez l'URL d'un site de premier niveau ou d'un sous-site SharePoint. Si vous ne spécifiez aucun site, le site de premier niveau par défaut est utilisé. Par exemple, http:// \<*servername> *, http://<* ServerName */\<*site>* ou http:// \<*servername> */\<*site>* / \<*subsite> *.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des rapports](../publish-reports.md)   
 [Publier un rapport dans une bibliothèque SharePoint](../reports/publish-a-report-to-a-sharepoint-library.md)   
 [Définir les propriétés de déploiement &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md)   
 [Aide sur le Concepteur de rapports via la touche F1](report-designer-f1-help.md)  
  
  
