---
title: Utilisation des curseurs côté serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: rothja
ms.author: jroth
ms.openlocfilehash: e596af3c46849313d813ce2d7f1dab2a7425c090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603515"
---
# <a name="using-server-cursors"></a>Utilisation des curseurs côté serveur
  Si une application ODBC définit l’un des attributs de curseur ODBC sur une valeur autre que les valeurs par défaut, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC native client demande au serveur d’implémenter un curseur côté serveur d’API du même type. L'utilisation de curseurs côté serveur d'API libère la mémoire sur le client et peut réduire considérablement le trafic réseau entre le client et le serveur.  
  
 Un inconvénient possible des curseurs côté serveur d'API est qu'ils ne prennent pas en charge toutes les instructions SQL. Les curseurs côté serveur d'API ne peuvent pas être utilisés pour exécuter :  
  
-   Les lots ou les procédures stockées qui retournent plusieurs ensembles de résultats.  
  
-   Les instructions SELECT contenant les clauses COMPUTE, COMPUTE BY, FOR BROWSE ou INTO.  
  
-   Une instruction EXECUTE faisant référence à une procédure stockée distante.  
  
 En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'exécution d'une instruction avec ces caractéristiques à l'aide d'un curseur côté serveur provoque la conversion du curseur en un jeu de résultats par défaut. En cas de connexion aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il s'ensuit une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](how-cursors-are-implemented.md)  
  
  
