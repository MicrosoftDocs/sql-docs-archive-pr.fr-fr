---
title: Guide pratique pour gérer un service CDC local | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 437590d4b91f2fc80d5bb8a90251bf0dc7c8e18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694672"
---
# <a name="how-to-manage-a-local-cdc-service"></a>Procédure : gérer un service de capture de données modifiées local
  Cette procédure décrit comment utiliser la console de configuration du service de capture de données modifiées pour gérer des services de capture de données modifiées spécifiques.  
  
### <a name="to-manage-a-specific-cdc-service"></a>Pour gérer un service de capture de données modifiées spécifique  
  
1.  Dans le menu **Démarrer** , sélectionnez **Configuration du service de capture de données modifiées pour Oracle**.  
  
2.  Dans le volet gauche de la console de configuration du service de capture de données modifiées, développez **Services de capture de données modifiées locaux**.  
  
3.  Sélectionnez le service de capture de données modifiées à utiliser.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée.  
  
     **OR**  
  
     Sélectionnez **Services de capture de données modifiées locaux** dans le volet gauche de la console de configuration du service de capture de données modifiées, puis sélectionnez le service que vous souhaitez utiliser dans la section centrale de la console de configuration du service de capture de données modifiées.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée.  
  
4.  Vous pouvez effectuer les tâches suivantes lorsque vous utilisez un service de capture de données modifiées.  
  
    -   **Supprimer le service**  
  
         Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Supprimer** pour supprimer le service.  
  
         Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées à supprimer et sélectionner **Supprimer**.  
  
         **Remarque**: si le service est en cours d'exécution lors de sa suppression, il est arrêté avant d'être supprimé.  
  
         Pour supprimer une définition de service Windows de capture de données modifiées Oracle, le programme doit disposer d'un accès de mise à jour à la base de données MSXDBCDC dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associée. Lorsque vous cliquez sur **OK** pour supprimer le service, le programme tente de supprimer l'inscription du service de capture de données modifiées Oracle dans la base de données MSXDBCDC. Si cette opération échoue en raison de l'absence d'autorisations, une boîte de dialogue s'affiche pour inviter l'utilisateur à entrer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un accès de mise à jour de la base de données MSXDBCDC.  
  
         Pour plus d'informations sur les données que vous devez taper dans la boîte de dialogue Connexion à SQL Server, consultez [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) et [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).  
  
    -   **Modifier les propriétés de service de capture de données modifiées**  
  
         Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Propriétés**.  
  
         Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées où vous souhaitez modifier les propriétés et sélectionner **Propriétés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer un service CDC Oracle](manage-an-oracle-cdc-service.md)  
  
  
