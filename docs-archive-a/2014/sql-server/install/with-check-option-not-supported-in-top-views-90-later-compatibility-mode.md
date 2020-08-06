---
title: L’OPTION WITH CHECK OPTION n’est pas prise en charge dans les vues qui contiennent TOP en mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604834"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>L'option WITH CHECK OPTION n'est pas prise en charge dans les vues contenant TOP en mode de compatibilité 90 ou ultérieur
  Le Conseiller de mise à niveau a détecté qu'une vue est définie à l'aide du mot clé WITH CHECK OPTION et d'une clause TOP dans l'instruction SELECT de la vue ou dans une vue référencée. Les vues ainsi définies autorisent de manière incorrecte la modification des données par le biais de la vue, ce qui peut produire des résultats imprécis lorsque la base de données est définie en mode de compatibilité 80 ou antérieur. Les données ne peuvent pas être insérées ou mises à jour par le biais d'une vue qui utilise le mot clé WITH CHECK OPTION si la vue ou une vue référencée utilise la clause TOP et que la base de données est définie en mode de compatibilité 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Avant de définir la base de données en mode de compatibilité 100 ou ultérieur, modifiez les vues qui utilisent WITH CHECK OPTION et TOP si la modification des données par le biais de la vue est requise. Pour plus d’informations, consultez [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
