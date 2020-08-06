---
title: Créer des packages dans SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604056"
---
# <a name="create-packages-in-sql-server-data-tools"></a>Créer des packages dans les outils de données SQL Server
  Les packages que vous créez dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] à l'aide du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] sont enregistrés dans le système de fichiers. Pour enregistrer un package dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le magasin de packages, vous devez enregistrer une copie du package. Pour plus d’informations, consultez [Enregistrer une copie d’un package](../../2014/integration-services/save-a-copy-of-a-package.md).  
  
 Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous pouvez créer un nouveau package à l'aide de l'une des méthodes suivantes :  
  
-   Utiliser le modèle de package inclus dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
-   Utiliser un modèle personnalisé  
  
     Pour utiliser des packages personnalisés comme modèles pour la création de nouveaux packages, il vous suffit de les copier dans le dossier DataTransformationItems. Par défaut, ce dossier se trouve dans C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
-   Copier un package existant.  
  
     Si des packages existants incluent des fonctionnalités que vous souhaitez réutiliser, vous pouvez construire le flux de contrôle et les flux de données dans le package plus rapidement en copiant et en collant des objets à partir de nouveaux packages. Pour plus d’informations sur le copier et coller dans des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , consultez [Réutiliser des objets de packages](reuse-of-package-objects.md).  
  
     Si vous créez un nouveau package en copiant un package existant ou en utilisant un package personnalisé comme modèle, le nom et le GUID du package existant sont copiés également. Vous devez mettre à jour le nom et le GUID du nouveau package pour le différencier plus facilement du package à partir duquel il a été copié. Par exemple, si des packages ont le même GUID, il est plus difficile d'identifier le package auquel appartiennent les données de journal. Vous pouvez régénérer le GUID dans les propriétés `ID` et mettre à jour la valeur de la propriété `Name` à l'aide de la fenêtre Propriétés dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Définir les propriétés d’un package](set-package-properties.md) et [Utilitaire dtutil](dtutil-utility.md).  
  
-   Utiliser un package personnalisé que vous avez désigné comme modèle.  
  
-   Exécuter l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
     L'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] crée un package complet pour une opération simple d'importation ou d'exportation. Cet Assistant configure les connexions, la source et la destination, et ajoute toutes les transformations de données requises pour vous permettre d'exécuter l'opération d'importation ou d'exportation immédiatement. Vous pouvez enregistrer, le cas échéant, le package pour l'exécuter de nouveau ultérieurement ou pour l'affiner et l'améliorer dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Toutefois, si vous enregistrez le package, vous devez l'ajouter à un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] existant avant de pouvoir le modifier ou l'exécuter dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Les procédures suivantes décrivent comment créer ou supprimer un package dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Pour obtenir une vidéo qui montre comment créer un package de base à l’aide du modèle de package par défaut, consultez [Création d’un package de base (Vidéo liée à SQL Server)](https://go.microsoft.com/fwlink/?LinkId=131023).  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>Pour créer un package dans les outils de données SQL Server à l'aide du modèle de package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans lequel vous souhaitez créer un package.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Packages SSIS** , puis cliquez sur **Nouveau package SSIS**.  
  
3.  Si vous le souhaitez, ajoutez des tâches de flux de contrôle, des tâches de flux de données et des gestionnaires d'événements au package. Pour plus d’informations, consultez [Flux de contrôle](control-flow/control-flow.md), [Flux de données](data-flow/data-flow.md) et [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md).  
  
4.  Dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés** pour enregistrer le nouveau package.  
  
    > [!NOTE]  
    >  Vous pouvez enregistrer un package vide.  
  
  
