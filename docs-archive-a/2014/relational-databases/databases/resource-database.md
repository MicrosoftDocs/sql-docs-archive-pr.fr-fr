---
title: Base de données Resource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604544"
---
# <a name="resource-database"></a>Base de données Resource
  La base de données Resource est une base de données en lecture seule qui contient tous les objets système fournis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les objets système, tels que sys.objects, sont conservés physiquement dans la base de données Resource, mais ils figurent logiquement dans le schéma sys de chaque base de données. La base de données Resource ne contient ni données utilisateur, ni métadonnées utilisateur.  
  
 La base de données Resource facilite et accélère la procédure de mise à niveau vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la mise à niveau nécessitait la suppression et la création d'objets système. Étant donné que le fichier de la base de données Resource contient tous les objets système, il suffit désormais tout simplement de copier le seul fichier de la base de données Resource sur le serveur local pour effectuer une mise à niveau.  
  
## <a name="physical-properties-of-resource"></a>Propriétés physiques de la base de données Resource  
 Les noms de fichiers physiques de la base de données Resource sont mssqlsystemresource.mdf et mssqlsystemresource.ldf. Ces fichiers se trouvent dans \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ et ne doivent pas être déplacés. Chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède un seul fichier mssqlsystemresource.mdf associé et les instances ne partagent pas ce fichier.  
  
> [!WARNING]  
>  Les Service Packs et les mises à niveau fournissent parfois une nouvelle base de données de ressources qui est installée dans le dossier BINN. La modification de l'emplacement de la base de données de ressources n'est ni prise en charge, ni recommandée.  
  
## <a name="backing-up-and-restoring-the-resource-database"></a>Sauvegarde et restauration de la base de données Resource  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas sauvegarder la base de données Resource. Vous pouvez effectuer votre propre sauvegarde sur fichiers ou sur disque en traitant le fichier mssqlsystemresource.mdf comme un fichier binaire (.EXE), et non comme un fichier de base de données, mais vous ne pouvez pas utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour restaurer vos sauvegardes. La restauration d'une copie de sauvegarde du fichier mssqlsystemresource.mdf peut uniquement être effectuée manuellement et vous devez alors veiller à ne pas remplacer la version actuelle de la base de données Resource par une version obsolète ou potentiellement instable.  
  
> [!IMPORTANT]  
>  Après avoir restauré une sauvegarde de mssqlsystemresource.mdf, vous devez réappliquer toutes les mises à jour ultérieures.  
  
## <a name="accessing-the-resource-database"></a>Accès à la base de données Resource  
 La base de données Resource doit uniquement être modifiée par un spécialiste du support technique Microsoft, ou à l'initiative de ce dernier. L'ID de la base de données Resource est toujours 32767. Les autres valeurs importantes associées à la base de données Resource sont le numéro de version, ainsi que la date et l'heure de la dernière mise à jour de la base de données.  
  
 **Pour déterminer le numéro de version de la base de données** Resource **, utilisez**:  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 **Pour déterminer la date et l’heure auxquelles la base de données** Resource **a été mise à jour pour la dernière fois, utilisez**:  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 **Pour accéder aux définitions SQL des objets système, utilisez la fonction OBJECT_DEFINITION :**  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a>Contenu associé  
 [Bases de données système](system-databases.md)  
  
 [Connexion de diagnostic pour les administrateurs de base de données](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [Démarrer SQL Server en mode mono-utilisateur](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
