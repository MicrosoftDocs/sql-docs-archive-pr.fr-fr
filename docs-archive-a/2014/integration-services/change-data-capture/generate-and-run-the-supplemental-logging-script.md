---
title: Générer et exécuter le script de journalisation supplémentaire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695988"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Générer et exécuter le script de journalisation supplémentaire
  Utilisez la page Configurer des tables pour la capture des modifications pour exécuter un script sur la base de données source Oracle qui configure une journalisation supplémentaire.  
  
 **Pour exécuter les scripts de journalisation supplémentaire**  
  
 Cliquez sur **Exécuter le script** pour exécuter le script de journalisation supplémentaire sur les tables définies pour l'instance de capture de données modifiées. Ce script demande à la base de données Oracle d'écrire toutes les colonnes d'intérêt dans ses journaux des transactions lors de la journalisation des opérations de mise à jour (UPDATE) dans les tables capturées. Ce script est normalement examiné et exécuté par un administrateur système Oracle.  
  
 Vous pouvez également exécuter des scripts manuellement à l'aide de SQL*Plus.  
  
 **Pour exécuter les script manuellement**  
  
 Cliquez sur **Copier** pour coller le script dans le Presse-papiers. Ouvrez SQL*PLUS et accédez au répertoire contenant votre base de données source Oracle. Collez le script dans SQL\*Plus pour l’exécuter.  
  
 Pour enregistrer le script de journalisation supplémentaire dans un fichier texte, cliquez sur **Enregistrer sous** et accédez à l'emplacement où vous souhaitez enregistrer le fichier. Donnez un nom au fichier, puis cliquez sur **Enregistrer** pour enregistrer le fichier.  
  
 Cliquez sur **Suivant** pour [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](how-to-create-the-sql-server-change-database-instance.md)   
 [Examiner et générer des scripts de journalisation supplémentaires](review-and-generate-supplemental-logging-scripts.md)  
  
  
