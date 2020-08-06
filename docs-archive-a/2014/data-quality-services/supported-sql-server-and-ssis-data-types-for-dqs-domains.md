---
title: Types de données SQL Server et SSIS pris en charge pour les domaines DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad79983f570beb4c789379b2b48682b358c34e1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709960"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>Types de données SQL Server et SSIS pris en charge pour les domaines DQS
  Il existe de nombreux types de données dans SQL Server et SQL Server Integration Services (SSIS), mais seulement quatre types de données pour les domaines DQS : Date, Décimal, Entier et Chaîne. Les types de données SQL Server et SSIS ne sont pas tous pris en charge dans DQS. Vous ne pouvez mapper vos données source à un domaine DQS en vue d'y effectuer des activités portant sur la qualité des données que si le type de données source est pris en charge dans DQS et qu'il correspond au type de données du domaine DQS. Cette rubrique fournit des informations relatives aux types de données SQL Server et SSIS qui sont pris en charge et disponibles en vue d'un mappage à chacun des quatre types de données de domaine dans DQS.  
  
> [!NOTE]  
>  Dans les fichiers .xlsx et .xls, le type de données de la colonne source est déterminé par le type de données prédominant des huit premières lignes. Si une cellule n'est pas conforme à ce type de données, elle recevra une valeur NULL. De la même manière, dans les fichiers .csv, le type de données de la colonne source est déterminé par le type de données prédominant des huit premières lignes.  
  
##  <a name="supported-sql-server-data-types"></a><a name="SQLServer"></a>Types de données SQL Server pris en charge  
 Le tableau suivant fournit des informations sur les types de données SQL Server pris en charge pour chaque type de données de domaine DQS :  
  
|Type de données de domaine DQS|Type de données SQL Server pris en charge|  
|--------------------------|------------------------------------|  
|Date|date|  
|Decimal|Décimal<br /><br /> float<br /><br /> money<br /><br /> numeric<br /><br /> real<br /><br /> SMALLMONEY|  
|Integer|bigint<br /><br /> int<br /><br /> SMALLINT<br /><br /> TINYINT|  
|String|char<br /><br /> NCHAR<br /><br /> NVARCHAR<br /><br /> varchar|  
  
 Les autres types de données SQL Server ne sont pas pris en charge dans DQS. Pour plus d’informations sur les types de données SQL Server, consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
##  <a name="supported-ssis-data-types"></a><a name="SSIS"></a>Types de données SSIS pris en charge  
 Le tableau suivant fournit des informations sur les types de données SSIS pris en charge pour chaque type de données de domaine DQS :  
  
|Type de données de domaine DQS|Type de données SSIS pris en charge|  
|--------------------------|------------------------------|  
|Date|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Integer|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|String|DT_STR<br /><br /> DT_WSTR|  
  
 Les autres types de données SSIS ne sont pas pris en charge dans DQS Pour plus d'informations sur tous les types de données SSIS, consultez [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d'un domaine](../../2014/data-quality-services/managing-a-domain.md)  
  
  
