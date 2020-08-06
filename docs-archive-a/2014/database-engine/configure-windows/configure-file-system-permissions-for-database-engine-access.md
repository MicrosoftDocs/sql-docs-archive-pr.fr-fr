---
title: Configurer les autorisations du système de fichiers pour l’accès au moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d9abbd095f2d5be7415ed28a17fb710ff8ab504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614848"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Configurer les autorisations du système de fichiers pour l'accès au moteur de base de données
  Cette rubrique explique comment octroyer au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]un accès de système de fichiers à l'emplacement où sont stockés les fichiers de base de données. Le service [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit disposer d'une autorisation du système de fichiers Windows pour accéder au dossier de fichiers dans lequel sont stockés les fichiers de base de données. L'autorisation sur l'emplacement par défaut est configurée lors de l'installation. Si vous placez vos fichiers de base de données à un emplacement différent, vous devrez peut-être procéder comme suit pour octroyer au [!INCLUDE[ssDE](../../includes/ssde-md.md)] une autorisation de contrôle total sur cet emplacement.  
  
 Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , les autorisations sont affectées au SID par service pour chacun de ses services. Ce système aide à fournir une isolation de service et une défense en profondeur. Le SID par service est dérivé du nom du service et est propre à chaque service. La rubrique [Configurer les comptes de service Windows et les autorisations](configure-windows-service-accounts-and-permissions.md) décrit le SID par service et fournit les noms dans la section **Privilèges et droits Windows**. C'est le SID par service qui doit bénéficier d'une autorisation d'accès à l'emplacement de fichier.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>Pour octroyer une autorisation de système de fichiers au SID par service  
  
1.  À l'aide de l'Explorateur Windows, accédez à l'emplacement du système de fichiers où sont stockés les fichiers de base de données. Cliquez avec le bouton droit sur le dossier du système de fichiers, puis sélectionnez **Propriétés**.  
  
2.  Sous l’onglet **Sécurité** , cliquez sur **Modifier**, puis sur **Ajouter**.  
  
3.  Dans la boîte de dialogue **Choisir des utilisateurs, un ordinateur, un compte de service ou des groupes** , cliquez sur **Emplacements**, en haut de la liste des emplacements, sélectionnez le nom de votre ordinateur, puis cliquez sur **OK**.  
  
4.  Dans la zone **Entrez les noms des objets à sélectionner** , tapez le nom du SID par service figurant dans la rubrique de la documentation en ligne **configurer les comptes de service Windows et les autorisations**. (Pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] SID par service, utilisez **NT SERVICE\MSSQLSERVER** pour une instance par défaut ou **NT SERVICE\MSSQL $ InstanceName** pour une instance nommée.)  
  
5.  Cliquez sur **Vérifier les noms** pour valider l’entrée. La validation échoue souvent et peut indiquer que le nom était introuvable. Quand vous cliquez sur **OK**, une boîte de dialogue **Noms multiples trouvés** s’affiche.  
  
6.  Sélectionnez maintenant le SID par service, **MSSQLSERVER** ou **NT SERVICE\MSSQL $ nom_instance**, puis cliquez sur **OK**.  
  
7.  Cliquez à nouveau sur **OK** pour revenir à la boîte de dialogue **autorisations** .  
  
8.  Dans la zone noms de **groupes ou d’utilisateurs** , sélectionnez le SID par service, puis dans la zone **autorisations pour** \<name> , activez la case à cocher **autoriser** pour **contrôle total**.  
  
9. Cliquez sur **Appliquer**, puis cliquez à deux reprises sur **OK** pour quitter la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les services du moteur de base de données](manage-the-database-engine-services.md)   
 [Déplacer des bases de données système](../../relational-databases/databases/system-databases.md)   
 [Déplacer des bases de données utilisateur](../../relational-databases/databases/move-user-databases.md)  
  
  
