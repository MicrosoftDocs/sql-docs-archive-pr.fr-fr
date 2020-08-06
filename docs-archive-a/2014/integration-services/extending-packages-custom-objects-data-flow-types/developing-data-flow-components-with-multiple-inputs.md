---
title: Développement de composants de flux de données avec plusieurs entrées | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb56878c1b1b68dfdc4de19cb2b811de494c761b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705312"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a>Développement de composants de flux de données avec plusieurs entrées
  Un composant de flux de données avec plusieurs entrées peut consommer excessivement de la mémoire si ses entrées multiples produisent des données à des taux irréguliers. Lorsque vous développez un composant de flux de données personnalisé qui prend en charge plusieurs entrées, vous pouvez gérer cette sollicitation de la mémoire en utilisant les membres suivants dans l’espace de noms Microsoft.SqlServer.Dts.Pipeline :  
  
-   La propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> de la classe <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Définissez la valeur de cette propriété à `true` si vous souhaitez implémenter le code qui est nécessaire pour votre composant de flux de données personnalisé afin de gérer des données qui s'écoulent à des taux irréguliers.  
  
-   La méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> de la classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Vous devez fournir une implémentation de cette méthode si vous définissez la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> à `true`. Si vous ne fournissez pas d'implémentation, le moteur de flux de données lève une exception au moment de l'exécution.  
  
-   La méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> de la classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Vous devez également fournir une implémentation de cette méthode si vous définissez la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> à `true` et que votre composant personnalisé prend en charge plusieurs entrées. Si vous ne fournissez pas d'implémentation, le moteur de flux de données lève une exception au moment de l'exécution si l'utilisateur joint plusieurs entrées.  
  
 Ces deux membres vous permettent de développer une solution pour la sollicitation de la mémoire qui est semblable à la solution que Microsoft a développée pour les transformations de fusion et de jointure de la fusion.  
  
## <a name="setting-the-supportsbackpressure-property"></a>Définition de la propriété SupportsBackPressure  
 La première étape pour l'implémentation d'une meilleure gestion de la mémoire pour un composant de flux de données personnalisé qui prend en charge plusieurs entrées consiste à définir la valeur de la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> à `true` dans le <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Lorsque la valeur de <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> est `true`, le moteur de flux de données appelle la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> et, lorsqu'il y a plusieurs entrées, il appelle également la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> au moment de l'exécution.  
  
### <a name="example"></a>Exemple  
 Dans l'exemple suivant, l'implémentation du <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> définit la valeur de <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> à `true`.  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a>Implémentation de la méthode IsInputReady  
 Lorsque vous définissez la valeur de la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> à `true` dans l'objet <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>, vous devez également fournir une implémentation pour la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> de la classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
> [!NOTE]  
>  Votre implémentation de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> ne doit pas appeler les implémentations dans la classe de base. L'implémentation par défaut de cette méthode dans la classe de base lève simplement une `NotImplementedException`.  
  
 Lorsque vous implémentez cette méthode, vous définissez l’état d’un élément dans le tableau booléen *canProcess* pour chacune des entrées du composant. (Les entrées sont identifiées par leurs valeurs d’ID dans le tableau *inputIDs* .) Lorsque vous définissez la valeur d’un élément dans le tableau *canProcess* sur `true` pour une entrée, le moteur de workflow appelle la méthode du composant <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> et fournit davantage de données pour l’entrée spécifiée.  
  
 Alors que davantage de données en amont sont disponibles, la valeur de l’élément de tableau *canProcess* pour au moins une entrée doit toujours être `true` , sinon le traitement s’arrête.  
  
 Le moteur de flux de données appelle la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> avant d'envoyer chaque mémoire tampon de données pour  déterminer quelles entrées attendent de recevoir d'autres données. Lorsque la valeur de retour indique qu'une entrée est bloquée, le moteur de flux de données met temporairement en cache les mémoires tampon supplémentaires de données pour cette entrée au lieu de les envoyer au composant.  
  
