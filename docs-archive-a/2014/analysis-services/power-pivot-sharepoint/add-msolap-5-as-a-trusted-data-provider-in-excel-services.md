---
title: Ajouter MSOLAP. 5 en tant que Fournisseur de données approuvé dans Excel Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 876ec613f18b2d91b5e06ab5fed4a7b258c30a36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613171"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services
  MSOLAP.5 fait référence au fournisseur OLE DB Analysis Services pour SQL Server 2012. Excel Services doit approuver ce fournisseur avant d'effectuer la demande de connexion qui se traduit par la disponibilité des données PowerPivot sur un serveur.  
  
 Si vous avez configuré PowerPivot pour SharePoint à l'aide de l'outil de configuration PowerPivot, MSOLAP.5 est peut-être déjà un fournisseur approuvé, car l'outil inclut une action qui répond à cette exigence. Toutefois, si vous utilisez PowerShell, l'administration centrale, ou si vous avez exclu l'action du fournisseur approuvé dans l'outil de configuration, le fournisseur peut être manquant, auquel cas vous devez l'ajouter maintenant, dans le cadre de la configuration de la batterie de serveurs pour l'accès aux données PowerPivot.  
  
 Vous ne devez effectuer cette étape qu'une seule fois pour chaque application de service Excel Services.  
  
 Chaque serveur physique qui traite une requête de données PowerPivot, tel que PowerPivot pour SharePoint ou un serveur Excel Services, doit avoir installé le fournisseur OLE DB sur l'ordinateur. Une installation de PowerPivot pour SharePoint inclut toujours le fournisseur OLE DB, mais si Excel Services s'exécute sur un ordinateur qui ne dispose pas de PowerPivot pour SharePoint, vous devez installer le fournisseur manuellement. Pour plus d’informations, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="add-a-trusted-provider-to-excel-services"></a>Ajouter un fournisseur approuvé à Excel Services  
  
1.  Dans l'administration centrale, cliquez sur **Gérer les applications de service**, puis cliquez sur l'application de service Excel Services.  
  
2.  Cliquez sur **Fournisseurs de données approuvés**.  
  
3.  Vérifiez que MSOLAP.5 figure dans la liste. Selon la manière dont vous avez configuré PowerPivot pour SharePoint, MSOLAP.5 peut être déjà approuvé.  
  
4.  S'il n'est pas répertorié, cliquez sur **Ajouter un fournisseur de données approuvé**.  
  
5.  Pour l’ID du fournisseur, tapez `MSOLAP.5`.  
  
6.  Pour le type de fournisseur, vérifiez que OLE DB est sélectionné.  
  
7.  Dans la description du fournisseur, tapez **Fournisseur Microsoft OLE DB pour OLAP Services 11.0**.  
  
  
