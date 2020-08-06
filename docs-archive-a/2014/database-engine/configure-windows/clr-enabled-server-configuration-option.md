---
title: clr enabled (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601100"
---
# <a name="clr-enabled-server-configuration-option"></a>clr enabled (option de configuration de serveur)
  L'option clr enabled vous permet de spécifier si des assemblys utilisateur peuvent être exécutés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'option CLR activé fournit les valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|L'exécution de l'assembly n'est pas autorisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|L'exécution de l'assembly est autorisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 Les serveurs WOW64 doivent redémarrer pour que les modifications apportées à ce paramètre prennent effet. Le redémarrage n'est pas requis pour les autres types de serveurs.  
  
> [!NOTE]  
>  Lorsque l'instruction RECONFIGURE est exécutée et que la valeur d'exécution de l'option CLR activé est 0 et non plus 1, tous les domaines d'application contenant des assemblys utilisateur sont immédiatement déchargés.  
  
> [!NOTE]  
>  L'exécution du CLR (Common Language Runtime) n'est pas prise en charge sous l'option lightweight pooling. Désactivez l'une des deux options suivantes : « clr enabled » ou « lightweight pooling ». Les fonctionnalités qui reposent sur le CLR et qui ne fonctionnent pas correctement en mode fibre incluent le type de données `hierarchy`, la réplication et la Gestion basée sur des stratégies.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare indique d'abord le paramètre actuel de l'option clr enabled, puis active l'option en lui attribuant la valeur 1. Pour désactiver l'option, affectez-lui la valeur 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [lightweight pooling (option de configuration de serveur)](lightweight-pooling-server-configuration-option.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [lightweight pooling (option de configuration de serveur)](lightweight-pooling-server-configuration-option.md)  
  
  
