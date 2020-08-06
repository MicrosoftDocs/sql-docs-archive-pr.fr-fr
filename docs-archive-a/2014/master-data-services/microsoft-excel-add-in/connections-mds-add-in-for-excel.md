---
title: Connexions (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4dc41afc6dd59cade9e75475c7cb914d14a8937
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600124"
---
# <a name="connections-mds-add-in-for-excel"></a>Connexions (Complément MDS pour Excel)
  Pour télécharger des données dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous devez d’abord créer une connexion. Une connexion permet au service web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] de savoir à quelle base de données MDS se connecter.  
  
 La chaîne de connexion est généralement l’URL de l’application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], par exemple http://contoso/mds.  
  
 Chaque fois que vous démarrez Excel, vous devez vous connecter à un référentiel MDS. La seule exception est lorsque la feuille de calcul active contient déjà des données managées MDS. Dans ce cas, un rapport est automatiquement créé chaque fois que vous actualisez ou publiez des données dans la feuille.  
  
 Vous pouvez créer plusieurs connexions. La connexion récemment accédée est utilisée par défaut.  
  
 Plusieurs utilisateurs peuvent se connecter simultanément. Toutefois, des conflits peuvent se produire lorsque plusieurs utilisateurs tentent de publier les mêmes données. Pour plus d’informations, consultez [publication de données &#40;Complément MDS pour Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Connexion automatique et chargement de données fréquemment utilisées  
 Si vous souhaitez vous connecter toujours au même serveur et charger le même jeu de données, vous pouvez créer des fichiers de requête de raccourci contenant les informations de connexion et de filtre. Pour plus d’informations sur les fichiers de requête, consultez [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="data-quality-services"></a>Data Quality Services  
 Le [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] inclut la fonctionnalité Data Quality Services qui vous aide à mettre en correspondance les données avant de les publier sur le référentiel MDS. Lorsque vous vous connectez, si une base de données DQS est installée sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que la base de données MDS, vous pouvez voir les boutons DQS sur le ruban. Si la base de données DQS_Main n'existe pas sur l'instance, ces boutons ne sont pas affichés et les fonctionnalités de qualité des données ne sont pas disponibles.  
  
## <a name="troubleshooting-connections"></a>Dépannage des connexions  
 Lorsque vous vous connectez à MDS, si vous rencontrez des problèmes, consultez [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) pour obtenir des conseils de dépannage.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez une connexion à une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Se connecter à un référentiel MDS &#40;Complément MDS pour Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Chargez des données MDS dans Excel.|[Charger des données MDS dans Excel](export-data-to-excel-from-master-data-services.md)|  
|Filtrez les données MDS avant de les charger dans Excel.|[Filtrer les données avant de charger &#40;Complément MDS pour Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Chargement de données &#40;Complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Complément Master Data Services pour Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
