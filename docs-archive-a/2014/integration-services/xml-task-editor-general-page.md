---
title: Éditeur de tâche XML (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f73681a818d80c4e8b2755086e653e5c7e682f01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705239"
---
# <a name="xml-task-editor-general-page"></a>XML Task Editor (General Page)
  Utilisez le nœud **Général** de la boîte de dialogue **Éditeur de tâche XML** pour préciser le type d'opération à effectuer, puis la configurer.  
  
 Pour en savoir plus sur cette tâche, consultez [XML Task](control-flow/xml-task.md). Pour plus d'informations sur l'utilisation de documents et de données XML, consultez «[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)» (en anglais) dans MSDN Library.  
  
## <a name="static-options"></a>Options statiques  
 **OperationType**  
 Permet de sélectionner le type d'opération dans la liste. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Procéder à la validation**|Permet de valider le document XML en utilisant un DTD (Document Type Definition) ou un schéma XSD (XML Schema definition). Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **Valider**s'affichent alors.|  
|**XSLT**|Effectue les transformations XSL sur les documents XML. Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **XSLT**s'affichent alors.|  
|**XPATH**|Lance les requêtes et les évaluations XPath. Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **XPATH**s'affichent alors.|  
|**Fusionner**|Permet de fusionner deux documents XML. Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **Fusionner**s'affichent alors.|  
|**Diff**|Permet de comparer deux documents XML. Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **Diff**s'affichent alors.|  
|**Patch**|Permet d'appliquer la sortie de l'opération Diff afin de créer un document. Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **Patch**s'affichent alors.|  
  
 **SourceType**  
 Permet de sélectionner le type de source correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **Source**  
 Si **Source** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source de document**.  
  
 Si **Source** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **Source** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur **\<New variable...>** pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
## <a name="operationtype-dynamic-options"></a>Options dynamiques OperationType  
  
### <a name="operationtype--validate"></a>OperationType = Validate  
 Permet d'indiquer les options de l'opération Validate.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie produite par l'opération Validate.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **ValidationType**  
 Permet de sélectionner le type de validation. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**DTD**|Permet d'utiliser un DTD (Document Type Definition).|  
|**XSD**|Permet d'utiliser un schéma XSD (XML Schema Definition Language). Si cette valeur est sélectionnée, les options dynamiques incluses dans la section **ValidationType**s'affichent.|  
  
 **FailOnValidationFail**  
 Permet d'indiquer si le document doit ne pas être validé si l'opération échoue.  
  
 **ValidationDetails**  
 Fournit une sortie d’erreur détaillée quand la valeur de cette propriété est true. Pour plus d’informations, consultez [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).  
  
### <a name="validationtype-dynamic-options"></a>Options dynamiques de ValidationType  
  
#### <a name="validationtype--xsd"></a>ValidationType = XSD  
 **SecondOperandType**  
 Permet de sélectionner le type de source correspondant au deuxième document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source**.  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **XPathStringSourceType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
### <a name="operationtype--xslt"></a>OperationType = XSLT  
 Permet d'indiquer les options relatives à l'opération de transformation XSLT.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie produite par l'opération XSLT.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Si **DestinationType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DestinationType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperandType**  
 Permet de sélectionner le type de source correspondant au deuxième document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source**.  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **XPathStringSourceType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
### <a name="operationtype--xpath"></a>OperationType = XPATH  
 Permet de spécifier les options relatives à l'opération XPath.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie de l'opération XPath.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Si **DestinationType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DestinationType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperandType**  
 Permet de sélectionner le type de source correspondant au deuxième document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source**.  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **XPathStringSourceType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **PutResultInOneNode**  
 Permet de spécifier si le résultat doit être écrit dans un seul nœud.  
  
 **XPathOperation**  
 Permet d'indiquer le type de résultat XPath. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Evaluation**|Permet de retourner les résultats d'une fonction XPath.|  
|**Liste de nœuds**|Permet de retourner les nœuds sélectionnés en tant que fragment XML.|  
|**Valeurs**|Permet de retourner la valeur interne du texte correspondant à tous les nœuds sélectionnés, sous forme de chaîne concaténée.|  
  
### <a name="operationtype--merge"></a>OperationType = Fusionner  
 Permet d'indiquer les différentes options de l'opération Fusionner.  
  
 **XPathStringSourceType**  
 Permet de sélectionner le type de source correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **XPathStringSource**  
 Si **XPathStringSourceType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source de document**.  
  
 Si **XPathStringSourceType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **XPathStringSourceType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 Lorsque vous utilisez une instruction XPath pour identifier l'emplacement de fusion dans le document source, cette instruction est supposée retourner un nœud unique. Si elle retourne plusieurs nœuds, seul le premier est utilisé. Le contenu du deuxième document est fusionné sous le premier nœud que la requête XPath retourne.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie produite par l'opération Fusionner.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Si **DestinationType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DestinationType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperandType**  
 Permet de sélectionner le type de destination correspondant au deuxième document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source de document** .  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **SecondOperandType** a la valeur **Variable**, sélectionnez une variable existante, ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
### <a name="operationtype--diff"></a>OperationType = Diff  
 Permet d'indiquer les différentes options de l'opération Diff.  
  
 **DiffAlgorithm**  
 Permet de sélectionner l'algorithme Diff à utiliser pour la comparaison de documents. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Automatique**|Laisse la tâche XML déterminer si l'algorithme à utiliser est l'algorithme rapide ou l'algorithme précis.|  
|**Rapide**|L'algorithme de comparaison utilisé est le plus rapide des deux, mais aussi le moins précis.|  
|**Précise**|L'algorithme de comparaison utilisé est le plus précis des deux.|  
  
 **Options Diff**  
 Permet de définir les options de comparaison s'appliquant à l'opération Diff. Ces fonctions sont répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**IgnoreXMLDeclaration**|Permet d'indiquer si la déclaration XML doit être comparée.|  
|**IgnoreDTD**|Permet d'ignorer le DTD (Document Type Definition).|  
|**IgnoreWhite Spaces**|Spécifie s'il faut ignorer les différences dans le nombre d'espaces vides lorsque des documents sont comparés.|  
|**IgnoreNamespaces**|Permet d'indiquer si la comparaison doit aussi porter sur l'URI (Uniform Resource Identifier) d'espace de nom relatif à un élément ainsi que sur les noms d'attribut de ce même élément.<br /><br /> Remarque : si cette option a la valeur `True`, deux éléments possédant le même nom local, mais des espaces de nom distincts sont considérés comme identiques.|  
|**IgnoreProcessingInstructions**|Permet d'indiquer si les instructions de traitement doivent être comparées.|  
|**IgnoreOrderOf ChildElements**|Permet d'indiquer si l'ordre des éléments enfants doit être comparé.<br /><br /> Remarque : si cette option a la valeur `True`, les éléments enfants qui diffèrent uniquement par leur position dans une liste de frères sont considérés comme identiques.|  
|**IgnoreComments**|Permet d'indiquer si les nœuds de commentaires doivent être comparés.|  
|**IgnorePrefixes**|Permet d'indiquer si les préfixes d'un élément et ses noms d'attribut doivent être comparés.<br /><br /> Remarque : si vous définissez cette option sur `True`, deux éléments possédant le même nom local, mais des URI et des préfixes d’espace de nom distincts sont considérés comme identiques.|  
  
 **FailOnDifference**  
 Permet d'indiquer si la tâche échoue si l'opération Diff échoue.  
  
 **SaveDiffGram**  
 Permet d'enregistrer ou non le résultat de comparaison sous forme de document DiffGram.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie produite par l'opération Diff.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Si **DestinationType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DestinationType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperandType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source de document** .  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **SecondOperandType** a la valeur **Variable**, sélectionnez une variable existante, ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
### <a name="operationtype--patch"></a>OperationType = Patch  
 Permet d'indiquer les différentes options de l'opération Patch.  
  
 **SaveOperationResult**  
 Indique si la tâche XML enregistre ou non la sortie produite par l'opération Patch.  
  
 **OverwriteDestination**  
 Permet de spécifier si le fichier ou la variable de destination doit être remplacé.  
  
 **Destination**  
 Si **DestinationType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DestinationType** a la valeur **Variable**, sélectionnez une variable existante ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperandType**  
 Permet de sélectionner le type de destination correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **SecondOperand**  
 Si **SecondOperandType** a la valeur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton de sélection **(...)** pour fournir le code XML nécessaire dans la boîte de dialogue **Éditeur de source de document** .  
  
 Si **SecondOperandType** a la valeur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**New connection...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **SecondOperandType** a la valeur **Variable**, sélectionnez une variable existante, ou cliquez sur \<**New variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
