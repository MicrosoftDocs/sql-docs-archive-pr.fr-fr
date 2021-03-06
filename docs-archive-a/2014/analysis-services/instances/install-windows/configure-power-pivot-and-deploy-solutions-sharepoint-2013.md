---
title: Configurer PowerPivot et déployer des solutions (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697320"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a>Configurer PowerPivot et déployer des solutions (SharePoint 2013)
  Cette rubrique décrit le déploiement et la configuration des améliorations de niveau intermédiaire apportées aux fonctionnalités de PowerPivot dans [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] , dont la Galerie PowerPivot, l'actualisation planifiée des données, le tableau de bord de gestion et les fournisseurs de données. Exécutez l'outil **Configuration de PowerPivot pour SharePoint 2013** pour effectuer les opérations suivantes :  
  
-   Déployer les fichiers de solution SharePoint.  
  
-   Créer une application de service PowerPivot.  
  
-   Configurer une application Excel Services pour utiliser un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Pour plus d’informations sur les services principaux et l’installation [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] d’un serveur en mode SharePoint, consultez [PowerPivot pour SharePoint l’installation de 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
 Pour plus d’informations sur l’installation de l’outil de configuration PowerPivot pour SharePoint 2013, consultez [installer ou désinstaller le complément PowerPivot pour SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
 Cette rubrique contient les sections suivantes :  
  
 [Exécuter l'outil de configuration de PowerPivot pour SharePoint 2013](#bkmk_run_configuration_tool)  
  
 [Vérifier la configuration PowerPivot](#bkmk_verify_powerpivot)  
  
 [Résoudre les problèmes](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a>Exécuter PowerPivot pour SharePoint Configuration 2013  
 **Remarque :** l'Assistant Installation de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] installe deux outils de configuration différents pour [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]. Chacun d'eux prend en charge une version différente de SharePoint.  
  
|Nom|Description|  
|----------|-----------------|  
|Configuration de PowerPivot pour SharePoint 2013|SharePoint 2013|  
|Outil de configuration de PowerPivot|SharePoint 2010 avec SharePoint 2010 Service Pack 1 (SP1)|  
  
 **Remarque :** pour effectuer les étapes suivantes, vous devez être administrateur de batterie de serveurs. Si un message d'erreur semblable au suivant s'affiche :  
  
-   «L’utilisateur n’est pas un administrateur de batterie de serveurs. Traitez les échecs de validation et réessayez. »  
  
 Connectez-vous avec le compte qui a installé SharePoint ou configurez le compte d'installation en tant qu'administrateur principal du site Administration centrale de SharePoint.  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, puis sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Configuration PowerPivot pour SharePoint 2013**. L'outil est répertorié uniquement lorsque PowerPivot pour SharePoint est installé sur le serveur local.  
  
2.  Cliquez sur **Configurer ou réparer PowerPivot pour SharePoint** , puis cliquez sur **OK**.  
  
3.  L'outil exécute la validation pour vérifier l'état actuel de PowerPivot et les étapes nécessaires pour terminer la configuration. Affichez la fenêtre en plein écran. Vous devez voir une barre d'icônes en bas de la fenêtre qui comprend les commandes **Valider**, **Exécuter**et **Quitter** .  
  
4.  Dans l'onglet **Paramètres** :  
  
    1.  **Nom d'utilisateur de compte par défaut**: entrez un compte d'utilisateur de domaine pour le compte par défaut. Ce compte sera utilisé pour configurer des services, notamment le pool d'applications de service PowerPivot. Ne spécifiez pas un compte intégré tel que Service réseau ou Système local. L'outil bloque les configurations qui spécifient des comptes intégrés.  
  
    2.  **Serveur de base de données**: vous pouvez utiliser le moteur de base de données SQL Server pris en charge pour la batterie de serveurs SharePoint.  
  
    3.  **Phrase secrète**: entrez une phrase secrète. Si vous créez une batterie de serveurs SharePoint, la phrase secrète est utilisée chaque fois que vous ajoutez un serveur ou une application à la batterie de serveurs SharePoint. Si la batterie existe déjà, entrez la phrase secrète qui vous permet d'ajouter une application de serveur à la batterie.  
  
    4.  **Serveur PowerPivot pour Excel Services**: entrez le nom d'un serveur en mode SharePoint pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Dans un déploiement sur un seul serveur, il est identique à celui du serveur de base de données. `[ServerName]\powerpivot`  
  
    5.  Cliquez sur **Créer une collection de sites** dans la fenêtre de gauche. Notez l' **URL du site** afin de pouvoir y faire référence dans les étapes ultérieures. Si le serveur SharePoint n'est pas déjà configuré, l'Assistant de configuration définit par défaut l'application Web et les URL de collection de sites sur la racine de `http://[ServerName]`. Pour modifier les valeurs par défaut, examinez les pages suivantes dans la fenêtre de gauche : **Créer une application Web par défaut** et **Déployer une solution d'application Web**.  
  
5.  Éventuellement, examinez les valeurs d'entrée restantes utilisées pour effectuer chaque action. Cliquez sur chaque action dans la fenêtre à gauche pour afficher et passer en revue les détails de l'action. Pour plus d’informations sur chacune d’elles, consultez la section «valeurs d’entrée utilisées pour configurer le serveur dans [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) dans cette rubrique.  
  
6.  Éventuellement, supprimez toutes les actions que vous ne souhaitez pas traiter à ce stade. Par exemple, si vous souhaitez configurer le service Banque d'informations sécurisé ultérieurement, cliquez sur **Configurer le service Banque d'informations sécurisé**, puis désactivez la case à cocher **Inclure cette action dans la liste des tâches**.  
  
7.  Cliquez sur **Valider** pour vérifier que l'outil dispose d'informations suffisantes pour traiter les actions de la liste. Si des erreurs de validation s'affichent, cliquez sur les avertissements dans le volet gauche pour afficher les détails de l'erreur de validation. Corrigez toutes les erreurs de validation, puis cliquez de nouveau sur **Valider** .  
  
8.  Cliquez sur **Exécuter** pour traiter toutes les actions de la liste des tâches. Notez qu' **Exécuter** devient disponible lorsque vous avez validé les actions. Si **Exécuter** n'est pas activé, commencez par cliquer sur **Valider** .  
  
 Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a>Vérifier la configuration PowerPivot  
 **Services :**  
  
1.  Dans l’administration centrale, sous paramètres système, cliquez sur **gérer les services sur le serveur**.  
  
2.  Vérifiez que **SQL Server Analysis Services** et le **service système SQL Server PowerPivot** sont démarrés.  
  
 **Fonctionnalités de la batterie de serveurs :**  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les fonctionnalités des batteries de serveurs**.  
  
2.  Vérifiez que l'option **Fonctionnalité d'intégration PowerPivot** a la valeur **Activée**.  
  
 **Fonctionnalités de la collection de sites :**  
  
1.  Accédez à l'URL du site créé par l'outil de configuration.  
  
     Cliquez sur **paramètres**paramètres![SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Paramètres SharePoint"), puis sur **paramètres du site**.  
  
     Cliquez sur **Fonctionnalités de la collection de sites**.  
  
2.  Vérifiez que **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est **Activée**.  
  
 **Application de service PowerPivot :**  
  
1.  Dans l'Administration centrale, sous **Gestion des applications**, cliquez sur **Gérer les applications de service**.  
  
2.  Vérifiez que l'état de l'application de service est **Démarré**. Le nom par défaut est **application de service PowerPivot par défaut**.  
  
     Cliquez sur le nom de l'application de service pour ouvrir le Tableau de bord de gestion PowerPivot pour cette application de service. À la première utilisation, le tableau de bord prend plusieurs minutes à charger.  
  
 Pour plus d’informations, consultez [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a>Résoudre les problèmes  
 Pour aider les problèmes de dépannage, il peut être judicieux de vérifier que la journalisation du diagnostic est activée.  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Analyse** , puis sur **Configurer la collecte des données d'utilisation et d'intégrité**.  
  
2.  Vérifiez que l'option **Activer la collecte des données d'utilisation** est sélectionnée.  
  
3.  Vérifiez que les événements suivants sont sélectionnés :  
  
    -   Définition des champs d'utilisation de la télémesure d'éducation  
  
    -   Connexions PowerPivot  
  
    -   Utilisation des données de chargement PowerPivot  
  
    -   Utilisation des requêtes PowerPivot  
  
    -   Utilisation des données de déchargement PowerPivot  
  
4.  Vérifiez que l'option **Activer la collecte des données d'intégrité** est sélectionnée.  
  
5.  Cliquez sur **OK**.  
  
 Pour plus d’informations sur le dépannage de l’actualisation des données, consultez [résolution des problèmes d’actualisation des données PowerPivot](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) ( https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) .  
  
 Pour plus d'informations sur l'outil de configuration, consultez [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
  
