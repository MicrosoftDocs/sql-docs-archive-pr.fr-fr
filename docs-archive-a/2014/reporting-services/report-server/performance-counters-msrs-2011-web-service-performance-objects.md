---
title: Compteurs de performances pour le service Web MSRS 2014 et les objets de performance du service Windows MSRS 2014 (mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- Report Server Web service, performance counters
- Reporting Services performance object
- RS Web Service performance object
- counters [Reporting Services]
- performance [Reporting Services]
ms.assetid: c642fc4f-8734-4626-a194-42ac9cd8e2ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cbd223d8275aa2c2bf3fe4d714e5584b988252e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605085"
---
# <a name="performance-counters-for-the-msrs-2014-web-service-and-msrs-2014-windows-service-performance-objects-native-mode"></a>Compteurs de performance du service Web MSRS 2014 et objets de performance du service Windows MSRS 2014 (mode natif)
  Cette rubrique décrit les compteurs de performance pour les objets de performance `MSRS 2014 Web Service` et `MSRS 2014 Windows Service`.

> [!NOTE]
>  Ces objets de performance contrôlent des événements sur le serveur de rapports local. Si vous exécutez un serveur de rapports dans un déploiement avec montée en puissance parallèle, les chiffres s'appliquent au serveur actuel et non au déploiement avec montée en puissance parallèle.

 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode natif

 Les objets de performance sont disponibles dans l’Analyseur de performances Windows (**Perfmon.exe**). Pour plus d'informations, consultez la documentation Windows, [Profilage de runtime](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).

 Pour plus d’informations sur les compteurs de performances en mode SharePoint, consultez [compteurs de performances du service Web msrs 2014 en mode SharePoint et du service Windows msrs 2014 objets de performance en mode sharepoint &#40;&#41;en mode SharePoint ](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md).

 **Dans cette rubrique :**

-   [Compteurs de performance du service Web MSRS 2014](#bkmk_webservice)

-   [Compteurs de performance du service Windows MSRS 2014](#bkmk_windowsservice)

-   [Utiliser des applets de commande PowerShell pour retourner des listes](#bkmk_powershell)

##  <a name="msrs-2014-web-service-performance-counters"></a><a name="bkmk_webservice"></a>Compteurs de performance du service Web MSRS 2014
 L'objet de performance `MSRS 2014 Web Service` contrôle les performances du serveur de rapports. Cet objet de performance inclut une collection de compteurs utilisée pour suivre le traitement du serveur de rapports initialisé en général via des opérations de consultation du rapport interactives. Lorsque vous configurez ce compteur, vous pouvez l'appliquer à toutes les instances de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ou sélectionner des instances spécifiques. Ces compteurs sont réinitialisés à chaque interruption du service Web Report Server par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] .

 Le tableau suivant répertorie les compteurs inclus dans l'objet de performance `MSRS 2014 Web Service`.

|Compteur|Description|
|-------------|-----------------|
|`Active Sessions`|Nombre de sessions actives. Ce compteur fournit un nombre cumulatif de toutes les sessions de navigateur générées à partir d'exécutions de rapports, qu'elles soient toujours actives ou non.<br /><br /> Le compteur est décrémenté à mesure que les enregistrements de session sont supprimés. Par défaut, les sessions sont supprimées après dix minutes sans activité.|
|`Cache Hits/Sec`|Nombre de requêtes par seconde pour les rapports mis en cache. Les demandes sont relatives aux rapports qui font l'objet d'un nouveau rendu ; il ne s'agit pas de demandes concernant les rapports traités directement à partir du cache. (Consultez `Total Cache Hits` plus loin dans cette rubrique.)|
|`Cache Hits/Sec (Semantic Models)`|Nombre de requêtes par seconde pour le modèle mis en cache. Requêtes relatives aux rapports qui font l'objet d'un nouveau rendu, et non des requêtes concernant les rapports traités directement à partir du cache.|
|`Cache Misses/Sec`|Nombre de requêtes par seconde qui n'ont pas retourné un rapport à partir du cache. Utilisez ce compteur afin de déterminer si les ressources utilisées pour la mise en cache (disque ou mémoire) sont suffisantes.|
|`Cache Misses/Sec (Semantic Models)`|Nombre de requêtes par seconde qui n'ont pas retourné de modèle à partir du cache. Utilisez ce compteur afin de déterminer si les ressources utilisées pour la mise en cache (disque ou mémoire) sont suffisantes.|
|`First Session Requests/Sec`|Nombre de nouvelles sessions utilisateur démarrées chaque seconde à partir du cache du serveur de rapports.|
|`Memory Cache Hits/Sec`|Nombre de fois par seconde où les rapports sont récupérés du cache mémoire. Le*cache interne* fait partie de la mémoire cache qui stocke les rapports dans la mémoire de l’unité centrale. Quand le cache mémoire est utilisé, le serveur de rapports n’interroge pas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le contenu mis en cache.|
|`Memory Cache Misses/Sec`|Nombre de fois par seconde où les rapports n'ont pas pu être récupérés du cache mémoire.|
|`Next Session Requests/Sec`|Nombre de requêtes par seconde pour les rapports qui sont ouverts dans une session existante (tels que les rapports rendus à partir d'un instantané de session).|
|`Report Requests`|Nombre de rapports qui sont actuellement actifs et gérés par le serveur de rapports.|
|`Reports Executed/Sec`|Nombre d'exécutions de rapport réussies par seconde. Ce compteur fournit des statistiques à propos du volume de rapports. Utilisez ce compteur avec `Request/Sec` pour comparer l'exécution de rapports et les demandes de rapports pouvant être retournées par le cache.|
|`Requests/Sec`|Nombre de demandes par seconde envoyées au serveur de rapports. Ce compteur suit tous les types de demandes gérées par le serveur de rapports.|
|`Total Cache Hits`|Nombre total de demandes de rapports à partir du cache après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] .|
|`Total Cache Hits (Semantic Models)`|Nombre total de demandes de modèle à partir du cache après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par ASP.NET.|
|`Total Cache Misses`|Nombre total d'échecs de retour d'un rapport à partir du cache après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] . Utilisez ce compteur pour déterminer si l'espace disque et la mémoire sont suffisants.|
|`Total Cache Misses (Semantic Models)`|Nombre total d'échecs de retour d'un modèle à partir du cache après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par ASP.NET. Utilisez ce compteur pour déterminer si l'espace disque et la mémoire sont suffisants.|
|`Total Memory Cache Hits`|Nombre total de rapports mis en cache retournés par le cache mémoire après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] . Le*cache interne* fait partie de la mémoire cache qui stocke les rapports dans la mémoire de l’unité centrale. Quand le cache mémoire est utilisé, le serveur de rapports n’interroge pas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le contenu mis en cache.|
|`Total Memory Cache Misses`|Nombre total d'absences dans le cache mémoire après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] .|
|`Total Processing Failures`|Nombre d'erreurs de traitement des requêtes pour le service Web du serveur de rapports.|
|`Total Rejected Threads`|Nombre total de threads rejetés pour le traitement asynchrone, puis gérés comme processus synchrones dans le même thread. Chaque source de données est traitée sur un thread. Si le volume de threads dépasse la capacité, les threads sont rejetés pour le traitement asynchrone et sont traités ensuite en série.|
|`Total Reports Executed`|Nombre total de rapports qui ont été correctement exécutés après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] .|
|`Total Requests`|Nombre total des demandes envoyées au serveur de rapports après le démarrage du service. Ce compteur est réinitialisé à chaque interruption du service Web du serveur de rapports par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] .|

