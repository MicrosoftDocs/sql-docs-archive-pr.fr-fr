---
title: Feature Pack Azure | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696015"
---
# <a name="azure-feature-pack"></a>Feature Pack Azure
Le Feature Pack SQL Server Integration Services (SSIS) pour Azure est une extension qui fournit les composants répertoriés dans cette page afin de permettre à SSIS de se connecter aux services Azure, de transférer des données entre des sources de données Azure et locales, et de traiter des données stockées dans Azure.

## <a name="components-in-the-feature-pack"></a>Composants du Feature Pack
  
-   Gestionnaires de connexions  
  
    -   [Gestionnaire de connexions Stockage Azure](connection-manager/azure-storage-connection-manager.md)  
  
    -   [Gestionnaire de connexions d’abonnement Azure](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [Gestionnaire de connexions Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [Gestionnaire de connexions Azure Resource Manager](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [Gestionnaire de connexions Azure HDInsight](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   Tâches  
  
    -   [Tâche de chargement d’objets blob Azure](control-flow/azure-blob-upload-task.md)  
  
    -   [Tâche de téléchargement d’objets blob Azure](control-flow/azure-blob-download-task.md)  
  
    -   [Tâche Hive d’Azure HDInsight](control-flow/azure-hdinsight-hive-task.md)  
  
    -   [Tâche Pig Azure HDInsight](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)
  
    -   [Tâche de création d’un cluster Azure HDInsight](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [Tâche de suppression d’un cluster Azure HDInsight](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Tâche de chargement Azure SQL Data Warehouse](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [Tâche du système de fichiers Azure Data Lake Store](control-flow/file-system-task.md)    
  
-   Composants de flux de données  
  
    -   [Source des objets blob Azure](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)  
  
    -   [Destination des objets blob Azure](data-flow/azure-blob-destination.md)  
    
    -   [Source Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [Destination Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   Énumérateur d’objets BLOB Azure & énumérateur de fichier ADLS. Consultez [conteneur de boucles Foreach](control-flow/foreach-loop-container.md).  
  
 
## <a name="download-the-feature-pack"></a>Télécharger le Feature Pack  
Téléchargez le Feature Pack SQL Server Integration Services (SSIS) pour Azure.  
  
-   [Feature Pack Microsoft SQL Server 2014 Integration Services pour Azure](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a>Prérequis  
Avant d’installer le Feature Pack, vous devez vérifier que les conditions préalables suivantes sont remplies.  
  
-   SQL Server Integration Services  
-   .Net Framework 4.5  
  
## <a name="scenarios"></a>Scénarios  
  
### <a name="big-data-processing"></a>Traitement de données volumineuses  
 Utilisez le connecteur Azure pour accomplir le travail suivant de traitement de données volumineuses :  
  
1.  Utilisez la tâche de téléchargement d'objet blob Azure pour charger des données d'entrée dans le stockage d'objets blob Azure.  
  
2.  Utilisez la tâche de création de cluster Azure HDInsight pour créer un cluster Azure HDInsight. Cette étape est facultative si vous souhaitez utiliser votre propre cluster.  
  
3.  Utilisez la tâche Hive ou Pig Azure HDInsight pour invoquer un travail Pig ou Hive sur le cluster Azure HDInsight.  
  
4.  Utilisez la tâche de suppression de cluster Azure HDInsight pour supprimer le cluster HDInsight après utilisation, si vous avez créé un cluster HDInsight à la demande à l'étape 2.  
  
5.  Utilisez la tâche de téléchargement d'objet blob Azure HDInsight pour télécharger les données de sortie des travaux Pig/Hive à partir du stockage d'objets blob Azure.  
  
 ![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")  
  
### <a name="cloud-data-archiving"></a>Archivage de données de cloud  
 Utilisez la destination d'objets blob Azure dans un package SSIS pour écrire des données de sortie dans un stockage d'objets blob Azure, ou la source d'objets blob Azure pour lire des données à partir d'un stockage d'objets blob Azure.  
  
 ![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")  
  
 ![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")  
  
 Et utilisez le conteneur de boucles Foreach avec l'énumérateur d'objet blob Azure pour traiter des données dans plusieurs fichiers bob.  
  
 ![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")  
  
  