> [!NOTE]  
>  Vous n'appelez pas les méthodes <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> ou <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> dans votre propre code. Le moteur de flux de données appelle ces méthodes, et les autres méthodes de la classe `PipelineComponent` que vous remplacez, lorsque le moteur de flux de données exécute votre composant.  
  
### <a name="example"></a>Exemple  
 Dans l'exemple suivant, l'implémentation de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> indique qu'une entrée attend pour recevoir plus de données lorsque les conditions suivantes sont remplies :  
  
-   Plus de données en amont sont disponibles pour l'entrée (`!inputEOR`).  
  
-   Le composant n'a pas actuellement de données disponibles pour traiter l'entrée dans les mémoires tampon que le composant a déjà reçues (`inputBuffers[inputIndex].CurrentRow() == null`).  
  
 Si une entrée attend de recevoir plus de données, le composant de transmission de données indique cela en définissant sur `true` la valeur de l’élément dans le tableau *canProcess* qui correspond à cette entrée.  
  
 Inversement, lorsque le composant a encore des données disponibles à traiter pour l'entrée, l'exemple interrompt le traitement de l'entrée. L’exemple fait cela en définissant sur `false` la valeur de l’élément dans le tableau *canProcess* qui correspond à cette entrée.  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 L'exemple précédent utilise le tableau `inputEOR` booléen pour indiquer si davantage de données en amont sont disponibles pour chaque entrée. `EOR` dans le nom du tableau représente « fin d'ensemble de lignes » et fait référence à la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> de mémoires tampon de flux de données. Dans une partie de l'exemple qui n'est pas inclus ici, la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> vérifie la valeur de la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> pour chaque mémoire tampon des données qu'elle reçoit. Lorsqu'une valeur `true` indique que plus aucune donnée en amont n'est disponible pour une entrée, l'exemple définit la valeur de l'élément de tableau `inputEOR` pour cette entrée à `true`. Cet exemple de la <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> méthode définit la valeur de l’élément correspondant dans le tableau *canProcess* sur `false` pour une entrée lorsque la valeur de l' `inputEOR` élément de tableau indique qu’il n’y a plus de données en amont disponibles pour l’entrée.  
  
## <a name="implementing-the-getdependentinputs-method"></a>Implémentation de la méthode GetDependentInputs  
 Lorsque votre composant de flux de données personnalisé prend en charge plus de deux entrées, vous devez également fournir une implémentation pour la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> de la classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
> [!NOTE]  
>  Votre implémentation de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> ne doit pas appeler les implémentations dans la classe de base. L'implémentation par défaut de cette méthode dans la classe de base lève simplement une `NotImplementedException`.  
  
 Le moteur de flux de données appelle seulement la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> lorsque l'utilisateur joint plus de deux entrées au composant. Lorsqu’un composant a uniquement deux entrées, et <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> que la méthode indique qu’une entrée est bloquée (*canProcess*  =  `false` ), le moteur de workflow sait que l’autre entrée attend de recevoir plus de données. Toutefois, lorsqu'il y a plus de deux entrées, et que la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> indique qu'une entrée est bloquée, le code supplémentaire dans le <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> identifie quelles entrées attendent de recevoir plus de données.  
  
> [!NOTE]  
>  Vous n'appelez pas les méthodes <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> ou <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> dans votre propre code. Le moteur de flux de données appelle ces méthodes, et les autres méthodes de la classe `PipelineComponent` que vous remplacez, lorsque le moteur de flux de données exécute votre composant.  
  
### <a name="example"></a>Exemple  
 Pour une entrée spécifique bloquée, l'implémentation suivante de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> retourne une collection des entrées qui attendent de recevoir plus de données et par conséquent bloque l'entrée spécifiée. Le composant identifie les entrées bloquantes en recherchant d'autres entrées que celle qui est bloquée qui n'ont pas actuellement de données disponibles pour traiter dans les mémoires tampon que le composant a déjà reçues (`inputBuffers[i].CurrentRow() == null`). La méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> retourne ensuite la collection d'entrées bloquantes comme une collection d'ID d'entrée.  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  
