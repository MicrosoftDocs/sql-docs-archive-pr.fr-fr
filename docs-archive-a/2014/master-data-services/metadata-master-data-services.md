---
title: Métadonnées (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698405"
---
# <a name="metadata-master-data-services"></a>Métadonnées (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les métadonnées définies par l'utilisateur sont des informations qui vous permettent de décrire les objets de modèle. Par exemple, vous pouvez effectuer le suivi des propriétaires d'un modèle ou d'une entité spécifique, ou des systèmes sources qui fournissent des données à une entité.  
  
 Les métadonnées définies par l’utilisateur sont gérées par un modèle appelé **métadonnées**. Ce modèle est inclus automatiquement lorsque [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est installé, et il est similaire à tous les autres modèles MDS, sauf que vous ne pouvez pas en créer.  
  
 Après avoir rempli le modèle Métadonnées avec les métadonnées définies par l'utilisateur, vous pouvez l'inclure dans des vues d'abonnement, de façon à ce qu'il puisse être consommé par les systèmes d'abonnement.  
  
## <a name="metadata-entities"></a>Entités de métadonnées  
 Le modèle Métadonnées inclut cinq entités, chacune représentant un type d'objet modèle de données de référence qui prend en charge les métadonnées définies par l'utilisateur. Par exemple, l’entité de **définition des métadonnées du modèle** contient des membres qui représentent des modèles, et l’entité de **définition des métadonnées d’attribut** a des membres qui représentent tous les attributs de tous les modèles.  
  
 Pour définir les métadonnées d'un objet de modèle, vous devez remplir un de ces attributs de membre. Par exemple, dans l’entité de **définition des métadonnées d’entité** , vous pouvez remplir l’attribut Description du membre Price avec le texte suivant : **prix du produit lorsqu’il est vendu à un client**.  
  
 Les membres du modèle Métadonnées sont mis à jour automatiquement à chaque ajout ou suppression d'objets de modèle qui prennent en charge des métadonnées définies par l'utilisateur.  
  
 Le modèle Métadonnées ne peut pas être pourvu de version ; il n'est pas possible de lui ajouter des indicateurs de version ni de les modifier ; il ne peut pas être enregistré en tant que package de déploiement de modèle. Toutefois, il possède à l'identique toutes les autres fonctionnalités disponibles pour les autres modèles de données de référence. Par exemple, vous pouvez implémenter un jeu de règles d'entreprise sur le modèle Métadonnées pour appliquer des stratégies de données.  
  
## <a name="customizing-your-metadata-model"></a>Personnalisation de votre modèle de métadonnées  
 Chaque entité de définition de métadonnées inclut les attributs Name, Code et Description. Vous pouvez créer des attributs supplémentaires pour décrire plus précisément vos objets de modèle.  
  
 Par exemple, vous pouvez créer les attributs suivants :  
  
-   Un attribut basé sur un domaine nommé Owner, que vous utilisez pour effectuer le suivi du propriétaire de chaque objet de modèle.  
  
-   Un attribut de forme libre nommé Last Review Date, qui vous permet d'effectuer le suivi de la date à laquelle un objet a été révisé par le propriétaire pour la dernière fois.  
  
-   Un attribut basé sur un domaine nommé sources, que vous utilisez pour suivre et gérer les systèmes sources qui interagissent avec l' [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] instance.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Ajoutez des métadonnées à un objet de modèle.|[Ajouter des métadonnées &#40;Master Data Services&#41;](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a>Contenu associé  
  
-   [Exportation de données &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)  
  
  
