---
title: Boîte de dialogue Propriétés de la base de données (SSAS-tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.DatabaseProperties.f1
ms.assetid: 0f0ec02f-7b55-40ea-8a04-ed0deb1efd7a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41bf7838a714c35e2149e8163e21a7b8044a77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614905"
---
# <a name="database-properties-dialog-box-ssas---tabular"></a>Boîte de dialogue Propriétés de la base de données (SSAS - Tabulaire)
  Cette boîte de dialogue fournit des horodateurs et d'autres informations descriptives, ainsi que des propriétés personnalisables qui déterminent si la base de données utilise des données en mémoire cache. Les autres propriétés personnalisables incluent la modification du nom de la base de données et la spécification des options d'emprunt d'identité.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|**Nom** est le nom de base de données qui identifie de façon unique la base de données sur le serveur. Lorsque vous modifiez le nom de la base de données, pensez à l'incidence sur les rapports et les applications clientes qui utilisent le nom actuel dans les chaînes de connexion existantes. Vous devez mettre à jour les chaînes de connexion dans les rapports existants pour éviter les erreurs d'accès refusé. En outre, le modèle tabulaire qui est la source de cette base de données utilise très probablement le nom d'origine. Envisagez de mettre à jour les propriétés de déploiement de base de données dans le modèle pour vous assurer que les futures mises à jour de ce modèle seront publiées dans la base de données escomptée.|  
|**Identifiant**|Affiche l'identificateur de la base de données.|  
|**Description**|Entrez une nouvelle description pour changer la description de la base de données.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la base de données.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour des métadonnées de la base de données.|  
|**Dernière mise à jour**|Affiche la date et l'heure de la dernière mise à jour des données de la base de données.|  
|**Mode Lecture-écriture**|Il s’agit d’une propriété en lecture seule, mais vous pouvez la modifier à l’aide d’une séquence de commandes **Détacher** et **Attacher** , où la propriété est un paramètre de la commande **Attacher** . Pour plus d’informations, consultez [Base de données ReadWriteModes](multidimensional-models/database-readwritemodes.md).|  
|**DirectQueryMode**|Spécifie si la base de données utilise uniquement le stockage en mémoire (sans stockage sur disque), uniquement le stockage sur disque, ou une combinaison des deux. Les valeurs valides sont InMemory, DirectQuery, InMemoryWithDirectQuery (stockage en mémoire principalement, avec un peu de pagination sur le disque), ou DirectQueryWithInMemory (stockage sur le disque principalement, avec un peu stockage en mémoire). Pour plus d’informations, consultez [DirectQuery Deployment scenarios &#40;SSAS tabulaire&#41;](directquery-deployment-scenarios-ssas-tabular.md).|  
|**Informations d'emprunt d'identité de source de données**|Spécifie le compte d'emprunt d'identité utilisé pour les connexions de base de données lors du traitement ou de l'actualisation des données sur les partitions locales ou distantes, les requêtes qui s'exécutent sur une banque de données relationnelle (via DirectQuery), les liaisons hors ligne, et de la synchronisation de la cible vers la source.<br /><br /> Les valeurs valides incluent le compte de service Analysis Services ou un jeu d'informations d'identification Windows spécifique. Ne spécifiez pas **Utiliser les infos d’identification de l’utilisateur actuel**. Cette option d'identification n'est pas prise en charge pour une base de données model tabulaire.|  
|**Dernier traitement**|Affiche la date et l'heure du dernier traitement de la base de données.|  
|**Taille estimée**|Affiche la taille estimée de la base de données.|  
|**Emplacement de stockage**|Spécifie l'emplacement de la base de données. Si la base de données se trouve dans le répertoire de données par défaut, cette valeur sera vide.|  
  
  
