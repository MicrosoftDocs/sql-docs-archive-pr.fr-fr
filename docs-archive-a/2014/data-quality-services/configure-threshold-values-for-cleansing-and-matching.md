---
title: Configurer les valeurs de seuil pour le nettoyage et la correspondance | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696083"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Configurer les valeurs de seuil pour le nettoyage et la correspondance
  Cette rubrique explique comment configurer les valeurs de seuil qui seront utilisées pendant les activités de nettoyage et de correspondance assistées par ordinateur dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour configurer ces valeurs de seuil.  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> Configuration des valeurs de seuil  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Configuration**.  
  
3.  Ensuite, cliquez sur l’onglet **paramètres généraux** . Cet onglet vous permet de spécifier des valeurs de seuil pour les activités de nettoyage et de correspondance.  
  
4.  Pour spécifier des valeurs de seuil pour l'activité de nettoyage, spécifiez les valeurs appropriées dans les zones suivantes sous la zone **Nettoyage interactif** :  
  
    -   **Score minimal pour les suggestions**: score ou niveau de confiance minimal qui sera utilisé par DQS pour suggérer des remplacements d'une valeur pendant le processus de nettoyage assisté par ordinateur. Entrez une valeur en notation décimale de la valeur de pourcentage correspondante. Par exemple, tapez 0,75 pou 75 %. Cette valeur doit être inférieure ou égale à la valeur spécifiée dans la zone **Score minimal pour les corrections automatiques** . La valeur par défaut est 0,7.  
  
    -   **Score minimal pour les corrections automatiques**: score ou niveau de confiance minimal qui sera utilisé par DQS pour corriger automatiquement une valeur pendant le processus de nettoyage assisté par ordinateur. Entrez une valeur en notation décimale de la valeur de pourcentage correspondante. Par exemple, entrez 0,9 pour 90 %. La valeur par défaut est 0,8.  
  
5.  Pour spécifier la valeur de seuil pour l'activité de correspondance, spécifiez une valeur dans la zone **Score d'enregistrement minimal** sous la zone **Correspondance** . Cette valeur représente le score minimal pour qu'un enregistrement soit considéré comme une correspondance d'un autre enregistrement. La valeur par défaut est 80 %.  
  
6.  Cliquez sur **Fermer**.  
  
  
