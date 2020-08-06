---
title: Définir ou changer le classement du serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7be051c8cf63a272f2bf42fb54b1c45ed4160
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614647"
---
# <a name="set-or-change-the-server-collation"></a>Définir ou changer le classement du serveur
  Le classement du serveur agit en tant que classement par défaut pour toutes les bases de données système installées avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que pour toute base de données utilisateur nouvellement créée. Le classement du serveur est spécifié au cours de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Modification du classement du serveur  
 La modification du classement du serveur par défaut pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut s'avérer une opération complexe et implique les étapes suivantes :  
  
-   Vérifiez que vous disposez de toutes les informations ou de tous les scripts nécessaires pour recréer vos bases de données utilisateur et les objets qu'elles contiennent.  
  
-   Exportez toutes vos données à l’aide d’un outil tel que l’ [utilitaire bcp](../../tools/bcp-utility.md). Pour plus d’informations, consultez [Importation et exportation en bloc de données &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Supprimez toutes les bases de données utilisateur.  
  
-   Recréez la base de données MASTER en spécifiant le nouveau classement dans la propriété SQLCOLLATION de la commande **setup** . Par exemple :  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Pour plus d’informations, consultez [Reconstruire des bases de données système](../databases/system-databases.md).  
  
-   Créez toutes les bases de données et tous les objets qu'elles contiennent.  
  
-   Importez toutes vos données.  
  
> [!NOTE]  
>  Au lieu de changer le classement par défaut d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier un classement par défaut pour chaque nouvelle base de données que vous créez.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'Unicode et du classement](collation-and-unicode-support.md)   
 [Définir ou modifier le classement de la base de données](set-or-change-the-database-collation.md)   
 [Définir ou modifier le classement des colonnes](set-or-change-the-column-collation.md)   
 [Reconstruire des bases de données système](../databases/system-databases.md)  
  
  
