---
title: Transactions XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75fa8bc9a673d9e0e018b8578a35af2e46b5044c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698033"
---
# <a name="xtp-transactions"></a>Transactions XTP
  L'objet de performance Transactions XTP contient des compteurs connexes aux transactions du moteur XTP dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Ce tableau décrit les compteurs **Transactions XTP** .  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Abandons en cascade par seconde**|Nombre de transactions restaurées en raison d'une restauration de dépendance de validation (en moyenne), par seconde.|  
|**Dépendances de validation prises par seconde**|Nombre de dépendances de validation prises par des transactions (en moyenne), par seconde.|  
|**Transactions en lecture seule préparées par seconde**|Nombre de transactions en lecture seule qui ont été préparées pour le traitement de validation, par seconde.|  
|**Actualisations de point de sauvegarde par seconde**|Nombre de fois qu'un point de sauvegarde a été « actualisé » (en moyenne), par seconde. Une actualisation de point de sauvegarde se produit lorsqu'un point de sauvegarde existant est réinitialisé au point actuel dans la durée de vie de la transaction.|  
|**Restaurations de point de sauvegarde par seconde**|Nombre de fois qu'une transaction a été restaurée à un point de sauvegarde (en moyenne), par seconde.|  
|**Points de sauvegarde créés par seconde**|Nombre de points de sauvegarde créés (en moyenne), par seconde.|  
|**Échec de validation des transactions par seconde**|Nombre de transactions ayant échoué lors du traitement de validation (en moyenne), par seconde.|  
|**Transactions abandonnées par l'utilisateur par seconde**|Nombre de transactions abandonnées par l'utilisateur (en moyenne), par seconde.|  
|**Transactions abandonnées par seconde**|Nombre de transactions abandonnées par l'utilisateur et par le système (en moyenne), par seconde.|  
|**Transactions créées par seconde**|Nombre de transactions créées dans le système (en moyenne), par seconde.<br /><br /> Les transactions XTP sont comptées différemment que les transactions sur disque (comme obtenu par réflexion dans Databases:Transactions/sec). Par exemple, les transactions created/sec comptent les transactions read/only, contrairement à Databases:Transactions/sec.|  
  
## <a name="see-also"></a>Voir aussi  
 [Les compteurs de performances de l’OLTP en mémoire &#40;de XTP&#41;](../../integration-services/performance/performance-counters.md)  
  
  
