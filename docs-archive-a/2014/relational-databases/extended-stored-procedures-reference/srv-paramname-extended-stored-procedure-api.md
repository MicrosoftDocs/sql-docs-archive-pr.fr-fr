---
title: srv_paramname (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2227ac3d46efe7d09abc05964248229f3533d42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709484"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a>srv_paramname (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le nom d'un paramètre d'appel de procédure stockée distante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui correspond au handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu l'appel de procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *n*  
 Indique le numéro du paramètre. Le premier paramètre est 1.  
  
 *Len*  
 Fournit un pointeur vers une variable `int` qui contient la longueur, en octets, du nom de paramètre. Si *len* est NULL, la longueur du nom de paramètre de procédure stockée distante n’est pas retournée.  
  
## <a name="returns"></a>Retours  
 Pointeur vers une chaîne de caractères terminée par le caractère NULL qui contient le nom du paramètre. La longueur du nom de paramètre est stockée dans *len*. S’il n’y a aucun *n*ième paramètre ni aucune procédure stockée distante, la valeur NULL est retournée, la valeur -1 est affectée à *len* et un message d’erreur d’information est envoyé. Si le nom de paramètre est NULL, la valeur 0 est affectée à *len* et une chaîne vide se terminant par NULL est retournée.  
  
## <a name="remarks"></a>Notes  
 Cette fonction obtient le nom d'un paramètre d'appel de procédure stockée distante. Quand un appel de procédure stockée distante est effectué avec des paramètres, ceux-ci peuvent être passés par nom ou par position (sans nom). Si l'appel de procédure stockée distante est effectué avec certains paramètres passés par nom et certains passés par position, une erreur se produit. Le gestionnaire SRV_RPC est tout de même appelé, mais il apparaît comme s’il n’y avait aucun paramètre et **srv_rpcparams** retourne 0.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_rpcparams &#40;API de procédure stockée étendue&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
