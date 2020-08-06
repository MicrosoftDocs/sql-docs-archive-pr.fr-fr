---
title: Informations de référence sur l’interface utilisateur de la boîte de dialogue rôles de package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703179"
---
# <a name="package-roles-dialog-box-ui-reference"></a>Référence de l'interface utilisateur de la boîte de dialogue Rôles de package
  Utilisez la boîte de dialogue **Rôles de package** , disponible dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], pour spécifier les rôles au niveau de la base de données qui possèdent un accès en lecture au package et les rôles au niveau de la base de données qui possèdent un accès en écriture au package. Les rôles au niveau de la base de données s’appliquent uniquement aux packages stockés dans la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb**.  
  
 Pour en savoir plus sur les rôles au niveau de la base de données [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et leurs autorisations, consultez [Rôles Integration Services &#40;Service SSIS&#41;](security/integration-services-roles-ssis-service.md).  
  
 Les rôles répertoriés dans la boîte de dialogue sont les rôles actuels de la base de données système **msdb** . Si aucun rôle n'est sélectionné, les rôles [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] par défaut s'appliquent. Par défaut, le rôle de lecteur inclut **db_ssisadmin**, **db_ssisoperator**et l’utilisateur qui a créé le package. Un utilisateur membre de l'un de ces rôles ou qui a créé les packages peut énumérer, consulter, exporter et exécuter des packages. Par défaut, le rôle de rédacteur inclut **db_ssisadmin** et l’utilisateur qui a créé le package. Un utilisateur membre de ce rôle et l'utilisateur qui a créé les packages peuvent importer, supprimer et modifier des packages.  
  
 La colonne **ownersid** de la table **sysssispackages** contient l'identificateur de sécurité unique de l'utilisateur qui a créé le package.  
  
## <a name="options"></a>Options  
 **Nom du package**  
 Spécifiez le nom du package.  
  
 **Rôle de lecteur**  
 Sélectionnez un rôle dans la liste.  
  
 **Rôle Rédacteur**  
 Sélectionnez un rôle dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles au niveau de la base de données](../relational-databases/security/authentication-access/database-level-roles.md)   
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md)  
  
  
