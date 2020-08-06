---
title: Relire un fichier de trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 9e361275-c8fd-4499-8389-242cf8e27415
author: stevestein
ms.author: sstein
ms.openlocfilehash: d3a9f007b9b6d2b46be43abdb10db286a75c33fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705739"
---
# <a name="replay-a-trace-file-sql-server-profiler"></a>Relire un fichier de trace (SQL Server Profiler)
  La relecture est la possibilité d'ouvrir une trace enregistrée et de la relire. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contient un moteur de lecture à plusieurs threads capable de simuler les connexions utilisateur et l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La relecture est utile pour résoudre les problèmes d'applications ou de processus. Lorsque vous identifiez le problème et appliquez des corrections, exécutez la trace qui a détecté le problème potentiel sur l'application ou le processus corrigé. Relisez ensuite la trace d'origine et comparez les résultats.  
  
 En plus des autres classes d'événements que vous voulez analyser, des classes d'événements spécifiques doivent être capturées pour permettre la relecture. Ces événements sont capturés par défaut si vous utilisez le modèle de trace **TSQL_Replay** . Pour plus d’informations, consultez [Conditions préalables à la relecture](replay-requirements.md).  
  
### <a name="to-replay-a-trace-file"></a>Pour relire un fichier de trace  
  
1.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier de trace**. Sélectionnez un fichier de trace qui contient les classes d'événements indispensables pour la relecture.  
  
2.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous à l’instance de serveur sur laquelle vous voulez relire la trace.  
  
3.  Dans la boîte de dialogue **Configuration de la relecture** , sous l’onglet **Options de relecture de base** , spécifiez le **Serveur de relecture**. Cliquez sur **Modifier** pour changer le serveur affiché dans la zone **Serveur de relecture** .  
  
4.  Si vous le souhaitez, sélectionnez l'une des destinations suivantes afin d'y enregistrer la relecture :  
  
    -   **Enregistrer dans le fichier**: spécifie un fichier dans lequel la relecture sera enregistrée.  
  
    -   **Enregistrer dans la table**: spécifie une table de la base de données dans laquelle la relecture sera enregistrée.  
  
5.  Choisissez **Relire les événements selon leur ordre de suivi**ou **Relire les événements en utilisant plusieurs threads**. Le tableau suivant explique la différence entre ces paramètres.  
  
    |Option|Description|  
    |------------|-----------------|  
    |**Relire les événements selon leur ordre de suivi**|Permet de relire les événements selon l'ordre dans lequel ils ont été enregistrés. Cette option active le débogage.|  
    |**Relire les événements en utilisant plusieurs threads**|Cette option utilise plusieurs threads pour relire chaque événement indépendamment de la séquence. Cette option optimise les performances.|  
  
6.  Sélectionnez **Afficher les résultats de relecture** pour consulter la relecture lorsqu’elle a lieu.  
  
7.  Si vous le souhaitez, cliquez sur l’onglet **Options de relecture avancées**pour configurer les options suivantes :  
  
    -   Pour relire tous les ID de processus de serveur (SPID), sélectionnez **Relire les SPID système**.  
  
    -   Pour limiter la relecture aux processus appartenant à un SPID spécifique, sélectionnez **Relire un SPID uniquement**. Dans la zone **SPID à relire** , tapez le SPID.  
  
    -   Pour relire les événements qui se sont produits durant une période spécifique, sélectionnez **Limiter la relecture par date et heure**. Sélectionnez une date et une heure pour **Heure de début**et **Heure de fin**afin de spécifier la période à inclure dans la relecture.  
  
    -   Pour déterminer la manière dont SQL Server gèrera les processus durant la relecture, configurez les **Options du moniteur d’intégrité**.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations nécessaires pour exécuter SQL Server Profiler](sql-server-profiler.md)   
 [Relire des traces](replay-traces.md)   
 [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
