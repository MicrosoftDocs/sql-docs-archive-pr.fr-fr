---
title: Noms des sources de données et systèmes d’exploitation 64 bits | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602808"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a><span data-ttu-id="50d2f-102">Noms des sources de données et systèmes d'exploitation 64 bits</span><span class="sxs-lookup"><span data-stu-id="50d2f-102">Data Source Names and 64-Bit Operating Systems</span></span>
  <span data-ttu-id="50d2f-103">Pour générer et exécuter une application en tant qu'application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC à l'aide de l'Administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.</span><span class="sxs-lookup"><span data-stu-id="50d2f-103">To build and run an application as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50d2f-104">Notes</span><span class="sxs-lookup"><span data-stu-id="50d2f-104">Remarks</span></span>  
 <span data-ttu-id="50d2f-105">Un système d'exploitation Windows 64 bits possède deux fichiers odbcad32.exe :</span><span class="sxs-lookup"><span data-stu-id="50d2f-105">A 64-bit Windows operating system has two odbcad32.exe files:</span></span>  
  
-   <span data-ttu-id="50d2f-106">%SystemRoot%\system32\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="50d2f-106">%SystemRoot%\system32\odbcad32.exe is used to create and maintain data source names for 64-bit applications.</span></span>  
  
-   <span data-ttu-id="50d2f-107">%SystemRoot%\SysWOW64\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 32 bits, y compris les applications 32 bits qui s'exécutent sur des systèmes d'exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="50d2f-107">%SystemRoot%\SysWOW64\odbcad32.exe is used to create and maintain data source names for 32-bit applications, including 32-bit applications that run on 64-bit operating systems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d2f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50d2f-108">See Also</span></span>  
 [<span data-ttu-id="50d2f-109">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="50d2f-109">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  