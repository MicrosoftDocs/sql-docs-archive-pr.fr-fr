---
title: SQLDescribeCol | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: rothja
ms.author: jroth
ms.openlocfilehash: bc7ca9602e433f5e9ad26c39117e216eb0cc9564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705119"
---
# <a name="sqldescribecol"></a><span data-ttu-id="b75cb-102">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="b75cb-102">SQLDescribeCol</span></span>
  <span data-ttu-id="b75cb-103">Pour les instructions exécutées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’a pas besoin d’interroger le serveur pour décrire les colonnes d’un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="b75cb-103">For executed statements, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not need to query the server to describe columns in a result set.</span></span> <span data-ttu-id="b75cb-104">Dans ce cas, `SQLDescribeCol` n’entraîne pas l’aller-retour du serveur.</span><span class="sxs-lookup"><span data-stu-id="b75cb-104">In this case, `SQLDescribeCol` does not cause a server roundtrip.</span></span> <span data-ttu-id="b75cb-105">Comme [SQLColAttribute](sqlnumresultcols.md), l’appel `SQLDescribeCol` de sur des instructions préparées mais non exécutées génère un aller-retour sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b75cb-105">Like [SQLColAttribute](sqlnumresultcols.md), calling `SQLDescribeCol` on prepared but not executed statements generates a server roundtrip.</span></span>  
  
 <span data-ttu-id="b75cb-106">Lorsqu'une instruction ou un lot d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] retourne plusieurs ensembles de lignes de résultats, il est possible qu'une colonne, référencée par un ordinal, ait pour origine une table distincte ou référence une colonne entièrement différente dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="b75cb-106">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statement batch returns multiple result row sets, it is possible for a column, referenced by ordinal, to originate in a separate table or to refer to an entirely different column in the result set.</span></span> <span data-ttu-id="b75cb-107">`SQLDescribeCol`doit être appelé pour chaque ensemble.</span><span class="sxs-lookup"><span data-stu-id="b75cb-107">`SQLDescribeCol` should be called for each set.</span></span> <span data-ttu-id="b75cb-108">Lorsque le jeu de résultats change, l'application doit de nouveau lier les valeurs de données avant d'extraire les résultats de ligne.</span><span class="sxs-lookup"><span data-stu-id="b75cb-108">When the result set changes, the application should rebind data values prior to fetching row results.</span></span> <span data-ttu-id="b75cb-109">Pour plus d'informations sur la gestion de plusieurs retours de jeux de résultats, consultez [SQLMoreResults](sqlmoreresults.md).</span><span class="sxs-lookup"><span data-stu-id="b75cb-109">For more information about handling multiple result set returns, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="b75cb-110">Les attributs de colonnes sont signalés uniquement pour le premier jeu de résultats lorsque plusieurs jeux de résultats sont générés par un lot préparé d'instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="b75cb-110">Column attributes are reported for only the first result set when multiple result sets are generated by a prepared batch of SQL statements.</span></span>  
  
 <span data-ttu-id="b75cb-111">Pour les types de données de valeur élevée, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR.</span><span class="sxs-lookup"><span data-stu-id="b75cb-111">For large value data types, the value returned in *DataTypePtr* is SQL_VARCHAR, SQL_VARBINARY, or SQL_NVARCHAR.</span></span> <span data-ttu-id="b75cb-112">La valeur SQL_SS_LENGTH_UNLIMITED dans *ColumnSizePtr* indique que la taille est « illimitée ».</span><span class="sxs-lookup"><span data-stu-id="b75cb-112">A value of SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* indicates that the size is "unlimited".</span></span>  
  
 <span data-ttu-id="b75cb-113">Les améliorations apportées au moteur de base de données à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permettent à SQLDescribeCol d’obtenir des descriptions plus précises des résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="b75cb-113">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLDescribeCol to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="b75cb-114">Ces résultats plus précis peuvent différer des valeurs retournées par SQLDescribeCol dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b75cb-114">These more accurate results may differ from the values returned by SQLDescribeCol in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b75cb-115">Pour plus d’informations, consultez [Découverte des métadonnées](../native-client/features/metadata-discovery.md).</span><span class="sxs-lookup"><span data-stu-id="b75cb-115">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="b75cb-116">Prise en charge par SQLDescribeCol des fonctionnalités de date et heure améliorées</span><span class="sxs-lookup"><span data-stu-id="b75cb-116">SQLDescribeCol Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="b75cb-117">Les valeurs retournées pour les types date/heure sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b75cb-117">The values returned for date/time types are as follows:</span></span>  
  
