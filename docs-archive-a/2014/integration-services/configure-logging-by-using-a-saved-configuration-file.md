---
title: Configurer la journalisation à l’aide d’un fichier de configuration enregistré | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8eb517462d9e932906f739678fbd46c1004fb84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611228"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a>Configurer la journalisation à l'aide d'un fichier de configuration enregistré
  Cette procédure permet de configurer la journalisation de nouveaux conteneurs dans un package en chargeant un fichier de configuration de journalisation déjà enregistré.  
  
 Par défaut, tous les conteneurs d'un package utilisent la même configuration de journalisation que leur conteneur parent. Par exemple, les tâches d'une boucle Foreach utilisent la même configuration de journalisation que la boucle Foreach.  
  
### <a name="to-configure-logging-for-a-container"></a>Pour configurer la journalisation pour un conteneur  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans le menu **SSIS** , cliquez sur **Enregistrement**.  
  
3.  Développez l'arborescence du package et sélectionnez le conteneur à configurer.  
  
4.  Sous l’onglet **Fournisseurs et journaux** , sélectionnez les journaux à utiliser pour le conteneur.  
  
    > [!NOTE]  
    >  Vous ne pouvez créer des journaux qu'au niveau du package. Pour plus d’informations, consultez [Activer la journalisation des packages dans les outils de données SQL Server](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
5.  Cliquez sur l’onglet **Détails** , puis sur **Charger**.  
  
6.  Recherchez le fichier de configuration de journalisation que vous voulez utiliser et cliquez sur **Ouvrir**.  
  
7.  Si vous le souhaitez, sélectionnez une entrée de journal différente à consigner en cochant la case correspondante dans la colonne **Événements** . Cliquez sur **Avancé** pour sélectionner le type d’information à consigner pour cette entrée.  
  
    > [!NOTE]  
    >  Le nouveau conteneur peut inclure des entrées de journal supplémentaires qui ne sont pas disponibles pour le conteneur utilisé à l'origine pour créer la configuration de journalisation. Ces entrées de journal supplémentaires doivent être sélectionnées manuellement si vous voulez qu'elles soient journalisées.  
  
8.  Pour enregistrer la version mise à jour de la configuration de journalisation, cliquez sur **Enregistrer**.  
  
9. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
