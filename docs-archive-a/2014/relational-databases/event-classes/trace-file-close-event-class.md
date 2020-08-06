---
title: Trace File Close, classe d’événements
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34075f9c3a664198999873f2dc95f02b19799712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600939"
---
# <a name="trace-file-close-event-class"></a>classe d'événements Trace File Close
  La classe d’événements **Trace File Close** indique qu’un fichier de trace a été fermé pendant la substitution de ce dernier.  
  
## <a name="trace-file-close-event-class-data-columns"></a>Colonnes de la classe d'événements Trace File Close  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Type d’événement = 150.|27|Non|  
|**EventSequence**|**int**|Horodateur unique de cet événement déclenché dans cette trace. Ce nombre augmente par incréments fixes à chaque déclenchement d'événement.|51|Non|  
|**FileName**|**nvarchar**|Nom logique du fichier de trace en cours de fermeture.|36|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, NULL = utilisateur. Cette valeur est toujours égale à 1 pour cette classe d'événements.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur). La valeur est toujours « sa » pour cette classe d'événements.|11|Oui|  
|**ObjectID**|**int**|ID attribué par le système à la trace.|22|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
