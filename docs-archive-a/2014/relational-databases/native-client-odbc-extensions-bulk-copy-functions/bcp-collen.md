---
title: bcp_collen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709368"
---
# <a name="bcp_collen"></a>bcp_collen
  Définit la longueur des données dans la variable de programme pour la copie en bloc actuelle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *cbData*  
 Longueur des données dans la variable de programme, à l'exclusion de la longueur de tout indicateur de longueur ou terminateur. La définition de *cbData* avec la valeur SQL_NULL_DATA indique que toutes les lignes copiées sur le serveur contiennent une valeur NULL pour la colonne. La définition de cbData avec la valeur SQL_VARLEN_DATA indique qu'un terminateur de chaîne ou une autre méthode est utilisé pour déterminer la longueur des données copiées. S'il existe à la fois un indicateur de longueur et un terminateur, le système utilise celui qui entraîne la copie du moins grand nombre de données.  
  
 *idxServerCol*  
 Position ordinale de la colonne dans la table vers laquelle les données sont copiées. La première colonne est 1. La position ordinale d'une colonne est indiquée par [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **bcp_collen** vous permet de modifier la longueur de données dans la variable de programme pour une colonne particulière lors de la copie de données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec [bcp_sendrow](bcp-sendrow.md).  
  
 Initialement, la longueur de données est déterminée quand [bcp_bind](bcp-bind.md) est appelé. Si la longueur de données change entre des appels à **bcp_sendrow** et qu'aucun préfixe de longueur ou terminateur n'est en cours d'utilisation, vous pouvez appeler **bcp_collen** pour réinitialiser la longueur. L'appel suivant à **bcp_sendrow** utilise la longueur définie par l'appel à **bcp_collen**.  
  
 Vous devez appeler **bcp_collen** une fois pour chaque colonne de la table dont vous voulez modifier la longueur de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
