---
title: Utilisation de variables dans la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710744"
---
# <a name="using-variables-in-the-script-task"></a>Utilisation de variables dans la tâche de script
  Les variables permettent à la tâche de script d'échanger des données avec d'autres objets dans le package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../../integration-services-ssis-variables.md).  
  
 La tâche de script utilise la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> de l'objet `Dts` pour lire et écrire dans les objets <xref:Microsoft.SqlServer.Dts.Runtime.Variable> du package.  
  
> [!NOTE]  
>  La propriété <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> de la classe <xref:Microsoft.SqlServer.Dts.Runtime.Variable> est de type `Object`. Comme `Option Strict` est activé dans la tâche de script, vous devez effectuer un cast de la propriété <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> en type approprié avant de pouvoir l'utiliser.  
  
 Vous ajoutez des variables existantes aux listes <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> et <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> dans l’**éditeur de tâche de script** afin qu’elles puissent être utilisées dans le script personnalisé. N'oubliez pas que les noms de variables respectent la casse. Dans le script, vous accédez aux deux types de variables par le biais de la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> de l'objet `Dts`. Utilisez la propriété `Value` pour lire et écrire des variables individuelles. La tâche de script gère de façon transparente le verrouillage pendant que le script lit et modifie les valeurs des variables.  
  
 La méthode <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> de la collection <xref:Microsoft.SqlServer.Dts.Runtime.Variables> retournée par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> vous permet de vérifier l'existence d'une variable avant de l'utiliser dans votre code.  
  
 La propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> (Dts.VariableDispenser) vous permet également d’utiliser des variables dans la tâche de script. Lorsque vous utilisez la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, vous devez gérer à la fois la sémantique de verrouillage et la conversion des types de données pour les valeurs de variables dans votre propre code. Vous pourriez devoir utiliser la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> à la place de la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> si vous souhaitez utiliser une variable qui n'est pas disponible au moment de la conception mais qui est créée par programme au moment de l'exécution.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Utilisation de la tâche de script dans un conteneur de boucles Foreach  
 Lorsqu'une tâche de script s'exécute à plusieurs reprises dans un conteneur de boucles Foreach, le script doit généralement utiliser le contenu de l'élément actif dans l'énumérateur. Par exemple, lors de l'utilisation d'un énumérateur Foreach File, le script doit connaître le nom du fichier actif ; lors de l'utilisation d'un énumérateur ADO Foreach, le script doit connaître le contenu des colonnes dans la ligne de données en cours.  
  
 Les variables permettent d'établir cette communication entre le conteneur de boucles Foreach et la tâche de script. Dans la page **Mappage de variables** de l’**Éditeur de boucle Foreach**, assignez des variables à chaque élément de données qui est retourné par un même élément énuméré. Par exemple, un énumérateur Foreach File retourne uniquement un nom de fichier à l'index 0 et ne requiert donc qu'un seul mappage de variables, alors qu'un énumérateur qui retourne plusieurs colonnes de données dans chaque ligne requiert que vous mappiez une variable différente à chaque colonne que vous souhaitez utiliser dans la tâche de script.  
  
 Une fois que vous avez mappé les éléments énumérés aux variables, vous devez ajouter les variables mappées à la `ReadOnlyVariables` propriété dans la page **script** de l **'éditeur de tâche de script** pour les mettre à la disposition de votre script. Pour obtenir un exemple de tâche de script dans un conteneur de boucles Foreach qui traite les fichiers image dans un dossier, consultez [Utilisation d’images à l’aide de la tâche de script](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Exemple de variables  
 L'exemple suivant montre comment accéder à des variables et les utiliser dans une tâche de script pour déterminer le chemin d'accès du flux de travail du package. L’exemple suppose que vous avez créé des variables de type entier nommées et que vous les avez `CustomerCount` `MaxRecordCount` ajoutées à la `ReadOnlyVariables` collection dans l **'éditeur de tâche de script**. La variable `CustomerCount` contient le nombre d'enregistrements de client à importer. Si sa valeur est supérieure à la valeur de `MaxRecordCount`, la tâche de script signale une défaillance. Lorsqu'une défaillance se produit en raison du dépassement du seuil `MaxRecordCount`, le chemin d'accès aux erreurs du flux de travail peut implémenter les opérations de nettoyage requises.  
  
 Pour compiler correctement l'exemple, vous devez ajouter une référence à l'assembly Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services-ssis-variables.md)   
 [Utiliser des variables dans des packages](../../use-variables-in-packages.md)  
  
  
