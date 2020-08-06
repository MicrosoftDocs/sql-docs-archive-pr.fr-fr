---
title: Éditeur de tâche d’exécution de package | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610748"
---
# <a name="execute-package-task-editor"></a>Éditeur de tâche d'exécution de package
  Utilisez l'Éditeur de tâche d'exécution de package pour configurer la tâche d'exécution de package. La tâche d'exécution de package étend les fonctionnalités d'entreprise de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en permettant à des packages d'exécuter d'autres packages au sein d'un flux de travail.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l'Éditeur de tâche d'exécution de package](#open)  
  
-   [Définir les options sur la page Général](#general)  
  
-   [Définir les options sur la page Package](#package)  
  
-   [Définir les options sur la page Liaisons de paramètre](#parameter)  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> Ouvrir l'Éditeur de tâche d'exécution de package  
  
1.  Ouvrez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contient une tâche d'exécution de package.  
  
2.  Cliquez avec le bouton droit sur la tâche dans le Concepteur SSIS, puis cliquez sur **Modifier**.  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> Définir les options sur la page Général  
 **Nom**  
 Fournissez un nom unique pour la tâche d'exécution de package. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche d'exécution de package.  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> Définir les options sur la page Package  
 **ReferenceType**  
 Sélectionnez **Référence du projet** pour les packages enfants qui sont dans le projet. Sélectionnez **Référence externe** pour les packages enfants situés en dehors du package.  
  
> [!NOTE]  
>  L’option **ReferenceType** est en lecture seule et est définie sur **Référence externe** si le projet qui contient le package n’a pas été converti en modèle de déploiement de projet. Pour plus d’informations sur la conversion, consultez [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 **Mot de passe**  
 Si le package enfant s’avère protégé par un mot de passe, indiquez ce dernier ou cliquez sur le bouton représentant des points de suspension (...) afin de définir un nouveau mot de passe.  
  
 `ExecuteOutOfProcess`  
 Spécifiez si le package enfant s'exécute dans le processus du package parent ou dans un processus distinct. Par défaut, la propriété ExecuteOutOfProcess a de la tâche d’exécution de package a la valeur `False` , et le package enfant s’exécute dans le même processus que le package parent. Si vous affectez la valeur `true` à cette propriété, le package enfant s'exécute dans un processus indépendant. Cela peut ralentir le lancement du package enfant. En outre, si vous avez défini la propriété sur `true`, vous ne pouvez pas déboguer le package dans une installation d'outils uniquement ; vous devez installer le produit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Installer Integration Services](install-windows/install-integration-services.md).  
  
### <a name="referencetype-dynamic-options"></a>Options dynamiques de ReferenceType  
  
#### <a name="referencetype--external-reference"></a>ReferenceType = Référence externe  
 **Lieu**  
 Sélectionnez l'emplacement du package enfant. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**SQL Server**|Définissez l'emplacement d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|**Système de fichiers**|Permet de définir l'emplacement du système de fichiers.|  
  
 **Connection**  
 Sélectionnez le type d’emplacement de stockage du package enfant.  
  
 **PackageNameReadOnly**  
 Permet d'afficher le nom du package.  
  
#### <a name="referencetype--project-reference"></a>ReferenceType = Référence du projet  
 **PackageNameFromProjectReference**  
 Sélectionnez un package contenu dans le projet, qui sera le package enfant.  
  
### <a name="location-dynamic-options"></a>Options dynamiques pour la définition de l'emplacement  
  
#### <a name="location--sql-server"></a>Emplacement = SQL Server  
 **Connection**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md), [Configurer le gestionnaire de connexions OLE DB](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **PackageName**  
 Permet d’entrer le nom du package enfant ou de cliquer sur le bouton représenté par des points de suspension (...) pour atteindre le package.  
  
#### <a name="location--file-system"></a>Emplacement = Système de fichiers  
 **Connection**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**New connection...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 **PackageNameReadOnly**  
 Permet d'afficher le nom du package.  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> Définir les options sur la page Liaisons de paramètre  
 Vous pouvez passer des valeurs du package parent ou du projet au package enfant. Le projet doit utiliser le modèle de déploiement de projet et le package enfant doit être contenu dans le même projet qui contient le package parent.  
  
 Pour plus d’informations sur la conversion de projets en modèle de déploiement de projet, consultez [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 **Paramètre de package enfant**  
 Entrez ou sélectionnez un nom pour le paramètre de package enfant.  
  
 **Variable ou paramètre de liaison**  
 Sélectionnez le paramètre ou la variable contenant la valeur que vous souhaitez transmettre au package enfant.  
  
 **Ajouter**  
 Cliquez pour mapper un paramètre ou une variable à un paramètre de package enfant.  
  
 **Remove**  
 Cliquez pour supprimer un mappage entre un paramètre ou une variable et un paramètre de package enfant.  
  
  
