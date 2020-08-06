---
title: Paramètres de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704679"
---
# <a name="sql-server-parameters"></a>Paramètres du serveur SQL Server
  Dans cette page, définissez les paramètres que l’analyseur utilisera pour l' [!INCLUDE[ssDE](../../includes/ssde-md.md)] analyse.  ous pouvez analyser une, plusieurs ou toutes les bases de données, des fichiers de trace créés à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et des fichiers de commandes SQL.  
  
> [!NOTE]  
>  Certains problèmes de mise à niveau ne peuvent être détectés que si vous faites analyser des fichiers de trace ou des fichiers de commandes SQL.  
  
## <a name="options"></a>Options  
 **Base(s) de données à analyser**  
 Pour analyser toutes les bases de données, activez la case à cocher **toutes les bases de données** . Pour analyser une sélection de bases de données, activez la case à cocher située en regard de chaque base de données à inclure dans l'analyse.  
  
 **Analyser les fichiers de trace**  
 Activez cette case à cocher pour analyser les fichiers de trace du système de fichiers.  
  
 **Che. d'accès aux fich. de trace**  
 Vous pouvez analyser un ou plusieurs fichiers. Vous pouvez accéder à un emplacement et sélectionner plusieurs fichiers, ou vous pouvez fournir plusieurs noms de fichiers. Utilisez le chemin d'accès complet à chaque fichier, incluez le nom de fichier et séparez les entrées à l'aide de la barre verticale (|).  
  
 Si vous activez **analyser les fichiers de trace**, l' **étape suivante** est désactivée jusqu’à ce que vous entriez un nom de chemin d’accès et un nom de fichier.  
  
 **Analyser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les fichiers de commandes**  
 Activez cette case à cocher pour analyser les fichiers de commandes [!INCLUDE[tsql](../../includes/tsql-md.md)] du système de fichiers.  
  
 **Chemin d’accès au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x) fichier (s) batch**  
 Vous pouvez analyser un ou plusieurs fichiers de commandes. Vous pouvez accéder à un emplacement et sélectionner plusieurs fichiers, ou vous pouvez taper plusieurs noms de fichiers. Utilisez le chemin d'accès complet à chaque fichier, incluez le nom de fichier et séparez les entrées à l'aide de la barre verticale (|).  
  
 Si vous activez **analyser les fichiers de commandes SQL**, le bouton **suivant** est désactivé jusqu’à ce que vous entriez un nom de chemin d’accès et un nom de fichier.  
  
 **Délimiteur de lot SQL**  
 Texte utilisé pour séparer des lots d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. La valeur par défaut est **Go**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Guide de référence de l'interface utilisateur du Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
