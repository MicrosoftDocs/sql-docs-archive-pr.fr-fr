---
title: Syntaxe de la commande | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: rothja
ms.author: jroth
ms.openlocfilehash: da5ddb75a5c6fc10db031707b7d97ead71363e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709268"
---
# <a name="command-syntax"></a>Syntaxe de la commande
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client reconnaît la syntaxe de commande spécifiée par la macro DBGUID_SQL. Pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client, le spécificateur indique qu’un amalgame de ODBC SQL, ISO et [!INCLUDE[tsql](../../includes/tsql-md.md)] est une syntaxe valide. Par exemple, l'instruction SQL suivante utilise une séquence d'échappement ODBC SQL pour spécifier la fonction de chaîne LCASE :  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE retourne une chaîne de caractères, en convertissant toutes les majuscules en leurs équivalents minuscules. La fonction de chaîne ISO LOWER effectue la même opération, si bien que l'instruction SQL suivante correspond à l'équivalent ISO de l'instruction ODBC présentée ci-dessus :  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client traite les deux formes de l’instruction avec succès lorsqu’il est spécifié sous forme de texte pour une commande.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 Lors de l’exécution d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procédure stockée à l’aide d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commande du fournisseur OLE DB Native Client, utilisez la séquence d’échappement ODBC Call dans le texte de la commande. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client utilise ensuite le mécanisme d’appel de procédure distante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser le traitement des commandes. Par exemple, l'instruction ODBC SQL suivante correspond à un texte de commande préféré par rapport à la forme [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](commands.md)  
  
  
