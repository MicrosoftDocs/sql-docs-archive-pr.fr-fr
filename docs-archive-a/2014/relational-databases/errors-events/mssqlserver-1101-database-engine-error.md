---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 631b0ab1466815cbacfd71b4f9fd714fabd0f7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612922"
---
# <a name="mssqlserver_1101"></a>MSSQLSERVER_1101
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1101|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NOALLOCPG|  
|Texte du message|Impossible d’allouer une nouvelle page pour la base de données ’%.*ls’ en raison d’un espace disque insuffisant dans le groupe de fichiers ’%.\*ls’. Créez l'espace nécessaire en supprimant des objets dans le groupe de fichiers, en ajoutant des fichiers supplémentaires au groupe de fichiers ou en définissant Autogrowth à ON pour les fichiers existants dans le groupe de fichiers.|  
  
## <a name="explanation"></a>Explication  
 Il n’y a pas d’espace disque disponible dans un groupe de fichiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Les actions ci-dessous peuvent éventuellement créer de l'espace disponible dans le groupe de fichiers.  
  
-   Activez la croissance automatique.  
  
-   Ajoutez d'autres fichiers au groupe de fichiers.  
  
-   Libérez de l'espace disque en supprimant les index ou les tables inutiles dans le groupe de fichiers.  
  
  
