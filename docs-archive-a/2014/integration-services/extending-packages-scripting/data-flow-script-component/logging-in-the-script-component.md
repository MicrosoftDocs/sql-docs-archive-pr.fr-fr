---
title: Journalisation dans le composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c29dfffee6cacb39272aef07caa5539555cdd4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611162"
---
# <a name="logging-in-the-script-component"></a>Journalisation dans le composant Script
  La journalisation dans des packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] vous permet d'enregistrer des informations détaillées sur l'avancement, les résultats et les problèmes d'exécution en enregistrant des événements prédéfinis ou des messages définis par l'utilisateur en vue d'une analyse ultérieure. Le composant Script peut utiliser la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> de la classe `ScriptMain` pour enregistrer des données définies par l'utilisateur. Si la journalisation est activée et que l’événement **ScriptComponentLogEntry** est sélectionné pour la journalisation sous l’onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS**, un seul appel à la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> stocke les informations sur l’événement dans tous les modules fournisseurs d’informations configurés pour la tâche de flux de données.  
  
 Voici un exemple simple de journalisation :  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Bien qu'il soit possible d'exécuter la journalisation directement à partir du composant Script, il peut être préférable d'implémenter des événements plutôt que la journalisation. L'utilisation d'événements vous permet non seulement d'activer la journalisation des messages d'événements, mais également de répondre à un événement à l'aide de gestionnaires d'événements par défaut ou définis par l'utilisateur.  
  
 Pour plus d’informations sur la journalisation, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md).  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md)  
  
  
