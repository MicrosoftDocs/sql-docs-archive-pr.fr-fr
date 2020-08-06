---
title: Accorder à un utilisateur l’accès à un serveur de rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697444"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a>Accorder à un utilisateur l'accès à un serveur de rapports (Gestionnaire de rapports)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise la sécurité basée sur les rôles pour permettre à un utilisateur d’accéder à un serveur de rapports. Dans une nouvelle installation du serveur de rapports, seuls les utilisateurs membres du groupe Administrateurs local disposent d'autorisations relatives au contenu et au fonctionnement du serveur de rapports. Pour rendre le serveur de rapports accessible à d’autres utilisateurs, vous devez créer des attributions de rôles qui mappent des comptes d’utilisateurs ou de groupes à un rôle prédéfini spécifiant une collection de tâches.  
  
 **Serveurs de rapports en mode SharePoint :** pour un serveur de rapports configuré en mode intégré SharePoint, vous configurez l’accès à partir d’un site SharePoint à l’aide d’autorisations SharePoint. Les niveaux d'autorisation du site SharePoint déterminent l'accès au contenu du serveur de rapports et son bon fonctionnement. Vous devez être un administrateur de site pour pouvoir accorder des autorisations sur un site SharePoint. Pour plus d’informations, consultez [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
 **Serveurs de rapports en mode natif :** cette rubrique traite d’un serveur de rapports configuré pour le mode natif et de l’utilisation du Gestionnaire de rapports pour affecter des utilisateurs à un rôle. Il existe deux types de rôles :  
  
-   Les rôles au niveau élément permettent d'afficher, d'ajouter et de gérer le contenu du serveur de rapports, les abonnements, le traitement des rapports et l'historique de rapport. Les attributions de rôles au niveau élément sont définies sur le nœud racine (dossier de base) mais aussi sur des dossiers ou des éléments spécifiques situés plus bas dans l'arborescence.  
  
-   Les rôles de niveau système accordent l'accès aux opérations à l'échelle du site qui ne sont pas liées à un élément spécifique. Cela inclut par exemple l'utilisation du Générateur de rapports et des planifications partagées.  
  
     Les deux types de rôles sont complémentaires et doivent être utilisés ensemble. Par conséquent, l'ajout d'un utilisateur à un serveur de rapports est une opération en deux parties. Si vous attribuez un rôle au niveau élément à un utilisateur, vous devez également lui attribuer un rôle de niveau système. Lorsque vous attribuez un rôle à un utilisateur, vous devez sélectionner un rôle déjà défini. Pour créer, modifier ou supprimer des rôles, utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).  
  
## <a name="before-you-start"></a>Avant de commencer  
 Examinez la liste suivante avant d'ajouter des utilisateurs à un serveur de rapports en mode natif.  
  
-   Vous devez être membre du groupe Administrateurs local sur le serveur de rapports. Si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ou Windows Server 2008, vous devez effectuer une configuration supplémentaire pour pouvoir administrer un serveur de rapports localement. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
-   Pour déléguer cette tâche à d'autres utilisateurs, créez des attributions de rôles qui mappent des comptes d'utilisateurs aux rôles Gestionnaire de contenu et Administrateur système. Les utilisateurs qui disposent d'autorisations liées aux rôles Gestionnaire de contenu et Administrateur système peuvent ajouter des utilisateurs à un serveur de rapports.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], passez en revue les rôles prédéfinis pour les rôles système et les rôles d’utilisateurs pour vous familiariser avec les types de tâches de chaque rôle. Les descriptions des tâches ne sont pas visibles dans le Gestionnaire de rapports ; par conséquent, familiarisez-vous avec les rôles avant de commencer à ajouter des utilisateurs.  
  
-   Vous pouvez éventuellement personnaliser les rôles ou définir des rôles supplémentaires pour inclure la collection de tâches dont vous avez besoin. Par exemple, si vous envisagez d'utiliser des paramètres de sécurité personnalisés pour des éléments individuels, vous pouvez créer une définition de rôle qui permet d'afficher les dossiers.  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a>Pour ajouter un utilisateur ou un groupe à un rôle système  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Cliquez sur **Sécurité**.  
  
4.  Cliquez sur **Nouvelle attribution de rôle**.  
  
5.  Dans **nom d’utilisateur ou de groupe**, entrez un compte d’utilisateur ou de groupe de domaine Windows au format suivant : \<domain> \\<compte \> . Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.  
  
6.  Sélectionnez un rôle système, puis cliquez sur **OK**.  
  
     Les rôles sont cumulatifs ; par conséquent, si vous sélectionnez à la fois le rôle Administrateur système et le rôle Utilisateur système, un utilisateur ou un groupe pourra effectuer les tâches incluses dans les deux rôles.  
  
7.  Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a>Pour ajouter un utilisateur ou un groupe à un rôle au niveau élément  
  
1.  Démarrez le **Gestionnaire de rapports** , puis recherchez l’élément de rapport pour lequel vous souhaitez ajouter un utilisateur ou un groupe.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Sécurité**.  
  
4.  Cliquez sur **Nouvelle attribution de rôle**.  
  
    > [!NOTE]  
    >  Si un élément hérite actuellement de la sécurité de l’un de ses parents, cliquez sur **Modifier la sécurité de l’élément** dans la barre d’outils pour changer les paramètres de sécurité. Puis cliquez sur **Nouvelle attribution de rôle**.  
  
5.  Dans **nom d’utilisateur ou de groupe**, entrez un compte d’utilisateur ou de groupe de domaine Windows au format suivant : \<domain> \\<compte \> . Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.  
  
6.  Sélectionnez une ou plusieurs définitions de rôles décrivant la façon dont l’utilisateur ou le groupe doit accéder à l’élément, puis cliquez sur **OK**.  
  
7.  Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 (create-and-manage-role-assignments.md)   
 [Page nouvelle attribution de rôle : modifier l’attribution de rôle &#40;Gestionnaire de rapports&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md)   
 [Page Propriétés de sécurité, éléments &#40;Gestionnaire de rapports&#41;](../security-properties-page-items-report-manager.md)   
 [Attributions de rôles](role-assignments.md)   
 [Définitions de rôles](role-definitions.md)  
  
  
