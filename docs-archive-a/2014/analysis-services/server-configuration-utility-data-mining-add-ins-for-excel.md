---
title: Utilitaire de configuration du serveur (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710871"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a>Utilitaire de configuration du serveur (Compléments d'exploration de données pour Excel)
  Lorsque vous installez les compléments d’exploration de données pour Excel, un utilitaire de configuration de serveur est également installé et s’exécute la première fois que vous ouvrez les compléments. Cette rubrique explique comment utiliser l’utilitaire pour vous connecter à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et configurer une base de données pour travailler avec des modèles d’exploration de données.  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a>Étape 1 : se connecter à Analysis Services  
 Choisissez le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui fournit les algorithmes d'exploration de données et stocke vos modèles d'exploration de données.  
  
 Lorsque vous créez une connexion pour l'exploration de données, vous devez choisir un serveur sur lequel travailler avec les modèles d'exploration de données. Nous vous recommandons de créer une nouvelle base de données sur le serveur et de la dédier à l'exploration de données, ou de demander à votre administrateur de préparer un serveur d'exploration de données à votre place. Ainsi, vous pourrez créer des modèles sans affecter l'exécution d'autres services.  
  
 Notez que le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous utilisez pour l'exploration de données ne doit pas nécessairement être sur le même serveur que vos données source.  
  
 **Nom du serveur**  
 Tapez le nom du serveur qui contient l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous utiliserez pour l'exploration de données.  
  
 **Authentification**  
 Spécifiez les méthodes d'authentification. L'Authentification Windows est requise pour les connexions à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], sauf si votre administrateur a configuré l'accès au serveur via HTTPPump.  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a>Étape 2 : autoriser les modèles temporaires  
 Avant de pouvoir utiliser les compléments, une propriété du serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit être modifiée pour permettre la création de modèles d'exploration de données temporaires.  
  
 Les modèles d’exploration de données temporaires sont également appelés *modèles de session*. C'est parce que les modèles sont stockés uniquement tant que votre session actuelle est ouverte. Lorsque vous fermez votre connexion au serveur, la session est terminée et tous les modèles utilisés pendant la session sont supprimés.  
  
 L'utilisation de modèles d'exploration de données de session n'affecte pas l'espace de stockage disponible sur le serveur, mais la surcharge induite par la création de modèles d'exploration de données peut affecter les performances du serveur.  
  
 L'Assistant commence par détecter les paramètres du serveur spécifié. Si le serveur autorise déjà les modèles d’exploration de données temporaires, vous pouvez cliquer sur **suivant** pour continuer. L'Assistant fournit également des instructions pour activer les modèles d'exploration de données temporaires sur le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] spécifié, ou pour en faire la demande à votre administrateur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a>Étape 3 : créer une base de données pour les utilisateurs des compléments  
 Dans cette page de l'Assistant Installation et configuration, vous créez une nouvelle base de données qui est dédiée à l'exploration de données, ou vous sélectionnez une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] existante.  
  
> [!WARNING]  
>  L'exploration de données nécessite une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] exécutée en mode multidimensionnel. Le mode tabulaire ne prend pas en charge l'exploration de données.  
  
 Nous vous recommandons de créer une base de données distincte dédiée à l'exploration de données. Vous pourrez ainsi travailler avec les modèles d'exploration de données sans affecter les autres objets de la solution.  
  
 Si vous choisissez une base de données existante sur une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], notez qu'il est possible de remplacer les modèles existants si vous utilisez les compléments pour créer un modèle et si un modèle avec ce nom existe déjà.  
  
 **Create new database**  
 Sélectionnez cette option pour créer une nouvelle base de données sur le serveur sélectionné. Une base de données d'exploration de données stockera vos sources de données, ainsi que vos structures et vos modèles d'exploration de données.  
  
 **Nom de la base de données**  
 Tapez le nom de la nouvelle base de données. Si le nom n'est pas encore utilisé, il sera créé.  
  
 **Utiliser une base de données existante**  
 Sélectionnez cette option pour utiliser une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] existante.  
  
 **Sauvegarde de la base de données**  
 Si vous choisissez d'utiliser une base de données existante, vous devez sélectionner son nom dans la liste.  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a>Étape 4 : attribuer les autorisations appropriées aux utilisateurs des compléments  
 Assurez-vous que vous-même (et les autres utilisateurs des compléments) bénéficiez des autorisations nécessaires pour parcourir, modifier, traiter ou créer des structures et des modèles d'exploration de données.  
  
 Par défaut, l'Authentification Windows intégrée est un préalable de l'utilisation des compléments.  
  
 **Donner aux utilisateurs les autorisations d'administration sur la base de données**  
 Sélectionnez cette option pour accorder l'accès à la base de données aux utilisateurs répertoriés.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent uniquement à la base de données indiquée dans la zone **nom de la base de données** .  
  
 **Nom de la base de données**  
 Affiche le nom de la base de données sélectionnée.  
  
 **Spécifier les utilisateurs ou les groupes à ajouter**  
 Sélectionnez les connexions qui auront accès à la base de données utilisée pour l'exploration de données.  
  
 **Ajouter**  
 Cliquez pour ouvrir une boîte de dialogue et ajouter des utilisateurs ou des groupes.  
  
 **Remove**  
 Cliquez pour supprimer l'utilisateur ou le groupe de la liste des utilisateurs dotés d'autorisations d'administration.  
  
  
