---
title: SQLGetDescRec | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: rothja
ms.author: jroth
ms.openlocfilehash: 11e0e43b5c9cec15627b7f32ebe51fc28d74786c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602125"
---
# <a name="sqlgetdescrec"></a><span data-ttu-id="95c12-102">SQLGetDescRec</span><span class="sxs-lookup"><span data-stu-id="95c12-102">SQLGetDescRec</span></span>
  <span data-ttu-id="95c12-103">Cette rubrique décrit les fonctionnalités de SQLGetDescRec qui sont spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span><span class="sxs-lookup"><span data-stu-id="95c12-103">This topic discusses SQLGetDescRec functionality that is specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a><span data-ttu-id="95c12-104">SQLGetDescRec et paramètres table</span><span class="sxs-lookup"><span data-stu-id="95c12-104">SQLGetDescRec and Table-Valued Parameters</span></span>  
 <span data-ttu-id="95c12-105">SQLGetDescRec peut être utilisé pour obtenir des valeurs pour les attributs de paramètres table et les colonnes de paramètre table.</span><span class="sxs-lookup"><span data-stu-id="95c12-105">SQLGetDescRec can be used to get values for attributes of table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="95c12-106">Le paramètre *recnumber* de SQLGetDescRec correspond au paramètre *ParameterNumber* de SQLBindParameter.</span><span class="sxs-lookup"><span data-stu-id="95c12-106">The *RecNumber* parameter of SQLGetDescRec corresponds to the *ParameterNumber* parameter of SQLBindParameter.</span></span>  
  
 <span data-ttu-id="95c12-107">Les colonnes de paramètre table sont disponibles uniquement lorsque le champ d'en-tête de descripteur SQL_SOPT_SS_PARAM_FOCUS est défini sur l'ordinal d'un enregistrement pour lequel SQL_DESC_TYPE a la valeur SQL_SS_TABLE.</span><span class="sxs-lookup"><span data-stu-id="95c12-107">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="95c12-108">Pour plus d’informations sur les SQL_SOPT_SS_PARAM_FOCUS sur, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).</span><span class="sxs-lookup"><span data-stu-id="95c12-108">For more information about SQL_SOPT_SS_PARAM_FOCUS about, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="95c12-109">SQLGetDescRec retourne les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="95c12-109">SQLGetDescRec returns the following data:</span></span>  
  
