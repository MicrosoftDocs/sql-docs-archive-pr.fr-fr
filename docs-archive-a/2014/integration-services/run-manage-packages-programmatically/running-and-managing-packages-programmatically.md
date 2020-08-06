---
title: Exécution et gestion de packages par programmation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b07b0b98674fa17891dbbcb01ec42934c2a72e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698447"
---
# <a name="running-and-managing-packages-programmatically"></a>Exécution et gestion de packages par programme
  Si vous devez gérer et exécuter des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] hors de l'environnement de développement, vous pouvez manipuler les packages par programme. Cette méthode vous offre un choix d'options :  
  
-   Charger et exécuter un package existant sans modification.  
  
-   Charger un package existant, le reconfigurer (par exemple, spécifier une source de données différente) et l'exécuter.  
  
-   Créer un package, ajouter et configurer des composants objet par objet et propriété par propriété, l'enregistrer, puis l'exécuter.  
  
 Vous pouvez charger et exécuter un package existant à partir d'une application cliente en écrivant quelques lignes de code seulement.  
  
 Cette section décrit et explique comment exécuter un package existant par programme et comment accéder à la sortie du flux d'autres applications. Une option de programmation avancée vous permet de créer par programmation un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ligne par ligne, comme indiqué dans la rubrique [Génération de packages par programmation](../building-packages-programmatically/building-packages-programmatically.md).  
  
 Cette section présente également d'autres tâches d'administration que vous pouvez effectuer par programme pour gérer des packages stockés, des packages en cours d'exécution et des rôles de package.  
  
## <a name="running-packages-on-the-integration-services-server"></a>Exécution de packages sur le serveur Integration Services  
 Lorsque vous déployez des packages sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez exécuter les packages par programme à l'aide de l'espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices>. L'assembly Microsoft.SqlServer.Management.IntegrationServices est compilé avec le .NET Framework 3.5. Si vous générez une application .NET Framework 4.0, vous devrez peut-être ajouter la référence d'assembly directement dans votre fichier projet.  
  
 Vous pouvez également utiliser l'espace de noms pour déployer et gérer des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour obtenir une vue d'ensemble de l'espace de noms et des extraits de code, consultez l'entrée de blog, [Aperçu du modèle d'objet géré du catalogue SSIS](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), sur blogs.msdn.com.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation des différences entre l’exécution locale et l’exécution distante](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 Examine les différences essentielles entre l'exécution d'un package localement ou sur le serveur.  
  
 [Chargement et exécution d’un package local par programmation](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 Décrit comment exécuter un package existant à partir d'une application cliente sur l'ordinateur local.  
  
 [Chargement et exécution d’un package distant par programmation](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 Décrit comment exécuter un package existant à partir d'une application cliente et s'assurer que le package s'exécute sur le serveur.  
  
 [Chargement de la sortie d’un package local](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 Décrit comment exécuter un package sur l'ordinateur local et charger la sortie du flux de données dans une application cliente à l'aide de la destination DataReader et de l'espace de noms DtsClient.  
  
 [Énumération des packages disponibles par programmation](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 Décrit comment découvrir les packages disponibles gérés par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 [Gestion des packages et des dossiers par programmation](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 Décrit comment créer, renommer et supprimer des packages et des dossiers.  
  
 [Gestion des packages en cours d’exécution par programmation](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 Décrit comment répertorier les packages en cours d'exécution, examiner leurs propriétés et arrêter un package exécuté.  
  
 [Gestion par programmation des rôles de package &#40;Service SSIS&#41;](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 Explique comment obtenir ou définir des informations sur les rôles attribués à un package ou un dossier.  
  
## <a name="reference"></a>Informations de référence  
 [Guide de référence des erreurs et des messages propres à Integration Services](../integration-services-error-and-message-reference.md)  
 Répertorie les codes d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfinis avec leur nom symbolique et leur description.  
  
## <a name="related-sections"></a>Sections connexes  
 [Extension de packages avec des scripts](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Explique comment étendre le flux de contrôle à l'aide de la tâche de script, et comment étendre le flux de données à l'aide du composant Script.  
  
 [Extension de packages avec des objets personnalisés](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Explique comment créer des tâches personnalisées de programme, des composants de flux de données et d'autres objets de package à utiliser dans plusieurs packages.  
  
 [Génération de packages par programmation](../building-packages-programmatically/building-packages-programmatically.md)  
 Explique comment créer, configurer et enregistrer des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par programme.  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les téléchargements, articles, exemples et vidéos les plus récents de [!INCLUDE[msCoName](../../includes/msconame-md.md)], ainsi que les solutions retenues par la communauté informatique, consultez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
