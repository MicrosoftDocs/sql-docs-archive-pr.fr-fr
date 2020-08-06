---
title: Présentation des erreurs du moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa8747066433488a8517d2931ad51f082075a66f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610646"
---
# <a name="understanding-database-engine-errors"></a>Présentation des erreurs du moteur de base de données
  Les attributs des erreurs déclenchées par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] sont décrits dans le tableau suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|Numéro d'erreur|Chaque message d'erreur possède un numéro d'erreur unique.|  
|Chaîne de message d'erreur|Le message d'erreur contient des informations sur la cause probable de l'erreur. De nombreux messages d'erreur ont des variables de substitution contenant des informations telles que le nom de l'objet à l'origine de l'erreur.|  
|severity|La gravité indique l'importance de l'erreur. Les erreurs dont le degré de gravité est faible (1 ou 2), sont de simples messages d'information ou des avertissements peu importants. Si le degré de gravité est élevé, le problème doit être résolu le plus rapidement possible. Pour plus d’informations sur les niveaux de gravité, consultez [Niveaux de gravité des erreurs du moteur de base de données](database-engine-error-severities.md).|  
|State|Certains messages d'erreur peuvent apparaître en de multiples endroits du code du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. L'erreur 1105 par exemple, peut être provoquée par différentes conditions. Un code d'état unique est assigné à chaque condition spécifique qui déclenche une erreur.<br /><br /> Lors de la consultation de bases de données contenant des informations sur les problèmes connus, par exemple la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] , le numéro d'état vous permet de déterminer si le problème enregistré est identique à l'erreur rencontrée. Par exemple, si un article de la Base de connaissances décrit l'erreur 1105 avec le numéro d'état 2, et si le message d'erreur 1105 que vous avez reçu a le numéro d'état 3, il est probable que l'erreur n'a pas la même origine que celle signalée dans l'article.<br /><br /> Un ingénieur du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] peut également utiliser le code d'état d'une erreur pour déterminer l'emplacement du code source d'où provient ce code d'erreur. Ces informations peuvent apporter des indications supplémentaires sur la façon de diagnostiquer le problème.|  
|Nom de la procédure|Nom de la procédure stockée ou du déclencheur dans lequel l'erreur s'est produite.|  
|Numéro de ligne|Indique l'instruction qui a provoqué l'erreur dans un traitement, une procédure stockée, un déclencheur ou une fonction.|  
  
 Tous les messages d’erreur système et tous les messages d’erreur définis par l’utilisateur dans une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont contenus dans l’affichage catalogue **sys.messages** . Vous pouvez utiliser l'instruction RAISERROR pour retourner à une application des messages d'erreur définis par l'utilisateur.  
  
 Toutes les API de base de données, telles que l’espace de noms **SQLClient** de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], ADO (ActiveX Data Objects), OLE DB et ODBC (Open DataBase Connectivity) signalent les attributs d’erreur de base. Ces informations comprennent le numéro de l'erreur et la chaîne du message. Cependant, toutes les API ne signalent pas l'ensemble des autres attributs d'erreur.  
  
 Les informations relatives à une erreur qui se produit dans la portée du bloc TRY d’une construction TRY...CATCH peuvent être obtenues en code [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de fonctions telles que ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY et ERROR_STATE dans la portée du bloc CATCH associé. Pour plus d’informations, consultez [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant interroge l'affichage catalogue `sys.messages` pour renvoyer une liste de tous les messages d'erreur système et de tous les messages d'erreur définis par l'utilisateur du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui contiennent du texte anglais (`1033`).  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 Pour plus d’informations, consultez [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).  
  
## <a name="see-also"></a>Voir aussi  
 [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)   
 [@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql)   
 [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)   
 [ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql)   
 [ERROR_STATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-state-transact-sql)  
  
  