|<span data-ttu-id="95c12-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="95c12-110">Parameter</span></span>|<span data-ttu-id="95c12-111">Paramètre table</span><span class="sxs-lookup"><span data-stu-id="95c12-111">Table-valued parameter</span></span>|<span data-ttu-id="95c12-112">Colonnes de paramètre table et autres paramètres</span><span class="sxs-lookup"><span data-stu-id="95c12-112">Table-valued parameter columns and other parameters</span></span>|  
|---------------|-----------------------------|----------------------------------------------------------|  
|<span data-ttu-id="95c12-113">*Nom*</span><span class="sxs-lookup"><span data-stu-id="95c12-113">*Name*</span></span>|<span data-ttu-id="95c12-114">Nom de paramètre formel pour un appel de procédure stockée ; sinon, chaîne de longueur 0.</span><span class="sxs-lookup"><span data-stu-id="95c12-114">The formal parameter name for a stored procedure call; otherwise, a 0 length string.</span></span>|<span data-ttu-id="95c12-115">Nom de la colonne de paramètre table.</span><span class="sxs-lookup"><span data-stu-id="95c12-115">The table-valued parameter column name.</span></span>|  
|<span data-ttu-id="95c12-116">*TypePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-116">*TypePtr*</span></span>|<span data-ttu-id="95c12-117">SQL_DESC_TYPE.</span><span class="sxs-lookup"><span data-stu-id="95c12-117">SQL_DESC_TYPE.</span></span> <span data-ttu-id="95c12-118">Pour les paramètres table, il s'agit de SQL_SS_TABLE.</span><span class="sxs-lookup"><span data-stu-id="95c12-118">For table-vaued parameters, this is SQL_SS_TABLE.</span></span>|<span data-ttu-id="95c12-119">SQL_DESC_TYPE</span><span class="sxs-lookup"><span data-stu-id="95c12-119">SQL_DESC_TYPE</span></span>|  
|<span data-ttu-id="95c12-120">*SubTypePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-120">*SubTypePtr*</span></span>|<span data-ttu-id="95c12-121">Indéfini</span><span class="sxs-lookup"><span data-stu-id="95c12-121">Undefined</span></span>|<span data-ttu-id="95c12-122">SQL_DESC_DATETIME_INTERVAL_CODE (pour les enregistrements de type SQL_DATETIME ou SQL_INTERVAL.)</span><span class="sxs-lookup"><span data-stu-id="95c12-122">SQL_DESC_DATETIME_INTERVAL_CODE (For records of type SQL_DATETIME or SQL_INTERVAL.)</span></span>|  
|<span data-ttu-id="95c12-123">*LengthPtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-123">*LengthPtr*</span></span>|<span data-ttu-id="95c12-124">0</span><span class="sxs-lookup"><span data-stu-id="95c12-124">0</span></span>|<span data-ttu-id="95c12-125">SQL_DESC_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="95c12-125">SQL_DESC_OCTET_LENGTH</span></span>|  
|<span data-ttu-id="95c12-126">*PrecisionPtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-126">*PrecisionPtr*</span></span>|<span data-ttu-id="95c12-127">0</span><span class="sxs-lookup"><span data-stu-id="95c12-127">0</span></span>|<span data-ttu-id="95c12-128">SQL_DESC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="95c12-128">SQL_DESC_PRECISION</span></span>|  
|<span data-ttu-id="95c12-129">*ScalePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-129">*ScalePtr*</span></span>|<span data-ttu-id="95c12-130">0</span><span class="sxs-lookup"><span data-stu-id="95c12-130">0</span></span>|<span data-ttu-id="95c12-131">SQL_DESC_SCALE</span><span class="sxs-lookup"><span data-stu-id="95c12-131">SQL_DESC_SCALE</span></span>|  
|<span data-ttu-id="95c12-132">*NullablePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-132">*NullablePtr*</span></span>|<span data-ttu-id="95c12-133">1</span><span class="sxs-lookup"><span data-stu-id="95c12-133">1</span></span>|<span data-ttu-id="95c12-134">SQL_DESC_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="95c12-134">SQL_DESC_NULLABLE</span></span>|  
  
 <span data-ttu-id="95c12-135">Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span><span class="sxs-lookup"><span data-stu-id="95c12-135">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="95c12-136">Prise en charge  par SQLGetDescRec des fonctionnalités de date et heure améliorées</span><span class="sxs-lookup"><span data-stu-id="95c12-136">SQLGetDescRec Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="95c12-137">Les valeurs retournées pour les types date/heure sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="95c12-137">The values returned for date/time types are as follows:</span></span>  
  
