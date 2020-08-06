---
title: Personnaliser le composant WebPart Visionneuse de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- Report Viewer Web Part [Reporting Services]
ms.assetid: 086d6546-7299-41bc-bca9-083a15a53679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bab401254cbe49f1239b4dc983d6a4ad68e077e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708983"
---
# <a name="customize-the-report-viewer-web-part"></a>Personnaliser le composant WebPart Visionneuse de rapports
  Vous pouvez utiliser le composant WebPart Visionneuse de rapports pour afficher les rapports qui s'exécutent sur un serveur de rapports configuré pour l'intégration SharePoint. Les rapports consultables comprennent des fichiers de définition de rapport (.rdl) et des rapports Générateur de rapports. Les rapports s'ouvrent automatiquement dans le composant WebPart de visionneuse de rapports dans une nouvelle page, mais vous pouvez aussi ajouter un composant WebPart de visionneuse de rapports à une page ou un site Web existant ou si vous souhaitez qu'un rapport particulier soit toujours visible sur cette page.  
  
 Vous pouvez personnaliser le composant WebPart de visionneuse de rapports comme suit :  
  
-   modifiez l'aspect du composant WebPart en définissant des propriétés ;  
  
-   choisissez quelles fonctionnalités de création de rapport interactives sont disponibles sur la barre d'outils Rapports ;  
  
-   spécifiez quelles zones d'affichage sont disponibles ; Le composant WebPart de visionneuse de rapports possède une zone d'affichage de rapport, une zone de paramètres, et une zone d'informations d'identification.  
  
 Vous ne pouvez pas étendre le composant WebPart de visionneuse de rapports pour prendre en charge d'autres types de fichiers et vous ne pouvez pas remplacer la barre d'outils Rapports par une barre d'outils personnalisée ou ajouter de nouvelles fonctionnalités à la barre d'outils existante. Si vous devez personnaliser les fonctionnalités standard, créez un composant WebPart personnalisé.  
  
## <a name="setting-web-part-properties"></a>Définition des propriétés d'un composant WebPart  
 Un composant WebPart possède des propriétés personnalisées qui servent à configurer des fonctionnalités spécifiques. Un composant WebPart possède aussi des propriétés communes qui se retrouvent dans chaque composant.  
  
### <a name="change-default-properties"></a>Modifier les propriétés par défaut  
 Le composant WebPart de visionneuse de rapports possède des propriétés par défaut qui conviennent parfaitement à l'ouverture à la demande de rapports à partir d'un dossier ou d'une bibliothèque. Par défaut, tous les contrôles disponibles sont affichés dans la barre d'outils ; en outre, la hauteur et la largeur sont définies pour utiliser tout l'espace disponible sur la page Web. Si vous souhaitez modifier les propriétés par défaut, vous pouvez personnaliser le composant WebPart à l’aide des **paramètres du site**.  
  
1.  Dans le menu **Actions de site** , cliquez sur **Paramètres du site**.  
  
2.  Sous galeries, cliquez sur **composants WebPart**.  
  
3.  Cliquez sur **ReportViewer.dwp**.  
  
4.  Ouvrez le volet Outils et définissez les propriétés de votre choix.  
  
### <a name="customize-an-embedded-report-viewer-in-a-web-page"></a>Personnaliser une Visionneuse de rapports intégrée dans une page Web  
 Vous pouvez définir des propriétés pour intégrer la Visionneuse de rapports dans une page Web. La Visionneuse de rapports peut utiliser le même style et les couleurs que la page qui la contient. Vous pouvez masquer tout ou une partie de la barre d'outils, de l'explorateur de document et de la zone des paramètres pour maximiser la zone d'affichage des rapports dans l'espace alloué. Le rapport utilise toujours les styles qui lui sont attribués à sa création ; vous ne pouvez pas personnaliser l'aspect des rapports après leur publication dans une bibliothèque SharePoint.  
  
 Si vous incorporez le composant WebPart Visionneuse de rapports dans une page Web, vous devez définir la propriété **URL du rapport** sur un rapport spécifique. Dans le cas contraire, la Visionneuse de rapports affiche des instructions de liaison à un rapport. Vous ne pouvez pas personnaliser ou supprimer les instructions.  
  
### <a name="custom-properties-of-the-report-viewer-web-part"></a>Propriétés personnalisées du composant WebPart Visionneuse de rapports  
 Lorsque vous définissez des propriétés personnalisées, sachez que certaines propriétés ne sont utilisées que si le composant WebPart de visionneuse de rapports est incorporé à une page. Les exemples comprennent le titre, la hauteur, la largeur, le style de cadre et la zone. D'autres propriétés, de barre d'outils et de paramètres par exemple, sont utilisées indépendamment de l'affichage de la Visionneuse de rapports dans une page ou de l'ouverture d'un rapport en mode page entière.  
  
 Les propriétés personnalisées du composant WebPart Visionneuse de rapports sont listées ci-dessous.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Rapport|Chemin d'accès complet d'un rapport situé sur le site SharePoint actuel ou sur un site inclus dans la même batterie de serveurs ou application Web. Pour obtenir les résultats optimaux lors de la définition de propriétés supplémentaires, cliquez sur Appliquer après avoir spécifié l'URL du rapport.|  
