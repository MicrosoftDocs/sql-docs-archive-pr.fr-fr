---
title: Représentation de la connexion (tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60f3fdc10baf5dc3be9cd1b0ee6196d2a8da3d2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603681"
---
# <a name="connection-representation-tabular"></a>Représentation de la connexion (tabulaire)
  L'objet de connexion définit la source des données qui remplissent le modèle tabulaire.  
  
## <a name="connection-representation"></a>Représentation de la connexion  
 La spécification de l'objet de connexion suit les règles du fournisseurs OLE DB.  
  
### <a name="connection-in-amo"></a>Connexion dans AMO  
 Lorsque vous utilisez AMO pour gérer une base de données de modèle tabulaire, l'objet <xref:Microsoft.AnalysisServices.DataSource> dans AMO a une correspondance un-à-un avec l'objet logique de connexion dans un modèle tabulaire.  
  
 L'extrait de code suivant montre comment créer une source de données AMO, ou un objet de connexion dans un modèle tabulaire.  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a>Exemple d'AMO 2012 tabulaire  
 Pour savoir comment utiliser AMO pour créer et manipuler des représentations de connexion, consultez le code source de l'exemple AMO 2012 tabulaire ; plus précisément, archivez le fichier source suivant : Database.cs. L'exemple est disponible sur Codeplex. Le code est fourni uniquement comme un support aux concepts logiques expliqués ici et ne doit pas être utilisé dans un environnement de production, ni à des fins autres que pédagogiques.  
  
  
