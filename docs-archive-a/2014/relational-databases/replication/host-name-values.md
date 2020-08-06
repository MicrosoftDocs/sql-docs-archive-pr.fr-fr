---
title: Valeurs HOST_NAME | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67d01df05c8d56fd435eb0ee1b42ba2da6a312ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601334"
---
# <a name="host_name-values"></a>Valeurs HOST_NAME
  Les publications de fusion associées à des filtres paramétrés utilisent la fonction SUSER_SNAME() et/ou HOST_NAME() pour filtrer les données. La fonction concernée est spécifiée dans l'Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication** .  
  
 Par défaut, la fonction HOST_NAME() retourne le nom de l'ordinateur qui se connecte au serveur de publication. Lors de l'utilisation de filtres paramétrés, il est fréquent de remplacer cette valeur par une autre dans cette page de l'Assistant. La fonction HOST_NAME() retourne alors la valeur spécifiée à la place du nom de l'ordinateur. Pour plus d’informations, consultez la section « Substitution de la valeur de HOST_NAME() » dans [Filtres paramétrés - Filtres de lignes paramétrés](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Si vous remplacez la valeur de HOST_NAME(), tous les appels de la fonction HOST_NAME() retourneront la valeur que vous avez spécifiée. Assurez-vous que les autres applications ne dépendent pas de la fonction HOST_NAME() avec retour du nom de l'ordinateur.  
  
## <a name="options"></a>Options  
 **Propriétés de l'abonnement**  
 Entrez une valeur pour chaque abonné dans la colonne **Valeur HOST_NAME** ou acceptez la valeur par défaut, c'est-à-dire le nom de l'ordinateur de l'abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)   
 [Afficher et modifier les propriétés d’un abonnement par émission de données](view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