|Cible du lien hypertexte|Code HTML standard qui spécifie le cadre cible permettant d'afficher le contenu lié au sein du document actuel. Pour les rapports qui comportent des liens hypertexte vers des sites Web externes, vous pouvez spécifier si un document cible doit s'ouvrir à la place du rapport existant dans la fenêtre active, ou s'il doit s'ouvrir dans une nouvelle fenêtre de navigateur. Les valeurs valides sont `_Top`, `_Blank` et `_Self`. `_Top` utilise la fenêtre active, `_Blank` charge le document dans une nouvelle fenêtre de navigateur et `_Self` ouvre le document dans le cadre actif. Bien que `_Parent` soit une valeur valide pour l'attribut Target en langage HTML, ne l'utilisez pas pour un composant WebPart Visionneuse de rapports incorporé dans une page.|  
|Générer automatiquement le titre du composant WebPart|Titre généré qui inclut le nom du composant WebPart Visionneuse de rapports et le nom du rapport, séparés par un tiret. Si le rapport n'a pas de titre, le nom du fichier de rapport est utilisé. Le titre est visible lorsque vous ajoutez un composant WebPart à une page. Si cette case à cocher est activée, le titre est généré chaque fois que la page est actualisée.|  
|Générer automatiquement le lien des détails du titre du composant WebPart|Lien hypertexte généré qui s'affiche au-dessus du composant WebPart. Vous pouvez cliquer sur le lien afin d'ouvrir le rapport dans une nouvelle page, en mode page entière.|  
|Afficher l'élément de menu Générateur de rapports|Affiche ou masque l’option de menu **Actions** pour ouvrir le Générateur de rapports.|  
|Afficher l'élément de menu Abonnement|Affiche ou masque l’option de menu **Actions** pour créer un abonnement pour le rapport.|  
|Afficher l'élément de menu Imprimer|Affiche ou masque l’option de menu **Actions** pour imprimer le rapport.|  
|Afficher l'élément de menu Exporter|Affiche ou masque l’option de menu **Actions** pour exporter le rapport.|  
|Afficher le bouton Actualiser|Affiche ou masque le bouton Actualiser sur la barre d'outils.|  
|Afficher les commandes de navigation entre les pages|Affiche ou masque les boutons de navigation dans les rapports sur la barre d'outils. Cette option modifie la visibilité de tous les contrôles de navigation.|  
|Afficher le bouton Précédente|Affiche ou masque le bouton Précédente sur la barre d'outils.|  
|Afficher les commandes de recherche|Affiche ou masque les commandes de recherche sur la barre d'outils. Les commandes de recherche autorisent un utilisateur à rechercher le texte dans le rapport rendu. Cette option modifie la visibilité de toutes les commandes de recherche.|  
|Afficher le contrôle de zoom|Affiche ou masque le contrôle de zoom sur la barre d'outils.|  
|Afficher le bouton Flux Atom|Affiche ou masque le bouton Flux Atom sur la barre d'outils.<br /><br /> ![htmlviewer_datafeed](media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|  
|Emplacement de la barre d'outils|Détermine l'emplacement de la barre d'outils dans la visionneuse de rapports. Les valeurs autorisées comprennent `Top` et `Bottom`.|  
|Zone de message|Les valeurs valides sont `Displayed`, `Collapsed` et `Hidden`. `Displayed` permet l'affichage de la zone Paramètres pour les rapports qui comportent des valeurs paramétrables et qui nécessitent une entrée utilisateur comme condition d'exécution. Utilisez `Hidden`, si tous les paramètres du rapport sont spécifiés et si vous ne souhaitez pas que la zone des paramètres soit visible par les utilisateurs.|  
|Largeur de la zone des paramètres|Vous pouvez choisir l'unité de mesure et la valeur. La valeur par défaut est 200 pixels. Cette propriété doit respecter une seule exigence, elle doit être supérieure à zéro.|  
|Explorateur de documents|Contrôle de navigation entre les rapports qui est défini dans le rapport et qui permet d'accéder en un seul clic à des sections spécifiques d'un rapport. Il est disponible dans les rapports HTML. L'Explorateur de documents s'affiche dans une zone réductible en regard de la zone d'affichage du rapport. Les valeurs valides sont `Displayed`, `Collapsed` et `Hidden`. Si un Explorateur de documents est défini pour un rapport, la zone est développée par défaut, à moins qu'elle ne soit cachée ou réduite via les propriétés du composant WebPart. Si l'Explorateur de documents est réduit, vous pouvez cliquer sur la flèche pour le développer.|  
|Largeur de la zone de l'explorateur de documents|Vous pouvez choisir l'unité de mesure et la valeur. La valeur par défaut est 200 pixels. Cette propriété doit respecter une seule exigence, elle doit être supérieure à zéro.|  
|Charger les paramètres|Récupérez les propriétés de paramètre pour le rapport. Tous les rapports n'ont pas des paramètres. Si le rapport n'a pas de paramètres, aucune valeur n'est retournée. Si vous définissez les propriétés d'un rapport que vous venez de télécharger, vous risquez de recevoir une erreur indiquant que la connexion à la source de données a été supprimée. Si cela se produit, réinitialisez la connexion, puis terminez la définition des propriétés des paramètres une fois la connexion spécifiée. Pour plus d’informations sur la définition de la connexion, consultez [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).<br /><br /> Pour obtenir des résultats optimaux, cliquez sur **Appliquer** avant de cliquer sur Charger les paramètres.<br /><br /> Une fois que vous avez chargé les propriétés des paramètres, vous pouvez les définir de la même façon que dans les pages de propriétés des paramètres du rapport. Pour plus d’informations sur la définition des paramètres, consultez [Définir les paramètres sur un rapport publié &#40;Reporting Services en mode intégré SharePoint&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).|  
  
## <a name="customizing-the-toolbar"></a>Personnalisation de la barre d'outils  
 La barre d'outils s'affiche sous le titre et s'étend sur toute la partie supérieure du rapport. La barre d’outils fournit un menu **Actions** , la navigation entre les pages pour les rapports paginés, l’actualisation et le zoom. Elle inclut un contrôle d'Explorateur de documents pour les rapports qui disposent d'un Explorateur de documents. Le menu **Actions** comprend des commandes permettant d’exporter un rapport, de rechercher du texte ou des nombres dans un rapport, d’imprimer un rapport et d’ouvrir le rapport dans le Générateur de rapports.  
  
 Vous ne pouvez pas ajouter de nouvelles commandes au menu  **Actions** mais vous pouvez le personnaliser en modifiant les options visibles aux utilisateurs. Pour modifier la visibilité des boutons et des contrôles de la barre d’outils, vous modifiez les options dans la section visibilité des éléments de la **barre d’outils** du composant WebPart. Vous pouvez également supprimer la commande **Imprimer** ou des formats d’exportation spécifiques en rendant ces fonctionnalités inaccessibles sur le serveur de rapports. Les contrôles de navigation entre les pages sont disponibles pour les rapports qui comportent des sauts de page ; à défaut, le rapport est constitué d'une seule page de longueur variable. La commande**Actualiser** permet de traiter à nouveau le rapport à l’aide des paramètres actuels du rapport. Pour afficher tous les contrôles sur une ligne, attribuez au moins une valeur de 400 pixels à la largeur globale du composant WebPart.  
  
## <a name="customizing-the-viewing-area"></a>Personnalisation de la zone d'affichage  
 Une zone d'affichage sert à afficher les rapports. La zone d'affichage du rapport est partagée avec les zones Paramètres et Informations d'identification, si celles-ci sont utilisées. Si des informations d'identification sont requises, la zone Informations d'identification s'affiche en regard d'une zone d'affichage du rapport vide. La zone Informations d'identification disparaît une fois que l'utilisateur fournit les informations d'identification et qu'il exécute le rapport. Pour personnaliser le texte invitant les utilisateurs à fournir des informations d’identification, modifiez les propriétés de connexion de la source de données. Pour plus d’informations, consultez [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
 La zone Paramètres fournit des champs permettant d'entrer des valeurs avant l'exécution du rapport. Elle n'est utilisée que lorsqu'une définition de rapport comprend des paramètres. Lorsque la zone Paramètres ou Informations d'identification est visible, l'affichage du rapport est ajusté en fonction de la largeur restante du composant WebPart. Vous pouvez définir les propriétés du composant WebPart afin de personnaliser la largeur de la zone Paramètres. Vous pouvez également définir les étiquettes qui s'affichent en regard des paramètres individuels sur la page. Pour plus d’informations sur la modification des étiquettes de paramètres, consultez [Définir les paramètres sur un rapport publié &#40;Reporting Services en mode intégré SharePoint&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composant WebPart Visionneuse de rapports sur un site SharePoint](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Ajouter le composant WebPart Visionneuse de rapports à une page web &#40;Reporting Services en mode intégré SharePoint&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  
