---
title: Connexion à un Azure SQL Database à l’aide de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: rothja
ms.author: jroth
ms.openlocfilehash: 177c655f97e32f2044460e87c6cd775cdf8fcde9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611030"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a><span data-ttu-id="08917-102">Connexion à une base de données Azure SQL à l’aide de SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="08917-102">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>
  <span data-ttu-id="08917-103">Pour obtenir un exemple qui montre comment se connecter à à [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] l’aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, consultez [développement : rubriques de procédures (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span><span class="sxs-lookup"><span data-stu-id="08917-103">For a sample that shows how to connect to a [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Development: How-to Topics (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span></span>  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a><span data-ttu-id="08917-104">Problèmes connus lors de la connexion à une base de données SQL</span><span class="sxs-lookup"><span data-stu-id="08917-104">Known Issues When Connecting to a SQL Database</span></span>  
 <span data-ttu-id="08917-105">Voici les problèmes connus liés à la connexion à une [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :</span><span class="sxs-lookup"><span data-stu-id="08917-105">The following are known issues when connecting to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="08917-106">Une connexion établie avec `SQLBrowseConnect` peut être refusée si `SQLBrowseConnect` est utilisé au cours des étapes.</span><span class="sxs-lookup"><span data-stu-id="08917-106">A connection made with `SQLBrowseConnect` may be rejected if `SQLBrowseConnect` is used in stages.</span></span>  <span data-ttu-id="08917-107">Supposons que le nom du pilote est transmis dans le premier appel, le serveur et les informations d'identification (utilisateur et mot de passe) sont envoyés dans le deuxième appel, établissant la connexion, et un nom de base de données et un langage sont envoyés dans le troisième appel.</span><span class="sxs-lookup"><span data-stu-id="08917-107">For example, if the driver name is sent in the first call, server and credentials (user and password) sent in the second call, establishing the connection, and a database name and a language in the third call.</span></span>  <span data-ttu-id="08917-108">Le troisième appel indique à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client d'émettre une instruction USE pour modifier les bases de données.</span><span class="sxs-lookup"><span data-stu-id="08917-108">The third call will cause [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to issue a USE statement to change databases.</span></span> <span data-ttu-id="08917-109">Toutefois, l'instruction USE n'est pas prise en charge dans [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], ce qui génère l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="08917-109">However, the USE statement is not supported in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], generating the following error:</span></span>  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08917-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08917-110">See Also</span></span>  
 [<span data-ttu-id="08917-111">Génération d’applications avec SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="08917-111">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
