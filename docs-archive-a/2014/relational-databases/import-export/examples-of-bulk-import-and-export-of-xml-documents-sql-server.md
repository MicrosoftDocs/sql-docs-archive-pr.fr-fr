---
title: Exemples d’importation et d’exportation en bloc de documents XML (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d72c84a7ed84503e0c88d2a46c808196903900b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612345"
---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a><span data-ttu-id="b870c-102">Exemples d'importation et d'exportation en bloc de documents XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b870c-102">Examples of Bulk Import and Export of XML Documents (SQL Server)</span></span>
    
##  <a name="you-can-bulk-import-xml-documents-into-a-ssnoversion-database-or-bulk-export-them-from-a-ssnoversion-database-this-topic-provides-examples-of-both"></a><a name="top"></a><span data-ttu-id="b870c-103">Vous pouvez importer en bloc des documents XML dans une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données ou les exporter en bloc à partir d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="b870c-103">You can bulk import XML documents into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or bulk export them from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="b870c-104">Cette rubrique fournit des exemples de chaque.</span><span class="sxs-lookup"><span data-stu-id="b870c-104">This topic provides examples of both.</span></span>  
  
 <span data-ttu-id="b870c-105">Pour importer des données en bloc à partir d'un fichier de données dans une table ou une vue non partitionnée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez utiliser les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b870c-105">To bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or non-partitioned view, you can use the following:</span></span>  
  
-   <span data-ttu-id="b870c-106">utilitaire**bcp**</span><span class="sxs-lookup"><span data-stu-id="b870c-106">**bcp** utility</span></span>  
  
     <span data-ttu-id="b870c-107">Vous pouvez aussi faire appel à l’utilitaire **bcp** pour exporter des données à partir de n’importe quel emplacement d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant une instruction SELECT, vues partitionnées comprises.</span><span class="sxs-lookup"><span data-stu-id="b870c-107">You can also use the **bcp** utility to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that a SELECT statement works, including partitioned views.</span></span>  
  
-   <span data-ttu-id="b870c-108">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="b870c-108">BULK INSERT</span></span>  
  
-   <span data-ttu-id="b870c-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="b870c-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="b870c-110">Pour plus d’informations, consultez [Importer et exporter des données en bloc à l’aide de l’utilitaire bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) et [importer des données en bloc à l’aide de BULK INSERT ou d’OPENROWSET&#40;Bulk... ](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)&#41; &#40;SQL Server&#41;.</span><span class="sxs-lookup"><span data-stu-id="b870c-110">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) and [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b870c-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="b870c-111">Examples</span></span>  
 <span data-ttu-id="b870c-112">Voici les exemples :</span><span class="sxs-lookup"><span data-stu-id="b870c-112">The examples are the following:</span></span>  
  
-   <span data-ttu-id="b870c-113">R.</span><span class="sxs-lookup"><span data-stu-id="b870c-113">A.</span></span> [<span data-ttu-id="b870c-114">Importation en bloc de données XML sous forme de flux d’octets binaires</span><span class="sxs-lookup"><span data-stu-id="b870c-114">BULK importing XML data as a binary byte stream</span></span>](#binary_byte_stream)  
  
-   <span data-ttu-id="b870c-115">B.</span><span class="sxs-lookup"><span data-stu-id="b870c-115">B.</span></span> [<span data-ttu-id="b870c-116">Importation en bloc de données XML dans une ligne existante</span><span class="sxs-lookup"><span data-stu-id="b870c-116">Bulk importing XML data in an existing row</span></span>](#existing_row)  
  
-   <span data-ttu-id="b870c-117">C.</span><span class="sxs-lookup"><span data-stu-id="b870c-117">C.</span></span> [<span data-ttu-id="b870c-118">Importation en bloc de données XML à partir d’un fichier contenant une DTD</span><span class="sxs-lookup"><span data-stu-id="b870c-118">Bulk importing XML data from a file that contains a DTD</span></span>](#file_contains_dtd)  
  
-   <span data-ttu-id="b870c-119">D.</span><span class="sxs-lookup"><span data-stu-id="b870c-119">D.</span></span> [<span data-ttu-id="b870c-120">Spécification explicite de la marque de fin de champ à l’aide d’un fichier de format</span><span class="sxs-lookup"><span data-stu-id="b870c-120">Specifying the field terminator explicitly using a format file</span></span>](#field_terminator_in_format_file)  
  
-   <span data-ttu-id="b870c-121">E.</span><span class="sxs-lookup"><span data-stu-id="b870c-121">E.</span></span> [<span data-ttu-id="b870c-122">Exportation en bloc de données XML</span><span class="sxs-lookup"><span data-stu-id="b870c-122">Bulk exporting XML data</span></span>](#bulk_export_xml_data)  
  
###  <a name="a-bulk-importing-xml-data-as-a-binary-byte-stream"></a><a name="binary_byte_stream"></a> <span data-ttu-id="b870c-123">A.</span><span class="sxs-lookup"><span data-stu-id="b870c-123">A.</span></span> <span data-ttu-id="b870c-124">Importation en bloc de données XML sous forme de flux d'octets binaires</span><span class="sxs-lookup"><span data-stu-id="b870c-124">Bulk importing XML data as a binary byte stream</span></span>  
 <span data-ttu-id="b870c-125">Si vous importez en bloc des données XML à partir d’un fichier contenant la déclaration d’encodage à appliquer, spécifiez l’option SINGLE_BLOB dans la clause OPENROWSET(BULK...).</span><span class="sxs-lookup"><span data-stu-id="b870c-125">When you bulk import XML data from a file that contains an encoding declaration that you want to apply, specify the SINGLE_BLOB option in the OPENROWSET(BULK...) clause.</span></span> <span data-ttu-id="b870c-126">Cette option permet à l'analyseur XML de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'importer les données conformément au schéma d'encodage spécifié dans la déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="b870c-126">The SINGLE_BLOB option makes sure that the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imports the data according to the encoding scheme specified in the XML declaration.</span></span>  
  
#### <a name="sample-table"></a><span data-ttu-id="b870c-127">Exemple de table</span><span class="sxs-lookup"><span data-stu-id="b870c-127">Sample Table</span></span>  
 <span data-ttu-id="b870c-128">Pour tester l'exemple A, créez la table d'exemple `T`.</span><span class="sxs-lookup"><span data-stu-id="b870c-128">To test example A, you must create sample table `T`.</span></span>  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a><span data-ttu-id="b870c-129">Fichier de données d'exemple</span><span class="sxs-lookup"><span data-stu-id="b870c-129">Sample Data File</span></span>  
 <span data-ttu-id="b870c-130">Avant de pouvoir exécuter l’exemple A, vous devez créer un fichier encodé en UTF-8 (`C:\SampleFolder\SampleData3.txt`) : ce dernier contient l’instance d’exemple suivante qui spécifie le schéma d’encodage `UTF-8` .</span><span class="sxs-lookup"><span data-stu-id="b870c-130">Before you can run example A, you must create a UTF-8 encoded file (`C:\SampleFolder\SampleData3.txt`) that contains the following sample instance that specifies the `UTF-8` encoding scheme.</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a><span data-ttu-id="b870c-131">Exemple A</span><span class="sxs-lookup"><span data-stu-id="b870c-131">Example A</span></span>  
 <span data-ttu-id="b870c-132">Cet exemple utilise l'option `SINGLE_BLOB` dans une instruction `INSERT ... SELECT * FROM OPENROWSET(BULK...)` pour importer des données à partir d'un fichier nommé `SampleData3.txt` et insérer une instance XML dans la table de colonne unique, la table d'exemple `T`.</span><span class="sxs-lookup"><span data-stu-id="b870c-132">This example uses the `SINGLE_BLOB` option in an `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement to import data from a file named `SampleData3.txt` and insert an XML instance in the single-column table, sample table `T`.</span></span>  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a><span data-ttu-id="b870c-133">Notes</span><span class="sxs-lookup"><span data-stu-id="b870c-133">Remarks</span></span>  
 <span data-ttu-id="b870c-134">En utilisant SINGLE_BLOB dans ce cas, vous évitez toute discordance entre l'encodage du document XML (tel qu'il est spécifié par la déclaration d'encodage XML) et la page de codes de type chaîne inhérente au serveur.</span><span class="sxs-lookup"><span data-stu-id="b870c-134">By using SINGLE_BLOB in this case, you can avoid a mismatch between the encoding of the XML document (as specified by the XML encoding declaration) and the string codepage implied by the server.</span></span>  
  
 <span data-ttu-id="b870c-135">Si vous utilisez les types de données NCLOB ou CLOB et que vous rencontrez un conflit de pages de codes ou d'encodage, effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b870c-135">If you use NCLOB or CLOB data types and run into a codepage or encoding conflict, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="b870c-136">supprimer la déclaration XML pour réussir l'importation du contenu du fichier de données XML ;</span><span class="sxs-lookup"><span data-stu-id="b870c-136">Remove the XML declaration to successfully import the contents of the XML data file.</span></span>  
  
-   <span data-ttu-id="b870c-137">spécifier, dans l'option CODEPAGE de la requête, une page de codes qui correspond au schéma d'encodage utilisé dans la déclaration XML ;</span><span class="sxs-lookup"><span data-stu-id="b870c-137">Specify a code page in the CODEPAGE option of the query that matches the encoding scheme that is used in the XML declaration.</span></span>  
  
-   <span data-ttu-id="b870c-138">faire coïncider, ou corriger, les paramètres de classement avec un schéma d'encodage XML non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="b870c-138">Match, or resolve, the database collation settings with a non-Unicode XML encoding scheme.</span></span>  
  
 [<span data-ttu-id="b870c-139">&#91;Haut&#93;</span><span class="sxs-lookup"><span data-stu-id="b870c-139">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="b-bulk-importing-xml-data-in-an-existing-row"></a><a name="existing_row"></a> <span data-ttu-id="b870c-140">B.</span><span class="sxs-lookup"><span data-stu-id="b870c-140">B.</span></span> <span data-ttu-id="b870c-141">Importation en bloc de données XML dans une ligne existante</span><span class="sxs-lookup"><span data-stu-id="b870c-141">Bulk importing XML data in an existing row</span></span>  
 <span data-ttu-id="b870c-142">Cet exemple utilise le fournisseur d'ensemble de lignes en bloc `OPENROWSET` pour ajouter une instance XML à une ligne ou des lignes existantes dans la table d'exemple `T`.</span><span class="sxs-lookup"><span data-stu-id="b870c-142">This example uses the `OPENROWSET` bulk rowset provider to add an XML instance to an existing row or rows in sample table `T`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b870c-143">Pour exécuter cet exemple, vous devez d'abord terminer le script de test de l'exemple A. Cet exemple crée la table `tempdb.dbo.T` et importe des données en bloc à partir de `SampleData3.txt`.</span><span class="sxs-lookup"><span data-stu-id="b870c-143">To run this example, you must first complete the test script provided in example A. That example creates the `tempdb.dbo.T` table and bulk imports data from `SampleData3.txt`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="b870c-144">Fichier de données d'exemple</span><span class="sxs-lookup"><span data-stu-id="b870c-144">Sample Data File</span></span>  
 <span data-ttu-id="b870c-145">L'exemple B utilise une version modifiée du fichier de données d'exemple `SampleData3.txt` à partir de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="b870c-145">Example B uses a modified version of the `SampleData3.txt` sample data file from the preceding example.</span></span> <span data-ttu-id="b870c-146">Pour exécuter cet exemple, modifiez le contenu de ce fichier comme suit :</span><span class="sxs-lookup"><span data-stu-id="b870c-146">To run this example, modify the content of this file as follows:</span></span>  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a><span data-ttu-id="b870c-147">Exemple B</span><span class="sxs-lookup"><span data-stu-id="b870c-147">Example B</span></span>  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 [<span data-ttu-id="b870c-148">&#91;Haut&#93;</span><span class="sxs-lookup"><span data-stu-id="b870c-148">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="c-bulk-importing-xml-data-from-a-file-that-contains-a-dtd"></a><a name="file_contains_dtd"></a> <span data-ttu-id="b870c-149">C.</span><span class="sxs-lookup"><span data-stu-id="b870c-149">C.</span></span> <span data-ttu-id="b870c-150">Importation en bloc de données XML à partir d'un fichier contenant une DTD</span><span class="sxs-lookup"><span data-stu-id="b870c-150">Bulk importing XML data from a file that contains a DTD</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b870c-151">Il est recommandé de ne pas activer la prise en charge des définitions de type de document (DTD) si celle-ci n'est pas nécessaire à votre environnement XML.</span><span class="sxs-lookup"><span data-stu-id="b870c-151">We recommended that you not enable support for Document Type Definitions (DTDs) if it is not required in your XML environment.</span></span> <span data-ttu-id="b870c-152">En effet, son activation augmente la zone de surface attaquable de votre serveur qui peut se retrouver exposé à une attaque de déni de service.</span><span class="sxs-lookup"><span data-stu-id="b870c-152">Turning on DTD support increases the attackable surface area of your server, and may expose it to a denial-of-service attack.</span></span> <span data-ttu-id="b870c-153">Si vous devez activer la prise en charge DTD, vous pouvez réduire ce risque lié à la sécurité en traitant uniquement des documents XML approuvés.</span><span class="sxs-lookup"><span data-stu-id="b870c-153">If you must enable DTD support, you can reduce this security risk by processing only trusted XML documents.</span></span>  
  
 <span data-ttu-id="b870c-154">Si vous essayez d'utiliser une commande [bcp](../../tools/bcp-utility.md) pour importer des données XML à partir d'un fichier qui contient une DTD, une erreur semblable à celle-ci peut se produire :</span><span class="sxs-lookup"><span data-stu-id="b870c-154">During an attempt to use a [bcp](../../tools/bcp-utility.md) command to import XML data from a file that contains a DTD, an error similar to the following can occur:</span></span>  
  
 <span data-ttu-id="b870c-155">"SQLState = 42000, NativeError = 6359"</span><span class="sxs-lookup"><span data-stu-id="b870c-155">"SQLState = 42000, NativeError = 6359"</span></span>  
  
 <span data-ttu-id="b870c-156">"Erreur = [Microsoft][SQL Server Native Client][SQL Server]L'analyse de XML avec des DTD de sous-ensemble internes n'est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="b870c-156">"Error = [Microsoft][SQL Server Native Client][ SQL Server]Parsing XML with internal subset DTDs not allowed.</span></span> <span data-ttu-id="b870c-157">Utilisez CONVERT avec l'option de style 2 pour permettre une prise en charge limitée des DTD de sous-ensemble internes."</span><span class="sxs-lookup"><span data-stu-id="b870c-157">Use CONVERT with style option 2 to enable limited internal subset DTD support."</span></span>  
  
 <span data-ttu-id="b870c-158">"Échec de la copie BCP %s"</span><span class="sxs-lookup"><span data-stu-id="b870c-158">"BCP copy %s failed"</span></span>  
  
 <span data-ttu-id="b870c-159">Pour résoudre ce problème, vous pouvez importer des données XML à partir d'un fichier de données qui contient une DTD à l'aide de la fonction `OPENROWSET(BULK...)` et en spécifiant l'option `CONVERT` dans la clause `SELECT` de la commande.</span><span class="sxs-lookup"><span data-stu-id="b870c-159">To work around this problem, you can import XML data from a data file that contains a DTD by using the `OPENROWSET(BULK...)` function and then specifying the `CONVERT` option in the `SELECT` clause of the command.</span></span> <span data-ttu-id="b870c-160">La syntaxe de base pour la commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b870c-160">The basic syntax for the command is:</span></span>  
  
 `INSERT ... SELECT CONVERT(...) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a><span data-ttu-id="b870c-161">Fichier de données d'exemple</span><span class="sxs-lookup"><span data-stu-id="b870c-161">Sample Data File</span></span>  
 <span data-ttu-id="b870c-162">Avant de pouvoir tester cet exemple d’importation en bloc, créez un fichier (`C:\temp\Dtdfile.xml`) qui contient l’instance d’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b870c-162">Before you can test this bulk import example, create a file (`C:\temp\Dtdfile.xml`) that contains the following sample instance:</span></span>  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="b870c-163">Exemple de table</span><span class="sxs-lookup"><span data-stu-id="b870c-163">Sample Table</span></span>  
 <span data-ttu-id="b870c-164">L'exemple C utilise la table d'exemple `T1` créée par l'instruction `CREATE TABLE` suivante :</span><span class="sxs-lookup"><span data-stu-id="b870c-164">Example C uses the `T1` sample table that is created by the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a><span data-ttu-id="b870c-165">Exemple C</span><span class="sxs-lookup"><span data-stu-id="b870c-165">Example C</span></span>  
 <span data-ttu-id="b870c-166">Cet exemple utilise `OPENROWSET(BULK...)` et spécifie l'option `CONVERT` dans la clause `SELECT` pour importer les données XML à partir du fichier `Dtdfile.xml` dans la table d'exemple `T1`.</span><span class="sxs-lookup"><span data-stu-id="b870c-166">This example uses `OPENROWSET(BULK...)` and specifies the `CONVERT` option in the `SELECT` clause to import the XML data from `Dtdfile.xml` into sample table `T1`.</span></span>  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 <span data-ttu-id="b870c-167">Une fois l'instruction `INSERT` exécutée, la DTD est supprimée du code XML, puis stockée dans la table `T1` .</span><span class="sxs-lookup"><span data-stu-id="b870c-167">After the `INSERT` statement executes, the DTD is stripped from the XML and stored in the `T1` table.</span></span>  
  
 [<span data-ttu-id="b870c-168">&#91;Haut&#93;</span><span class="sxs-lookup"><span data-stu-id="b870c-168">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="d-specifying-the-field-terminator-explicitly-using-a-format-file"></a><a name="field_terminator_in_format_file"></a> <span data-ttu-id="b870c-169">D.</span><span class="sxs-lookup"><span data-stu-id="b870c-169">D.</span></span> <span data-ttu-id="b870c-170">Spécification explicite de la marque de fin de champ à l'aide d'un fichier de format</span><span class="sxs-lookup"><span data-stu-id="b870c-170">Specifying the field terminator explicitly using a format file</span></span>  
 <span data-ttu-id="b870c-171">L'exemple suivant montre l'importation en bloc du document XML suivant, `Xmltable.dat`.</span><span class="sxs-lookup"><span data-stu-id="b870c-171">The following example shows how to bulk import the following XML document, `Xmltable.dat`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="b870c-172">Fichier de données d'exemple</span><span class="sxs-lookup"><span data-stu-id="b870c-172">Sample Data File</span></span>  
 <span data-ttu-id="b870c-173">Le document dans le fichier `Xmltable.dat` contient deux valeurs XML, une pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="b870c-173">The document in `Xmltable.dat` contains two XML values, one for each row.</span></span> <span data-ttu-id="b870c-174">La première valeur XML est encodée en UTF-16, et la seconde en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b870c-174">The first XML value is encoded with UTF-16, and the second value is encoded with UTF-8.</span></span>  
  
 <span data-ttu-id="b870c-175">Le contenu de ce fichier de données est présenté dans le vidage hexadécimal suivant :</span><span class="sxs-lookup"><span data-stu-id="b870c-175">The contents of this data file are shown in the following Hex dump:</span></span>  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="b870c-176">Exemple de table</span><span class="sxs-lookup"><span data-stu-id="b870c-176">Sample Table</span></span>  
 <span data-ttu-id="b870c-177">Durant une importation ou une exportation en bloc d’un document XML, vous devez utiliser une [marque de fin de champ](specify-field-and-row-terminators-sql-server.md) qu’il est impossible de trouver dans les documents ; par exemple, une série de quatre valeurs Null (`\0`) suivie de la lettre `z`: `\0\0\0\0z`.</span><span class="sxs-lookup"><span data-stu-id="b870c-177">When you bulk import or export an XML document, you should use a [field terminator](specify-field-and-row-terminators-sql-server.md) that cannot possibly appear in any of the documents; for example, a series of four nulls (`\0`) followed by the letter `z`: `\0\0\0\0z`.</span></span>  
  
 <span data-ttu-id="b870c-178">Cet exemple illustre l'utilisation de cette marque de fin de champ pour la table d'exemple `xTable` .</span><span class="sxs-lookup"><span data-stu-id="b870c-178">This example shows how to use this field terminator for the `xTable` sample table.</span></span> <span data-ttu-id="b870c-179">Pour créer cette table d'exemple, utilisez les instructions `CREATE TABLE` suivantes :</span><span class="sxs-lookup"><span data-stu-id="b870c-179">To create this sample table, use the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a><span data-ttu-id="b870c-180">Fichier de format d'exemple</span><span class="sxs-lookup"><span data-stu-id="b870c-180">Sample Format File</span></span>  
 <span data-ttu-id="b870c-181">Le délimiteur de fin de champ doit être spécifié dans le fichier de format.</span><span class="sxs-lookup"><span data-stu-id="b870c-181">The field terminator must be specified in the format file.</span></span> <span data-ttu-id="b870c-182">L'exemple D utilise un fichier de format non XML intitulé `Xmltable.fmt` qui contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b870c-182">Example D uses a non-XML format file named `Xmltable.fmt` that contains the following:</span></span>  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 <span data-ttu-id="b870c-183">Vous pouvez utiliser ce fichier de format pour importer en bloc des documents XML dans la table `xTable` à l'aide d'une commande `bcp` ou d'une instruction `BULK INSERT` ou `INSERT ... SELECT * FROM OPENROWSET(BULK...)` .</span><span class="sxs-lookup"><span data-stu-id="b870c-183">You can use this format file to bulk import XML documents into the `xTable` table by using a `bcp` command or a `BULK INSERT` or `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="b870c-184">Exemple D</span><span class="sxs-lookup"><span data-stu-id="b870c-184">Example D</span></span>  
 <span data-ttu-id="b870c-185">Cet exemple utilise le fichier de format `Xmltable.fmt` dans une instruction `BULK INSERT` pour importer le contenu d'un fichier de données XML intitulé `Xmltable.dat`.</span><span class="sxs-lookup"><span data-stu-id="b870c-185">This example uses the `Xmltable.fmt` format file in a `BULK INSERT` statement to import the contents of an XML data file named `Xmltable.dat`.</span></span>  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 [<span data-ttu-id="b870c-186">&#91;Haut&#93;</span><span class="sxs-lookup"><span data-stu-id="b870c-186">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="e-bulk-exporting-xml-data"></a><a name="bulk_export_xml_data"></a> <span data-ttu-id="b870c-187">E.</span><span class="sxs-lookup"><span data-stu-id="b870c-187">E.</span></span> <span data-ttu-id="b870c-188">Exportation en bloc de données XML</span><span class="sxs-lookup"><span data-stu-id="b870c-188">Bulk exporting XML data</span></span>  
 <span data-ttu-id="b870c-189">L'exemple suivant utilise la commande `bcp` pour exporter en bloc des données XML à partir de la table créée dans l'exemple précédent, à l'aide du même fichier de format XML.</span><span class="sxs-lookup"><span data-stu-id="b870c-189">The following example uses `bcp` to bulk export XML data from the table that is created in the preceding example by using the same XML format file.</span></span> <span data-ttu-id="b870c-190">Dans la commande `bcp` suivante, `<server_name>` et `<instance_name>` représentent des espaces réservés qui doivent être remplacés par les valeurs appropriées :</span><span class="sxs-lookup"><span data-stu-id="b870c-190">In the following `bcp` command, `<server_name>` and `<instance_name>` represent placeholders that must be replaced with appropriate values:</span></span>  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b870c-191">n'enregistre pas l'encodage XML lorsque les données XML sont conservées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b870c-191">does not save the XML encoding when XML data is persisted in the database.</span></span> <span data-ttu-id="b870c-192">Par conséquent, l'encodage original des champs XML n'est pas disponible lorsque les données XML sont exportées.</span><span class="sxs-lookup"><span data-stu-id="b870c-192">Therefore, the original encoding of XML fields is not available when XML data is exported.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b870c-193">utilise l’encodage UTF-16 durant l’exportation de données XML.</span><span class="sxs-lookup"><span data-stu-id="b870c-193">uses UTF-16 encoding when exporting XML data.</span></span>  
  
 [<span data-ttu-id="b870c-194">&#91;Haut&#93;</span><span class="sxs-lookup"><span data-stu-id="b870c-194">&#91;Top&#93;</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="b870c-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b870c-195">See Also</span></span>  
 <span data-ttu-id="b870c-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b870c-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="b870c-197">[Clause SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b870c-197">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="b870c-198">[Utilitaire bcp](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b870c-198">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="b870c-199">[Importation et exportation en bloc de données &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b870c-199">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="b870c-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b870c-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="b870c-201">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b870c-201">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  