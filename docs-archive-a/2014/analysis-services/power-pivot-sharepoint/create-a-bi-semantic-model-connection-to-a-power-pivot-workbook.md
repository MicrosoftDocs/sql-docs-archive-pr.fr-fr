---
title: Créer une connexion de modèle sémantique BI à un classeur PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612533"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a>Créer une connexion de modèle sémantique BI à un classeur PowerPivot
  Utilisez les informations de cette rubrique pour configurer une connexion de modèle sémantique BI qui redirige vers un classeur PowerPivot dans la même batterie.  
  
 Après avoir créé une connexion de modèle sémantique BI et configuré les autorisations SharePoint, vous pouvez l'utiliser comme source de données pour les rapports Excel ou [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
 Cette rubrique comprend les sections suivantes. Effectuez chaque tâche dans l'ordre indiqué.  
  
 [Examiner la configuration requise](#bkmk_prereq)  
  
 [Créer une connexion](#bkmk_create)  
  
 [Configurer des autorisations SharePoint sur la connexion de modèle sémantique BI](#bkmk_permissions)  
  
 [Configurer les autorisations SharePoint sur le classeur](#bkmk_userdb)  
  
 [Next Steps](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a>Vérifier les conditions préalables  
 Vous devez disposer d'autorisations Collaboration ou supérieures pour créer un fichier de connexion de modèle sémantique BI.  
  
 Vous devez disposer d'une bibliothèque qui prend en charge le type de contenu Connexion de modèle sémantique BI. Pour plus d’informations, consultez [Ajouter un type de contenu de connexion de modèle sémantique bi à une bibliothèque &#40;PowerPivot pour SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).  
  
 Vous devez connaître l’URL du classeur PowerPivot pour lequel vous configurez une connexion de modèle sémantique BI (par exemple, http://adventure-works/shared documents/myworkbook.xlsx). Le classeur doit figurer dans la même batterie de serveurs.  
  
 Tous les ordinateurs et utilisateurs qui participent à la séquence de connexion doivent être dans le même domaine ou dans un domaine approuvé (approbation bidirectionnelle).  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a>Créer une connexion  
  
1.  Dans la bibliothèque qui contiendra la connexion de modèle sémantique BI, cliquez sur **Documents** sur le ruban SharePoint. Cliquez sur la flèche de déroulement de Nouveau document, puis sélectionnez **Fichier de connexion BISM** pour ouvrir la page Nouvelle connexion de modèle sémantique BI.  
  
     ![Sous-menu Nouveau document dans une bibliothèque SharePoint](../media/ssas-bismconnection-new.gif "Sous-menu Nouveau document dans une bibliothèque SharePoint")  
  
2.  Définissez la propriété de **serveur** sur l’URL SharePoint du classeur PowerPivot (par exemple, ** http://mysharepoint/shared documents/myWorkbook.xlsx**. Dans un déploiement PowerPivot pour SharePoint, les données peuvent être chargées sur tout serveur de la batterie. Pour cette raison, les connexions de la source de données aux données PowerPivot spécifient juste le chemin d'accès au classeur. Le service système PowerPivot détermine quel serveur charge les données.  
  
     N’utilisez pas la propriété **de base de données** ; elle n’est pas utilisée lors de la spécification de l’emplacement d’un classeur PowerPivot.  
  
     Votre page doit ressembler à l'illustration suivante.  
  
     ![Page de connexion BISM affichant l'URL du classeur](../media/ssas-bismconnection-ppvtds.gif "Page de connexion BISM affichant l'URL du classeur")  
  
     Éventuellement, si vous disposez d'autorisations SharePoint sur le classeur, une étape supplémentaire de validation est effectuée pour s'assurer que l'emplacement est valide. Si vous n'êtes pas autorisé à accéder aux données, vous avez la possibilité d'enregistrer la connexion de modèle sémantique BI sans la réponse de validation.  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a>Configurer des autorisations SharePoint sur la connexion de modèle sémantique BI  
 La possibilité d'utiliser une connexion de modèle sémantique BI comme source de données pour un classeur Excel ou un rapport Reporting Services requiert des autorisations de **Lecture** sur l'élément de connexion de modèle sémantique BI dans une bibliothèque SharePoint. Le niveau d'autorisation Lecture inclut l'autorisation **Ouvrir les éléments** qui permet le téléchargement des informations de connexion de modèle sémantique BI vers une application bureautique Excel.  
  
 Il existe plusieurs manières d'accorder des autorisations dans SharePoint. L’instruction suivante explique comment créer un groupe appelé **Utilisateurs BISM** qui dispose du niveau d’autorisation **Read** .  
  
 Vous devez être le propriétaire du site pour modifier des autorisations.  
  
1.  Dans Actions du site, cliquez sur **Autorisations de site**.  
  
2.  Cliquez sur **Créer un groupe** et nommez le nouveau groupe **Utilisateurs BISM**.  
  
3.  Choisissez le niveau d'autorisation **Lecture** et cliquez sur **Créer**.  
  
4.  Sélectionnez **Utilisateurs BISM** dans Personnes et groupes.  
  
5.  Pointez sur Nouveau, cliquez sur **Ajouter des utilisateurs**, puis ajoutez des comptes d'utilisateur ou de groupe.  
  
     Ces utilisateurs et groupes bénéficient maintenant d'autorisations de lecture sur l'ensemble du site, notamment les bibliothèques et listes qui héritent des autorisations au niveau du site. Si ces autorisations sont trop élevées, vous pouvez sélectivement supprimer ce groupe de bibliothèques, de listes ou d'éléments spécifiques.  
  
 Pour supprimer sélectivement des autorisations au niveau de l'élément, procédez comme suit :  
  
1.  Dans une bibliothèque, sélectionnez un document. Cliquez sur la flèche vers le bas, puis sur **Gérer les autorisations**.  
  
2.  Par défaut, un élément hérite des autorisations. Pour modifier les autorisations de documents individuels dans cette bibliothèque, cliquez sur **Arrêter l’héritage des autorisations**.  
  
3.  Cochez la case en regard d’ **Utilisateurs BISM**.  
  
4.  Cliquez sur **Supprimer les autorisations des utilisateurs**.  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a>Configurer des autorisations SharePoint sur le classeur  
 Si vous utilisez une base de données PowerPivot dans un classeur Excel, les autorisations SharePoint sur le classeur Excel déterminent l'accès aux données par l'intermédiaire de la connexion de modèle sémantique BI. Tous les utilisateurs qui accèdent au classeur doivent disposer d'autorisations de lecture sur le classeur pour pouvoir l'utiliser comme source de données externe.  
  
 Si vous avez créé un groupe **Utilisateurs BISM** à l’aide des instructions de la section précédente, les comptes d’utilisateur et de groupe qui sont membres d’ **Utilisateurs BISM** disposent des autorisations requises sur le classeur ainsi que sur le fichier de connexion du modèle sémantique BI, en supposant que le classeur utilise des autorisations héritées.  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> Étapes suivantes  
 Après avoir créé et sécurisé une connexion de modèle sémantique BI, vous pouvez la spécifier en tant que source de données. Pour plus d’informations, consultez [Utiliser une connexion de modèle sémantique BI dans Excel ou Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion de modèle sémantique BI PowerPivot &#40;. BISM&#41;](power-pivot-bi-semantic-model-connection-bism.md)   
 [Utiliser une connexion de modèle sémantique BI dans Excel ou Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)   
 [Créer une connexion de modèle sémantique BI à une base de données model tabulaire](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
