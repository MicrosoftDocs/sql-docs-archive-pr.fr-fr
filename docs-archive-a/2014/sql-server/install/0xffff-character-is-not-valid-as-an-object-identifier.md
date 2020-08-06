---
title: le caractère 0xFFFF n’est pas valide en tant qu’identificateur d’objet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604999"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>Le caractère 0xFFFF n'est pas un identificateur d'objet valide
  Le Conseiller de mise à niveau a détecté le caractère 0xFFFF dans un identificateur d'objet. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, les objets tels que les bases de données, les tables et les colonnes qui contiennent ce caractère dans leurs identificateurs ne peuvent pas être référencés ou renommés si le mode de compatibilité de la base de données est défini à 90 ou ultérieur. Lorsque vous effectuez une mise à niveau vers [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le mode de compatibilité des bases de données utilisateur ne change pas. Avant de définir le mode de compatibilité à 90 ou ultérieur, renommez l'objet qui contient le caractère 0xFFFF.  
  
 Pour plus d'informations sur les identificateurs, consultez « Identificateurs » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d'informations sur les modes de compatibilité de la base de données, consultez « sp_dbcmptlevel » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
