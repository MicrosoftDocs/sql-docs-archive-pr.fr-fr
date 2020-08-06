---
title: Surveillance des compteurs de performances à l’aide de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 143e11ff966eb11961aa15073a503522c4b9c86b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705291"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a>Surveillance des compteurs de performances à l'aide de la tâche de script
  Les administrateurs peuvent avoir besoin de surveiller les performances des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui effectuent des transformations complexes sur de grandes quantités de données. L’espace de noms **System.Diagnostics** de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit des classes permettant d’utiliser des compteurs de performances existants et de créer vos propres compteurs de performances.  
  
 Les compteurs de performances stockent des informations sur les performances des applications que vous pouvez utiliser pour analyser les performances des logiciels dans le temps. Les compteurs de performances peuvent être surveillés localement ou à distance en utilisant l’outil **Analyseur de performances**. Vous pouvez stocker les valeurs des compteurs de performances dans des variables à des fins de branchement ultérieur du flux de contrôle dans le package.  
  
 Comme alternative à l'utilisation des compteurs de performances, vous pouvez déclencher l'événement <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> de l'objet `Dts`. L'événement <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> indique à la fois les stades intermédiaires de l'avancement et le pourcentage d'avancement à l'exécution [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 L'exemple suivant crée un compteur de performance personnalisé et incrémente le compteur. Tout d'abord, l'exemple détermine si le compteur de performance existe déjà. Si le compteur de performance n'a pas été créé, le script appelle la méthode `Create` de l'objet `PerformanceCounterCategory` pour le créer. Après avoir créé le compteur de performance, le script incrémente le compteur. Enfin, l'exemple suit la méthode conseillée qui consiste à appeler la méthode `Close` sur le compteur de performance lorsqu'il n'est plus nécessaire.  
  
> [!NOTE]  
>  La création d'une nouvelle catégorie de compteur de performance et d'un compteur de performance requiert des droits d'administration. En outre, la nouvelle catégorie et le compteur subsistent sur l'ordinateur après leur création.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
-   Utilisez une `Imports` instruction dans votre code pour importer l’espace de noms **System. Diagnostics** .  
  
### <a name="example-code"></a>Exemple de code  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
