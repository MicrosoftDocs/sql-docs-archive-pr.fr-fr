---
title: Propriétés des protocoles clients (onglet ordre) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client protocols [SQL Server]
ms.assetid: 64fd7135-1756-4885-bed9-9ab8997ecc6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a367cff3495389d1a707ed108ba75e1e736538b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697328"
---
# <a name="client-protocols-properties-order-tab"></a>Propriétés de protocoles clients (onglet Ordre)
  La page **Ordre**de la boîte de dialogue **Propriétés de protocoles clients** vous permet d’afficher et d’activer les protocoles clients.  
  
 Cliquez sur un protocole, puis sur **Activer** ou **Désactiver** pour déplacer le protocole sélectionné vers la liste **Protocoles désactivés** ou **Protocoles activés** .  
  
 Les protocoles sont essayés dans l'ordre dans lequel ils sont répertoriés, en commençant par le premier de la liste. Déplacez les protocoles vers le haut ou vers le bas dans la liste **Protocoles activés** , en cliquant sur les flèches haut et bas. Lors de l’établissement d’une connexion à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un client installé sur cet ordinateur, le protocole **Mémoire partagée** est toujours essayé en premier, s’il est activé.  
  
> [!NOTE]  
>  Ces paramètres ne sont pas utilisés par SqlClient [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET. L'ordre des protocoles pour SqlClient .NET commence par TCP, puis viennent les canaux nommés, qui ne peuvent pas être modifiés.  
  
## <a name="options"></a>Options  
 **Protocoles désactivés**  
 Répertorie les protocoles installés mais actuellement non utilisés.  
  
 **Protocoles activés**  
 Répertorie les protocoles disponibles pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les clients sur cet ordinateur.  
  
 **>**  
 Active le protocole affiché en surbrillance dans la zone **Protocoles désactivés** , en le déplaçant vers la zone **Protocoles activés** .  
  
 **\<**  
 Désactive le protocole affiché en surbrillance dans la zone **Protocoles activés** , en le déplaçant vers la zone **Protocoles désactivés** .  
  
 Flèche haut  
 Déplace le protocole affiché en surbrillance vers le haut de la liste. Cela vous permet d'augmenter la priorité avec laquelle la Net-Library essaie d'utiliser le protocole sélectionné pour les connexions.  
  
 Flèche bas  
 Déplace le protocole affiché en surbrillance vers le bas de la liste. Cela vous permet de diminuer la priorité avec laquelle la Net-Library essaie d'utiliser le protocole sélectionné pour les connexions.  
  
 **Activer le protocole de mémoire partagée**  
 Lors de l’établissement d’une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un client installé sur cet ordinateur, active le protocole de mémoire partagée qui est toujours essayé en premier (s’il est activé).  
  
> [!NOTE]  
>  Si le protocole est spécifié par le biais d'un préfixe ou à l'intérieur de la chaîne de connexion, seul le protocole spécifié est essayé.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
