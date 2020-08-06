---
title: Éditeur de tâche de service Web (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dbacf2a2a867ab01039678ff4f43eebac839c11a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613523"
---
# <a name="web-service-task-editor-general-page"></a>Éditeur de tâche de service Web (page Général)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir un gestionnaire de connexions HTTP, spécifier l’emplacement du fichier WSDL (Web Services Description Language) qu’utilise la tâche de service web, décrire la tâche de service web et télécharger le fichier WSDL.  
  
 Pour plus d’informations sur cette tâche, consultez [Tâche de service Web](control-flow/web-service-task.md).  
  
## <a name="options"></a>Options  
 **HTTPConnection**  
 Sélectionnez un gestionnaire de connexions dans la liste ou cliquez sur \<**New connection...**> pour en créer un.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 **Rubriques connexes :**  [Gestionnaire de connexions HTTP](connection-manager/http-connection-manager.md), [Éditeur du gestionnaire de connexions &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Tapez le chemin d’accès qualifié complet d’un fichier WSDL qui est en local sur l’ordinateur ou cliquez sur le bouton Parcourir **(...)** et recherchez ce fichier.  
  
 Si vous avez déjà téléchargé manuellement le fichier WSDL sur l'ordinateur, sélectionnez-le. Toutefois, si le fichier WSDL n'a pas encore été téléchargé, procédez comme suit :  
  
-   Créez un fichier vide ayant l'extension de nom de fichier .wsdl.  
  
-   Sélectionnez ce fichier vide pour l’option **WSDLFile** .  
  
-   Affectez à **OverwriteWsdlFile** la valeur `True` pour permettre au fichier vide d’être remplacé par le fichier WSDL réel.  
  
-   Cliquez sur **Télécharger WSDL** pour télécharger le fichier WSDL réel et remplacer le fichier vide.  
  
    > [!NOTE]  
    >  L’option **Télécharger WSDL** n’est pas activée tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile** .  
  
 **OverwriteWSDLFile**  
 Indiquez si le fichier WSDL de la tâche de service Web peut être remplacé.  
  
 Si vous envisagez de télécharger le fichier WSDL à l’aide du bouton **Télécharger WSDL** , définissez cette valeur sur `True` .  
  
 **Nom**  
 Fournissez un nom unique pour la tâche de service Web. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche de service Web.  
  
 **Télécharger WSDL**  
 Téléchargez le fichier WSDL.  
  
 Ce bouton n’est pas activé tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile** .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page d’entrée&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Éditeur de tâche de service Web &#40;page sortie&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
