---
title: optimize for ad hoc workloads (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b217e48d6e4b0ffa0f687ff170f16d4d77ad17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697163"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>optimize for ad hoc workloads (option de configuration de serveur)
  L'option **optimize for ad hoc workloads** permet d'améliorer l'efficacité du cache du plan pour les charges de travail qui contiennent de nombreux lots ad hoc à usage unique. Lorsque cette option a la valeur 1, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] stocke un petit stub du plan compilé dans le cache du plan lorsqu'un lot est compilé pour la première fois, au lieu du plan compilé complet. La mémoire est ainsi moins sollicitée car le cache du plan n'est pas saturé de plans compilés qui ne sont pas réutilisés.  
  
 Le stub du plan compilé permet au [!INCLUDE[ssDE](../../includes/ssde-md.md)] de reconnaître que ce lot ad hoc a déjà été compilé mais qu'il n'a stocké qu'un stub du plan compilé. Par conséquent, lorsque le lot est à nouveau appelé (compilé ou exécuté), le [!INCLUDE[ssDE](../../includes/ssde-md.md)] compile le lot, supprime le stub du plan compilé du cache du plan et ajoute le plan compilé complet au cache du plan.  
  
 Attribuer la valeur 1 à l'option **Optimiser pour les charges de travail ad hoc** affecte uniquement les nouveaux plans ; les plans qui se trouvent déjà dans le cache du plan ne sont pas concernés.  
  
 Le stub du plan compilé est l'un des types d'objets cache contenus dans l'affichage catalogue sys.dm_exec_cached_plans. Il possède un handle SQL et un handle de plan qui sont uniques. Aucun plan d'exécution n'est associé au stub du plan compilé et interroger le handle du plan ne retourne pas de plan d'exécution de requêtes XML.  
  
 L'indicateur de trace 8 032 rétablit les paramètres de limitation du cache au paramètre RTM [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] qui permet en général aux caches d'être plus volumineux. Utilisez ce paramètre quand les entrées du cache fréquemment utilisées ne tiennent pas dans le cache et que l’ *option de configuration de serveur Optimiser pour les charges de travail ad hoc* ne permet pas de résoudre le problème avec le cache du plan.  
  
> [!WARNING]  
>  L'indicateur de trace 8 032 peut altérer les performances si des caches volumineux diminuent la mémoire disponible pour les autres consommateurs, tels que le pool de mémoires tampons.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
