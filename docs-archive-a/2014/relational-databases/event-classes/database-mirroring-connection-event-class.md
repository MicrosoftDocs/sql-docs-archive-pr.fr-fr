---
title: Database Mirroring Connection, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: b59dccc9-f40d-4c82-aa35-ac40acea86ff
author: stevestein
ms.author: sstein
ms.openlocfilehash: db652167bd3136b0c57e68ca1ada0f13d272d011
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705127"
---
# <a name="database-mirroring-connection-event-class"></a>Classe d'événements de connexion de mise en miroir de bases de données
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement de **connexion de mise en miroir de bases de données** pour indiquer l’état d’une connexion de transport gérée par la mise en miroir de bases de données.  
  
## <a name="database-mirroringconnection-event-class-data-columns"></a>Mise en miroir de bases de données:Colonnes de données de la classe d'événements de connexion  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur d’une base de données à l’aide de la fonction **DB_ID** .|3|Oui|  
|**Error**|`int`|Numéro d’ID de message dans **sys. messages** pour le texte de l’événement. Si cet événement signale une erreur, il s'agit du numéro d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|31|Non|  
|**EventClass**|`int`|Type de classe d'événements capturée. Toujours **151** pour **Connexion de mise en miroir de bases de données**.|27|Non|  
|**EventSequence**|`int`|Numéro de séquence de cet événement.|51|Non|  
|**EventSubClass**|`nvarchar`|État de cette connexion. Pour cet événement, la sous-classe peut prendre l'une des valeurs suivantes.<br /><br /> **Connexion**en tant que. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lance une connexion de transport.<br /><br /> **Connecté**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a établi une connexion de transport.<br /><br /> **Connect Failed**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas réussi à établir une connexion de transport.<br /><br /> **Fermeture**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ferme la connexion de transport.<br /><br /> **Fermé**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a fermé la connexion de transport.<br /><br /> **Acceptez**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a accepté une connexion de transport de la part d’une autre instance.<br /><br /> **Send IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré une erreur de transport pendant l’envoi d’un message.<br /><br /> **Receive IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré une erreur de transport pendant la réception d’un message.|21|Oui|  
|**GUID**|`uniqueidentifier`|ID du point de terminaison de cette connexion.|54|Non|  
|**HostName**|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom d’hôte, utilisez la fonction **HOST_NAME** .|8|Oui|  
|**IntegerData**|`int`|Nombre de fois où cette connexion a été fermée.|25|Oui|  
|**IsSystem**|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.<br /><br /> 0 = utilisateur<br /><br /> 1 = système|60|Non|  
|**LoginSid**|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectName**|`nvarchar`|Descripteur de conversation du dialogue.|34|Non|  
|**ServerName**|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SPID**|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TextData**|`ntext`|Texte du message d'erreur lié à l'événement. Si les événements ne signalent pas d'erreur, ce champ reste vide. Le message d'erreur peut être un message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un message d'erreur Windows.|1|Oui|  
|**TransactionID**|`bigint`|ID affecté à la transaction par le système.|4|Non|  
  
  
