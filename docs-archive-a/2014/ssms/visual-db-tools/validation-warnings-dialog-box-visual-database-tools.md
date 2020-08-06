---
title: Avertissements de validation, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f94c3ae91e077af853db949847bc8448f6a4753
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610918"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a>Avertissements de validation, boîte de dialogue (Visual Database Tools)
  Cette boîte de dialogue apparaît si vous tentez d'enregistrer des modifications ayant des effets secondaires potentiellement préjudiciables, ou si l'opération de validation de la base de données risque d'échouer. Cette boîte de dialogue indique quels pourraient être ces effets secondaires ou la raison pour laquelle l'opération de validation pourrait échouer. Elle vous donne la possibilité de continuer la modification ou d'annuler l'opération.  
  
> [!NOTE]  
>  Cette boîte de dialogue apparaît lorsque vous tentez de transmettre vos modifications à la base de données lors de l'enregistrement d'un script de modification.  
  
 La boîte de dialogue peut apparaître pour l'une de ces raisons :  
  
-   Il est possible que vous n'ayez pas les autorisations de la base de données pour valider toutes les modifications.  
  
-   Vos modifications auraient pour résultat des colonnes dérivées mal constituées, des contraintes DEFAULT ou CHECK.  
  
-   Une modification apportée à un type de donnée de la colonne peut provoquer une perte de données.  
  
-   Une modification aurait pour résultat un index supérieur à 900 octets.  
  
-   Une modification pourrait modifier une table ou une colonne contribuant à une vue liée à un schéma ou à une fonction définie par l'utilisateur.  
  
-   Une modification aurait pour résultat la recréation d'une table ayant un ou plusieurs déclencheurs chiffrés ; les déclencheurs seront supprimés.  
  
-   Vos modifications suspendront les paramètres remarquables de ANSI_NULLS ou ANSI_PADDING ou les deux pour les colonnes dans une table.  
  
## <a name="options"></a>Options  
 **Oui**  
 Continue l'opération et entraîne la génération du script de modification ou le transfert des modifications à la base de données. L'opération de validation peut encore échouer si vous n'avez pas les privilèges nécessaires pour modifier la base de données, ou si vos modifications ont pour résultat un index supérieur à 900 octets ou une colonne calculée, une contrainte DEFAULT ou une contrainte CHECK mal constituée.  
  
 **Non**  
 Annule la demande d'enregistrement.  
  
 **Enregistrer comme fichier texte**  
 Affiche la boîte de dialogue **Enregistrer sous** , où vous pouvez spécifier un emplacement pour un fichier texte contenant une liste des avertissements.  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir des tables &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
