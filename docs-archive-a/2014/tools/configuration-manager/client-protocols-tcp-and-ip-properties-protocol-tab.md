---
title: Protocoles clients-propriétés TCP et IP (onglet protocole) | Microsoft Docs
description: Découvrez comment spécifier les options TCP/IP dans Microsoft SQL Server Configuration Manager, telles que le paramètre Keep Alive et le numéro de port par défaut.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
ms.openlocfilehash: dfcf0348dc863970384a40cc9e773481adeedb35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705815"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>Protocoles clients - Propriétés TCP/IP (onglet Protocole)
  Dans le Gestionnaire de connexions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez l’onglet **Protocole** de la boîte de dialogue **Propriétés TCP/IP** pour afficher ou spécifier les options suivantes. Pour vous connecter à un autre port, tapez le numéro du port dans la zone **Port par défaut** . Pour plus d’informations sur les chaînes de connexion, consultez [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Options  
 **Port par défaut**  
 Spécifie le port par défaut que la Net-Library TCP/IP essaie d'utiliser pour se connecter à l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le port par défaut est 1433.  
  
 Lorsqu'un client se connecte à une instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)], il utilise cette valeur. Si une instance par défaut a été configurée pour écouter sur un port différent, remplacez cette valeur par ce numéro de port.  
  
 Lorsqu'un client se connecte à une instance nommée de [!INCLUDE[ssDE](../../includes/ssde-md.md)], il essaie d'obtenir le numéro de port auprès du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser exécuté sur l'ordinateur serveur. Si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser n'est pas en cours d'exécution, le numéro de port doit être spécifié par le biais de ce paramètre ou dans la chaîne de connexion.  
  
 **Activé**  
 Les valeurs possibles sont **Yes** et **no**.  
  
 **Conserver actif**  
 Ce paramètre (en millisecondes) contrôle la fréquence à laquelle TCP tente de vérifier qu’une connexion inactive est toujours intacte en envoyant un paquet **KEEPALIVE** . La valeur par défaut est 30  000 millisecondes.  
  
 **Intervalle Keep Alive**  
 Ce paramètre (en millisecondes), détermine l’intervalle qui sépare les retransmissions **KEEPALIVE** jusqu’à ce qu’une réponse soit reçue. La valeur par défaut est 1 000 millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Nouvel alias &#40;onglet alias&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [Propriétés d’&#60;alias&#62; &#40;onglet Alias&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
