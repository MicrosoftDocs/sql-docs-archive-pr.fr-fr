---
title: Définir des options de chiffrement sur des serveurs cibles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613274"
---
# <a name="set-encryption-options-on-target-servers"></a>Définir des options de chiffrement sur des serveurs cibles
  Si vous ne pouvez pas utiliser de certificat pour les communications chiffrées SSL (Secure Sockets Layer) entre des serveurs maîtres et tous ou une partie de vos serveurs cibles, mais que vous souhaitez chiffrer le canal entre ces serveurs, configurez le serveur cible de façon à utiliser le niveau de sécurité requis.  
  
 Pour configurer le niveau de sécurité approprié requis pour un canal de communication serveur maître/serveur cible spécifique, définissez la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous-clé de registre de l’agent **\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Microsoft SQL Server \\ ** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD)** sur le serveur cible sur l’une des valeurs suivantes. La valeur de \<*instance_name*> est **MSSQL.** _n_. Par exemple, **MSSQL.1** ou **MSSQL.3**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Désactive le chiffrement entre ce serveur cible et le serveur maître. Ne choisissez cette option que lorsque le canal entre le serveur cible et le serveur maître est sécurisé par d'autres moyens.|  
|**1**|Active le chiffrement uniquement entre ce serveur cible et le serveur maître, mais aucune validation de certificat n'est requise.|  
|**2**|Active le chiffrement SSL et la validation de certificat complets entre ce serveur cible et le serveur maître. Il s’agit du paramètre par défaut. Sauf si vous avez une raison particulière de choisir une valeur différente, nous vous recommandons de ne pas le modifier.|  
  
 Si **1** ou **2** est spécifié, le protocole SSL doit être activé sur les serveurs maîtres et cibles. Si **2** est spécifié, un certificat signé correctement doit également être présent sur le serveur maître.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Activer les connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
