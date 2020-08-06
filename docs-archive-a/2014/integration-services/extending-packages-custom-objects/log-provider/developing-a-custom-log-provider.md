---
title: Développement d’un module fournisseur d’informations personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88d4f70fa9d50628b831b56f9fa22100648fce51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601617"
---
# <a name="developing-a-custom-log-provider"></a>Développement d'un module fournisseur d'informations personnalisé
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] possède des fonctions de journalisation étendues qui permettent de capturer les événements qui se produisent pendant l'exécution de package. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut divers modules fournisseurs d’informations qui permettent de créer et de stocker des journaux dans différents formats, tels que XML, texte et base de données ou dans le journal des événements Windows. Si les modules fournisseurs d'informations et les formats de sortie fournis ne répondent pas totalement à vos besoin, vous pouvez créer un module fournisseur d'informations personnalisé.

 Pour créer un module fournisseur d'informations personnalisé, vous devez créer une classe qui hérite de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, appliquer l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> à la nouvelle classe et substituer les méthodes et propriétés importantes de la classe de base, notamment la propriété <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> et la méthode <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>.

## <a name="in-this-section"></a>Dans cette section
 Cette section explique comment créer, configurer et coder un module fournisseur d'informations personnalisé.

 [Création d’un module fournisseur d’informations personnalisé](creating-a-custom-log-provider.md) Décrit comment créer les classes d’un projet de module fournisseur d’informations personnalisé.

 [Codage d’un module fournisseur d’informations personnalisé](coding-a-custom-log-provider.md) Décrit comment implémenter un module fournisseur d’informations personnalisé en substituant les méthodes et les propriétés de la classe de base.

 [Développement d’une interface utilisateur pour un module fournisseur d’informations personnalisé](developing-a-user-interface-for-a-custom-log-provider.md) Les interfaces utilisateur personnalisées pour les modules fournisseurs d’informations personnalisés ne sont pas prises en charge dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .

## <a name="related-topics"></a>Rubriques connexes

### <a name="information-common-to-all-custom-objects"></a>Informations communes à tous les objets personnalisés
 Pour obtenir les informations communes à tous les types d'objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :

 [Développement d’objets personnalisés pour Integration Services](../developing-custom-objects-for-integration-services.md) Décrit les étapes de base de l’implémentation de tous les types d’objets personnalisés pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .

 [Persistance des objets personnalisés](../persisting-custom-objects.md) Décrit la persistance personnalisée et explique quand elle est nécessaire.

 [Génération, déploiement et débogage d’objets personnalisés](../building-deploying-and-debugging-custom-objects.md) Décrit les techniques permettant de générer, signer, déployer et déboguer des objets personnalisés.

### <a name="information-about-other-custom-objects"></a>Informations sur les autres objets personnalisés
 Pour plus d’informations sur les autres types d’objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :

 [Développement d’une tâche personnalisée](../task/developing-a-custom-task.md) Explique comment programmer des tâches personnalisées.

 [Développement d’un gestionnaire de connexions personnalisé](../connection-manager/developing-a-custom-connection-manager.md) Explique comment programmer des gestionnaires de connexions personnalisés.

 [Développement d’un énumérateur foreach personnalisé](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Explique comment programmer des énumérateurs personnalisés.

 [Développement d’un composant de workflow de données personnalisé](../data-flow/developing-a-custom-data-flow-component.md) Explique comment programmer des sources, des transformations et des destinations de workflow de données personnalisées.

![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.


