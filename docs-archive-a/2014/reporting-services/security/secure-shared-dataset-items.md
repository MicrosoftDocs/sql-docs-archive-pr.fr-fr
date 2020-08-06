---
title: Sécuriser les éléments de dataset partagé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 08e6d8b5-d88c-4ed2-9c05-55c757e00014
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 559faa14851f9def4ebe480a4fae9335825480d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610423"
---
# <a name="secure-shared-dataset-items"></a>Sécuriser les éléments de dataset partagés
  Sur un serveur de rapports, les éléments de dataset partagés peuvent être utilisés par plusieurs rapports. Vous pouvez sécuriser des datasets partagés pour contrôler le degré d'accès dont disposent les utilisateurs. Par défaut, seuls les utilisateurs qui sont membres du groupe prédéfini **Administrateurs** peuvent consulter des datasets partagés, modifier des propriétés, activer la mise en cache, créer des plans d’actualisation du cache et supprimer les éléments. Tous les autres utilisateurs possèdent des attributions de rôles créées pour eux qui autorisent l'accès à un dataset partagé.  
  
 Pour définir la sécurité, vous créez une attribution de rôle qui spécifie quel compte d'utilisateur ou de groupe dispose de l'accès au dataset partagé.  
  
## <a name="role-based-access-to-shared-datasets"></a>Accès aux datasets partagés basé sur rôle  
 Pour accorder l'accès datasets partagés, vous pouvez autoriser les utilisateurs à hériter des attributions de rôles existantes d'un dossier parent ou à créer une nouvelle attribution de rôle sur l'élément proprement dit.  
  
 Les attributions de rôle par défaut qui vous permettent d'ajouter, de supprimer, de modifier les propriétés de l'élément, et d'afficher les rapports associés ainsi que les sources de données partagées pour les datasets partagés sont Gestionnaire de Contenu, Mes Rapports et Serveur de publication. Pour modifier une définition de dataset partagé, utilisez les attributions de rôle par défaut Générateur de rapports ou Gestionnaire de Contenu.  
  
 Étant donné que les attributions de rôle sont héritées en général d'un nœud parent, un dossier dont la tâche **Afficher les rapports** est activée transmet cette autorisation aux datasets partagés et aux rapports du dossier.  
  
 Pour fournir davantage de contrôle sur les datasets partagés et leurs résultats de requête, configurez la sécurité au niveau de l'élément sur l'élément de dataset partagé ou enregistrez les datasets partagés dans un dossier et configurez la sécurité au niveau de l'élément sur le dossier.  
  
## <a name="shared-dataset-parameters"></a>Paramètres de dataset partagé  
 Les paramètres de dataset partagés ne peuvent pas être utilisés pour restreindre des données pour les utilisateurs spécifiques. L'objectif des paramètres de dataset partagés est d'offrir un moyen pour spécifier les données à inclure lorsque le dataset partagé est traité. Sur le serveur de rapports, vous ne pouvez pas sécuriser les valeurs pour un paramètre de dataset partagé.  
  
 Dans la définition de dataset partagée, vous pouvez marquer des paramètres comme étant en lecture seule et spécifier des valeurs par défaut. Les paramètres marqués comme étant en lecture seule ne peuvent pas être remplacés sur le serveur. Par exemple, dans un plan d'actualisation de cache pour un dataset partagé, vous ne pouvez pas spécifier de valeurs pour les paramètres en lecture seule. Si les paramètres de dataset partagé incluent des expressions qui font référence à la collection globale Utilisateur, ou qui ont d'autres dépendances d'utilisateur, vous ne pouvez pas créer de plan d'actualisation du cache pour le dataset partagé.  
  
## <a name="tasks-access-to-items-and-default-roles"></a>Tâches, accès aux éléments et rôles par défaut  
 Les datasets partagés suivent le même modèle de sécurité que les rapports. Pour fournir à un utilisateur l'autorisation pour des actions spécifiques, choisissez un rôle qui inclut la tâche correspondante qui inclut ces autorisations. Le tableau suivant répertorie les tâches et les actions incluses.  
  
|Sélectionnez cette tâche|Pour autoriser les utilisateurs à effectuer les opérations suivantes|Rôles par défaut qui incluent la tâche|  
|----------------------|---------------------------------|-----------------------------------------|  
|Afficher les rapports|Afficher les éléments de dataset dans l'arborescence des dossiers. Sans cette tâche, l'élément n'est pas visible pour les utilisateurs et ils peuvent ignorer que le dataset est disponible.|Browser<br /><br /> Gestionnaire de contenu<br /><br /> Générateur de rapports<br /><br /> Mes rapports|  
|Gérer les rapports|Afficher les propriétés qui spécifient le nom, la description et les informations de connexion. Cette tâche est également utilisée pour afficher un élément de sdataset partagé dans la hiérarchie de dossiers. Si vous choisissez cette tâche, vous pouvez omettre la tâche « Afficher les rapports ».|Gestionnaire de contenu<br /><br /> Serveur de publication<br /><br /> Mes rapports|  
|Lire les rapports|Consulter la définition de dataset partagé.|Gestionnaire de contenu<br /><br /> Générateur de rapports|  
|Définir la sécurité au niveau des éléments|Créer et modifier des attributions de rôles qui contrôlent l'accès au dataset partagé. Cette tâche doit être utilisée avec les tâches « Afficher les rapports » ou « Gérer les rapports ». Si tel n'est pas le cas, elle est sans effet puisque l'utilisateur ne peut pas sélectionner l'élément.|Gestionnaire de contenu|  
  
 Pour plus d’informations, consultez [Tâches au niveau élément](tasks-and-permissions-item-level-tasks.md) et [Rôles prédéfinis](role-definitions-predefined-roles.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des datasets partagés](../report-data/manage-shared-datasets.md)   
 [Dossiers sécurisés](secure-folders.md)   
 [Sécuriser des rapports et des ressources](secure-reports-and-resources.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](granting-permissions-on-a-native-mode-report-server.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](granting-permissions-on-a-native-mode-report-server.md)  
  
  
