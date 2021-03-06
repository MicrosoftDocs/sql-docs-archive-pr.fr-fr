---
title: Bitmap Warning, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Bitmap Warning event class
ms.assetid: 5bf9b4e3-0eba-4e67-8ba9-30ca4b48e1d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: db6009c9bdbf8affbd6be15302aa4b0f8594e6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612378"
---
# <a name="bitmap-warning-event-class"></a>Bitmap Warning, classe d'événements
  La classe d’événements **Bitmap Warning** permet de surveiller l’utilisation de filtres bitmap dans les requêtes. La sous-classe d'événements permet de signaler lorsque des filtres bitmap ont été désactivés dans une requête.  
  
## <a name="bitmap-warning-event-class-data-columns"></a>Colonnes de données de la classe d'événements Bitmap Warning  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|**DatabaseID**|`int`|Identificateur de la base de données spécifiée par l’instruction USE *base de données* ou celui de la base de données par défaut si aucune instruction USE *base de données* n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**EventClass**|`int`|Type d’événement = 212.|27|Non|  
|**EventSequence**|`int`|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**EventSubClass**|`int`|Type de sous-classe d'événements. 0 = le filtre bitmap est désactivé.|21|Oui|  
|**HostName**|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginName**|`nvarchar`|Nom de la connexion de l’utilisateur (soit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la connexion de sécurité, soit les informations d’identification de connexion Windows au format *domaine\nom_utilisateur*).|11|Oui|  
|**LoginSid**|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|**ObjectID**|`int`|ID de nœud de la racine de l'équipe de hachage impliquée dans la répartition. Correspond à l'ID de nœud dans le plan d'exécution de requêtes.|22|Oui|  
|**RequestID**|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|**ServerName**|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|`datetime`|Heure à laquelle a débuté l'événement, si disponible.|14|Oui|  
|**TransactionID**|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|**XactSequence**|`bigint`|Jeton qui décrit la transaction en cours.|50|Oui|  
  
  
