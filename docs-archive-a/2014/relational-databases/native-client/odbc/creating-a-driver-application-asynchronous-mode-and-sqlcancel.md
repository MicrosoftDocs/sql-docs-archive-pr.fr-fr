---
title: Mode asynchrone et SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9071c6821e6edeb577b639223e42899d2927bced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612255"
---
# <a name="asynchronous-mode-and-sqlcancel"></a>Mode asynchrone et SQLCancel
  Certaines fonctions ODBC peuvent fonctionner en mode synchrone ou asynchrone. L'application peut activer les opérations asynchrones pour un descripteur d'instruction ou un handle de connexion. Si l'option est définie pour un handle de connexion, tous les descripteurs d'instruction sur le handle de connexion sont affectés. L'application utilise les instructions suivantes pour activer ou désactiver les opérations asynchrones :  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Lorsqu'une application appelle une fonction ODBC en mode synchrone, le pilote ne rend pas le contrôle à l'application jusqu'à ce qu'il soit averti que le serveur a terminé la commande.  
  
 En mode asynchrone, le pilote rend immédiatement le contrôle à l'application, avant même d'envoyer la commande au serveur. Le pilote définit le code de retour sur SQL_STILL_EXECUTING. L'application peut ensuite effectuer un autre travail.  
  
 Lorsque l'application teste l'achèvement de la commande, il effectue le même appel de fonction avec les mêmes paramètres sur le pilote. Si le pilote n'a pas encore reçu de réponse du serveur, il retourne de nouveau SQL_STILL_EXECUTING. L'application doit tester régulièrement la commande jusqu'à ce que le code de retour soit différent de SQL_STILL_EXECUTING. Lorsque l'application obtient un autre code de retour, même SQL_ERROR, elle peut déterminer que la commande est terminée.  
  
 Une commande peut parfois rester longtemps en attente. Si l’application doit annuler la commande sans attendre de réponse, elle peut le faire en appelant **SQLCancel** avec le même descripteur d’instruction que la commande en suspens. Il s’agit de la seule fois où **SQLCancel** doit être utilisé. Certains programmeurs utilisent **SQLCancel** lorsqu’ils ont traité des éléments dans un jeu de résultats et veulent annuler le reste du jeu de résultats. [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) ou [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) doit être utilisé pour annuler le reste d’un jeu de résultats en suspens, et non **SQLCancel**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de pilote ODBC SQL Server Native Client](creating-a-driver-application.md)  
  
  
