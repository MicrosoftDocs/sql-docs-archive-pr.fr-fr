---
title: Utilisation de fichiers Excel avec la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68a764452de548cd46e74d2a7f2f588a050a21c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605656"
---
# <a name="working-with-excel-files-with-the-script-task"></a>Utilisation de fichiers Excel avec la tâche de script
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit le gestionnaire de connexions Excel, la source Excel et la destination Excel pour utiliser des données stockées dans des feuilles de calcul au format de fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Les techniques décrites dans cette rubrique utilisent la tâche de script pour obtenir des informations sur les bases de données (fichiers de classeur) et tables (feuilles de calcul et plages nommées) Excel disponibles. Ces exemples peuvent être modifiés facilement afin d'utiliser l'une des autres sources de données basées sur des fichiers prises en charge par le fournisseur OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
 [Configuration d’un package pour tester les exemples](#configuring)  
  
 [Exemple 1 : vérifier si un fichier Excel existe](#example1)  
  
 [Exemple 2 : vérifier si une table Excel existe](#example2)  
  
 [Exemple 3 : obtenir la liste des fichiers Excel contenus dans un dossier](#example3)  
  
 [Exemple 4 : obtenir la liste des tables contenues dans un fichier Excel](#example4)  
  
 [Affichage des résultats des exemples](#testing)  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
##  <a name="configuring-a-package-to-test-the-samples"></a><a name="configuring"></a> Configuration d’un package pour tester les exemples  
 Vous pouvez configurer un package unique pour tester tous les exemples de cette rubrique. Les exemples utilisent de nombreuses variables de package et classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] identiques.  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>Pour configurer un package à utiliser avec les exemples de cette rubrique  
  
1.  Créez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et ouvrez le package par défaut afin de le modifier.  
  
2.  **Variables**. Ouvrez la fenêtre **Variables** et définissez les variables suivantes :  
  
    -   `ExcelFile`, de type `String`. Entrez le chemin d'accès complet et le nom de fichier d'un classeur Excel existant.  
  
    -   `ExcelTable`, de type `String`. Entrez le nom d'une feuille de calcul ou d'une plage nommée existante dans le classeur nommé dans la valeur de la variable `ExcelFile`. Cette valeur respecte la casse.  
  
    -   `ExcelFileExists`, de type `Boolean`.  
  
    -   `ExcelTableExists`, de type `Boolean`.  
  
    -   `ExcelFolder`, de type `String`. Entrez le chemin d'accès complet d'un dossier qui contient au moins un classeur Excel.  
  
    -   `ExcelFiles`, de type `Object`.  
  
    -   `ExcelTables`, de type `Object`.  
  
3.  **Instructions Imports**. La plupart des exemples de code impliquent que vous importiez l'un des espaces de noms [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] suivants ou les deux au début de votre fichier de script :  
  
    -   `System.IO`, pour les opérations du système de fichiers.  
  
    -   `System.Data.OleDb`, pour ouvrir des fichiers Excel en tant que sources de données.  
  
4.  **Références**. Les exemples de code qui lisent des informations de schéma à partir de fichiers Excel requièrent une référence supplémentaire, dans le projet de script, à l'espace de noms `System.Xml`.  
  
5.  Définissez le langage de script par défaut du composant Script en utilisant l’option **Langage de script** dans la page **Général** de la boîte de dialogue **Options**. Pour plus d'informations, consultez [General Page](../general-page-of-integration-services-designers-options.md).  
  
##  <a name="example-1-description-check-whether-an-excel-file-exists"></a><a name="example1"></a> Description de l’exemple 1 : vérifier si un fichier Excel existe  
 Cet exemple détermine si le fichier de classeur Excel spécifié dans la variable `ExcelFile` existe, puis définit la valeur booléenne de la variable `ExcelFileExists` sur le résultat. Vous pouvez utiliser cette valeur booléenne pour créer une branche dans le flux de travail du package.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajoutez une nouvelle tâche de script au package et remplacez son nom par `ExcelFileExists` .  
  
2.  Dans l’**Éditeur de tâche de script**, sous l’onglet **Script**, cliquez sur **ReadOnlyVariables** et entrez la valeur de la propriété en utilisant l’une des méthodes suivantes :  
  
    -   Tapez `ExcelFile`.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la `ExcelFile` variable.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide de l’une des méthodes suivantes :  
  
    -   Tapez `ExcelFileExists`.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la `ExcelFileExists` variable.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une instruction `Imports` pour l'espace de noms `System.IO` au début du fichier de script.  
  
6.  Ajoutez le code ci-dessous.  
  
### <a name="example-1-code"></a>Code de l’exemple 1  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example-2-description-check-whether-an-excel-table-exists"></a><a name="example2"></a> Description de l’exemple 2 : vérifier si une table Excel existe  
 Cet exemple détermine si la feuille de calcul ou la plage nommée Excel spécifiée dans la variable `ExcelTable` existe dans le fichier de classeur Excel spécifié dans la variable `ExcelFile`, puis définit la valeur booléenne de la variable `ExcelTableExists` sur le résultat. Vous pouvez utiliser cette valeur booléenne pour créer une branche dans le flux de travail du package.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajoutez une nouvelle tâche de script au package et remplacez son nom par `ExcelTableExists` .  
  
2.  Dans l’**Éditeur de tâche de script**, sous l’onglet **Script**, cliquez sur **ReadOnlyVariables** et entrez la valeur de la propriété en utilisant l’une des méthodes suivantes :  
  
    -   Tapez `ExcelTable` et `ExcelFile` séparez-les par des virgules`.`  
  
         -ou-  
  
    -   Cliquez sur le bouton des points de suspension (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez les `ExcelTable` `ExcelFile` variables et.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide de l’une des méthodes suivantes :  
  
    -   Tapez `ExcelTableExists`.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la `ExcelTableExists` variable.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une référence à l'assembly `System.Xml` dans le projet de script.  
  
6.  Ajoutez des instructions `Imports` pour les espaces de noms `System.IO` et `System.Data.OleDb` au début du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
### <a name="example-2-code"></a>Code de l’exemple 2  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example-3-description-get-a-list-of-excel-files-in-a-folder"></a><a name="example3"></a> Description de l’exemple 3 : obtenir la liste des fichiers Excel contenus dans un dossier  
 Cet exemple remplit un tableau à l'aide de la liste des fichiers Excel détectés dans le dossier spécifié dans la valeur de la variable `ExcelFolder`, puis copie le tableau dans la variable `ExcelFiles`. Vous pouvez utiliser l'énumérateur Foreach à partir d'une variable pour parcourir les fichiers inclus dans le tableau.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajoutez une nouvelle tâche de script au package et remplacez son nom par **GetExcelFiles**.  
  
2.  Ouvrez l’**Éditeur de tâche de script**, puis sous l’onglet **Script**, cliquez sur **ReadOnlyVariables** et entrez la valeur de la propriété en utilisant l’une des méthodes suivantes :  
  
    -   Tapez `ExcelFolder`.  
  
         -ou-  
  
    -   Cliquez sur le bouton des points de suspension (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la variable ExcelFolder.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide de l’une des méthodes suivantes :  
  
    -   Tapez `ExcelFiles`.  
  
         -ou-  
  
    -   Cliquez sur le bouton des points de suspension (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la variable EXCELFiles.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une instruction `Imports` pour l'espace de noms `System.IO` au début du fichier de script.  
  
6.  Ajoutez le code ci-dessous.  
  
### <a name="example-3-code"></a>Code de l’exemple 3  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a>Autre solution  
 Au lieu d'utiliser une tâche de script pour dresser la liste des fichiers Excel dans un tableau, vous pouvez également utiliser l'énumérateur ForEach File pour parcourir tous les fichiers Excel inclus dans un dossier. Pour plus d’informations, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md).  
  
##  <a name="example-4-description-get-a-list-of-tables-in-an-excel-file"></a><a name="example4"></a> Description de l’exemple 4 : obtenir la liste des tables contenues dans un fichier Excel  
 Cet exemple remplit un tableau à l'aide de la liste des feuilles de calcul et plages nommées détectées dans le fichier de classeur Excel spécifié par la valeur de la variable `ExcelFile`, puis copie le tableau dans la variable `ExcelTables`. Vous pouvez utiliser l'énumérateur Foreach à partir d'une variable pour parcourir les tables incluses dans le tableau.  
  
> [!NOTE]  
>  La liste des tableaux d'un classeur Excel comprend à la fois les feuilles de calcul (affectées du suffixe $) et les plages nommées. Si vous devez filtrer la liste uniquement pour obtenir uniquement les feuilles de calcul ou les plages nommées, vous pouvez être amené à ajouter du code supplémentaire.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajoutez une nouvelle tâche de script au package et remplacez son nom par **GetExcelTables**.  
  
2.  Ouvrez l’**Éditeur de tâche de script**, puis sous l’onglet **Script**, cliquez sur **ReadOnlyVariables** et entrez la valeur de la propriété en utilisant l’une des méthodes suivantes :  
  
    -   Tapez `ExcelFile`.  
  
         -ou-  
  
    -   Cliquez sur le bouton des points de suspension (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez la variable ExcelFile.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide de l’une des méthodes suivantes :  
  
    -   Tapez `ExcelTables`.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables** , sélectionnez ExcelTablesvariable.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une référence à l'espace de noms `System.Xml` dans le projet de script.  
  
6.  Ajoutez une instruction `Imports` pour l'espace de noms `System.Data.OleDb` au début du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
### <a name="example-4-code"></a>Code de l'exemple 4  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a>Autre solution  
 Au lieu d'utiliser une tâche de script pour dresser la liste des tables Excel dans un tableau, vous pouvez également utiliser l'énumérateur d'ensemble de lignes du schéma ADO.NET Foreach pour parcourir toutes les tables (autrement dit, les feuilles de calcul et les plages nommées) contenues dans un fichier de classeur Excel. Pour plus d’informations, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md).  
  
##  <a name="displaying-the-results-of-the-samples"></a><a name="testing"></a> Affichage des résultats des exemples  
 Si vous avez configuré chacun des exemples de cette rubrique dans le même package, vous pouvez connecter toutes les tâches de script à une tâche de script supplémentaire qui affiche la sortie de tous les exemples.  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>Pour configurer une tâche de script afin d'afficher la sortie des exemples de cette rubrique  
  
1.  Ajoutez une nouvelle tâche de script au package et remplacez son nom par **DisplayResults**.  
  
2.  Connectez les quatre exemples de tâche de script entre eux, afin que chaque tâche s’exécute une fois que la tâche précédente s’est correctement achevée, puis connectez le quatrième exemple de tâche à la tâche **DisplayResults**.  
  
3.  Ouvrez la tâche **DisplayResults** dans l’**Éditeur de tâche de script**.  
  
4.  Sous l’onglet **Script**, cliquez sur **ReadOnlyVariables** et utilisez l’une des méthodes suivantes pour ajouter les sept variables répertoriées dans [Configuration d’un package pour tester les exemples](#configuring) :  
  
    -   Tapez le nom de chaque variable en les séparant par des virgules.  
  
         -ou-  
  
    -   Cliquez sur le bouton des points de suspension (**...**) en regard du champ de propriété, puis dans la boîte de dialogue **Sélectionner des variables, sélectionnez** les variables.  
  
5.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script.  
  
6.  Ajoutez des instructions `Imports` pour les espaces de noms `Microsoft.VisualBasic` et `System.Windows.Forms` au début du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
8.  Exécutez le package et examinez les résultats qui s'affichent dans un message.  
  
### <a name="code-to-display-the-results"></a>Code permettant d'afficher les résultats  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Excel](../connection-manager/excel-connection-manager.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md)  
  
  
