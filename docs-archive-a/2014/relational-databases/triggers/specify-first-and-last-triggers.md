---
title: Spécifier les premier et dernier déclencheurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- first triggers [SQL Server]
- last triggers
- DML triggers, first or last triggers
- INSTEAD OF triggers
- AFTER triggers
ms.assetid: 9e6c7684-3dd3-46bb-b7be-523b33fae4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddb352b00dc759362c8f6ef1e861e55b6f184f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613869"
---
# <a name="specify-first-and-last-triggers"></a>Spécifier les premier et dernier déclencheurs
  Vous pouvez définir l'un des déclencheurs AFTER associés à une table comme étant le premier ou le dernier déclencheur AFTER activé pour chaque action de déclenchement INSERT, DELETE et UPDATE. L'ordre d'exécution des déclencheurs AFTER activés entre les premier et dernier déclencheurs est indéfini.  
  
 Pour spécifier l’ordre d’exécution d’un déclencheur AFTER, utilisez la procédure stockée **sp_settriggerorder** . **sp_settriggerorder** comporte les options suivantes.  
  
|Option|Description|  
|------------|-----------------|  
|**Première**|Spécifie que le déclencheur DML est le premier déclencheur AFTER activé dans le cadre d'une action de déclenchement.|  
|**Dernière**|Spécifie que le déclencheur DML est le dernier déclencheur AFTER activé dans le cadre d'une action de déclenchement.|  
|**Aucun**|Spécifie qu'il n'existe aucun ordre spécifique pour l'activation du déclencheur DML. Cette option est principalement destinée à réinitialiser un déclencheur qui était le premier ou le dernier déclencheur.|  
  
 L’exemple suivant illustre l’utilisation de la procédure stockée **sp_settriggerorder**:  
  
```  
sp_settriggerorder @triggername = 'MyTrigger', @order = 'first', @stmttype = 'UPDATE'  
```  
  
> [!IMPORTANT]  
>  Le premier déclencheur et le dernier déclencheur doivent être deux déclencheurs DML distincts.  
  
 Plusieurs déclencheurs INSERT, UPDATE et DELETE peuvent être définis simultanément sur une table. Chaque type d'instruction peut posséder ses propres premier et dernier déclencheurs à condition qu'ils soient différents.  
  
 Si le premier ou dernier déclencheur défini pour une table ne couvre pas une action de déclenchement, telle que FOR UPDATE, FOR DELETE ou FOR INSERT, aucun premier ou dernier déclencheur n'est associé aux actions manquantes.  
  
 Un déclencheur INSTEAD OF ne peut pas être défini en tant que premier ou dernier déclencheur. Il est activé avant l'apport de mises à jour aux tables sous-jacentes. Si des mises à jour sont apportées par un déclencheur INSTEAD OF à des tables sous-jacentes, elles se produisent avant l'activation des déclencheurs AFTER définis sur la table. Par exemple, si un déclencheur INSTEAD OF INSERT sur une vue insère des données dans une table de base et si la table de base contient un déclencheur INSTEAD OF INSERT et trois déclencheurs AFTER INSERT, le déclencheur INSTEAD OF INSERT sur la table de base est activé au lieu de l'action d'insertion, et les déclencheurs AFTER sur la table de base sont activés après toute action d'insertion sur celle-ci. Pour plus d'informations, consultez [DML Triggers](dml-triggers.md).  
  
 Si une instruction ALTER TRIGGER modifie un premier ou un dernier déclencheur, l’attribut **First** ou **Last** est supprimé et l’ordre d’exécution prend la valeur **None**. L’ordre d’exécution doit être réinitialisé à l’aide de **sp_settriggerorder**.  
  
 La fonction OBJECTPROPERTY signale si un déclencheur est défini comme le premier ou le dernier à l’aide des propriétés **ExecIsFirstTrigger** et **ExecIsLastTrigger**.  
  
 La réplication génère automatiquement un premier déclencheur pour toute table qui est incluse dans un abonnement avec mise à jour immédiate ou en attente. Elle nécessite un déclencheur qui soit le premier. Elle génère une erreur si vous essayez d'inclure une table détenant un premier déclencheur dans un abonnement mis à jour immédiatement ou en attente. Si vous tentez de définir un déclencheur comme premier déclencheur après qu’une table a été incluse dans un abonnement, **sp_settriggerorder** retourne une erreur. Si vous utilisez ALTER sur le déclencheur de réplication ou si vous utilisez **sp_settriggerorder** pour que l’ordre corresponde au premier déclencheur ou pour qu’il n’y ait aucun ordre spécifique, l’abonnement ne fonctionnera pas correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql)   
 [sp_settriggerorder &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql)  
  
  
