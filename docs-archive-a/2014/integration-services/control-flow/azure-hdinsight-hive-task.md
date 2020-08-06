---
title: Hive Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afphivetask.f1
- sql11.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5905dee4a7a195a16d217b28b59cc10bb74dd9a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613086"
---
# <a name="azure-hdinsight-hive-task"></a>Tâche Hive Azure HDInsight
Utilisez la **tâche Hive Azure HDInsight** pour exécuter un script Hive sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Hive Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Hive Azure HDInsight** .  
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Dans le champ **HDInsightConnection**, sélectionnez un gestionnaire de connexions Azure HDInsight existant ou créez-en un qui fait référence au cluster Azure HDInsight utilisé pour exécuter le script.
  
2.  Dans le champ **AzureStorageConnection**, sélectionnez un gestionnaire de connexions Stockage Azure existant ou créez-en un qui fait référence au compte Stockage Azure associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
 
3.  Dans le champ **BlobContainer**, spécifiez le nom du conteneur de stockage associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
  
4.  Dans le champ **LocalLogFolder**, spécifiez le dossier dans lequel seront téléchargés les journaux de sortie d’exécution de script et les journaux d’erreurs. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.   
  
5.  Deux méthodes permettent de spécifier le script Hive à exécuter :
  
    1.  **Script en ligne** : renseignez le champ **Script** en tapant en ligne le script à exécuter dans la boîte de dialogue **Entrer le script**.
  
    2.  **Fichier de script** : téléchargez le fichier de script dans Stockage Blob Azure et renseignez le champ **BlobName**. Si l’objet blob ne se trouve pas dans le compte ou le conteneur de stockage par défaut associé au cluster HDInsight, vous devez renseigner les champs **ExternalStorageAccountName** et **ExternalBlobContainer**. Dans le cas d’un objet blob externe, assurez-vous qu’il est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script est utilisé et le script en ligne est ignoré.
