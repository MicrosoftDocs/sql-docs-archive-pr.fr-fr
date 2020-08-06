---
title: Démarrer ou arrêter un serveur PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41c38f8f96fcbc9175cf0f52dafd8b28a83e5497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605761"
---
# <a name="start-or-stop-a-powerpivot-for-sharepoint-server"></a>Démarrer ou arrêter un service PowerPivot pour un serveur SharePoint
  Service système PowerPivot et une [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance de fonctionnent ensemble sur le même serveur d’applications local pour prendre en charge le traitement des requêtes et des données coordonné dans une batterie de serveurs SharePoint.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Dépendances de service](#dependencies)  
  
 [Démarrer ou arrêter les services](#startstop)  
  
 [Conséquences de l'arrêt d'un serveur PowerPivot](#effects)  
  
##  <a name="service-dependencies"></a><a name="dependencies"></a>Dépendances de service  
 Le service système PowerPivot est dépendant de l'instance de serveur Analysis Services locale qui est installée avec le service PowerPivot sur le même serveur physique. Si vous arrêtez le service système PowerPivot, vous devez également arrêter manuellement l'instance de serveur Analysis Services locale. Si un service s'exécute sans l'autre, vous rencontrerez des erreurs d'allocation des requêtes pour le traitement des données PowerPivot.  
  
 Le serveur Analysis Services doit être exécuté seul uniquement si vous diagnostiquez ou résolvez un problème. Dans tous les autres cas, le serveur nécessite l'exécution locale du service système PowerPivot sur le même serveur.  
  
##  <a name="start-or-stop-the-services"></a><a name="startstop"></a>Démarrer ou arrêter les services  
 Utilisez toujours l'Administration centrale pour démarrer ou arrêter le service système PowerPivot ou l'instance du serveur Analysis Services. L'Administration centrale vous permet de démarrer ou d'arrêter les services de la même page ensemble. De plus, l'Administration centrale utilise un travail du minuteur appelé **Des services ont démarré ou se sont arrêtés** afin de redémarrer des services qui pour lui doivent s'exécuter. Si vous arrêtez le service système PowerPivot ou Analysis Services à l'aide d'un outil autre que SharePoint, les services seront redémarrés lors de l'exécution du travail du minuteur.  
  
 Le démarrage ou l'arrêt de services est une action qui s'applique à une instance de service physique. S'il existe d'autres serveurs PowerPivot pour SharePoint dans la batterie, les autres serveurs de la batterie continueront d'accepter les requêtes concernant des données PowerPivot.  
  
 Vous ne pouvez pas démarrer ou arrêter tous les services physiques simultanément dans la batterie de serveurs. Vous devez sélectionner chaque serveur, puis démarrer ou arrêter un service spécifique.  
  
 Vous ne pouvez pas démarrer, suspendre ou arrêter un service système PowerPivot pour une application Web spécifique, mais vous pouvez supprimer un service de la liste de connexions par défaut pour le rendre non disponible. Pour plus d’informations, consultez [connecter une application de service PowerPivot à une application Web SharePoint dans l’administration centrale](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
1.  Dans Administration centrale, sous **Paramètres système**, cliquez sur **Gérer les services sur le serveur**.  
  
2.  En haut de la page, sous Serveur, cliquez sur la flèche orientée vers le bas, puis sur **Changer de serveur**.  
  
3.  Sélectionnez le serveur SharePoint sur lequel est exécuté le service système PowerPivot ou l'instance du [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] que vous voulez démarrer ou arrêter.  
  
4.  Sélectionnez le service, puis cliquez sur l'action. N'oubliez pas de démarrer ou d'arrêter les services sous forme de paire. Si vous démarrez ou arrêtez le service système PowerPivot, pensez également à démarrer ou à arrêter l'instance de serveur Analysis Services qui s'exécute sur le même ordinateur.  
  
##  <a name="effects-of-stopping-a-powerpivot-server"></a><a name="effects"></a>Conséquences de l’arrêt d’un serveur PowerPivot  
 Le tableau suivant décrit les conséquences de l'arrêt du service système PowerPivot et du service Analysis Services sur un serveur SharePoint.  
  
|Éléments affectés|Description|  
|---------------|-----------------|  
|Requêtes existantes|Les requêtes en cours sur un serveur Analysis Services s'arrêtent immédiatement. L'utilisateur reçoit une erreur signalant des données introuvables ou une connexion à la source de données introuvable.|  
|Travaux d'actualisation des données en cours de traitement|Les travaux en cours sur le serveur Analysis Services actif s'arrêtent immédiatement. L'actualisation des données échoue et une erreur est journalisée dans l'historique d'actualisation des données.<br /><br /> Vous pouvez consulter l'état des travaux en cours avant d'arrêter le service en utilisant la page Vérifier l'état du travail dans l'Administration centrale de SharePoint.<br /><br /> Vous avez la possibilité de savoir quels sont les travaux en cours de traitement. En revanche, il est impossible d'afficher la file d'attente pour voir si d'autres travaux sont sur le point de démarrer.|  
|Demandes d'actualisation des données dans la file d'attente|Les demandes d'actualisation planifiée des données restent dans la file d'attente de traitement pendant l'intégralité d'un cycle de la planification (autrement dit, elles sont conservées dans la file d'attente jusqu'à l'heure de début de l'actualisation suivante). Si le service système PowerPivot n'est pas redémarré dans ce délai, la demande d'actualisation des données est supprimée et une erreur est journalisée.|  
|Nouvelles demandes pour des requêtes ou une actualisation des données|Si vous arrêtez le seul serveur PowerPivot pour SharePoint de la batterie, les nouvelles demandes de données PowerPivot ne sont pas traitées et une demande de données génère une erreur signalant que les données sont introuvables.<br /><br /> Si vous disposez d'autres serveurs PowerPivot pour SharePoint, la demande est transmise à l'un des serveurs disponibles.|  
|Données d'utilisation|Les données d'utilisation ne seront pas recueillies pendant la période d'arrêt des services.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des comptes de service PowerPivot](configure-power-pivot-service-accounts.md)  
  
  
