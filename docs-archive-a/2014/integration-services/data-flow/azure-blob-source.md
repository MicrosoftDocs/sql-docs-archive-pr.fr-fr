---
title: Source des objets blob Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobsrc.f1
- sql11.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a14c7022437c8a23f898a0f29c211bd9ae82aa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613580"
---
# <a name="azure-blob-source"></a>Azure Blob Source
 Le composant **Azure Blob Source** permet à un package SSIS de lire les données provenant d’un blob Azure. Les formats de fichier pris en charge sont CSV et AVRO. Pour afficher l’éditeur d’Azure Bloc Source, faites glisser **Azure Blob Source** sur le concepteur de flux de données et double-cliquez dessus pour ouvrir l’éditeur.  
  
1.  Dans le champ **Gestionnaire de connexions du Stockage Azure**, spécifiez un gestionnaire de connexions du Stockage Azure existant ou créez-en un qui fera référence à un compte de Stockage Azure.  
  
2.  Dans le champ **Nom du conteneur d’objets blob** , spécifiez le nom du conteneur d’objets blob qui contient les fichiers sources.  
  
3.  Dans le champ **Nom de l’objet blob** , indiquez le chemin d’accès à l’objet blob.  
  
4.  Dans le champ **Format de fichier d’objet blob** , spécifiez le format d’objet blob à utiliser.  
  
5.  Si le format de fichier est CSV, vous devez renseigner le champ **Caractère séparateur de colonnes** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  
  
6.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  
  
  
