---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f56a104841c4825bba1f60b3588fadd63555c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604531"
---
# <a name="mssqlserver_17194"></a>MSSQLSERVER_17194
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17194|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Le serveur n'a pas pu charger la bibliothèque de fournisseurs SSL requise pour la connexion ; cette connexion a été fermée. SSL sert à chiffrer la séquence d'ouverture de session ou l'ensemble des communications, en fonction de la manière dont l'administrateur a configuré le serveur. Consultez la documentation en ligne pour plus d’informations sur ce message d’erreur :  0xXXXX. [CLIENT : 11.11.11.11]|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le client a fermé la connexion. Elle peut survenir si le délai de connexion a expiré. Le message d'erreur affiche une valeur provenant du système d'exploitation qui décrit le problème sous-jacent.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si le code d'erreur dans le message est 0x2746 (valeur décimale 10054), cela signifie que le client a réinitialisé la connexion, généralement suite à un délai d'attente. Pour résoudre l'erreur, augmentez le délai de la connexion sur le client ou le programme appelant.  
  
 Pour identifier une solution possible pour d’autres valeurs du message d’erreur, utilisez la commande **net helpmsg** du système d’exploitation et précisez la valeur décimale du code d’erreur.  
  
 Pour plus d’informations sur la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Configuration réseau du serveur](../../database-engine/configure-windows/server-network-configuration.md) et [Configuration du réseau client](../../database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Interne uniquement  
  
