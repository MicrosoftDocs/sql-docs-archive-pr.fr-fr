---
title: Configurer un pare-feu pour l’accès FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612979"
---
# <a name="configure-a-firewall-for-filestream-access"></a>Configurer un pare-feu pour l'accès FILESTREAM
  Pour pouvoir utiliser FILESTREAM dans un environnement protégé par un pare-feu, le client et le serveur doivent être en mesure de résoudre les noms DNS sur le serveur qui contient les fichiers FILESTREAM. FILESTREAM requiert l'ouverture des ports 139 et 445 dédiés au partage de fichiers Windows.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Pour ouvrir les ports de partage de fichiers Windows sur un ordinateur qui exécute Windows 7  
  
1.  Dans le Panneau de configuration, ouvrez **Pare-feu Windows**.  
  
2.  Dans le volet gauche, cliquez sur **Paramètres avancés**. Si vous êtes invité à entrer un mot de passe administrateur ou une confirmation, tapez le mot de passe ou confirmez.  
  
3.  Dans la boîte de dialogue **Pare-feu Windows avec fonctions avancées de sécurité** , dans le volet gauche, cliquez sur **Règles de trafic entrant**, puis, dans le volet droit, cliquez sur **Nouvelle règle**.  
  
4.  Suivez les instructions de l'Assistant Nouvelle règle de trafic entrant pour ajouter le port TCP 139.  
  
5.  Répétez l'étape précédente pour ajouter le port TCP 445.  
  
6.  Fermez la boîte de dialogue **Pare-feu Windows avec fonctions avancées de sécurité** .  
  
  
