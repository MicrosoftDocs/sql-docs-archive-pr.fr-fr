---
title: Boîte de message d’exception de programme | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9d49bdf8c73f86b2c334018d40510b4ae67c85ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708591"
---
# <a name="program-exception-message-box"></a>Programmer la boîte de message d'exceptions
  Vous pouvez utiliser la boîte de message d'exception dans vos applications pour fournir un contrôle nettement supérieur sur les messages que celui fourni par la classe <xref:System.Windows.Forms.MessageBox>. Pour plus d’informations, consultez [programmation de la boîte de message d’exception](../../../2014/database-engine/dev-guide/exception-message-box-programming.md). Pour plus d'informations sur la façon d'obtenir et de déployer le fichier .dll de boîte de message d'exception, consultez [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a>Pour gérer une exception en utilisant la boîte de message d'exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  Facultatif Ajoutez une `using` directive (C#) ou `Imports` ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .net) pour utiliser l' <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez un bloc try-catch pour gérer l'exception anticipée.  
  
4.  Au sein du bloc `catch`, créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>. Passe l' <xref:System.Exception> objet géré par le `try` - `catch` bloc.  
  
5.  (Facultatif) Définissez une ou plusieurs des propriétés suivantes sur <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> :  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>énumération qui spécifie les boutons à afficher dans la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>énumération qui spécifie le bouton par défaut pour la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>énumération que vous utilisez pour contrôler d’autres comportements de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>énumération qui spécifie le symbole à afficher dans la boîte de message d’exception.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
7.  Facultatif Notez la valeur de l' <xref:System.Windows.Forms.DialogResult> énumération retournée si vous devez déterminer sur quel bouton l’utilisateur a cliqué.  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a>Pour afficher la boîte de message d'exception sans exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  Facultatif Ajoutez une `using` directive (C#) ou `Imports` (Visual Basic .net) pour utiliser l' <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>. Passez le texte du message comme une valeur <xref:System.String>.  
  
4.  (Facultatif) Définissez une ou plusieurs des propriétés suivantes sur <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> :  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>énumération qui spécifie les boutons à afficher dans la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - légende de boîte de dialogue de la boîte de message d'exception ;  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>énumération qui spécifie le bouton par défaut de la boîte de dialogue de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>énumération que vous utilisez pour contrôler d’autres comportements de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>énumération qui spécifie le symbole à afficher dans la boîte de message d’exception.  
  
5.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
6.  (Facultatif) Notez la valeur de l'énumération <xref:System.Windows.Forms.DialogResult> retournée si vous devez déterminer sur quel bouton l'utilisateur a cliqué.  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a>Pour afficher la boîte de message d'exception avec des boutons personnalisés  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  Facultatif Ajoutez une `using` directive (C#) ou `Imports` (Visual Basic .net) pour utiliser l' <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> en appliquant l'une des deux méthodes suivantes :  
  
    -   Passe l' <xref:System.Exception> objet géré par un `try` - `catch` bloc.  
  
    -   Passez le texte du message comme une valeur <xref:System.String>.  
  
4.  Définissez l'une des valeurs suivantes pour <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> :  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore>-affiche les boutons **abandonner**, **Réessayer**et **Ignorer** .  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - affiche les boutons personnalisés.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK>-affiche le bouton **OK** .  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel>-affiche les boutons **OK** et **Annuler** .  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel>-affiche les boutons **Réessayer** et **Annuler** .  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo>-affiche les boutons **Oui** et **non** .  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel>-affiche les boutons **Oui**, **non**et **Annuler** .  
  
5.  (Facultatif) Si vous utilisez des boutons personnalisés, appelez l'une des surcharges de la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> pour spécifier le texte de cinq boutons personnalisés au plus.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
7.  (Facultatif) Notez la valeur de l'énumération <xref:System.Windows.Forms.DialogResult> retournée si vous devez déterminer sur quel bouton l'utilisateur a cliqué. Si vous utilisez des boutons personnalisés, notez la valeur de <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> pour la propriété <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> pour déterminer sur lequel des boutons personnalisés l'utilisateur a cliqué.  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a>Pour permettre aux utilisateurs de décider d'afficher ou non la boîte de message d'exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  Facultatif Ajoutez une `using` directive (C#) ou `Imports` (Visual Basic .net) pour utiliser l' <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> en appliquant l'une des deux méthodes suivantes :  
  
    -   Passe l' <xref:System.Exception> objet géré par un `try` - `catch` bloc.  
  
    -   Passez le texte du message comme une valeur <xref:System.String>.  
  
4.  Affectez à la propriété <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> la valeur `true`.  
  
5.  (Facultatif) Spécifiez le texte qui demande à l'utilisateur de décider d'afficher encore ou non la boîte de message d'exception pour <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>. Le texte par défaut est "Ne plus afficher ce message".  
  
6.  Si vous devez conserver la décision de l'utilisateur uniquement pour la durée de l'exécution de l'application, définissez la valeur de <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> sur une variable <xref:System.Boolean> globale. Évaluez cette valeur avant de créer une instance de la boîte de message d'exception.  
  
7.  Si vous devez stocker définitivement la décision d'un utilisateur, procédez comme suit :  
  
    1.  Appelez la méthode CreateSubKey pour ouvrir une clé de Registre personnalisée que votre application utilise et définissez <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> sur l'objet RegistryKey retourné.  
  
    2.  Attribuez à <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> le nom de la valeur de Registre utilisée.  
  
    3.  Définissez <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> sur `true`.  
  
    4.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . La clé de Registre spécifiée est évaluée et la boîte de message d'exception est affichée uniquement si les données stockées dans la clé de Registre sont définies sur 0. Si la boîte de dialogue est affichée et que l'utilisateur active la case à cocher avant de cliquer sur un bouton, les données dans la clé de Registre sont définies sur 1.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d’exception avec le bouton **OK** uniquement pour afficher les informations d’une exception d’application qui comprend l’exception gérée ainsi que des informations supplémentaires spécifiques à l’application.  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d’exception avec les boutons **Oui** et **non** que l’utilisateur choisit.  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d'exception avec des boutons personnalisés.  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la case à cocher pour déterminer s'il faut afficher la boîte de message d'exception.  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la case à cocher et une clé du Registre pour déterminer s'il faut afficher la boîte de message d'exception.  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d'exception pour afficher des informations supplémentaires utiles lors d'un dépannage ou d'un débogage.  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
