---
title: Référence des paramètres de configuration (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3b57dd3f-7820-4ba8-b233-01dc68908273
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01a1c0d4c5273dccb6ba7057d1cd5c26a6f8890c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697272"
---
# <a name="configuration-setting-reference-powerpivot-for-sharepoint"></a>Référence de paramètre de configuration (PowerPivot pour SharePoint)
  Cette rubrique fournit une documentation de référence pour les paramètres de configuration utilisés par les applications de service PowerPivot dans une batterie de serveurs SharePoint. Si vous utilisez du script PowerShell pour configurer un serveur, ou si vous souhaitez rechercher des informations sur un paramètre spécifique, les informations de cette rubrique fournissent des descriptions détaillées.  
  
 Les paramètres de configuration sont définis pour chaque application de service PowerPivot. Dans une batterie de serveurs, vous pouvez créer plusieurs applications de service de façon à configurer des instances logiques indépendantes de la même instance de service physique. Les paramètres de configuration sont stockés dans la base de données d'application PowerPivot créée pour chaque application de service que vous configurez.  
  
 Si vous modifiez des paramètres de configuration, les modifications sont immédiatement relevées et utilisées pour les requêtes et connexions suivantes. Les opérations en cours sont régies par les paramètres en vigueur au début de l'opération.  
  
 Cliquez sur les liens suivants pour en savoir plus sur le domaine de configuration en question :  
  
 [Délai de chargement des données](#LoadingData)  
  
 [Pools de connexions](#ConnectionPool)  
  
 [Équilibrage de charge](#AllocationScheme)  
  
 [Actualisation des données](#DataRefresh)  
  
 [Collecte des données d’utilisation](#UsageData)  
  
 Pour obtenir des instructions sur la création d’une application de service PowerPivot, consultez [créer et configurer une application de service PowerPivot dans l’administration centrale](create-and-configure-power-pivot-service-application-in-ca.md).  
  
##  <a name="data-load-timeout"></a><a name="LoadingData"></a> Délai d'attente du chargement de données  
 Les données PowerPivot sont récupérées et chargées par les instances du serveur Analysis Services de la batterie. Selon le moment où le dernier accès aux données s'est produit et la façon dont il s'est produit, les données seront chargées à partir d'une bibliothèque de contenu ou d'un cache de fichiers local. Les données sont chargées en mémoire à chaque réception d'une requête ou d'une demande de traitement. Pour optimiser la disponibilité globale du serveur, vous pouvez définir une valeur de délai d'attente qui indique au serveur d'interrompre une demande de chargement de données si elle ne peut pas être exécutée dans le délai imparti.  
  
|Nom|Default|Valeurs valides|Description|  
|----------|-------------|------------------|-----------------|  
|Délai d'attente du chargement de données|1800 (en secondes)|1 à 3600|Spécifie la durée pendant laquelle une application de service PowerPivot attend une réponse d'une instance spécifique du serveur Analysis Services.<br /><br /> Par défaut, l'application de service attendra 30 minutes une charge utile de données en provenance de l'instance du service de moteur à laquelle elle a transféré une requête spécifique.<br /><br /> Si la source de données PowerPivot ne peut pas être chargée dans ce laps de temps, le thread sera arrêté et un nouveau sera démarré.|  
  
##  <a name="connection-pools"></a><a name="ConnectionPool"></a>Pools de connexions  
 L'application de service PowerPivot crée et gère des pools de connexions pour permettre la réutilisation de connexions. Il existe deux types de pools de connexions : un pour les connexions de données aux données en lecture seule et un pour les connexions au serveur.  
  
 Les pools de connexions de données contiennent des connexions mises en cache pour la source de données PowerPivot. Chaque pool de connexions est basé sur le contexte qui a été défini lorsque la base de données a été chargée. Ce contexte inclut l'identité de l'instance du service physique, l'ID de la base de données et l'identité de l'utilisateur SharePoint qui demande des données. Un pool de connexions distinct est créé pour chaque combinaison. Par exemple, les requêtes émanant de différents utilisateurs de la même base de données exécutée sur le même serveur consommeront des connexions de différents pools.  
  
 L'objectif d'un pool de connexions est d'utiliser des connexions mises en cache pour les requêtes en lecture seule émanant du même utilisateur SharePoint et concernant la même base de données Analysis Services. L'instance de service PowerPivot est le serveur où les données sont chargées en mémoire. L’ID de la base de données est un identificateur interne pour les structures de données en mémoire du modèle de données (un modèle est instancié sous forme de base de données de cube [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ). Les informations de version sont incorporées implicitement dans l'identificateur.  
  
 Les pools de connexions au serveur contiennent des connexions mises en cache d'une instance d'application de service PowerPivot à une instance du serveur Analysis Services, où l'application de service se connecte avec des autorisations Sysadmin [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur le serveur Analysis Services. Ces connexions sont utilisées pour émettre une requête de chargement de base de données et surveiller l'intégrité du système.  
  
 Chaque type de pool de connexions a des limites supérieures que vous pouvez configurer afin de garantir une utilisation optimale de la mémoire système pour la gestion des connexions.  
  
|Nom|Default|Valeurs valides|Description|  
|----------|-------------|------------------|-----------------|  
|Délai d'attente du pool de connexions|1800 (en secondes)|1 à 3 600.|Ce paramètre s'applique aux pools de connexions de données.<br /><br /> Il spécifie la durée pendant laquelle une connexion inactive peut rester dans un pool de connexions avant d'être supprimée.<br /><br /> Par défaut, l'application de service supprime une connexion si celle-ci est inactive depuis plus de cinq minutes.|  
|Taille maximale du pool de connexions utilisateur|1 000|-1, 0 ou 1 à 10000.<br /><br /> -1 spécifie un nombre illimité de connexions inactives.<br /><br /> 0 signifie qu'aucune connexion inactive n'est conservée. Les nouvelles connexions à une source de données PowerPivot doivent être créées à chaque fois.|Ce paramètre s'applique au nombre de connexions inactives dans tous les pools de connexions de données créés pour une instance spécifique d'application de service PowerPivot.<br /><br /> Les pools de connexions individuels sont créés pour les combinaisons uniques d'un utilisateur SharePoint, de données PowerPivot et d'une instance du service. Si vous avez de nombreux utilisateurs qui accèdent à diverses sources de données PowerPivot, une augmentation de la taille du pool de connexions peut améliorer les performances du serveur.<br /><br /> S'il existe plus de 100 connexions inactives à une instance de service PowerPivot, les connexions devenues inactives le plus récemment sont déconnectées au lieu de rejoindre le pool.|  
|Taille maximale du pool de connexions administrateur|200|-1, 0 ou 1 à 10000.<br /><br /> -1 spécifie un nombre illimité de connexions inactives.|Nombre maximal de connexions au serveur inactives dans tous les pools de connexions d'administration créés pour les connexions d'application de service PowerPivot à une instance du serveur Analysis Services. Les connexions au serveur sont utilisées pour les requêtes de chargement de base de données et de réenregistrement des modifications dans la base de données SharePoint.|  
  
##  <a name="load-balancing"></a><a name="AllocationScheme"></a>Équilibrage de charge  
 L'une des fonctions qu'assure le service PowerPivot consiste à déterminer où les données Analysis Services seront chargées parmi les instances du service PowerPivot disponibles. Le paramètre `AllocationMethod` spécifie les critères selon lesquels une instance du service est sélectionnée.  
  
|Nom|Default|Valeurs valides|Description|  
|----------|-------------|------------------|-----------------|  
|Méthode d'allocation|RoundRobin|Tourniquet (round robin)<br /><br /> Selon l'intégrité|Méthode d'allocation des requêtes de chargement parmi deux instances du serveur Analysis Services ou davantage.<br /><br /> Par défaut, le service PowerPivot alternera les demandes selon l'intégrité du serveur. La méthode selon l'intégrité alloue les requêtes au serveur où les ressources système disponibles sont les plus importantes, d'après la mémoire disponible et l'utilisation du processeur.<br /><br /> La méthode « tourniquet » (round robin) passe les demandes entre les serveurs disponibles dans un ordre séquentiel, indépendamment de la charge actuelle ou de l'intégrité du serveur.|  
  
##  <a name="data-refresh"></a><a name="DataRefresh"></a> Actualisation des données  
 Spécifiez la plage horaire qui définit la journée de travail normale ou classique dans votre organisation. Ces paramètres de configuration déterminent quand, après les heures d'ouverture, le traitement des données intervient pour les opérations d'actualisation des données. Le traitement après les heures d'ouverture peut commencer à l'heure où se termine la journée de travail. Le traitement après les heures d'ouverture est une option de planification pour les propriétaires de documents qui souhaitent actualiser une source de données PowerPivot avec les données transactionnelles qui ont été générées pendant les heures d'ouverture normales.  
  
|Nom|Default|Valeurs valides|Description|  
|----------|-------------|------------------|-----------------|  
|Heure de début|4h00|1 à 12 heures, où la valeur est un entier valide appartenant à cette plage.<br /><br /> Le type est Time.|Définit la limite inférieure d'une plage d'heures d'ouverture.|  
|Heure de fin|08:00 PM|1 à 12 heures, où la valeur est un entier valide appartenant à cette plage.<br /><br /> Le type est Time.|Définit la limite supérieure d'une plage d'heures d'ouverture.|  
|Compte d’actualisation des données PowerPivot sans assistance|None|ID d'une application cible|Ce compte est utilisé pour exécuter des travaux d'actualisation des données de la part d'un propriétaire de planification.<br /><br /> Le compte d'actualisation des données sans assistance doit être défini au préalable, avant de pouvoir être référencé dans la page de configuration d'application de service. Pour plus d’informations, consultez [configurer le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).|  
|Autoriser les utilisateurs à entrer des informations d'identification Windows personnalisées|activé|Boolean|Détermine si la page de configuration d'actualisation des données planifiée affiche une option qui permet à un propriétaire de planification de spécifier le compte d'utilisateur Windows et le mot de passe correspondant pour exécuter un travail d'actualisation des données.<br /><br /> Le service Banque d'informations sécurisé doit être activé pour que cette option fonctionne. Pour plus d’informations, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).|  
|Longueur maximale de l'historique de traitement|365|1 à 5000 jours|Détermine la durée de conservation de l'historique d'actualisation des données dans la base de données d'application de service PowerPivot. Pour plus d'informations, consultez [PowerPivot Usage Data Collection](power-pivot-usage-data-collection.md).|  
  
##  <a name="usage-data-collection"></a><a name="UsageData"></a>Collecte des données d’utilisation  
 Les rapports d'utilisation qui s'affichent dans le Tableau de bord de gestion PowerPivot peuvent fournir des informations importantes à propos de l'utilisation des classeurs compatibles PowerPivot. Les paramètres de configuration suivants contrôlent les aspects de la collecte des données d'utilisation pour les événements de serveur PowerPivot présentés par la suite dans des rapports d'utilisation ou d'activité.  
  
|Nom|Default|Valeurs valides|Description|  
|----------|-------------|------------------|-----------------|  
|Intervalle de consignation des requêtes|300 (en secondes)|1 à n secondes, où n est un entier valide.|Pour faire en sorte que cette collecte des données d'utilisation ne consomme pas une part trop importante de la capacité de transfert de données de la batterie de serveurs, les statistiques sur les requêtes sont collectées sur chaque connexion et consignées dans les rapports comme un événement unique. L'intervalle de consignation des requêtes détermine la fréquence à laquelle un événement est signalé. Par défaut, les statistiques de requêtes font l'objet d'un rapport toutes les 5 minutes.<br /><br /> Parce que les connexions sont fermées immédiatement après l'envoi d'une requête, le système génère un grand nombre de connexions, même pour un seul utilisateur accédant à une seule source de données PowerPivot. De ce fait, les pools de connexions sont créés pour chaque combinaison utilisateur/source de données PowerPivot afin qu'une connexion, une fois créée, puisse être réutilisée par le même utilisateur pour les mêmes données. Régulièrement, selon l'intervalle spécifié par le biais de ce paramètre de configuration, l'application de service PowerPivot crée un rapport des données d'utilisation de chaque connexion du pool.<br /><br /> Plus la valeur de cet intervalle est élevée, moins le nombre d'événements journalisés est important. Toutefois, si vous choisissez une valeur trop élevée, vous risquez de perdre les données d'événement en cas de redémarrage du serveur ou de fermeture d'une connexion.<br /><br /> Abaisser cette valeur entraîne la journalisation d'un plus grand nombre d'événements, à une fréquence plus élevée, ce qui se traduit par l'ajout de davantage de données d'utilisation relatives à PowerPivot au système de collecte de données de la base de données d'utilisation SharePoint.<br /><br /> Il est par conséquent généralement recommandé de ne pas modifier ce paramètre de configuration, hormis pour résoudre un problème spécifique (par exemple, si la base de données d'utilisation croît trop rapidement en raison des données d'utilisation PowerPivot).|  
|Historique des données d'utilisation|365 (en jours)|0 ou 1 à n jours, où n est un entier valide.<br /><br /> 0 signifie que l'historique est conservé indéfiniment, jamais supprimé.|Par défaut, les données d'utilisation sont conservées pendant un an dans la base de données d'application de service PowerPivot. Les enregistrements datant de plus d'un an sont supprimés de la base de données.<br /><br /> Un contrôle des données d'historique ayant expiré est effectué quotidiennement, lors de l'exécution du travail Traitement des données d'utilisation de Microsoft SharePoint Foundation. Le travail du minuteur lit ce paramètre et déclenche une commande de suppression des données de l'historique expiré dans la base de données d'application de service PowerPivot.|  
|Limite supérieure de réponse triviale|500 (en millisecondes)|1 à n millisecondes, où n est un entier valide.|Par défaut, le seuil fixé pour les demandes triviales est d'une demi-seconde.<br /><br /> Les demandes triviales sont par exemple les tests Ping sur le serveur, les demandes qui concernent les métadonnées et les démarrages de sessions.|  
|Limite supérieure de réponse rapide|1000 (en millisecondes)|1 à n millisecondes, où n est un entier valide.|Par défaut, le seuil fixé pour les demandes rapides est d'une seconde.<br /><br /> Les demandes rapides sont celles qui ont un très petit dataset ou qui concernent des métadonnées couvrant de grands jeux de membres.|  
|Limite supérieure de réponse attendue|3000 (en millisecondes)|1 à n millisecondes, où n est un entier valide.|Par défaut, le seuil fixé pour les demandes attendues est de trois secondes.<br /><br /> Ce seuil définit la limite supérieure d'une durée de requête attendue.|  
|Limite supérieure de réponse longue|10 000 (en millisecondes)|1 à n millisecondes, où n est un entier valide.|Par défaut, le seuil fixé pour les demandes longues est de dix secondes.<br /><br /> Ces demandes sont celles dont l'exécution dure plus longtemps que prévu, tout en restant dans une plage acceptable.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et configurer une application de service PowerPivot dans l’administration centrale](create-and-configure-power-pivot-service-application-in-ca.md)   
 [Actualisation des données PowerPivot avec SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [Configurer des comptes de service PowerPivot](configure-power-pivot-service-accounts.md)   
 [Tableau de bord de gestion PowerPivot et données d’utilisation](power-pivot-management-dashboard-and-usage-data.md)  
  
  
