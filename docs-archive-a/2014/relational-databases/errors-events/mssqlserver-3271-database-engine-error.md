---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56bdb5875dbba3fbe5037a308d713170a9b6f9ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604512"
---
# <a name="mssqlserver_3271"></a>MSSQLSERVER_3271
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|3271|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DMPIO_IO_ERROR|  
|Texte du message|Une erreur d'E/S non récupérable s'est produite dans le fichier "%ls" : %ls|  
  
## <a name="explanation"></a>Explication  
 Il s'agit d'une erreur générale qui survient lorsque le système d'exploitation déclenche une erreur en effectuant une E/S au cours d'une opération de sauvegarde ou de restauration. La cause la plus courante est simplement que le support de sauvegarde est plein.  
  
 L'erreur peut inclure un texte supplémentaire du système d'exploitation indiquant que le disque est plein. Lorsque vous effectuez une opération de sauvegarde ou de restauration à l'aide d'un logiciel tiers de sauvegarde, un message supplémentaire peut s'afficher pour signaler l'échec de la sauvegarde. Il peut se formuler comme suit :  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 Ceci indique que le logiciel de sauvegarde a demandé l'arrêt de l'opération de sauvegarde ou de restauration.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Effectuez les tâches suivantes comme il convient :  
  
-   Consultez les messages d'erreur du système sous-jacent et de SQL Server qui ont précédé, afin d'identifier la cause de la défaillance.  
  
-   Assurez-vous que le support de sauvegarde et de restauration possède suffisamment d'espace.  
  
-   Corrigez toutes les erreurs déclenchées par le logiciel tiers de sauvegarde et de restauration.  
  
  
