---
title: Propriétés de la source OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8139f79ed595ca3e6204f96823f6bc95e6fb40df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708500"
---
# <a name="odata-source-properties"></a>Propriétés de la source OData
  Quand vous cliquez avec le bouton droit sur **Source OData** dans le flux de données, puis cliquez sur **Propriétés**, vous voyez les propriétés du composant **Source OData** dans la fenêtre **Propriétés** .  
  
|||  
|-|-|  
|Propriété|Description|  
|CollectionName|Nom de la collection que vous souhaitez à extraire du service OData. La propriété **CollectionName** est utilisée quand **UseResourcePath** a la valeur false.<br /><br /> Cette propriété utilise des expressions et permet de définir la valeur au moment de l'exécution. Cependant, si les métadonnées de la collection ne correspondent pas aux métadonnées utilisées au moment de la conception, une erreur de validation est générée, et l'exécution du flux de données échouera.|  
|DefaultStringLength|Cette valeur spécifie la longueur par défaut des colonnes de chaîne qui n'ont pas de longueur maximale.<br /><br /> **Valeur par défaut :** 4000|  
|Query|Paramètres de requête OData. Cette propriété utilise des expressions et peut être définie au moment de l'exécution.|  
|ResourcePath|Utilisez cette propriété lorsque vous devez spécifier un chemin d'accès de ressources complet, plutôt que sélectionner uniquement un nom de collection. Cette propriété est utilisée lorsque **UseResourcePath** a la valeur True.|  
|UseResourcePath|Lorsque la valeur est définie à True, la valeur **ResourcePath** est ajoutée à l'URL de base pour déterminer l'emplacement du flux OData. Lorsque la valeur est False, la valeur **CollectionName** est utilisée.<br /><br /> **Par défaut :** Fausses|  
  
  
