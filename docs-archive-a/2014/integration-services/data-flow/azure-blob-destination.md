---
title: Azure Blob Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb406d38b17748e8284acee4b2849a9fd99e53ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706612"
---
# <a name="azure-blob-destination"></a>Destination d’objet blob Azure
  Le composant **Destination d’objet blob Azure** permet à un package SSIS d’écrire des données dans un objet blob Azure. Les formats de fichier pris en charge sont CSV et AVRO. Ddrag-déposez la **destination d’objet BLOB Azure** dans le concepteur de workflow et double-cliquez dessus pour voir l’éditeur).  
  
1.  Dans le champ **Gestionnaire de connexions du Stockage Azure**, spécifiez un gestionnaire de connexions du Stockage Azure existant ou créez-en un qui fera référence à un compte de Stockage Azure.  
  
2.  Dans le champ **Nom du conteneur d’objets blob** , spécifiez le nom du conteneur d’objets blob qui contient les fichiers sources.  
  
3.  Dans le champ **Nom de l’objet blob** , indiquez le chemin d’accès à l’objet blob.  
  
4.  Dans le champ **Format de fichier d’objet blob** , spécifiez le format d’objet blob à utiliser.  
  
5.  Si le format de fichier est CSV, vous devez renseigner le champ **Caractère séparateur de colonnes** . Sélectionnez également les **noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonnes.  
  
6.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  
  
  
