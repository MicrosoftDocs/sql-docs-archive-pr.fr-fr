---
title: Collections de schémas XML volumineuses et conditions de mémoire insuffisante | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710408"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Collections de schémas XML volumineuses et conditions de mémoire insuffisante
  Lors d'un appel à la fonction intégrée XML_SCHEMA_NAMESPACE() sur une collection de schémas XML de grande taille ou si vous tentez de supprimer une telle collection, une condition de mémoire insuffisante peut se produire. Pour pallier ce problème, envisagez les solutions suivantes :  
  
-   Si la charge imposée au système est faible, utilisez la commande DROP_XML_SCHEMA_COLLECTION. Si cette mesure ne permet pas de résoudre le problème, placez la base de données en mode mono-utilisateur à l'aide de l'instruction ALTER DATABASE et réexécutez DROP XML SCHEMA COLLECTION. Si la collection de schémas XML existe dans **master**, **model**ou **tempdb**, un redémarrage du serveur est requis pour passer en mode mono-utilisateur.  
  
-   Quand vous appelez XML_SCHEMA_NAMESPACE, essayez d'extraire un espace de noms de schéma XML, tentez l'appel à un moment où la charge système est moindre ou alors en mode mono-utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