##  <a name="msrs-2014-windows-service-performance-counters"></a><a name="bkmk_windowsservice"></a>Compteurs de performance du service Windows MSRS 2014
 L'objet de performance `MSRS 2014 Windows Service` contrôle le service Windows du serveur de rapports. Cet objet de performance inclut une collection de compteurs utilisée pour suivre le traitement des rapports initialisé via des opérations planifiées. Les opérations planifiées peuvent englober l'abonnement et la remise, les instantanés d'exécution de rapport et l'historique de rapport. Lorsque vous configurez ce compteur, vous pouvez l'appliquer à toutes les instances de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ou sélectionner des instances spécifiques.

 Le tableau suivant répertorie les compteurs inclus dans l'objet de performance `MSRS 2014 Windows Service`.

|Compteur|Description|
|-------------|-----------------|
|`Active Sessions`|Nombre de sessions actives stockées dans la base de données du serveur de rapports. Ce compteur fournit un nombre cumulatif de toutes les sessions de navigateur utilisables générées à partir d'abonnements à un rapport, qu'elles soient encore actives ou non.|
|`Cache Flushes/Sec`|Nombre de vidages du cache par seconde.|
|`Cache Hits/Sec`|Nombre de requêtes par seconde pour les rapports mis en cache. Les demandes sont relatives aux rapports qui font l'objet d'un nouveau rendu ; il ne s'agit pas de demandes concernant les rapports traités directement à partir du cache. (Consultez `Total Cache Hits` plus loin dans cette rubrique.)|
|`Cache Hits/Sec (Semantic Models)`|Nombre de requêtes par seconde pour les modèles mis en cache.|
|`Cache Misses/Sec`|Nombre de requêtes par seconde qui n'ont pas retourné un rapport à partir du cache. Utilisez ce compteur afin de déterminer si les ressources utilisées pour la mise en cache (disque ou mémoire) sont suffisantes.|
|`Cache Misses/Sec (Semantic Models)`|Nombre de requêtes par seconde qui n'ont pas retourné de modèle à partir du cache. Utilisez ce compteur afin de déterminer si les ressources utilisées pour la mise en cache (disque ou mémoire) sont suffisantes.|
|`Delivers/Sec`|Nombre de remises de rapport par seconde, de toute extension de remise.|
|`Events/Sec`|Nombre d'événements traités par seconde. Les événements contrôlés incluent `SnapshotUpdated` et `TimedSubscription`.|
|`First Session Requests/Sec`|Nombre de nouvelles sessions d'exécution de rapport crées par seconde.|
|`Memory Cache Hits/Sec`|Nombre de fois par seconde où les rapports sont récupérés du cache mémoire. Le*cache interne* fait partie de la mémoire cache qui stocke les rapports dans la mémoire de l’unité centrale. Quand le cache mémoire est utilisé, le serveur de rapports n’interroge pas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le contenu mis en cache.|
|`Memory Cache Misses/Sec`|Nombre de fois par seconde où les rapports ne peuvent pas être récupérés du cache mémoire.|
|`Next Session Requests/Sec`|Nombre de requêtes par seconde pour les rapports qui sont ouverts dans une session existante (tels que les rapports rendus à partir d'un instantané de session).|
|`Report Requests`|Nombre de rapports qui sont actuellement actifs et gérés par le serveur de rapports. Utilisez ce compteur pour évaluer la stratégie de mise en cache. Il peut exister beaucoup plus de requêtes que de rapports générés.|
|`Reports Executed/Sec`|Nombre de rapports correctement générés par seconde.|
|`Requests/Sec`|Nombre total des demandes réussies que le service du serveur de rapports a traitées par seconde.|
|`Snapshot Updates/Sec`|Nombre total de mises à jour d'instantanés d'exécution de rapport par seconde.|
|`Total App Domain Recycles`|Nombre total de cycles de domaine d'application après le démarrage du service Windows Report Server.|
|**Total des vidages du cache**|Nombre total de mises à jour du cache du serveur de rapports après le démarrage du service. Ce compteur est remis à zéro lorsque le domaine d'application se recycle. Consultez `Cache Flushes/Sec`.|
|`Total Cache Hits`|Nombre total de requêtes pour les rapports traités directement à partir du cache après le démarrage du service Windows Report Server. Ce compteur est remis à zéro lorsque le domaine d'application se recycle. Consultez `Cache Hits/Sec`.|
|`Total Cache Hits (Semantic Models)`|Nombre total de requêtes pour les modèles traités directement à partir du cache après le démarrage du service Windows Report Server. Ce compteur est remis à zéro lorsque le domaine d'application se recycle. Consultez `Cache Hits/Sec`.|
|`Total Cache Misses`|Nombre total d'échecs de retour d'un rapport à partir du cache après le démarrage du service Windows Report Server. Ce compteur est remis à zéro lorsque le domaine d'application se recycle. Consultez `Cache Misses/Sec`.|
|`Total Cache Misses (Semantic Models)`|Nombre total d'échecs de retour d'un modèle à partir du cache après le démarrage du service Windows Report Server. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Deliveries`|Nombre total de rapports remis via le processeur de planification et de livraison, pour toutes les extensions de remise. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Events`|Nombre total d'événements après le démarrage du service Windows du serveur de rapports. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Memory Cache Hits`|Nombre total de rapports mis en cache retournés par le cache interne après le démarrage du service Windows du serveur du rapports. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Memory Cache Misses`|Nombre total d'absences dans le cache mémoire après le démarrage du service. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Processing Failures`|Nombre d'erreurs de traitement des demandes dans le service Windows du serveur de rapports.|
|`Total Rejected Threads`|Nombre total de threads rejetés pour le traitement asynchrone, puis gérés comme processus synchrone dans le même thread. En cas de charge modérée ou élevée, ce compteur augmente régulièrement.|
|`Total Reports Executed`|Nombre total de rapports exécutés.|
|`Total Requests`|Nombre total de rapports qui ont été correctement exécutés après le démarrage du service. Ce compteur est remis à zéro lorsque le domaine d'application se recycle.|
|`Total Snapshot Updates`|Nombre total de mises à jour d'instantanés d'exécution de rapport.|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a>Utiliser des applets de commande PowerShell pour retourner des listes
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")Le script Windows PowerShell suivant retourne les ensembles de compteurs dans lesquels CounterSetName commence par « msr » :

```powershell
Get-Counter -ListSet msr*
```

 Le script Windows PowerShell suivant retourne la liste des compteurs de performance de CounterSetName.

```powershell
(Get-Counter -ListSet "MSRS 2014 Windows Service").Paths
```

## <a name="see-also"></a>Voir aussi
 [Analyse](monitoring-report-server-performance.md) [des compteurs de performance des performances du serveur de rapports pour le service Web MSRS 2014 en mode SharePoint et le service Windows MSRS 2014 objets de performance en mode SharePoint &#40;le mode SharePoint&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [les compteurs de performance pour les objets de performance ReportServer : service et ReportServerSharePoint : service](performance-counters-reportserver-service-performance-objects.md)
