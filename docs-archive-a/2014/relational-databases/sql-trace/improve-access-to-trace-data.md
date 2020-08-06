---
title: Améliorer l’accès aux données de trace | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e01ad04ddd9f7fe6d858c399abb552716f2bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697655"
---
# <a name="improve-access-to-trace-data"></a>Améliorer l'accès aux données de trace
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] utilise l’espace du répertoire **temp** pour améliorer l’accès aux données de trace. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] nécessite au moins 10 mégaoctets (Mo) d’espace libre. Si l’espace disponible descend en dessous de 10 Mo pendant que vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], toutes les fonctions de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] sont interrompues.  
  
 Quand [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] utilise l’espace du répertoire **temp** , cette utilisation d’espace peut entraîner la croissance rapide du répertoire **temp** . Pour éviter tout problème de croissance de fichier, vous pouvez placer le répertoire **temp** sur un lecteur non système en modifiant la valeur de la variable d’environnement TEMP.  
  
 La procédure ci-dessous décrit comment modifier la valeur de la variable d'environnement TEMP dans la plupart des systèmes d'exploitation Microsoft Windows. Pour plus d'informations sur la définition des variables d'environnement, consultez la documentation de votre système d'exploitation Windows.  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a>Pour modifier la variable d'environnement TEMP dans les systèmes d'exploitation Windows  
  
1.  Dans le menu **Démarrer** , choisissez **Panneau de configuration**, puis cliquez sur **Système**.  
  
2.  Dans la boîte de dialogue **Propriétés système** , cliquez sur l’onglet **Avancé** , puis sur **Variables d’environnement**.  
  
3.  Faites défiler la liste **Variables système**, sélectionnez la ligne qui correspond à la variable **TEMP** , puis cliquez sur **Modifier**.  
  
4.  Dans la boîte de dialogue **Modifier la variable système** , entrez le nom et le chemin du lecteur sur lequel vous voulez placer le répertoire **temp** .  
  
5.  Cliquez sur **OK** pour enregistrer la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
