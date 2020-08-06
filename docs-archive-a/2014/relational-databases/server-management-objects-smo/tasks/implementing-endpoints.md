---
title: Implémentation des points de terminaison | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 293a661c6e1ad6f6139e30e0824e99686af98f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707323"
---
# <a name="implementing-endpoints"></a>Implémentation de points de terminaison
  Un point de terminaison est un service qui peut écouter les requêtes en mode natif. SMO prend en charge différents types de points de terminaison en utilisant l'objet <xref:Microsoft.SqlServer.Management.Smo.Endpoint>. Vous pouvez créer un service de point de terminaison qui gère un type spécifique de charge utile, qui utilise un protocole spécifique, en créant une instance d'un objet <xref:Microsoft.SqlServer.Management.Smo.Endpoint> et en définissant ses propriétés.  
  
 La propriété <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Endpoint> peut être utilisée pour spécifier l'un des types de charge utile suivants :  
  
-   Mise en miroir de bases de données  
  
-   SOAP (la prise en charge des points de terminaison SOAP est présente dans [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] et les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )  
  
-   Service Broker  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 En outre, la propriété <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> peut être utilisée pour spécifier les deux protocoles pris en charge qui suivent :  
  
-   Protocole HTTP  
  
-   Protocole TCP  
  
 Après avoir précisé le type de charge utile, il est possible de définir la charge utile réelle à l'aide de la propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A>. La propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.Payload> fournit une référence vers un objet de charge utile du type spécifié, dont les propriétés peuvent être modifiées.  
  
 Pour l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload>, vous devez spécifier le rôle de mise en miroir et si le chiffrement est activé. L'objet <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> requiert des informations à propos du transfert de messages, du nombre maximal de connexions autorisé et du mode d'authentification. L'objet <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> requiert la définition de différentes propriétés, notamment la propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> qui spécifie les méthodes de charge utile SOAP disponibles pour les clients (procédures stockées et fonctions définies par l'utilisateur).  
  
 De la même façon, le protocole réel peut être défini à l'aide de la propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> qui référence un objet de protocole du type spécifié par propriété <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A>. L'objet <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> requiert une liste d'adresses IP restreintes, ainsi que des informations sur le port, le site Web et l'authentification. L'objet <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> requiert également une liste d'adresses IP restreintes, ainsi que des informations sur le port.  
  
 Lorsque le point de terminaison a été créé et complètement défini, l'accès peut être accordé, révoqué ou refusé aux utilisateurs, groupes, rôles et ouvertures de session de la base de données.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un projet Visual C&#35; Smo dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a>Création d'un service de point de terminaison de mise en miroir de bases de données en Visual Basic  
 L'exemple de code montre comment créer un point de terminaison pour la mise en miroir de bases de données dans SMO. Cette étape est requise avant la création du miroir de base de données. Utilisez la propriété <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> et d'autres propriétés sur l'objet <xref:Microsoft.SqlServer.Management.Smo.Database> pour créer un miroir de base de données.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a>Création d'un service de point de terminaison de mise en miroir de bases de données en Visual C#  
 L'exemple de code montre comment créer un point de terminaison pour la mise en miroir de bases de données dans SMO. Cette étape est requise avant la création du miroir de base de données. Utilisez la propriété <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> et d'autres propriétés sur l'objet <xref:Microsoft.SqlServer.Management.Smo.Database> pour créer un miroir de base de données.  
  
```csharp
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a>Création d'un service de point de terminaison de mise en miroir de bases de données dans PowerShell  
 L'exemple de code montre comment créer un point de terminaison pour la mise en miroir de bases de données dans SMO. Cette étape est requise avant la création du miroir de base de données. Utilisez la propriété <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> et d'autres propriétés sur l'objet <xref:Microsoft.SqlServer.Management.Smo.Database> pour créer un miroir de base de données.  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
