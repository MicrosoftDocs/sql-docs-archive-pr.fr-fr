---
title: Initialiser un abonnement avec un instantané | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b776e71e9d1197bc174169aee8ccf692884308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601332"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a>Initialiser un abonnement avec un instantané
  Lorsqu'une publication est créée, un instantané initial est généralement créé puis copié dans le dossier d'instantanés (cela se produit par défaut pour les publications de fusion créées avec l'Assistant Nouvelle publication). Il est ensuite appliqué à l'Abonné par l'Agent de distribution (pour les publications transactionnelles et d'instantané) ou l'Agent de fusion (pour les publications de fusion) lors de la synchronisation initiale de l'abonnement. Le processus d'instantané dépend du type de publication :  
  
-   Si l'instantané est pour une publication d'instantané, une publication transactionnelle ou une publication de fusion n'utilisant pas de filtres paramétrés, l'instantané contient le schéma et les données dans des fichiers programme (bcp) de copie en bloc, ainsi que des contraintes, des propriétés étendues, des index, des déclencheurs et les tables système nécessaires à la réplication. Pour plus d’informations sur la création et l’application de l’instantané, consultez [Créer et appliquer un instantané](create-and-apply-the-snapshot.md).  
  
-   Si l'instantané est pour une publication de fusion utilisant des filtres paramétrés, il est créé à l'aide d'un processus en deux parties. D'abord, un instantané de schéma est créé contenant les scripts de réplication et le schéma des objets publiés, mais pas les données. Ensuite, chaque abonnement est initialisé avec un instantané comprenant les scripts et le schéma copiés à partir de l'instantané de schéma et des données appartenant à la partition de l'abonnement. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 L'instantané se compose de fichiers différents qui dépendent du type de réplication et des articles que comprend la publication. Ces fichiers sont copiés sur le dossier d'instantanés par défaut spécifié lors de la configuration du serveur de distribution, ou sur le dossier d'instantanés de remplacement spécifié lors de la création de la publication.  
  
|Type de réplication|Fichiers d'instantanés courants|  
|-------------------------|---------------------------|  
|Réplication d'instantané ou réplication transactionnelle|schéma (.sch) ; données (.bcp) ; contraintes et index (.dri) ; contraintes (.idx) ; déclencheurs (.trg) : pour la mise à jour d'abonnés uniquement ; fichiers d'instantanés compressés (.cab).|  
|Réplication de fusion|schéma (.sch) ; données (.bcp) ; contraintes et index (.dri) ; déclencheurs (.trg) ; données des tables système (.sys) ; tables de conflits (.cft) ; fichiers d'instantanés compressés (.cab).|  
  
 Si le transfert de l'instantané est interrompu à n'importe quel moment, il reprendra automatiquement et ne renverra aucun fichier déjà transféré en totalité. L'unité de remise pour l'Agent d'instantané est le fichier bcp pour chaque article de publication, les fichiers partiellement remis doivent donc être remis à nouveau en totalité. Cependant, la reprise de l'instantané peut diminuer de manière significative la quantité de données transmise et garantir la remise de l'instantané en temps voulu, même si la connexion n'est pas fiable.  
  
## <a name="snapshot-options"></a>Options d'instantané  
 Il existe de nombreuses options disponibles lors de l'initialisation d'un abonnement avec un instantané. Vous pouvez :  
  
-   Spécifier un emplacement de dossier d'instantanés de remplacement à la place, ou en plus de l'emplacement de dossier d'instantanés par défaut. Pour plus d’informations, consultez [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).  
  
-   Compresser les instantanés pour un stockage sur support amovible ou pour un transfert sur un réseau lent. Pour plus d’informations, consultez [Compressed Snapshots](compressed-snapshots.md).  
  
-   Exécuter des scripts Transact-SQL avant ou après l'application de l'instantané. Pour plus d’informations, consultez [Exécuter des scripts avant et après l’application de l’instantané](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).  
  
-   Transférer des fichiers d'instantanés via le protocole FTP. Pour plus d’informations, consultez [Transférer des instantanés via FTP](transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement](initialize-a-subscription.md)   
 [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md)  
  
  
