---
title: Propriétés de l’objet table (colonne) (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.QueryViewColumn
ms.assetid: 212d9bcd-aded-4313-a6b9-d7e2270e5954
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2837851c50f770820eb5059e61f196890e2c23e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704595"
---
# <a name="table-valued-object-column-properties-visual-database-tools"></a>Propriétés de l’objet table (colonne) (Visual Database Tools)
  Ces propriétés s’affichent quand vous sélectionnez une colonne d’un objet table dans le volet **Diagramme** du Concepteur de requêtes et de vues.  
  
> [!NOTE]  
>  Les propriétés mentionnées dans cette rubrique sont classées par catégorie et non par ordre alphabétique.  
  
> [!NOTE]  
>  Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** .  
  
 **Catégorie Identité**  
 Développe pour afficher la propriété **Nom** .  
  
 **Nom**  
 Affiche le nom de la colonne sélectionnée.  
  
 **Catégorie Concepteur de requêtes**  
 Peut être développée pour afficher les propriétés de **Autoriser les valeurs NULL**, **Classement**, **Type de données**, **Longueur**, **Précision**, **Échelle**et **Taille**.  
  
 **Null autorisé**  
 Précise si le type de données de la colonne autorise les valeurs NULL.  
  
 **Classement**  
 Affiche le paramètre de classement pour la colonne sélectionnée. Le classement peut être défini dans l'onglet Propriétés de la colonne du Concepteur de tables.  
  
 **Type de données**  
 Affiche le type de données de la colonne sélectionnée.  
  
 **Longueur**  
 Affiche le nombre de caractères ou de chiffres autorisé par le type de données de la colonne sélectionnée. Cette propriété est disponible uniquement pour les types de données basés sur les caractères.  
  
> [!NOTE]  
>  Pour afficher la taille en octets, consultez la propriété **Taille** ci-dessous.  
  
 **Précision**  
 Affiche le nombre maximal de chiffres autorisés pour les types de données numériques. Cette propriété affiche **0** pour les types de données non numériques.  
  
 **Mettre à l'échelle**  
 Affiche le nombre maximal de chiffres qui peuvent apparaître à droite de la virgule décimale pour les types de données numériques. Cette valeur doit être inférieure ou égale à la précision. Cette propriété affiche **0** pour les types de données non numériques.  
  
 **Taille**  
 Affiche la taille en octets autorisée par le type de données de la colonne. Par exemple, un type de données nchar peut avoir une longueur de 10 (nombre de caractères), mais une taille de 20 pour tenir compte des jeux de caractères Unicode.  
  
  