||<span data-ttu-id="95c12-138">*TypePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-138">*TypePtr*</span></span>|<span data-ttu-id="95c12-139">*SubTypePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-139">*SubTypePtr*</span></span>|<span data-ttu-id="95c12-140">*LengthPtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-140">*LengthPtr*</span></span>|<span data-ttu-id="95c12-141">*PrecisionPtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-141">*PrecisionPtr*</span></span>|<span data-ttu-id="95c12-142">*ScalePtr*</span><span class="sxs-lookup"><span data-stu-id="95c12-142">*ScalePtr*</span></span>|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|<span data-ttu-id="95c12-143">DATETIME</span><span class="sxs-lookup"><span data-stu-id="95c12-143">datetime</span></span>|<span data-ttu-id="95c12-144">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="95c12-144">SQL_DATETIME</span></span>|<span data-ttu-id="95c12-145">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="95c12-145">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="95c12-146">4</span><span class="sxs-lookup"><span data-stu-id="95c12-146">4</span></span>|<span data-ttu-id="95c12-147">3</span><span class="sxs-lookup"><span data-stu-id="95c12-147">3</span></span>|<span data-ttu-id="95c12-148">3</span><span class="sxs-lookup"><span data-stu-id="95c12-148">3</span></span>|  
|<span data-ttu-id="95c12-149">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="95c12-149">smalldatetime</span></span>|<span data-ttu-id="95c12-150">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="95c12-150">SQL_DATETIME</span></span>|<span data-ttu-id="95c12-151">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="95c12-151">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="95c12-152">8</span><span class="sxs-lookup"><span data-stu-id="95c12-152">8</span></span>|<span data-ttu-id="95c12-153">0</span><span class="sxs-lookup"><span data-stu-id="95c12-153">0</span></span>|<span data-ttu-id="95c12-154">0</span><span class="sxs-lookup"><span data-stu-id="95c12-154">0</span></span>|  
|<span data-ttu-id="95c12-155">Date</span><span class="sxs-lookup"><span data-stu-id="95c12-155">date</span></span>|<span data-ttu-id="95c12-156">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="95c12-156">SQL_DATETIME</span></span>|<span data-ttu-id="95c12-157">SQL_CODE_DATE</span><span class="sxs-lookup"><span data-stu-id="95c12-157">SQL_CODE_DATE</span></span>|<span data-ttu-id="95c12-158">6</span><span class="sxs-lookup"><span data-stu-id="95c12-158">6</span></span>|<span data-ttu-id="95c12-159">0</span><span class="sxs-lookup"><span data-stu-id="95c12-159">0</span></span>|<span data-ttu-id="95c12-160">0</span><span class="sxs-lookup"><span data-stu-id="95c12-160">0</span></span>|  
|<span data-ttu-id="95c12-161">time</span><span class="sxs-lookup"><span data-stu-id="95c12-161">time</span></span>|<span data-ttu-id="95c12-162">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="95c12-162">SQL_SS_TIME2</span></span>|<span data-ttu-id="95c12-163">0</span><span class="sxs-lookup"><span data-stu-id="95c12-163">0</span></span>|<span data-ttu-id="95c12-164">10</span><span class="sxs-lookup"><span data-stu-id="95c12-164">10</span></span>|<span data-ttu-id="95c12-165">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-165">0..7</span></span>|<span data-ttu-id="95c12-166">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-166">0..7</span></span>|  
|<span data-ttu-id="95c12-167">datetime2</span><span class="sxs-lookup"><span data-stu-id="95c12-167">datetime2</span></span>|<span data-ttu-id="95c12-168">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="95c12-168">SQL_DATETIME</span></span>|<span data-ttu-id="95c12-169">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="95c12-169">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="95c12-170">16</span><span class="sxs-lookup"><span data-stu-id="95c12-170">16</span></span>|<span data-ttu-id="95c12-171">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-171">0..7</span></span>|<span data-ttu-id="95c12-172">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-172">0..7</span></span>|  
|<span data-ttu-id="95c12-173">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="95c12-173">datetimeoffset</span></span>|<span data-ttu-id="95c12-174">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="95c12-174">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="95c12-175">0</span><span class="sxs-lookup"><span data-stu-id="95c12-175">0</span></span>|<span data-ttu-id="95c12-176">20</span><span class="sxs-lookup"><span data-stu-id="95c12-176">20</span></span>|<span data-ttu-id="95c12-177">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-177">0..7</span></span>|<span data-ttu-id="95c12-178">0..7</span><span class="sxs-lookup"><span data-stu-id="95c12-178">0..7</span></span>|  
  
 <span data-ttu-id="95c12-179">Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span><span class="sxs-lookup"><span data-stu-id="95c12-179">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a><span data-ttu-id="95c12-180">Prise en charge par SQLSetDescRec des grands types CLR définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="95c12-180">SQLGetDescRec Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="95c12-181">`SQLGetDescRec` prend en charge les grands types CLR définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95c12-181">`SQLGetDescRec` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="95c12-182">Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span><span class="sxs-lookup"><span data-stu-id="95c12-182">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c12-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95c12-183">See Also</span></span>  
 <span data-ttu-id="95c12-184">[SQLGetDescRec](https://go.microsoft.com/fwlink/?LinkId=80707) </span><span class="sxs-lookup"><span data-stu-id="95c12-184">[SQLGetDescRec](https://go.microsoft.com/fwlink/?LinkId=80707) </span></span>  
 [<span data-ttu-id="95c12-185">Détails de l’implémentation d’API ODBC</span><span class="sxs-lookup"><span data-stu-id="95c12-185">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  