---
title: Showplan Text, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan Text event class
ms.assetid: f36c73b2-a1d1-4513-9594-78818f3fcb0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: da0c24aa83c965c948365eddb9f8bd9820468579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695660"
---
# <a name="showplan-text-event-class"></a>Showplan Text (classe d'événements)
  La classe d’événements Showplan Text intervient quand [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute une instruction SQL. Les informations comprises sont un sous-ensemble des informations disponibles dans les classes d’événements Showplan All, Showplan XML Statistics Profile ou Showplan XML.  
  
 Si vous incluez la classe d'événements Showplan Text dans une trace, le surcroît de charge imposée au système diminue sensiblement les performances. Pour limiter ce problème, n'utilisez cette classe d'événements qu'avec les traces surveillant des problèmes spécifiques pendant de brèves périodes. Showplan Text ne mobilise pas autant de ressources système que les autres classes d'événements Showplan.  
  
 Si vous incluez la classe d'événements Showplan Text dans une trace, la colonne de données BinaryData doit être sélectionnée. Dans le cas contraire, les informations de cette classe ne seront pas affichées dans la trace.  
  
## <a name="showplan-text-event-class-data-columns"></a>Colonnes de données de la classe d'événements Showplan Text  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|BinaryData|`image`|Coût estimé du texte Showplan.|2|Non|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|nom_base_de_données|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|Classe d'événements|`int`|Type d’événement = 96.|27|Non|  
|EventSequence|`int`|Séquence d'un événement donné au sein de la demande.|51|Non|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|Integer Data|`integer`|Estimation du nombre de lignes retournées|25|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LineNumber|`int`|Affiche le numéro de la ligne qui contient l'erreur.|5|Oui|  
|SID de connexion|`bitmap`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Non|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|NestLevel|`int`|Entier représentant les données retournées par @@NESTLEVEL.|29|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|ObjectID|`int`|ID affecté à l'objet par le système.|22|Oui|  
|ObjectName|`nvarchar`|Nom de l'objet référencé.|34|Oui|  
|ObjectType|`int`|Valeur représentant le type de l'objet qui intervient dans l'événement. Cette valeur correspond à la colonne de type dans sysobjects. Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).|28|Oui|  
|RequestID|`int`|Identification de la demande à l'origine de la requête de texte intégral.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|`bigint`|Jeton utilisé pour décrire la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Guide de référence des opérateurs Showplan logiques et physiques](../showplan-logical-and-physical-operators-reference.md)   
 [Showplan All, classe d’événements](showplan-all-event-class.md)   
 [Showplan XML Statistics Profile (classe d’événements)](showplan-xml-statistics-profile-event-class.md)   
 [Showplan XML, classe d’événements](showplan-xml-event-class.md)  
  
  
