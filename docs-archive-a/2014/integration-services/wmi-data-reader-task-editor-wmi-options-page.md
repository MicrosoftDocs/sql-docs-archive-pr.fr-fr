---
title: Éditeur de tâche lecteur de données WMI (page Options WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613506"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Éditeur de tâche Lecteur de données WMI (page Options WMI)
  Utilisez la page **Options WMI** de la boîte de dialogue **Éditeur de tâche Lecteur de données WMI** pour définir la source de la requête WQL (Windows Management Instrumentation Query Language) et la destination du résultat de la requête.  
  
 Pour en savoir plus sur cette tâche, consultez [WMI Data Reader Task](control-flow/wmi-data-reader-task.md). Pour plus d’informations sur le langage de requêtes WMI (WQL), consultez la rubrique [Requêtes avec WQL](https://go.microsoft.com/fwlink/?LinkId=79045)dans la documentation Windows Management Instrumentation de la bibliothèque MSDN.  
  
## <a name="static-options"></a>Options statiques  
 **WMIConnectionName**  
 Sélectionnez un gestionnaire de connexions WMI dans la liste ou cliquez sur \<**New WMI Connection...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions WMI](connection-manager/wmi-connection-manager.md), [Éditeur du gestionnaire de connexions WMI](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Sélectionnez le type de la source de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définit la source d'une requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
|**Connexion de fichiers**|Sélectionnez un fichier qui contient la requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
|**Variable**|Définissez la source dans une variable qui définit la requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
  
 **OutputType**  
 Indiquez si la sortie doit être une table de données, une valeur de propriété ou un nom et une valeur de propriété.  
  
 **OverwriteDestination**  
 Indique s'il faut conserver ou remplacer les données d'origine dans le fichier ou la variable de destination, ou leur ajouter des données.  
  
 **DestinationType**  
 Sélectionnez le type de la destination de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Sélectionnez un fichier pour y enregistrer le résultat de la requête WQL. Cette valeur affiche l'option dynamique **DestinationType**.|  
|**Variable**|Définissez la variable de stockage du résultat de la requête WQL. Cette valeur affiche l'option dynamique **DestinationType**.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>Options dynamiques WQLQuerySourceType  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Entrée directe  
 **WQLQuerySource**  
 Fournissez une requête ou cliquez sur le bouton de sélection (...) et entrez une requête en utilisant la boîte de dialogue **Requête WQL**.  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = Connexion de fichiers  
 **WQLQuerySource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**New connection...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Variable  
 **WQLQuerySource**  
 Sélectionnez une variable dans la liste, ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>Options dynamiques DestinationType  
  
### <a name="destinationtype--file-connection"></a>DestinationType = Connexion de fichiers  
 **Destination**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**New connection...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = Variable  
 **Destination**  
 Sélectionnez une variable dans la liste, ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche lecteur de données WMI &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Tâche Observateur d’événement WMI](control-flow/wmi-event-watcher-task.md)  
  
  
