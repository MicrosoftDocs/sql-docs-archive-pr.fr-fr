---
title: Utilisation du partitionnement de table et d’index | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e05087f63da163b8fa339befae039eb5e7e8245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602781"
---
# <a name="using-table-and-index-partitioning"></a><span data-ttu-id="cb866-102">Utilisation du partitionnement des tables et des index</span><span class="sxs-lookup"><span data-stu-id="cb866-102">Using Table and Index Partitioning</span></span>
  <span data-ttu-id="cb866-103">Les données peuvent être stockées en utilisant les algorithmes de stockage fournis par les [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="cb866-103">Data can be stored by using the storage algorithms provided by [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md).</span></span> <span data-ttu-id="cb866-104">Le partitionnement permet de rendre des tables et des index volumineux plus gérables et plus évolutifs.</span><span class="sxs-lookup"><span data-stu-id="cb866-104">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
## <a name="index-and-table-partitioning"></a><span data-ttu-id="cb866-105">Partitionnement des tables et des index</span><span class="sxs-lookup"><span data-stu-id="cb866-105">Index and Table Partitioning</span></span>  
 <span data-ttu-id="cb866-106">Cette fonctionnalité permet de répartir les données des tables et index sur plusieurs groupes de fichiers dans des partitions.</span><span class="sxs-lookup"><span data-stu-id="cb866-106">The feature enables index and table data to be spread across multiple file groups in partitions.</span></span> <span data-ttu-id="cb866-107">Une fonction de partition définit comment les lignes d'une table ou d'un index sont mappées à un ensemble de partitions selon les valeurs de certaines colonnes, appelées « colonnes de partitionnement ».</span><span class="sxs-lookup"><span data-stu-id="cb866-107">A partition function defines how the rows of a table or index are mapped to a set of partitions based on the values of certain columns, referred to as partitioning columns.</span></span> <span data-ttu-id="cb866-108">Un schéma de partition mappe chaque partition spécifiée par la fonction de partition avec un groupe de fichiers.</span><span class="sxs-lookup"><span data-stu-id="cb866-108">A partition scheme maps each partition specified by the partition function to a file group.</span></span> <span data-ttu-id="cb866-109">Vous pouvez ainsi développer des stratégies d'archivage qui permettent de répartir les tables sur plusieurs groupes de fichiers, et par conséquent sur plusieurs périphériques physiques.</span><span class="sxs-lookup"><span data-stu-id="cb866-109">This lets you develop archiving strategies that enable tables to be scaled across file groups, and therefore physical devices.</span></span>  
  
 <span data-ttu-id="cb866-110">L'objet <xref:Microsoft.SqlServer.Management.Smo.Database> contient une collection d'objets <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> qui représentent les fonctions de partition implémentées et une collection d'objets <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> qui décrivent comment les données sont mappées avec les groupes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="cb866-110">The <xref:Microsoft.SqlServer.Management.Smo.Database> object contains a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> objects that represent the implemented partition functions and a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> objects that describe how data is mapped to file groups.</span></span>  
  
 <span data-ttu-id="cb866-111">Chaque objet <xref:Microsoft.SqlServer.Management.Smo.Table> et <xref:Microsoft.SqlServer.Management.Smo.Index> spécifie quel schéma de partition il utilise dans la propriété <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> et spécifie les colonnes dans la <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="cb866-111">Each <xref:Microsoft.SqlServer.Management.Smo.Table> and <xref:Microsoft.SqlServer.Management.Smo.Index> object specifies which partition scheme it uses in the <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> property and specifies the columns in the <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb866-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb866-112">Example</span></span>  
 <span data-ttu-id="cb866-113">Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application.</span><span class="sxs-lookup"><span data-stu-id="cb866-113">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="cb866-114">Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un projet Visual C&#35; Smo dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span><span class="sxs-lookup"><span data-stu-id="cb866-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a><span data-ttu-id="cb866-115">Installation d'un schéma de partition pour une table en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb866-115">Setting Up a Partition Scheme for a Table in Visual Basic</span></span>  
 <span data-ttu-id="cb866-116">L'exemple de code montre comment créer une fonction de partition et un schéma de partition pour la table `TransactionHistory` de l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cb866-116">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="cb866-117">Les partitions sont organisées par date dans le but de déplacer les enregistrements anciens vers la table `TransactionHistoryArchive` .</span><span class="sxs-lookup"><span data-stu-id="cb866-117">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a><span data-ttu-id="cb866-118">Installation d'un schéma de partition pour une table en Visual C#</span><span class="sxs-lookup"><span data-stu-id="cb866-118">Setting Up a Partition Scheme for a Table in Visual C#</span></span>  
 <span data-ttu-id="cb866-119">L'exemple de code montre comment créer une fonction de partition et un schéma de partition pour la table `TransactionHistory` de l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cb866-119">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="cb866-120">Les partitions sont organisées par date dans le but de déplacer les enregistrements anciens vers la table `TransactionHistoryArchive` .</span><span class="sxs-lookup"><span data-stu-id="cb866-120">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```csharp
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a><span data-ttu-id="cb866-121">Installation d'un schéma de partition pour une table dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb866-121">Setting Up a Partition Scheme for a Table in PowerShell</span></span>  
 <span data-ttu-id="cb866-122">L'exemple de code montre comment créer une fonction de partition et un schéma de partition pour la table `TransactionHistory` de l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cb866-122">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="cb866-123">Les partitions sont organisées par date dans le but de déplacer les enregistrements anciens vers la table `TransactionHistoryArchive` .</span><span class="sxs-lookup"><span data-stu-id="cb866-123">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb866-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb866-124">See Also</span></span>  
 [<span data-ttu-id="cb866-125">Tables et index partitionnés</span><span class="sxs-lookup"><span data-stu-id="cb866-125">Partitioned Tables and Indexes</span></span>](../../partitions/partitioned-tables-and-indexes.md)  