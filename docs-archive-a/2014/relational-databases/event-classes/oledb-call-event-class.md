---
title: OLEDB Call, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB Call event class
ms.assetid: e1be1e90-98cc-47a3-addd-59d4aeca6547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a26781a34b75893dfb8aad54cea8e7f6d2c2e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601498"
---
# <a name="oledb-call-event-class"></a>OLEDB Call (classe d'événements)
  La classe d’événements **OLEDB Call** se produit quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appelle un fournisseur OLE DB pour les requêtes distribuées et les procédures stockées distantes.  
  
 Incluez la classe d’événements **OLEDB Call** dans les traces pour surveiller uniquement les appels qui ne demandent pas de données ou les appels qui ne sont pas effectués pour la méthode **QueryInterface** . Quand la classe d’événements **OLEDB Call** est incluse dans une trace, la charge engagée dépend de la fréquence à laquelle les appels OLE DB se produisent sur la base de données pendant la trace. Si les appels se produisent fréquemment, la trace peut dégrader notablement les performances.  
  
## <a name="oledb-call-event-class-data-columns"></a>Colonnes de données de la classe d'événements OLEDB Call  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`Int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|DatabaseID|`Int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|nom_base_de_données|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|Duration|`Bigint`|Durée nécessaire pour exécuter l'événement d'appel OLE DB.|13|Non|  
|EndTime|`Datetime`|Heure de fin de l'événement.|15|Oui|  
|Error|`int`|Numéro d'erreur d'un événement donné. Il s'agit souvent du numéro d'erreur stocké dans l'affichage catalogue sys.messages.|31|Oui|  
|EventClass|`Int`|Type d’événement = 119.|27|Non|  
|EventSequence|`Int`|Séquence de la classe d'événements OLE DB dans le lot.|51|Non|  
|EventSubClass|`Int`|0=Démarrage<br /><br /> 1=Terminée|21|Non|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LinkedServerName|`nvarchar`|Nom du serveur lié.|45|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|`Image`|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|MethodName|`nvarchar`|Nom de la méthode OLE DB.|47|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ProviderName|`nvarchar`|Nom du fournisseur OLE DB.|46|Oui|  
|RequestID|`Int`|ID de la demande contenant l'instruction.|49|Oui|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Exemple : si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom d'utilisateur Login1 et exécutez une instruction sous le nom Login2, `SessionLoginName` retourne Login1 et `LoginName` retourne Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`Int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`nvarchar`|Paramètres envoyés et reçus au sein de l'appel OLE DB.|1|Non|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Objets OLE Automation dans Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
