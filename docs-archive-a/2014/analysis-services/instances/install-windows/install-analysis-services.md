---
title: Installer Analysis Services en mode tabulaire | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697284"
---
# <a name="install-analysis-services-in-tabular-mode"></a>Installer Analysis Services en mode tabulaire
  Si vous installez Analysis Services afin d'utiliser les nouvelles fonctionnalités tabulaires de modélisation, vous devez installer Analysis Services dans un mode serveur qui prend en charge ce type de modèle. Le mode serveur est un mode tabulaire configuré pendant l'installation.  
  
 Après avoir installé le serveur dans ce mode, vous pouvez l'utiliser pour héberger des solutions que vous créez dans le générateur de modèle tabulaire. Un serveur en mode tabulaire est indispensable si vous souhaitez accéder aux données du modèle tabulaire par le réseau.  
  
 Vous pouvez spécifier le mode Tabulaire dans l'Assistant Installation ou dans une installation par ligne de commande. Les sections suivantes décrivent chaque méthode.  
  
## <a name="installation-wizard"></a>Assistant Installation  
 La liste suivante montre les pages de l'assistant Installation de SQL Server utilisées pour installer Analysis Services en mode tabulaire :  
  
1.  Sélectionnez **Analysis Services** dans l'Arborescence de fonctionnalités dans l'Installation.  
  
     ![Arborescence de la fonctionnalité Programme d'installation d'Analysis Services](../../../sql-server/install/media/ssas-setupas.gif "Arborescence de la fonctionnalité Programme d'installation d'Analysis Services")  
  
2.  Dans la page Configuration d'Analysis Services, veillez à sélectionner **Mode Tabulaire**.  
  
     ![Page installation avec les options de configuration d'Analysis Services](../../../sql-server/install/media/ssas-setupasconfig.gif "Page installation avec les options de configuration d'Analysis Services")  
  
 Le mode tabulaire utilise le moteur d'analyse en mémoire xVelocity (VertiPaq), qui est le stockage par défaut pour les modèles tabulaires que vous déployez dans Analysis Services. Après le déploiement des solutions de modèle tabulaire sur le serveur, vous pouvez configurer les solutions tabulaires de manière sélective pour qu'elles utilisent le stockage sur disque de DirectQuery comme alternative au stockage gourmand en mémoire.  
  
## <a name="command-line-setup"></a>Installation à partir de ligne de commande  
 L'installation de SQL Server inclut un nouveau paramètre (`ASSERVERMODE`) qui spécifie le mode serveur. L'exemple suivant illustre une installation par ligne de commande qui installe Analysis Services en mode serveur tabulaire.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 `INSTANCENAME` doit contenir moins de 17 caractères.  
  
 Toutes les valeurs de compte de l'espace réservé doivent être remplacées par des comptes valides et un mot de passe.  
  
 Des outils, tels que SQL Server Management Studio ou [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] , ne sont pas installés à l'aide de l'exemple de syntaxe de ligne de commande fourni. Pour plus d’informations sur l’ajout de fonctionnalités, voir [installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 `ASSERVERMODE` respecte la casse.  Toutes les valeurs doivent être exprimées en majuscules. Le tableau suivant décrit les valeurs valides pour `ASSERVERMODE`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|Valeur par défaut. Si vous ne définissez pas `ASSERVERMODE`, le serveur est installé en mode serveur multidimensionnel.|  
|POWERPIVOT|Cette valeur est facultative. En pratique, si vous définissez le paramètre `ROLE`, le mode serveur est automatiquement défini sur 1, ce qui rend `ASSERVERMODE` facultatif pour une installation de PowerPivot pour SharePoint. Pour plus d'informations, consultez [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).|  
|TABULAR|Cette valeur est obligatoire si vous installez Analysis Services en mode tabulaire à partir de la ligne de commande.|  
  
## <a name="see-also"></a>Voir aussi  
 [Déterminer le mode serveur d’une instance de Analysis Services](../determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Configurer l’accès en mémoire ou DirectQuery pour une base de données model tabulaire](../../tabular-models/enable-directquery-mode-in-ssms.md)   
 [Modélisation tabulaire &#40;la&#41;tabulaire SSAS](../../tabular-models/tabular-models-ssas.md)  
  
  
