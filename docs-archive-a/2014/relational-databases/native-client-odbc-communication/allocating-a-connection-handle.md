---
title: Allocation d’un handle de connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: rothja
ms.author: jroth
ms.openlocfilehash: d3cf84e541f114d527d9a00cd19bce705a09af30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709395"
---
# <a name="allocating-a-connection-handle"></a>Allocation d'un handle de connexion
  Pour que l'application puisse se connecter à une source de données ou à un pilote, elle doit auparavant allouer un handle de connexion. Pour ce faire, appelez **SQLAllocHandle** avec le paramètre *comme handletype* défini sur SQL_HANDLE_DBC et *InputHandle* pointant vers un handle d’environnement initialisé.  
  
 Les caractéristiques de la connexion sont contrôlées en définissant des attributs de connexion. Par exemple, étant donné que les transactions se produisent au niveau de la connexion, le niveau d'isolation de la transaction est un attribut de connexion. De la même façon, le délai d'expiration de la connexion (c'est-à-dire le nombre de secondes s'écoulant avant l'expiration de la tentative de connexion) est un attribut de connexion.  
  
 Les attributs de connexion sont définis avec [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)et leurs paramètres actuels sont récupérés avec [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md). Si le pilote **SQLSetConnectAttr** est appelé avant une tentative de connexion, le gestionnaire de pilotes ODBC stocke les attributs dans sa structure de connexion et les définit dans le pilote dans le cadre du processus de connexion. Certains attributs de connexion doivent être définis avant toute tentative de connexion de l'application ; d'autres peuvent être définis une fois la connexion établie. Par exemple, SQL_ATTR_ODBC_CURSORS doit être défini avant l'établissement d'une connexion, mais SQL_ATTR_AUTOCOMMIT peut être défini une fois la connexion établie.  
  
 Les applications s'exécutant sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 ou version ultérieure peuvent améliorer leurs performances en réinitialisant la taille du paquet réseau du flux TDS (Tabular Data Stream). La taille du paquet par défaut est définie au niveau du serveur avec la valeur 4 Ko. Une taille de paquet comprise entre 4 Ko et 8 Ko offre généralement les meilleures performances. Si les tests indiquent qu'une taille de paquet différente offre de meilleures performances, l'application peut réinitialiser la taille du paquet. Les applications ODBC peuvent effectuer cette opération avant de se connecter en appelant **SQLSetConnectAttr** avec l’option SQL_ATTR_PACKET_SIZE. Certaines applications fonctionnent mieux avec une taille de paquet plus grande, mais les gains en termes de performances sont généralement minimes pour les tailles de paquet supérieures à 8 Ko.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client possède un certain nombre d’attributs de connexion étendus qu’une application peut utiliser pour augmenter ses fonctionnalités. Certains de ces attributs contrôlent les mêmes options que celles qui peuvent être spécifiées dans les sources de données et qui sont utilisées pour remplacer n'importe quelle option définie dans une source de données. Par exemple, si une application utilise des identificateurs entre guillemets, elle peut attribuer à l'attribut SQL_COPT_SS_QUOTED_IDENT spécifique au pilote la valeur SQL_QI_ON pour faire en sorte que cette option soit toujours définie indépendamment du paramètre dans une source de données quelconque.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
