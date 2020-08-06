---
title: Valider des informations de partition pour un abonné de fusion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3032ff13af69a0690e1f81f08f7b3fb17aae0ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600755"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a>Valider des informations de partition pour un Abonné de fusion
  Quand vous définissez un filtre de lignes paramétrable pour une publication de fusion, vous utilisez une fonction qui référence des informations de l'Abonné, telles que son nom de connexion. Par défaut, la réplication valide les informations de l'Abonné sur la base de cette fonction avant chaque synchronisation et si un instantané est appliqué à l'Abonné. Le processus de validation vérifie que ces données sont partitionnées correctement pour chaque Abonné. Le fonctionnement de la validation est contrôlé par la propriété de publication **validate_subscriber_info**, qui peut être modifiée à l’aide de [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) ou sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication**. Pour plus d'informations sur la modification des propriétés d'une publication, consultez [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
## <a name="how-partition-validation-works"></a>Fonctionnement de la validation de partition  
 Lorsqu'une publication est filtrée par exemple à l'aide de la fonction **SUSER_SNAME()**, l'Agent de fusion applique l'instantané initial à chaque Abonné en fonction des données qui sont valides pour l'expression **SUSER_SNAME()** .  
  
 Si la validation est activée, quand l'Abonné se reconnecte au serveur de publication pour la synchronisation suivante, l'Agent de fusion valide les informations sur l'Abonné et vérifie que la partition de chaque Abonné est la même que celle reçue dans l'instantané initial. Pour chaque application de fusion ou d'instantané suivante, l'Agent de fusion valide la partition de chaque abonné.  
  
 Si l'Agent de fusion détecte que la fonction utilisée dans l'expression de filtrage renvoie une valeur différente de celle qu'elle a renvoyée lors de l'instantané initial, l'application de fusion ou d'instantané échoue, et l'abonnement de cet Abonné peut nécessiter une réinitialisation. La réinitialisation peut être nécessaire pour empêcher des problèmes qui peuvent survenir si les paramètres de fusion d'un Abonné ont changé, mais elle peut être suffisante pour ramener les informations sur l'Abonné, par exemple le nom de connexion, à la valeur utilisée au moment de l'instantané original.  
  
 Quand l'Agent de fusion valide une partition, en plus de valider la partition relativement aux valeurs renvoyées par toutes les fonctions utilisées dans les expressions de filtrage, l'agent vérifie également si l'instantané a été généré avant des modifications qui l'invalident, par exemple des opérations de nettoyage des métadonnées ou des modifications de schéma. Si un instantané partitionné est trop ancien, l'Agent de fusion renvoie une erreur et vous devez régénérer un instantané partitionné pour cet Abonné sur la base d'un instantané normal en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [FAQ sur l’administration de la réplication](administration/frequently-asked-questions-for-replication-administrators.md)   
 [Meilleures pratiques pour l’administration de la réplication](administration/best-practices-for-replication-administration.md)   
 [Réinitialiser des abonnements](reinitialize-subscriptions.md)   
 [Valider des données répliquées](validate-data-at-the-subscriber.md)  
  
  
