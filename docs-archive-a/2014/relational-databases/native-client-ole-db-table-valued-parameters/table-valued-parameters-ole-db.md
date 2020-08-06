---
title: Paramètres table (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
ms.openlocfilehash: 41d125bcb254125d7f7562ca1873e8af03dab929
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706411"
---
# <a name="table-valued-parameters-ole-db"></a>Paramètres table (OLE DB)
  Cette section décrit la prise en charge des paramètres table dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour plus d’informations sur la vue d’ensemble, consultez [paramètres Table &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md). Pour obtenir un exemple, consultez [Utiliser les paramètres table &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Notes  
 Vous pouvez actuellement envoyer des données à lignes multiples au serveur en tant que paramètres à une procédure avec des jeux de paramètres (le paramètre DBPARAMS dans `ICommand::Execute`). Avec des jeux de paramètres, chaque élément du jeu doit être envoyé dans une demande d'appel de procédure distante séparée au serveur. Les paramètres table fournissent des fonctionnalités semblables, mais l'intégration avec le serveur est meilleure. Cela réduit le nombre de demandes d'appel de procédure distante et autorise des opérations basées sur des jeux sur le serveur.  
  
 Les paramètres table sont pris en charge dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client en tant qu'objets `Rowset` OLE DB. Tout objet `Rowset` peut être fourni par le consommateur (autrement dit, l'application cliente utilisant le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) en tant qu'espace réservé pour les paramètres de paramètre table. Les paramètres table sont traités comme tout autre type de paramètre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fournit des interfaces de création, de découverte, de spécification, de liaison et de schéma.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d'un ensemble de lignes de paramètre table](table-valued-parameter-rowset-creation.md)  
  
-   [Découverte du type de paramètre table](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [Exécution de commandes contenant des paramètres table](executing-commands-containing-table-valued-parameters.md)  
  
-   [Insertion de données dans des paramètres table](inserting-data-into-table-valued-parameters.md)  
  
-   [Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Prise en charge du type de paramètre table OLE DB](ole-db-table-valued-parameter-type-support.md)  
  
-   [Prise en charge des types de paramètre table OLE DB &#40;méthodes&#41;](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Prise en charge des types de paramètre table OLE DB &#40;propriétés&#41;](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
