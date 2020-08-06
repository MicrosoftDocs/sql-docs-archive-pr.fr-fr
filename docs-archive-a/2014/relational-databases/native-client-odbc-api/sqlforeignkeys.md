---
title: SQLForeignKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: rothja
ms.author: jroth
ms.openlocfilehash: a61e80867abb8ecb4d2628b74dc9956051c8e4ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603528"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les mises à jour en cascade et les suppressions via le mécanisme de contrainte de clé étrangère. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne SQL_CASCADE pour les colonnes UPDATE_RULE et/ou DELETE_RULE si l'option CASCADE est spécifiée dans la clause ON UPDATE et/ou ON DELETE des contraintes FOREIGN KEY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne SQL_NO_ACTION pour les colonnes UPDATE_RULE et/ou DELETE_RULE si l'option NO ACTION est spécifiée dans la clause ON UPDATE et/ou ON DELETE des contraintes FOREIGN KEY.  
  
 Lorsque des valeurs non valides sont présentes dans un paramètre **SQLForeignKeys** , **SQLForeignKeys** retourne SQL_SUCCESS lors de l’exécution. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLForeignKeys** peut être exécuté sur un curseur côté serveur statique. Une tentative d’exécution de **SQLForeignKeys** sur un curseur pouvant être mis à jour (dynamique ou de jeu de clés) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge les informations de création de rapports pour les tables des serveurs liés en acceptant un nom en deux parties pour les paramètres *FKCatalogName* et *PKCatalogName* : *linked_server_name. catalog_name*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLForeignKeys fonction)](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
