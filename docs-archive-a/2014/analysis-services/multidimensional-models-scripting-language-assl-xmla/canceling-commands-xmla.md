---
title: Annulation de commandes (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696260"
---
# <a name="canceling-commands-xmla"></a>Annulation de commandes (XMLA)
  En fonction des autorisations d’administration de l’utilisateur qui émet la commande, la commande [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) dans XML for Analysis (XMLA) peut annuler une commande sur une session, une session, une connexion, un processus serveur ou une session ou une connexion associée.  
  
## <a name="canceling-commands"></a>Annulation de commandes  
 Un utilisateur peut annuler la commande en cours d'exécution dans le contexte de la session explicite active en envoyant une commande `Cancel` sans aucune propriété spécifiée.  
  
> [!NOTE]  
>  Une commande en cours d'exécution dans une session implicite ne peut pas être annulée par un utilisateur.  
  
### <a name="canceling-batch-commands"></a>Annulation de commandes Batch  
 Si un utilisateur annule une commande `Batch`, toutes les commandes qu'il reste à exécuter dans la commande `Batch` sont annulées. Si la commande `Batch` était transactionnelle, les commandes qui ont été exécutées avant l'exécution de la commande `Cancel` sont annulées.  
  
## <a name="canceling-sessions"></a>Annulation de sessions  
 En spécifiant un identificateur de session pour une session explicite dans la propriété [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) de la `Cancel` commande, un administrateur de base de données ou un administrateur de serveur peut annuler une session, y compris la commande en cours d’exécution. Un administrateur de base de données ne peut annuler les sessions que pour les bases de données pour lesquelles il dispose d'autorisations administratives.  
  
 Un administrateur de base de données peut récupérer les sessions actives pour une base de données spécifiée en récupérant l'ensemble de lignes de schéma DISCOVER_SESSIONS. Pour récupérer l’ensemble de lignes de schéma DISCOVER_SESSIONS, l’administrateur de base de données utilise la `Discover` méthode XMLA et spécifie l’identificateur de base de données approprié pour la colonne de restriction SESSION_CURRENT_DATABASE dans la propriété [restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) de la `Discover` méthode.  
  
## <a name="canceling-connections"></a>Annulation de connexions  
 En spécifiant un identificateur de connexion dans la propriété [ID_de_connexion](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) de la `Cancel` commande, un administrateur de serveur peut annuler toutes les sessions associées à une connexion donnée, y compris toutes les commandes en cours d’exécution, et annuler la connexion.  
  
> [!NOTE]  
>  Si l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne peut pas localiser et annuler les sessions associées à une connexion, par exemple lorsque la pompe de données ouvre plusieurs sessions tout en fournissant une connectivité http, l’instance ne peut pas annuler la connexion. Si ce cas est rencontré pendant l'exécution d'une commande `Cancel`, une erreur se produit.  
  
 Un administrateur de serveur peut récupérer les connexions actives pour une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en récupérant l'ensemble de lignes de schéma DISCOVER_CONNECTIONS à l'aide de la méthode XMLA `Discover`.  
  
## <a name="canceling-server-processes"></a>Annulation de processus serveur  
 En spécifiant un identificateur de processus serveur (SPID) dans la propriété [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) de la `Cancel` commande, un administrateur de serveur peut annuler les commandes associées à un SPID donné.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Annulation de sessions et de connexions associées  
 Vous pouvez définir la propriété [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) sur true pour annuler les connexions, les sessions et les commandes associées à la connexion, à la session ou au SPID spécifié dans la `Cancel` commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Discover &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
