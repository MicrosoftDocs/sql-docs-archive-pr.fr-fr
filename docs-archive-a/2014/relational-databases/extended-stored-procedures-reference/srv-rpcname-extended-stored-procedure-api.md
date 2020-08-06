---
title: srv_rpcname (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
author: rothja
ms.author: jroth
ms.openlocfilehash: 21530b3e7b8aaa8c5a3f8770762cde7e258e3a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709476"
---
# <a name="srv_rpcname-extended-stored-procedure-api"></a>srv_rpcname (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le composant de nom de procédure pour la procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *Len*  
 Pointeur vers une variable de type entier qui reçoit la longueur du nom de la base de données. Si *len* est NULL, la longueur du nom de procédure stockée distante n'est pas retournée.  
  
## <a name="returns"></a>Retours  
 Un pointeur DBCHAR vers la chaîne terminée par le caractère NULL pour le composant de nom de procédure stockée distante de la procédure stockée distante actuelle. S'il n'y a pas de procédure stockée distante actuelle, NULL est retourné et *len* est défini à -1.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne uniquement le nom de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le propriétaire, le nom de la base de données et le numéro de procédure stockée distante.  
  
 Étant donné qu'il est valide d'appeler **srv_rpcname** lorsqu'il n'y a pas de procédure stockée distante (aucune erreur informative ne se produit), cette fonction fournit une méthode pour déterminer si une procédure stockée distante existe.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
