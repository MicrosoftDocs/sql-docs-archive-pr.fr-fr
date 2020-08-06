---
title: Supprimer une source de données (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e8acd6414b39b317ff0fcfe1b7b9fbab38ae0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603493"
---
# <a name="delete-a-data-source-odbc"></a>Supprimer une source de données (ODBC)
  Vous pouvez supprimer une source de données à l’aide de l’administrateur ODBC, par programmation (à l’aide de [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) ou en supprimant un fichier (si un nom de source de données de fichier).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Pour supprimer une source de données à l'aide de l'Administrateur ODBC  
  
1.  Dans **le panneau de configuration**, ouvrez **Outils d’administration**, puis double-cliquez sur **sources de données (ODBC)**. Vous pouvez également exécuter odbcad32.exe à partir de l'invite de commandes.  
  
2.  Cliquez sur l’onglet **DSN utilisateur**, **système DSN**ou **fichier DSN** .  
  
3.  Cliquez sur la source de données à supprimer.  
  
4.  Cliquez sur **supprimer**, puis confirmez la suppression.  
  
## <a name="example"></a>Exemple  
 Pour supprimer par programmation une source de données, appelez [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) en utilisant ODBC_REMOVE_DSN ou ODBC_REMOVE_SYS_DSN comme deuxième paramètre.  
  
 L'exemple suivant vous montre comment supprimer une source de données par programme.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques des procédures relatives à la configuration du pilote ODBC SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
