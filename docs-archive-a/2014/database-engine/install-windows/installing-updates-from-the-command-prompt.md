---
title: Installation de mises à jour à partir de l’invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3ced6cd72bfc972743d0f9d8c7c2a9ce57dfdd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601643"
---
# <a name="installing-updates-from-the-command-prompt"></a>Installation de mises à jour à partir de l'invite de commandes
  Testez et modifiez les scripts d'installation selon les besoins de votre organisation.  
  
## <a name="sample-syntax-for-installation"></a>Exemple de syntaxe pour l'installation  
 Le nom du package de mise à jour peut varier et inclure une langue, une édition et un processeur. Appliquez une mise à jour à partir de l'invite de commandes en remplaçant <nom_package> par le nom de votre package de mise à jour :  
  
-   Mettez à jour une seule instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et tous les composants partagés, comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et Outils d’administration : Vous pouvez spécifier l'instance à l'aide du paramètre InstanceName ou du paramètre InstanceID. Pour mettre à jour une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez spécifier le paramètre InstanceID<package_name # C1.exe/QS/IAcceptSQLServerLicenseTerms/action = patch/InstanceName = MyInstance ou <package_name # C3.exe/QS/IAcceptSQLServerLicenseTerms/action = patch/InstanceId = \<Instance ID> .  
  
-   Le programme d'installation peut intégrer les dernières mises à jour du produit avec l'installation principale du produit de sorte que le produit principal et ses mises à jour applicables sont installées en même temps. Vous pouvez préparer une installation de l’instance du moteur de base de données pour inclure la mise à jour du produit : setup.exe/q/IAcceptSQLServerLicenseTerms/ACTION = PrepareImage/UpdateEnabled = true/UpdateEnabled = true/UpdateSource =/InstanceId =/features = SQLEngine \<path where the update is downloaded> \<Instance ID> .  
  
-   Mettre à jour uniquement les composants partagés de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils d'administration : <nom_du_package>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
  
-   Mettre à jour toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présentes sur l'ordinateur et tous les composants partagés, comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils d'administration : <NomPackage>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.  
  
 Supprimez une mise à jour à partir de l'invite de commandes en remplaçant <NomPackage> par le nom de votre package de mise à jour :  
  
-   Supprimer une mise à jour d'une seule instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et tous les composants partagés, comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils d'administration : <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.  
  
-   Supprimer une mise à jour des composants partagés de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uniquement, comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils d'administration : <package_name>.exe /qs /Action=RemovePatch  
  
    > [!NOTE]  
    >  Le programme d'installation de mise à niveau permet que les composants partagés soient toujours de la même version ou une version ultérieure par rapport à l'instance de niveau le plus élevé.  
  
## <a name="supported-command-prompt-parameters"></a>Paramètres d'invite de commandes pris en charge  
  
> [!IMPORTANT]  
>  Lorsque cela est possible, fournissez les informations d'identification de sécurité au moment de l'exécution. Si vous devez stocker des informations d'identification dans un fichier de script, sécurisez le fichier pour empêcher tout accès non autorisé.  
  
|Commutateur|Description|  
|------------|-----------------|  
|**/?**|Affiche de l'aide sur l'invite de commandes d'une installation sans assistance|  
|**/action=Patch ou /action=RemovePatch**|Spécifie l’action d’installation : Patch ou RemovePatch.|  
|**/allinstances**|Applique la mise à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partagés ne dépendant pas des instances.|  
|**/InstanceName = nom_instance** <sup>1</sup>|Applique la mise à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommée InstanceName et à tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partagés ne dépendant pas des instances.|  
|**/InstanceID=Inst1**|Applique la mise à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Inst1 et à tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partagés ne dépendant pas des instances.|  
|**/quiet**|Exécute le programme d'installation de mise à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode sans assistance.|  
|**/qs**|Affiche uniquement la boîte de dialogue de progression.|  
|**/UpdateEnabled**|Spécifie si le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit découvrir et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut les mises à jour trouvées.|  
|**/IAcceptSQLServerLicenseTerms**|Obligatoire uniquement lorsque le paramètre /Q ou /QS est spécifié pour les installations sans assistance.|  
  
 <sup>1</sup> vous ne pouvez pas spécifier ce paramètre pour appliquer une mise à jour à une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous devez spécifier à la place le paramètre /instanceID.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble de l'installation de maintenance de SQL Server](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  
