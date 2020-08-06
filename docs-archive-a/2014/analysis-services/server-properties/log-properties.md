---
title: Propriétés du journal | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3761ce3dca232db8968a2a7cba083dcc5554d792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710847"
---
# <a name="log-properties"></a>Propriétés du journal
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur de journal répertoriées dans les tableaux suivants. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
## <a name="general"></a>Général  
 `File`  
 Propriété de type chaîne qui spécifie le nom du fichier journal du serveur. Cette propriété s'applique uniquement si vous utilisez un fichier sur disque pour l'enregistrement, au lieu d'une table de base de données (comportement par défaut).  
  
 La valeur par défaut de cette propriété est msmdsrv.log.  
  
 `FileBufferSize`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MessageLogs`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="error-log"></a>Journal des erreurs de SQL Server  
 Vous pouvez définir ces propriétés au niveau de l'instance du serveur pour modifier les valeurs par défaut de la configuration d'erreur qui s'affichent dans d'autres outils et concepteurs. Pour plus d’informations [, consultez Configuration d’erreur pour le traitement des cubes, des partitions et des dimensions &#40;SSAS-multidimensionnel&#41;](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> .  
  
 **ErrorLog\ErrorLogFileName**  
 Propriété utilisée comme valeur par défaut durant une opération de traitement effectuée par le serveur.  
  
 **ErrorLog\ErrorLogFileSize**  
 Propriété utilisée comme valeur par défaut durant une opération de traitement effectuée par le serveur.  
  
 **ErrorLog\KeyErrorAction**  
 Spécifie l'action que doit entreprendre le serveur en cas d'erreur `KeyNotFound`. Les réponses valides à cette erreur sont :  
  
-   `ConvertToUnknown` indique au serveur d'allouer la valeur de clé d'erreur au membre inconnu.  
  
-   `DiscardRecord` indique au serveur d'exclure l'enregistrement.  
  
 **ErrorLog\KeyErrorLogFile**  
 Il s'agit d'un nom de fichier défini par l'utilisateur qui doit avoir une extension de fichier .log, situé dans un dossier sur lequel le compte de services dispose des autorisations d'accès en lecture/écriture. Ce fichier journal contient uniquement les erreurs générées lors du traitement. Utilisez la Boîte noire si vous avez besoin de plus d'informations.  
  
 **ErrorLog\KeyErrorLimit**  
 Il s'agit du nombre maximal d'erreurs d'intégrité des données que le serveur autorise avant que le traitement échoue. Une valeur égale à -1 indique un nombre illimité. La valeur par défaut est 0, ce qui signifie que le traitement s'arrête après la première erreur. Vous pouvez également définir un nombre entier.  
  
 **ErrorLog\KeyErrorLimitAction**  
 Spécifie l'action entreprise par le serveur lorsque le nombre maximal d'erreurs de clé est atteint. Les réponses valides à cette action sont :  
  
-   `StopProcessing` indique au serveur d'arrêter le traitement lorsque le nombre maximal d'erreurs est atteint.  
  
-   `StopLogging` indique au serveur d'arrêter l'enregistrement des erreurs lorsque le nombre maximal d'erreurs est atteint, mais d'autoriser la poursuite du traitement.  
  
 **ErrorLog\ LogErrorTypes\KeyNotFound**  
 Spécifie l'action que doit entreprendre le serveur en cas d'erreur `KeyNotFound`. Les réponses valides à cette erreur sont :  
  
-   `IgnoreError` indique au serveur de poursuivre le traitement sans enregistrer l'erreur ou la compter dans le nombre maximal d'erreurs de clé. Lorsque vous ignorez l'erreur, vous permettez au traitement de continuer sans ajouter l'erreur au nombre d'erreurs ou l'enregistrer à l'écran ou dans le fichier journal. L'enregistrement en question rencontre un problème d'intégrité des données et ne peut pas être ajouté à la base de données. L'enregistrement est ignoré ou agrégé à un membre inconnu, tel que le détermine la propriété `KeyErrorAction`.  
  
-   `ReportAndContinue` indique au serveur d'enregistrer l'erreur, de la compter dans le nombre maximal d'erreurs de clé et de continuer le traitement. L'enregistrement déclenchant l'erreur est ignoré ou converti en membre inconnu.  
  
-   `ReportAndStop` indique au serveur d'enregistrer l'erreur et d'arrêter le traitement immédiatement, quel que soit le nombre maximal d'erreurs de clé. L'enregistrement déclenchant l'erreur est ignoré ou converti en membre inconnu.  
  
 **ErrorLog\ LogErrorTypes\KeyDuplicate**  
 Spécifie l'action entreprise par le serveur lorsqu'une clé dupliquée est détectée. Les valeurs valides sont `IgnoreError` pour continuer le traitement comme si l'erreur ne s'était pas produite, `ReportAndContinue` pour enregistrer l'erreur et continuer le traitement et `ReportAndStop` pour enregistrer l'erreur et arrêter le traitement immédiatement, même si le nombre d'erreurs est inférieur au nombre maximal.  
  
 **ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**  
 Spécifie l'action entreprise par le serveur lorsqu'une clé NULL a été convertie en membre inconnu. Les valeurs valides sont `IgnoreError` pour continuer le traitement comme si l'erreur ne s'était pas produite, `ReportAndContinue` pour enregistrer l'erreur et continuer le traitement et `ReportAndStop` pour enregistrer l'erreur et arrêter le traitement immédiatement, même si le nombre d'erreurs est inférieur au nombre maximal.  
  
 **ErrorLog\ LogErrorTypes\NullKeyNotAllowed**  
 Spécifie l'action entreprise par le serveur lorsque `NullProcessing` a la valeur `Error` pour un attribut de dimension. Une erreur est générée lorsqu'une valeur NULL n'est pas autorisée dans un attribut donné. Cette propriété de configuration d'erreur informe l'étape suivante, qui consiste à créer un rapport d'erreurs et poursuivre le traitement tant que le nombre maximal d'erreurs n'est pas atteint. Les valeurs valides sont `IgnoreError` pour continuer le traitement comme si l'erreur ne s'était pas produite, `ReportAndContinue` pour enregistrer l'erreur et continuer le traitement et `ReportAndStop` pour enregistrer l'erreur et arrêter le traitement immédiatement, même si le nombre d'erreurs est inférieur au nombre maximal.  
  
 **ErrorLog\ LogErrorTypes\CalculationError**  
 Propriété utilisée comme valeur par défaut durant une opération de traitement effectuée par le serveur.  
  
 **ErrorLog\IgnoreDataTruncation**  
 Propriété utilisée comme valeur par défaut durant une opération de traitement effectuée par le serveur.  
  
## <a name="exception"></a>Exception  
 **Exception\CreateAndSendCrashReports**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\CrashReportsFolder**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\SQLDumperFlagsOn**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\SQLDumperFlagsOff**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\MiniDumpFlagsOn**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\MinidumpErrorList**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="flight-recorder"></a>Boîte noire SQL  
 **FlightRecorder\Enabled**  
 Propriété booléenne qui indique si la fonctionnalité de boîte noire SQL est activée.  
  
 **FlightRecorder\FileSizeMB**  
 Propriété dont la valeur est un entier 32 bits signé qui définit la taille du fichier sur disque de la boîte noire SQL, exprimée en mégaoctets.  
  
 **FlightRecorder\LogDurationSec**  
 Propriété dont la valeur est un entier 32 bits signé qui définit la fréquence en secondes selon laquelle l'enregistrement reprend au début dans la boîte noire SQL.  
  
 **FlightRecorder\SnapshotDefinitionFile**  
 Propriété de type chaîne qui spécifie le nom du fichier de définition d'instantané, qui contient les commandes de découverte envoyées au serveur lorsqu'un instantané est réalisé.  
  
 La valeur par défaut de cette propriété est vide, ce qui correspond au nom de fichier par défaut FlightRecorderSnapshotDef.txt.  
  
 **FlightRecorder\SnapshotFrequencySec**  
 Propriété dont la valeur est un entier 32 bits signé qui définit la fréquence en secondes des instantanés.  
  
 **FlightRecorder\TraceDefinitionFile**  
 Propriété de type chaîne qui spécifie le nom du fichier de définition de trace de la boîte noire SQL.  
  
 La valeur par défaut de cette propriété est vide, ce qui correspond au nom de fichier par défaut FlightRecorderTraceDef.txt.  
  
## <a name="query-log"></a>Journal des requêtes  
 **S’applique à :** Mode serveur multidimensionnel uniquement  
  
 **QueryLog\QueryLogFileName**  
 Propriété de type chaîne qui spécifie le nom du fichier journal des requêtes. Cette propriété s'applique uniquement si vous utilisez un fichier sur disque pour l'enregistrement, au lieu d'une table de base de données (comportement par défaut).  
  
 **QueryLog\QueryLogSampling**  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie le taux d'échantillonnage du journal des requêtes.  
  
 La valeur par défaut de cette propriété, 10, signifie qu'une requête sur 10 est enregistrée.  
  
 **QueryLog\QueryLogFileSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **QueryLog\QueryLogConnectionString**  
 Propriété de type chaîne qui spécifie la connexion à la base de données du journal des requêtes.  
  
 **QueryLog\QueryLogTableName**  
 Propriété de type chaîne qui spécifie le nom de la table du journal des requêtes.  
  
 La valeur par défaut de cette propriété est OlapQueryLog.  
  
 **QueryLog\CreateQueryLogTable**  
 Propriété booléenne qui spécifie si la table du journal des requêtes doit être créée.  
  
 La valeur par défaut de cette propriété, False, indique que ne serveur ne crée pas automatiquement la table du journal et n'enregistre pas d'événements de requête.  
  
> [!NOTE]  
>  Pour plus d’informations sur la configuration du journal des requêtes, consultez [opérations de journalisation dans Analysis Services](../instances/log-operations-in-analysis-services.md).  
  
## <a name="trace"></a>Trace  
 **Trace\TraceBackgroundDistributionPeriod**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceBackgroundFlushPeriod**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceFileBufferSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceFileWriteTrailerPeriod**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceMaxRowsetSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceProtocolTraffic**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceQueryResponseTextChunkSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceReportFQDN**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceRequestParameters**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceRowsetBackgroundFlushPeriod**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
