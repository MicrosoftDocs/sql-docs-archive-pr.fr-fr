---
title: Source ADO NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706619"
---
# <a name="ado-net-source"></a><span data-ttu-id="c5528-102">Source ADO NET</span><span class="sxs-lookup"><span data-stu-id="c5528-102">ADO NET Source</span></span>
  <span data-ttu-id="c5528-103">La source ADO .NET exploite des données issues d'un fournisseur .NET et les met à la disposition du flux de données.</span><span class="sxs-lookup"><span data-stu-id="c5528-103">The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.</span></span>  
  
 <span data-ttu-id="c5528-104">Vous pouvez utiliser la source ADO .NET. pour vous connecter à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5528-104">You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="c5528-105">La connexion à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] via OLE DB n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c5528-105">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="c5528-106">Pour plus d’informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)], consultez [Recommandations générales et limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span><span class="sxs-lookup"><span data-stu-id="c5528-106">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="c5528-107">Prise en charge du type de données</span><span class="sxs-lookup"><span data-stu-id="c5528-107">Data Type Support</span></span>  
 <span data-ttu-id="c5528-108">La source convertit tout type de données qui ne mappe pas à un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] spécifique en un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DT_NTEXT.</span><span class="sxs-lookup"><span data-stu-id="c5528-108">The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="c5528-109">Cette conversion se produit même si le type de données est `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="c5528-109">This conversion occurs even if the data type is `System.Object`.</span></span>  
  
 <span data-ttu-id="c5528-110">Vous pouvez remplacer le type de données DT_NTEXT par le type de données DT_WSTR, et inversement.</span><span class="sxs-lookup"><span data-stu-id="c5528-110">You can change the DT_NTEXT data type to the DT_WSTR data type, or the change DT_WSTR to DT_NTEXT.</span></span> <span data-ttu-id="c5528-111">Pour modifier les types de données, définissez la propriété **DataType** dans la boîte de dialogue **Éditeur avancé** de la source ADO .NET.</span><span class="sxs-lookup"><span data-stu-id="c5528-111">You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source.</span></span> <span data-ttu-id="c5528-112">Pour plus d’informations, consultez [Propriétés communes](../common-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-112">For more information, see [Common Properties](../common-properties.md).</span></span>  
  
 <span data-ttu-id="c5528-113">Le type de données DT_NTEXT peut également être converti en type de données DT_BYTES ou DT_STR en utilisant une transformation de conversion de données après la source ADO .NET.</span><span class="sxs-lookup"><span data-stu-id="c5528-113">The DT_NTEXT data type can also be converted to the DT_BYTES or DT_STR data type by using a Data Conversion transformation after the ADO NET source.</span></span> <span data-ttu-id="c5528-114">Pour plus d’informations, voir [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-114">For more information, see [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span></span>  
  
 <span data-ttu-id="c5528-115">Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], les types de données de date, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2 et DT_DBTIMESTAMPOFFSET, mappent à certains types de données de date de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5528-115">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the date data types, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5528-116">Vous pouvez configurer la source ADO .NET pour convertir les types de données de date utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en types de données de date utilisés par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c5528-116">You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to those that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses.</span></span> <span data-ttu-id="c5528-117">Pour configurer la source ADO .NET pour convertir ces types de données de date, affectez à la propriété **Type System Version** du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] la valeur **Dernière**.</span><span class="sxs-lookup"><span data-stu-id="c5528-117">To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to **Latest**.</span></span> <span data-ttu-id="c5528-118">(La propriété **Type System Version** se trouve dans la page **Tous** de la boîte de dialogue **Gestionnaire de connexions** .</span><span class="sxs-lookup"><span data-stu-id="c5528-118">(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box.</span></span> <span data-ttu-id="c5528-119">Pour ouvrir la boîte de dialogue **Gestionnaire de connexions** , cliquez avec le bouton droit sur le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , puis cliquez sur **Modifier**.)</span><span class="sxs-lookup"><span data-stu-id="c5528-119">To open the **Connection Manager** dialog box, right-click the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, and then click **Edit**.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5528-120">Si la propriété **Type System Version** du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] a la valeur **SQL Server 2005**, le système convertit les types de données de date [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en DT_WSTR.</span><span class="sxs-lookup"><span data-stu-id="c5528-120">If the **Type System Version** property for the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types to DT_WSTR.</span></span>  
  
 <span data-ttu-id="c5528-121">Le système convertit les types de données définis par l’utilisateur (UDT) en objets blob (Binary Large Object) [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] quand le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] spécifie le fournisseur en tant que fournisseur de données .NET pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span><span class="sxs-lookup"><span data-stu-id="c5528-121">The system converts user-defined data types (UDTs) to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] binary large objects (BLOB) when the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span></span> <span data-ttu-id="c5528-122">Le système applique les règles suivantes quand il convertit le type de données UDT :</span><span class="sxs-lookup"><span data-stu-id="c5528-122">The system applies the following rules when it converts the UDT data type:</span></span>  
  
-   <span data-ttu-id="c5528-123">Si les données sont un UDT non volumineux, le système convertit les données en DT_BYTES.</span><span class="sxs-lookup"><span data-stu-id="c5528-123">If the data is a non-large UDT, the system converts the data to DT_BYTES.</span></span>  
  
-   <span data-ttu-id="c5528-124">Si les données sont un type UDT non volumineux et que la propriété **Length** de la colonne sur la base de données a la valeur -1 ou une valeur supérieure à 8 000 octets, le système convertit les données en DT_IMAGE.</span><span class="sxs-lookup"><span data-stu-id="c5528-124">If the data is a non-large UDT, and the **Length** property of the column on the database is set to -1 or a value greater than 8,000 bytes, the system converts the data to DT_IMAGE.</span></span>  
  
-   <span data-ttu-id="c5528-125">Si les données sont un UDT volumineux, le système convertit les données en DT_IMAGE.</span><span class="sxs-lookup"><span data-stu-id="c5528-125">If the data is a large UDT, the system converts the data to DT_IMAGE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c5528-126">Si la source ADO .NET n'est pas configurée pour utiliser la sortie d'erreur, le système transmet les données à la colonne DT_IMAGE par segments de 8 000 octets.</span><span class="sxs-lookup"><span data-stu-id="c5528-126">If the ADO NET source is not configured to use error output, the system streams the data to the DT_IMAGE column in chunks of 8,000 bytes.</span></span> <span data-ttu-id="c5528-127">Si la source ADO .NET est configurée pour utiliser la sortie d'erreur, le système passe la totalité du tableau d'octets à la colonne DT_IMAGE.</span><span class="sxs-lookup"><span data-stu-id="c5528-127">If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT_IMAGE column.</span></span> <span data-ttu-id="c5528-128">Pour plus d’informations sur la configuration des composants pour utiliser la sortie d’erreur, consultez [Gestion des erreurs dans les données](error-handling-in-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-128">For more information about how to configure components to use error output, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="c5528-129">Pour plus d’informations sur les types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , les conversions de types de données prises en charge et le mappage de types de données entre certaines bases de données incluant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Types de données d’Integration Services](integration-services-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-129">For more information about the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="c5528-130">Pour plus d’informations sur le mappage entre les types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les types de données managés, consultez [Utilisation de types de données dans le flux de données](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-130">For information about mapping [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span></span>  
  
## <a name="ado-net-source-troubleshooting"></a><span data-ttu-id="c5528-131">Résolution des problèmes liés à la source ADO .NET</span><span class="sxs-lookup"><span data-stu-id="c5528-131">ADO NET Source Troubleshooting</span></span>  
 <span data-ttu-id="c5528-132">Vous pouvez consigner les appels que la source ADO .NET effectue vers des fournisseurs de données externes.</span><span class="sxs-lookup"><span data-stu-id="c5528-132">You can log the calls that the ADO NET source makes to external data providers.</span></span> <span data-ttu-id="c5528-133">Cette fonctionnalité de journalisation permet de résoudre des problèmes liés au chargement de données qu'effectue la source ADO .NET à partir de sources de données externes.</span><span class="sxs-lookup"><span data-stu-id="c5528-133">You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs.</span></span> <span data-ttu-id="c5528-134">Pour consigner les appels que la source ADO .NET effectue vers des fournisseurs de données externes, activez la journalisation de package et sélectionnez l’événement **Diagnostic** au niveau du package.</span><span class="sxs-lookup"><span data-stu-id="c5528-134">To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="c5528-135">Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-135">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="ado-net-source-configuration"></a><span data-ttu-id="c5528-136">Configuration de la source ADO .NET</span><span class="sxs-lookup"><span data-stu-id="c5528-136">ADO NET Source Configuration</span></span>  
 <span data-ttu-id="c5528-137">Vous configurez la source ADO .NET en fournissant l'instruction SQL qui définit le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="c5528-137">You configure the ADO NET source by providing the SQL statement that defines the result set.</span></span> <span data-ttu-id="c5528-138">Par exemple, une source ADO .NET qui se connecte à la base de données [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] et utilise l’instruction SQL `SELECT * FROM Production.Product` extrait toutes les lignes de la table **Production.Product** et fournit le dataset à un composant en aval.</span><span class="sxs-lookup"><span data-stu-id="c5528-138">For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5528-139">Lorsque vous utilisez une instruction SQL pour appeler une procédure stockée qui retourne des résultats à partir d'une table temporaire, utilisez l'option WITH RESULT SETS afin de définir les métadonnées du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="c5528-139">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5528-140">Si vous utilisez une instruction SQL pour exécuter une procédure stockées et que le package échoue avec l'erreur suivante, vous pouvez résoudre l'erreur en ajoutant l'instruction `SET FMTONLY OFF` avant l'instruction exec.</span><span class="sxs-lookup"><span data-stu-id="c5528-140">If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the `SET FMTONLY OFF` statement before the exec statement.</span></span>  
>   
>  <span data-ttu-id="c5528-141">**La colonne « nom_colonne » est introuvable dans la source de données.**</span><span class="sxs-lookup"><span data-stu-id="c5528-141">**Column <column_name> cannot be found at the datasource.**</span></span>  
  
 <span data-ttu-id="c5528-142">La source ADO .NET utilise un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] pour se connecter à une source de données, et le gestionnaire de connexions spécifie le fournisseur .NET.</span><span class="sxs-lookup"><span data-stu-id="c5528-142">The ADO NET source uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider.</span></span> <span data-ttu-id="c5528-143">Pour plus d’informations, consultez [Gestionnaire de connexions ADO.NET](../connection-manager/ado-net-connection-manager.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-143">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c5528-144">La source ADO .NET a une sortie normale et une sortie d'erreur.</span><span class="sxs-lookup"><span data-stu-id="c5528-144">The ADO NET source has one regular output and one error output.</span></span>  
  
 <span data-ttu-id="c5528-145">Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.</span><span class="sxs-lookup"><span data-stu-id="c5528-145">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c5528-146">Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5528-146">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c5528-147">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="c5528-147">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="c5528-148">Propriétés personnalisées ADO NET</span><span class="sxs-lookup"><span data-stu-id="c5528-148">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="c5528-149">Pour plus d’informations sur la façon de définir les propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).</span><span class="sxs-lookup"><span data-stu-id="c5528-149">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5528-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5528-150">See Also</span></span>  
 <span data-ttu-id="c5528-151">[Destination DataReader](datareader-destination.md) </span><span class="sxs-lookup"><span data-stu-id="c5528-151">[DataReader Destination](datareader-destination.md) </span></span>  
 <span data-ttu-id="c5528-152">[Destination ADO NET](ado-net-destination.md) </span><span class="sxs-lookup"><span data-stu-id="c5528-152">[ADO NET Destination](ado-net-destination.md) </span></span>  
 [<span data-ttu-id="c5528-153">Flux de données</span><span class="sxs-lookup"><span data-stu-id="c5528-153">Data Flow</span></span>](data-flow.md)  
  
  