---
title: Procédures | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: rothja
ms.author: jroth
ms.openlocfilehash: a7ae4678d324ba7d07ae429793b1f75b57bb15e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600853"
---
# <a name="procedures"></a>Procédures
  Une procédure stockée est un objet exécutable précompilé qui contient une ou plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les procédures stockées peuvent posséder des paramètres d'entrée et de sortie et peuvent également émettre un code de retour de type entier. Une application peut énumérer les procédures stockées disponibles en utilisant des fonctions de catalogue.  
  
 Les applications ODBC qui ciblent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent utiliser uniquement l'exécution directe pour appeler une procédure stockée. Lorsqu’il est connecté à des versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client implémente la [fonction SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) en créant une procédure stockée temporaire, qui est ensuite appelée sur **SQLExecute**. Il ajoute une surcharge pour que **SQLPrepare** crée une procédure stockée temporaire qui appelle uniquement la procédure stockée cible plutôt que d’exécuter directement la procédure stockée cible. Même lors d'une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la préparation d'un appel requiert une boucle réseau supplémentaire et l'établissement d'un plan d'exécution qui appelle simplement le plan d'exécution de procédure stockée.  
  
 Les applications ODBC doivent utiliser la syntaxe ODBC CALL lors de l'exécution d'une procédure stockée. Le pilote est optimisé pour utiliser un mécanisme d'appel de procédure distante pour appeler la procédure lorsque la syntaxe ODBC CALL est utilisée. Ce mécanisme est plus efficace que celui utilisé pour envoyer une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE au serveur.  
  
 Pour plus d’informations, consultez [exécution de procédures stockées](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’instructions &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
