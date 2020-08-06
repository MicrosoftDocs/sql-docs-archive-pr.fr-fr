---
title: Utiliser le fournisseur PowerShell pour les événements étendus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], xevent
- extended events [SQL Server], PowerShell
- PowerShell [SQL Server], extended events
ms.assetid: 0b10016f-a479-4444-a484-46cb4677cf64
author: rothja
ms.author: jroth
ms.openlocfilehash: a9efbd389545dcde8285a38b06f41580fb65de6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611075"
---
# <a name="use-the-powershell-provider-for-extended-events"></a>Utiliser le fournisseur PowerShell pour les événements étendus
  Vous pouvez gérer les Événements étendus de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide du fournisseur PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le sous-dossier XEvent est disponible sous le lecteur SQLSERVER. Vous pouvez accéder à ce dossier selon l'une des méthodes suivantes :  
  
-   À l’invite de commandes, saisissez `sqlps`, puis appuyez sur ENTRÉE. Tapez `cd xevent`, puis appuyez sur ENTRÉE. À partir de là, vous pouvez **cd** utiliser les `dir` applets de commande CD et Commands (ou **set-location** et **obten-ChildItem** ) pour accéder au nom du serveur et au nom de l’instance.  
  
-   Dans l’Explorateur d’objets, développez le nom de l’instance, développez **Gestion**, cliquez avec le bouton droit sur **Événements étendus**, puis cliquez sur **Démarrer PowerShell**. Cela démarre PowerShell selon le chemin d'accès suivant :  
  
     PS SqlServer : \ XEvent \\ *nom_serveur* \\ *nom_instance*>  
  
    > [!NOTE]  
    >  Vous pouvez démarrer PowerShell à partir de n'importe quel nœud sous **Événements étendus**. Par exemple, vous pouvez cliquer avec le bouton droit sur **Sessions**, puis cliquer sur **Démarrer PowerShell**. Cela démarre PowerShell à un niveau plus profond, au niveau du dossier Sessions.  
  
 Vous pouvez parcourir l'arborescence des dossiers XEvent pour consulter les sessions Événements étendus existantes, ainsi que leurs événements, cibles et prédicats associés. Par exemple, à partir du chemin d’accès PS SqlServer : \ XEvent \\ *ServerName* \\ *nom_instance*>, si vous tapez `cd sessions` , appuyez sur entrée, tapez `dir` , puis appuyez sur entrée, vous pouvez voir la liste des sessions stockées sur cette instance. Vous pouvez également voir si la session est en cours (et si c'est le cas, pour combien de temps), et savoir si elle est configurée pour démarrer en même temps que l'instance.  
  
 Pour consulter les événements, leurs prédicats et les cibles associés à une session, vous pouvez attribuer le nom de la session aux répertoires, puis voir le dossier des événements ou des cibles. Par exemple, pour afficher les événements et leurs prédicats associés à la session d’intégrité système par défaut, à partir du chemin d’accès PS SqlServer : \ XEvent \\ *ServerName* \\ *nom_instance*\Sessions>, tapez `cd system_health\events,` Appuyez sur entrée, tapez `dir` , puis appuyez sur entrée.  
  
 Le fournisseur PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un outil puissant que vous pouvez utiliser pour créer, modifier et gérer des sessions Événements étendus. La section suivante fournit quelques exemples simples d'utilisation de scripts PowerShell avec des Événements étendus.  
  
## <a name="examples"></a>Exemples  
 Dans les exemples ci-après, notez les éléments suivants :  
  
-   Les scripts doivent être exécutés à partir de l’invite PS SQLSERVER : \\> (disponible en tapant `sqlps` à l’invite de commandes).  
  
-   Les scripts utilisent l'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Les scripts doivent être enregistrés avec une extension .ps1.  
  
-   La stratégie d'exécution de PowerShell doit autoriser l'exécution du script. Pour définir la stratégie d’exécution, utilisez l’applet de commande **Set-Executionpolicy** . (Pour en savoir plus, saisissez `get-help set-executionpolicy -detailed` et appuyez sur ENTRÉE.)  
  
 Le script suivant crée une nouvelle session nommée « TestSession ».  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 Le script suivant ajoute la cible de mémoire tampon en anneau à la session créée dans l'exemple précédent. (Cet exemple montre comment utiliser la méthode `Alter`. Sachez que vous pouvez ajouter la cible au moment même où vous créez la session).  
  
```powershell
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir | where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 Le script suivant crée une nouvelle session qui utilise une expression de prédicat. Dans ce cas, la session recueille les informations portant sur le moment où a été créé le fichier c:\temp.log (par le biais de l’événement sqlserver.file_written).  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -ArgumentList $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a>Sécurité  
 Pour créer, modifier ou supprimer une session Événements étendus, vous devez disposer de l'autorisation ALTER ANY EVENT SESSION.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)   
 [Utiliser la session system_health](use-the-ssms-xe-profiler.md)   
 [Outils associés aux événements étendus](extended-events-tools.md)  