||<span data-ttu-id="b75cb-118">*DataTypePtr*</span><span class="sxs-lookup"><span data-stu-id="b75cb-118">*DataTypePtr*</span></span>|<span data-ttu-id="b75cb-119">*ColumnSizePtr*</span><span class="sxs-lookup"><span data-stu-id="b75cb-119">*ColumnSizePtr*</span></span>|<span data-ttu-id="b75cb-120">*DecimalDigitsPtr*</span><span class="sxs-lookup"><span data-stu-id="b75cb-120">*DecimalDigitsPtr*</span></span>|  
|-|-------------------|---------------------|------------------------|  
|<span data-ttu-id="b75cb-121">DATETIME</span><span class="sxs-lookup"><span data-stu-id="b75cb-121">datetime</span></span>|<span data-ttu-id="b75cb-122">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="b75cb-122">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="b75cb-123">23</span><span class="sxs-lookup"><span data-stu-id="b75cb-123">23</span></span>|<span data-ttu-id="b75cb-124">3</span><span class="sxs-lookup"><span data-stu-id="b75cb-124">3</span></span>|  
|<span data-ttu-id="b75cb-125">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="b75cb-125">smalldatetime</span></span>|<span data-ttu-id="b75cb-126">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="b75cb-126">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="b75cb-127">16</span><span class="sxs-lookup"><span data-stu-id="b75cb-127">16</span></span>|<span data-ttu-id="b75cb-128">0</span><span class="sxs-lookup"><span data-stu-id="b75cb-128">0</span></span>|  
|<span data-ttu-id="b75cb-129">Date</span><span class="sxs-lookup"><span data-stu-id="b75cb-129">date</span></span>|<span data-ttu-id="b75cb-130">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="b75cb-130">SQL_TYPE_DATE</span></span>|<span data-ttu-id="b75cb-131">10</span><span class="sxs-lookup"><span data-stu-id="b75cb-131">10</span></span>|<span data-ttu-id="b75cb-132">0</span><span class="sxs-lookup"><span data-stu-id="b75cb-132">0</span></span>|  
|<span data-ttu-id="b75cb-133">time</span><span class="sxs-lookup"><span data-stu-id="b75cb-133">time</span></span>|<span data-ttu-id="b75cb-134">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="b75cb-134">SQL_SS_TIME2</span></span>|<span data-ttu-id="b75cb-135">8, 10..16</span><span class="sxs-lookup"><span data-stu-id="b75cb-135">8, 10..16</span></span>|<span data-ttu-id="b75cb-136">0..7</span><span class="sxs-lookup"><span data-stu-id="b75cb-136">0..7</span></span>|  
|<span data-ttu-id="b75cb-137">datetime2</span><span class="sxs-lookup"><span data-stu-id="b75cb-137">datetime2</span></span>|<span data-ttu-id="b75cb-138">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="b75cb-138">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="b75cb-139">19, 21..27</span><span class="sxs-lookup"><span data-stu-id="b75cb-139">19, 21..27</span></span>|<span data-ttu-id="b75cb-140">0..7</span><span class="sxs-lookup"><span data-stu-id="b75cb-140">0..7</span></span>|  
|<span data-ttu-id="b75cb-141">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="b75cb-141">datetimeoffset</span></span>|<span data-ttu-id="b75cb-142">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="b75cb-142">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="b75cb-143">26, 28..34</span><span class="sxs-lookup"><span data-stu-id="b75cb-143">26, 28..34</span></span>|<span data-ttu-id="b75cb-144">0..7</span><span class="sxs-lookup"><span data-stu-id="b75cb-144">0..7</span></span>|  
  
 <span data-ttu-id="b75cb-145">Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span><span class="sxs-lookup"><span data-stu-id="b75cb-145">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a><span data-ttu-id="b75cb-146">Prise en charge par SQLDescribeCol des grands types CLR définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b75cb-146">SQLDescribeCol Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="b75cb-147">`SQLDescribeCol` prend en charge les grands types CLR définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b75cb-147">`SQLDescribeCol` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="b75cb-148">Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span><span class="sxs-lookup"><span data-stu-id="b75cb-148">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75cb-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b75cb-149">See Also</span></span>  
 <span data-ttu-id="b75cb-150">[Fonction SQLDescribeCol](https://go.microsoft.com/fwlink/?LinkID=59338) </span><span class="sxs-lookup"><span data-stu-id="b75cb-150">[SQLDescribeCol Function](https://go.microsoft.com/fwlink/?LinkID=59338) </span></span>  
 [<span data-ttu-id="b75cb-151">Détails de l’implémentation d’API ODBC</span><span class="sxs-lookup"><span data-stu-id="b75cb-151">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  