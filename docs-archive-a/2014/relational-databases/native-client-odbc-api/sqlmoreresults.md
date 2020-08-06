---
title: SQLMoreResults | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLMoreResults function
ms.assetid: f65698c3-7291-480d-9dab-58b13feb7771
author: rothja
ms.author: jroth
ms.openlocfilehash: 58f306d585640dfb07c3a62aa1d885a4bf8ba56a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614031"
---
# <a name="sqlmoreresults"></a><span data-ttu-id="2172d-102">SQLMoreResults</span><span class="sxs-lookup"><span data-stu-id="2172d-102">SQLMoreResults</span></span>
  <span data-ttu-id="2172d-103">**SQLMoreResults** permet à l'application de récupérer plusieurs jeux de lignes de résultat.</span><span class="sxs-lookup"><span data-stu-id="2172d-103">**SQLMoreResults** allows the application to retrieve multiple sets of result rows.</span></span> <span data-ttu-id="2172d-104">Une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT contenant une clause COMPUTE, ou un lot soumis d'instructions ODBC ou [!INCLUDE[tsql](../../includes/tsql-md.md)] , entraîne la génération de plusieurs jeux de résultats par le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span><span class="sxs-lookup"><span data-stu-id="2172d-104">A [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement containing a COMPUTE clause, or a submitted batch of ODBC or [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, causes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver to generate multiple result sets.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2172d-105">n'autorise pas la création d'un curseur côté serveur pour traiter les résultats.</span><span class="sxs-lookup"><span data-stu-id="2172d-105">does not allow creating a server cursor to process the results in either case.</span></span> <span data-ttu-id="2172d-106">Par conséquent, le développeur doit s'assurer que l'instruction ODBC bloque.</span><span class="sxs-lookup"><span data-stu-id="2172d-106">Therefore, the developer must ensure that the ODBC statement is blocking.</span></span> <span data-ttu-id="2172d-107">Il doit consommer les données retournées ou annuler l'instruction ODBC avant de traiter les données des autres instructions actives sur la connexion.</span><span class="sxs-lookup"><span data-stu-id="2172d-107">The developer must exhaust the returned data or cancel the ODBC statement before processing data from other active statements on the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2172d-108">Une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT contenant une clause COMPUTE n'est prise en charge que lors de la connexion à une version de serveur antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2172d-108">A [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement containing a COMPUTE clause is only supported when connecting to a server version prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
 <span data-ttu-id="2172d-109">Le développeur peut déterminer les propriétés des colonnes et lignes de jeux de résultats qui sont générées par la clause COMPUTE d'un instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT.</span><span class="sxs-lookup"><span data-stu-id="2172d-109">The developer can determine properties of the result sets columns and rows that are generated by the COMPUTE clause of a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement.</span></span> <span data-ttu-id="2172d-110">Pour plus d'informations, consultez [SQLColAttribute](sqlcolattribute.md).</span><span class="sxs-lookup"><span data-stu-id="2172d-110">For more detail, see [SQLColAttribute](sqlcolattribute.md).</span></span>  
  
 <span data-ttu-id="2172d-111">Lorsque **SQLMoreResults** est appelé avec des lignes de données non extraites dans le jeu de résultats, ces lignes sont perdues, et les données de ligne du jeu de lignes de résultat suivant sont rendues disponibles.</span><span class="sxs-lookup"><span data-stu-id="2172d-111">When **SQLMoreResults** is called with unfetched data rows in the result set, those rows are lost, and row data from the next result row set is made available.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2172d-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="2172d-112">Examples</span></span>  
  
```  
void GetComputedRows  
    (  
    SQLHSTMT hStmt  
    )   
    {  
    SQLUSMALLINT    nCols;  
    SQLUSMALLINT    nCol;  
    PODBCSETINFO    pODBCSetInfo = NULL;  
    SQLRETURN       sRet;  
    UINT            nRow;  
    SQLINTEGER      nComputes = 0;  
    SQLINTEGER      nSet;  
    BYTE*           pValue;  
  
    // If SQLNumResultCols failed, then some error occurred in  
    //  statement execution. Exit.  
    if (!SQL_SUCCEEDED(SQLNumResultCols(hStmt, (SQLSMALLINT*) &nCols)))  
        {  
        goto EXIT;  
        }  
  
    // Determine the presence of COMPUTE clause result sets. The SQL  
    //  Server Native Client ODBC driver uses column attributes to report multiple  
    //  sets. The column number must be less than or equal to the   
    //  number of columns returned. You are guaranteed to have at least  
    //  one, so use '1' for the SQLColAttribute ColumnNumber  
    //  parameter.  
    SQLColAttribute(hStmt, 1, SQL_CA_SS_NUM_COMPUTES,  
        NULL, 0, NULL, (SQLPOINTER) &nComputes);  
  
    // Create a result info structure pointer array, one element for  
    //  the normal result rows and one for each compute result set.  
    //  Initialize the array to NULL pointers.  
    pODBCSetInfo = new ODBCSETINFO[1 + nComputes];  
  
    // Process the result sets...  
    nSet = 0;  
    while (TRUE)  
        {  
        // If required, get the column information for the result set.  
        if (pODBCSetInfo[nSet].pODBCColInfo == NULL)  
            {  
            if (pODBCSetInfo[nSet].nCols == 0)  
                {  
                SQLNumResultCols(hStmt, (SQLSMALLINT*) &nCols);  
                pODBCSetInfo[nSet].nCols = nCols;  
                }  
  
            if (GetColumnsInfo(hStmt, pODBCSetInfo[nSet].nCols,  
                &(pODBCSetInfo[nSet].pODBCColInfo)) == SQL_ERROR)  
                {  
                goto EXIT;  
                }  
            }  
  
        // Get memory for bound return values if required.  
        if (pODBCSetInfo[nSet].pRowValues == NULL)  
            {  
            CreateBindBuffer(&(pODBCSetInfo[nSet]));  
            }  
  
        // Rebind columns each time the result set changes.  
        myBindCols(hStmt, pODBCSetInfo[nSet].nCols,  
            pODBCSetInfo[nSet].pODBCColInfo,  
            pODBCSetInfo[nSet].pRowValues);  
  
        // Set for ODBC row array retrieval. Fast retrieve for all  
        //  sets. COMPUTE row sets have only a single row, but  
        //  normal rows can be retrieved in blocks for speed.  
        SQLSetStmtAttr(hStmt, SQL_ATTR_ROW_BIND_TYPE,  
            (void*) pODBCSetInfo[nSet].nResultWidth, SQL_IS_UINTEGER);  
        SQLSetStmtAttr(hStmt, SQL_ATTR_ROW_ARRAY_SIZE,  
            (void*) pODBCSetInfo[nSet].nRows, SQL_IS_UINTEGER);  
        SQLSetStmtAttr(hStmt, SQL_ATTR_ROWS_FETCHED_PTR,  
            (void*) &nRowsFetched, sizeof(SQLINTEGER));  
  
        while (TRUE)  
            {  
            // In ODBC 3.x, SQLFetch supports arrays of bound rows or  
            //  columns. SQLFetchScroll (or ODBC 2.x SQLExtendedFetch)  
            //  is not necessary to support fastest retrieval of   
            //  data rows.  
            if (!SQL_SUCCEEDED(sRet = SQLFetch(hStmt)))  
                {  
                break;  
                }  
  
            for (nRow = 0; nRow < (UINT) nRowsFetched; nRow++)  
                {  
                for (nCol = 0; nCol < pODBCSetInfo[nSet].nCols;  
                        nCol++)  
                    {  
                    // Processing row and column values...  
                    }  
                }  
            }  
  
        // sRet is not SQL_SUCCESS and is not SQL_SUCCESS_WITH_INFO.  
        //  If it's SQL_NO_DATA, then continue. If it's an  
        //  error state, stop.  
        if (sRet != SQL_NO_DATA)  
            {  
            break;  
            }  
  
        // If there's another set waiting, determine the result set  
        //  indicator. The indicator is 0 for regular row sets or an  
        //  ordinal indicating the COMPUTE clause responsible for the  
        //  set.  
        if (SQLMoreResults(hStmt) == SQL_SUCCESS)  
            {  
            sRet = SQLColAttribute(hStmt, 1, SQL_CA_SS_COMPUTE_ID,  
                NULL, 0, NULL, (SQLPOINTER) &nSet);  
            }  
        else  
            {  
            break;  
            }  
        }  
  
EXIT:  
    // Clean-up anything dynamically allocated and return.  
    return;  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="2172d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2172d-113">See Also</span></span>  
 <span data-ttu-id="2172d-114">[Fonction SQLMoreResults](https://go.microsoft.com/fwlink/?LinkId=59357) </span><span class="sxs-lookup"><span data-stu-id="2172d-114">[SQLMoreResults Function](https://go.microsoft.com/fwlink/?LinkId=59357) </span></span>  
 [<span data-ttu-id="2172d-115">Détails de l’implémentation d’API ODBC</span><span class="sxs-lookup"><span data-stu-id="2172d-115">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  