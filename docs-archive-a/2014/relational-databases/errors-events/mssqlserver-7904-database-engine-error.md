---
title: MSSQLSERVER_7904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7904 (Database Engine error)
ms.assetid: d047920c-f864-4338-b15f-49820886fbc5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e7be2e8413bc0267a642360da66a6a9ec0de8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605454"
---
# <a name="mssqlserver_7904"></a>MSSQLSERVER_7904
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|7904|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_FS_MISSING_FILE|  
|Texte du message|Erreur de table, le fichier Filestream correspondant à l’ID de colonne C_ID, ROWGUID RG_ID dans l’ID d’objet O_ID, ID d’index I_ID, ID de partition PN_ID est introuvable.|  
  
## <a name="explanation"></a>Explication  
 Une valeur de colonne d'une partition ne possède pas de fichier FILESTREAM correspondant dans le répertoire de colonne FILESTREAM correspondant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
 Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et des applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, ainsi que le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
 Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
 Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
 Si le problème n'est pas matériel et si une restauration réputée en bon état est disponible, restaurez la base de données à partir de la sauvegarde.  
  
### <a name="run-dbcc-checkdb"></a>Exécuter DBCC CHECKDB  
 Non applicable. Cette erreur ne peut pas être corrigée. Si vous ne pouvez pas restaurer la base de données à partir d'une sauvegarde, contactez le service clientèle et le support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
