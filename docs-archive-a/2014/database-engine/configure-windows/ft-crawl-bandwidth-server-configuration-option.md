---
title: ft crawl bandwidth (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33821ff1fdbc4248c71906d8307a8164a7f64d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708599"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>ft crawl bandwidth (option de configuration de serveur)
  Utilisez l’option **ft crawl bandwidth** pour spécifier la taille jusqu’à laquelle le pool des mémoires tampons volumineuses peut croître. Les mémoires tampons volumineuses ont une taille de 4 mégaoctets (Mo). La valeur du paramètre **max** spécifie le nombre maximal de mémoires tampons que le gestionnaire de mémoire de texte intégral doit conserver dans un pool de mémoires tampons volumineuses. Si la valeur **max** est nulle, il n’existe aucune limite supérieure au nombre possible de mémoires tampons dans un pool de mémoires tampons volumineuses.  
  
 La valeur du paramètre **min** spécifie le nombre minimal de mémoires tampons qui doivent être conservées dans le pool de mémoires tampons volumineuses. À la demande du gestionnaire de mémoire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tous les pools de mémoires tampons supplémentaires sont libérés, mais ce nombre minimal de mémoires tampons est conservé. Toutefois, si la valeur **min** spécifiée est nulle, toutes les mémoires tampons sont libérées.  
  
 Dans certains cas, le nombre de mémoires tampons actuellement allouées est inférieur à la valeur spécifiée par le paramètre **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [ft notify bandwidth (option de configuration de serveur)](ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
