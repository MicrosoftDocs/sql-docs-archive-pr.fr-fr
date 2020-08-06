---
title: Sélectionner des tables et des vues (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 891da51478670122f5dbce8fdd7be55c98c898c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706835"
---
# <a name="select-tables-and-views-ssas"></a>Sélectionner des tables et des vues (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de sélectionner les tables et les vues à partir desquelles vous voulez importer des données. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 L'apparence des tables et des vues dans cette page ne garantit pas que l'importation réussira. Si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée, l'importation échouera.  
  
 Pour les sources de données qui utilisent l'Authentification Windows, les informations d'identification de l'utilisateur actuel sont utilisées pour extraire les tables et les vues dans la boîte de dialogue Sélectionner des tables et des vues. Pour d'autres sources de données, les informations d'identification fournies dans la chaîne de connexion sont utilisées pour extraire les données.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
 **Serveur**  
 Affiche le serveur auquel vous êtes connecté.  
  
 **Sauvegarde de la base de données**  
 Affiche la base de données que vous avez sélectionnée.  
  
 **Tables et vues**  
 Répertorie les tables et vues contenues dans la base de données. Activez la case à cocher en regard de chaque table et vue que vous souhaitez importer.  
  
 **Table source**  
 Spécifie le nom de la table source en fonction du type de source de données.  
  
 **Schéma**  
 Spécifie le schéma contenant la table source. Selon le type de base de données, un schéma fonctionne comme un conteneur pour d'autres objets, tels que des tables, et peut également indiquer la propriété de ces objets.  
  
 **Nom convivial**  
 Spécifie le nom convivial de la table source. Par défaut, la colonne affiche le nom de la table source qui apparaît dans la colonne **Table source** . Modifiez le nom si vous souhaitez utiliser un nom différent de celui utilisé dans la base de données source.  
  
 **Détails du filtre**  
 Quand un filtre a été appliqué aux données importées, affiche le filtre d’importation de données dans la boîte de dialogue **Détails du filtre**. Pour plus d’informations, consultez [Détails du filtre &#40;SSAS&#41;](filter-details-ssas.md).  
  
 **Afficher un aperçu et filtrer**  
 Affiche la boîte de dialogue **Aperçu de la table sélectionnée** qui permet d’appliquer un filtre aux données importées. Pour plus d’informations, consultez [Aperçu de la table sélectionnée &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Sélectionner les tables associées**  
 Sélectionne pour l'importation les tables et les vues associées aux tables et aux vues que vous avez déjà sélectionnées.  
  
  
