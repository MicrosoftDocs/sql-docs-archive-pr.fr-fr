---
title: MSSQLSERVER_824 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d57b19bc8c837b92b65728fbb0046039b862d31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605441"
---
# <a name="mssqlserver_824"></a>MSSQLSERVER_824
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|824|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|B_HARDSSERR|  
|Texte du message|SQL Server a détecté une erreur d'E/S logique et relative à la cohérence. L'erreur %ls s'est produite pendant une opération de %S_MSG de la page %S_PGID dans la base de données avec l'ID %d au niveau du décalage %#016I64x dans le fichier '%ls'.  Vous trouverez peut-être plus de détails dans les messages supplémentaires qui figurent dans le journal des erreurs et le journal des événements système de SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que Windows considère que la page est correctement lue à partir du disque alors que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signale qu'il y a un problème avec la page. Cette erreur est similaire à l'erreur 823, à la différence qu'elle n'a pas été détectée par Windows. Cela indique généralement un problème dans le sous-système d'E/S, comme un lecteur de disque défaillant, des problèmes avec le microprogramme d'un disque, un pilote de périphérique défectueux, etc. Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S Microsoft SQL Server, chapitre 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
 Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et d'applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ainsi que le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
 Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
 Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
 S'il ne s'agit pas d'un problème de matériel et qu'une sauvegarde saine est disponible, restaurez la base de données à partir de cette sauvegarde.  
  
 Envisagez de modifier les bases de données afin qu'elles utilisent l'option PAGE_VERIFY CHECKSUM. Pour plus d’informations sur PAGE_VERIFY, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
