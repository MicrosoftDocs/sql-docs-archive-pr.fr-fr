---
title: Préparer et exécuter une instruction (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: rothja
ms.author: jroth
ms.openlocfilehash: 607d8ad1509eca1204f6d029842b04120d3f5d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707491"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>Préparer et exécuter une instruction (ODBC)
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>Pour préparer une instruction une fois, puis l'exécuter plusieurs fois  
  
1.  Appelez la fonction [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) pour préparer l'instruction.  
  
2.  Éventuellement, appelez [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) pour déterminer le nombre de paramètres dans l'instruction préparée.  
  
3.  Éventuellement, pour chaque paramètre dans l'instruction préparée :  
  
    -   Appelez [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) pour obtenir des informations sur les paramètres.  
  
    -   Liez chaque paramètre à une variable de programme à l'aide de [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md). Configurez tous les paramètres de données en cours d'exécution.  
  
4.  Pour chaque exécution d'une instruction préparée :  
  
    -   Si l'instruction a des marqueurs de paramètres, mettez les valeurs de données dans la mémoire tampon de paramètre lié.  
  
    -   Appelez [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) pour exécuter l'instruction préparée.  
  
    -   Si des paramètres d'entrée de données en cours d'exécution sont utilisés, [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) et [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>Pour préparer une instruction avec la liaison de paramètre selon les colonnes  
  
1.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
    -   Définissez SQL_ATTR_PARAMSET_SIZE au nombre de jeux (S) de paramètres.  
  
    -   Définissez SQL_ATTR_PARAM_BIND_TYPE à SQL_PARAMETER_BIND_BY_COLUMN.  
  
    -   Définissez l'attribut SQL_ATTR_PARAMS_PROCESSED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de paramètres traités.  
  
    -   Définissez SQL_ATTR_PARAMS_STATUS_PTR de sorte qu'il pointe vers un tableau [S] de variables SQLUSSMALLINT contenant les indicateurs d'état de paramètre.  
  
2.  Appelez SQLPrepare pour préparer l’instruction.  
  
3.  Éventuellement, appelez [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) pour déterminer le nombre de paramètres dans l'instruction préparée.  
  
4.  Si vous le souhaitez, pour chaque paramètre de l’instruction préparée, appelez SQLDescribeParam pour obtenir des informations sur les paramètres.  
  
5.  Pour chaque marqueur de paramètre :  
  
    -   Allouez un tableau de S mémoires tampons de paramètres pour stocker les valeurs de données.  
  
    -   Allouez un tableau de S mémoires tampons de paramètres pour stocker les longueurs de données.  
  
    -   Appelez SQLBindParameter pour lier les tableaux de valeur de données et de longueur de données de paramètre au paramètre d'instruction.  
  
    -   Si le paramètre est un paramètre d'image ou de texte de données en cours d'exécution, installez-le.  
  
    -   Si des paramètres de données en cours d'exécution sont utilisés, installez-les.  
  
6.  Pour chaque exécution d'une instruction préparée :  
  
    -   Mettez les valeurs de données S et les longueurs de données S dans les tableaux de paramètres liés.  
  
    -   Appelez SQLExecute pour exécuter l'instruction préparée.  
  
    -   Si des paramètres d'entrée de données en cours d'exécution sont utilisés, SQLExecute retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de SQLParamData et SQLPutData.  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>Pour préparer une instruction avec des paramètres liés selon les lignes  
  
1.  Allouez un tableau [S] de structures, où S est le nombre de jeux de paramètres. La structure dispose d'un élément pour chaque paramètre et chaque élément contient deux parties :  
  
    -   La première partie est une variable du type de données approprié destinée à contenir les données de paramètres.  
  
    -   La deuxième partie est une variable SQLINTEGER destinée à contenir l'indicateur d'état.  
  
2.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
    -   Définissez SQL_ATTR_PARAMSET_SIZE au nombre de jeux (S) de paramètres.  
  
    -   Définissez SQL_ATTR_PARAM_BIND_TYPE à la taille de la structure allouée à l'étape 1.  
  
    -   Définissez l'attribut SQL_ATTR_PARAMS_PROCESSED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de paramètres traités.  
  
    -   Définissez SQL_ATTR_PARAMS_STATUS_PTR de sorte qu'il pointe vers un tableau [S] de variables SQLUSSMALLINT contenant les indicateurs d'état de paramètre.  
  
3.  Appelez SQLPrepare pour préparer l’instruction.  
  
4.  Pour chaque marqueur de paramètre, appelez SQLBindParameter pour pointer la valeur des données de paramètre et le pointeur de longueur des données vers leurs variables dans le premier élément du tableau de structures alloué à l’étape 1. Si le paramètre est un paramètre de données en cours d'exécution, installez-le.  
  
5.  Pour chaque exécution d'une instruction préparée :  
  
    -   Remplissez le tableau de tampons de paramètres liés avec les valeurs de données.  
  
    -   Appelez SQLExecute pour exécuter l'instruction préparée. Le pilote exécute efficacement l'instruction SQL S fois, une fois pour chaque jeu de paramètres.  
  
    -   Si des paramètres d'entrée de données en cours d'exécution sont utilisés, SQLExecute retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de SQLParamData et SQLPutData.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à l’exécution de requêtes &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
