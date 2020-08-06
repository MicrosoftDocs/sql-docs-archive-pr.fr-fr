---
title: SqlToolsVSNativeHelpers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84f8a3a3408b68cb8c389b05b417f391a1f86c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710492"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
  Bibliothèque qui prend en charge les fonctionnalités de SQL Server dans Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne, `True` si le point d'entrée de la DLL s'est initialisé correctement, sinon `False`.  
  
## <a name="see-also"></a>Voir aussi  
 [FrameWindowVisible](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
