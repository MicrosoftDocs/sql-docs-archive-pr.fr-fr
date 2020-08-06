---
title: Simulation d’une sortie d’erreur pour le composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bed458ce378eb26cd863811b4974b5f39429e1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696995"
---
# <a name="simulating-an-error-output-for-the-script-component"></a>Simulation d'une sortie d'erreur pour le composant Script
  Bien qu'il soit impossible de configurer directement une sortie en tant que sortie d'erreur dans le composant Script à des fins de gestion automatique des lignes d'erreur, vous pouvez reproduire les fonctionnalités d'une sortie d'erreur intégrée en créant une sortie supplémentaire et en utilisant une logique conditionnelle dans votre script afin de diriger des lignes vers cette sortie, le cas échéant. Vous pouvez imiter le comportement d'une sortie d'erreur intégrée en ajoutant deux colonnes de sortie supplémentaires pour recevoir le numéro d'erreur et l'ID de la colonne dans laquelle une erreur s'est produite.  
  
 Si vous souhaitez ajouter la description d'erreur qui correspond à un code d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfini spécifique, vous pouvez utiliser la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, disponible via la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> du composant Script.  
  
## <a name="example"></a>Exemple  
 L'exemple indiqué ici utilise un composant Script configuré en tant que transformation qui possède deux sorties synchrones. L'objectif du composant Script est de filtrer les lignes d'erreur parmi les données d'adresse dans l'exemple de base de données AdventureWorks. Cet exemple fictif suppose que nous préparons une promotion pour les clients d'Amérique du Nord et que nous avons besoin d'éliminer les adresses qui ne se trouvent pas en Amérique du Nord par filtrage.  
  
#### <a name="to-configure-the-example"></a>Pour configurer l'exemple  
  
1.  Avant de créer le composant Script, créez un gestionnaire de connexions et configurez une source de flux de données qui sélectionne les données d'adresse de l'exemple de base de données AdventureWorks. Pour cet exemple, qui examine uniquement la colonne CountryRegionName, vous pouvez utiliser simplement la vue Person.vStateCountryProvinceRegion, ou vous pouvez sélectionner des données en liant les tables Person.Address, Person.StateProvince et Person.CountryRegion.  
  
2.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation. Ouvrez l' **Éditeur de transformation de script**.  
  
3.  Dans la page **Script**, définissez la propriété **ScriptLanguage** sur le langage de script que vous souhaitez utiliser pour coder le script.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
5.  Dans la méthode `Input0_ProcessInputRow`, tapez ou collez l'exemple de code indiqué ci-dessous.  
  
6.  Fermez VSTA.  
  
7.  Dans la page **Colonnes d’entrée**, sélectionnez les colonnes que vous souhaitez traiter dans la transformation de script. Cet exemple utilise uniquement la colonne CountryRegionName. Les colonnes d'entrée disponibles que vous n'avez pas sélectionnées seront tout simplement transférées sans être modifiées dans le flux de données.  
  
8.  Sur la page **entrées et sorties** , ajoutez une nouvelle sortie, puis définissez sa `SynchronousInputID` valeur sur l’ID de l’entrée, qui est également la valeur de la `SynchronousInputID` propriété de la sortie par défaut. Définissez la propriété `ExclusionGroup` des deux sorties sur la même valeur différente de zéro (par exemple, 1) pour indiquer que chaque ligne sera dirigée vers une seule des deux sorties. Attribuez à la nouvelle sortie d'erreur un nom distinct, tel que « MyErrorOutput ».  
  
9. Ajoutez des colonnes de sortie supplémentaires à la nouvelle sortie d'erreur pour capturer les informations d'erreur souhaitées, qui peuvent inclure le code de l'erreur, l'ID de la colonne dans laquelle l'erreur s'est produite et éventuellement la description de l'erreur. Cet exemple crée les nouvelles colonnes, ErrorColumn et ErrorMessage. Si vous interceptez des erreurs [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfinies dans votre propre implémentation, assurez-vous d'ajouter une colonne ErrorCode pour le numéro d'erreur.  
  
10. Notez la valeur d'ID de la ou des colonnes d'entrée dans lesquelles le composant Script va rechercher des conditions d'erreur. Cet exemple utilise cet identificateur de colonne pour renseigner la valeur ErrorColumn.  
  
11. Fermez l’**Éditeur de transformation de script**.  
  
12. Attachez les sorties du composant Script aux destinations appropriées. Les destinations de fichiers plats sont les plus faciles à configurer pour les tests ad hoc.  
  
13. Exécutez le package.  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs dans les données](../data-flow/error-handling-in-data.md)   
 [Utilisation des sorties d’erreur dans un composant de transmission de données](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Création d'une transformation synchrone à l'aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
