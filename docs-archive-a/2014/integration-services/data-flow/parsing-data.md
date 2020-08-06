---
title: Analyse de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bd34cd83351e31313ae96ff5709ec999a60f2f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602926"
---
# <a name="parsing-data"></a>Analyse de données
  Les flux de données des packages extraient et chargent des données à partir de banques de données hétérogènes qui peuvent utiliser différents types de données standard et personnalisés. Dans un flux de données, les sources [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sont chargées d’extraire les données, d’analyser les données de type string et de les convertir en données de type [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Les transformations effectuées par la suite peuvent analyser les données afin de les convertir en un type distinct ou créer des copies de colonnes avec d'autres types de données. Les expressions utilisées dans les composants peuvent également convertir les arguments et opérandes en d'autres types de données. Enfin, lorsque les données sont chargées dans une banque de données, la destination peut analyser les données afin de les convertir en un type de données utilisé par la destination. Pour plus d’informations, consultez [Types de données Integration Services](integration-services-data-types.md).  
  
## <a name="types-of-parsing"></a>Types d'analyses  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose deux types d’analyses en vue de convertir les données : l’analyse rapide et l’analyse standard.  
  
-   L'analyse rapide est un ensemble de routines simple et rapide d'analyse des données. Elle ne prend pas en charge la conversion des données présentant des spécificités régionales et accepte uniquement les formats de date et d'heure les plus courants. Pour plus d’informations, consultez [Analyse rapide](../fast-parse.md).  
  
-   L'analyse standard est un ensemble complet de routines d'analyse qui prend en charge la conversion de tous les types de données fournis par les API de conversion de type de données Automation disponibles dans Oleaut32.dll et Ole2dsip.dll. Pour plus d’informations, consultez [Analyse standard](../standard-parse.md).  
  
  
