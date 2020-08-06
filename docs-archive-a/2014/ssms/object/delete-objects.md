---
title: Supprimer les objets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599768"
---
# <a name="delete-objects"></a>Supprimer les objets
  Cette boîte de dialogue vous permet de supprimer une base de données ou un objet de base de données.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
 **Objet à supprimer**  
 Indique les noms, les types, les propriétaires et l'état des objets qui seront supprimés, ainsi que tous les messages sur les erreurs au cours de l'exécution.  
  
> [!NOTE]  
>  Exécuter **Supprimer** sur une base de données équivaut à exécuter DROP DATABASE dans [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Afficher les dépendances**  
 Cliquez ici pour afficher à la fois les objets qui dépendent de l'objet actuellement sélectionné et les objets dont dépend l'objet actuel (dépendance ascendante et descendante). Les informations affichées dans la boîte de dialogue **Afficher les dépendances** sont en lecture seule.  
  
> [!NOTE]  
>  Le bouton **Afficher les dépendances** n'est pas affiché pour tous les types d'objets de base de données. Pour afficher les dépendances quand le bouton **Afficher les dépendances** n’est pas disponible, cliquez avec le bouton droit sur l’objet dans l’Explorateur d’objets, puis cliquez sur **Afficher les dépendances**.  
  
 **Supprimer les informations d'historique de sauvegarde et de restauration pour les bases de données**  
 Cette case à cocher apparaît seulement quand une base de données est supprimée et elle permet de supprimer l’historique de sauvegarde et de restauration pour la base de données d’objet dans la base de données **msdb** .  
  
 **Fermer les connexions existantes**  
 Cette case à cocher apparaît seulement lorsqu'une base de données est supprimée et elle permet de mettre fin aux connexions à la base de données d'objet.  
  
  
