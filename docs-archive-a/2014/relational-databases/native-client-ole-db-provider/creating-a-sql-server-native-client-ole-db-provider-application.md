---
title: Création d’une application de fournisseur d’OLE DB SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: a661f23cdacc4b581dadbe7625cb6e2ea318857f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698123"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Création d'une application de fournisseur OLE DB de SQL Server Native Client
  La création d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application de fournisseur OLE DB Native Client implique les étapes suivantes :  
  
1.  Établissement d'une connexion à une source de données.  
  
2.  Exécution d'une commande.  
  
3.  Traitement des résultats.  
  
> [!NOTE]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez rendre les informations d’identification persistantes, chiffrez-les avec [l’API de chiffrement Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Établissement d'une connexion à une source de données](establishing-a-connection-to-a-data-source.md)  
  
-   [Exécution d'une commande](executing-a-command.md)  
  
-   [Traitement des résultats](processing-results.md)  
  
-   [À propos des propriétés OLE DB](about-ole-db-properties.md)  
  
-   [Utilisation de la clause OUTPUT avec OLE DB dans SQL Server Native Client](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
