---
title: 'Leçon 8 : créer un filtre de données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c11d4cf83619e53cd7e8f00091c66cc8e50ad76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601954"
---
# <a name="lesson-8-create-a-data-filter"></a>Leçon 8 : créer un filtre de données
  Après avoir ajouté une action d'extraction dans le rapport parent, l'étape suivante consiste à créer un filtre de données pour la table de données que vous avez définie pour le rapport enfant.  
  
 Vous pouvez créer un filtre de table **ou** un filtre de requête pour le rapport d’extraction. Cette leçon contient des instructions pour ces deux options.  
  
## <a name="table-based-filter"></a>Filtre de table  
 Vous devez effectuer les tâches suivantes pour implémenter un filtre de table.  
  
-   Ajoutez une expression de filtre dans le tableau matriciel du rapport enfant.  
  
-   Créez une fonction qui sélectionne les données non filtrées dans la table `PurchaseOrderDetail`.  
  
-   Ajoutez un gestionnaire d'événements qui lie l'objet DataTable `PurchaseOrderDetail` au rapport enfant.  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a>Pour ajouter une expression de filtre dans le tableau matriciel du rapport enfant  
  
1.  Ouvrez le rapport enfant.  
  
2.  Sélectionnez un en-tête de colonne dans le tableau matriciel, cliquez avec le bouton droit sur la cellule grise qui se trouve au-dessus de l’en-tête de colonne, puis cliquez sur Propriétés du tableau **matriciel**.  
  
3.  Cliquez sur la page **filtres** , puis sur **Ajouter**.  
  
4.  Dans l' **expression** classée, cliquez dans `ProductID` la liste déroulante. Il s'agit de la colonne à laquelle vous appliquez le filtre.  
  
5.  Cliquez sur l’opérateur EQUAL ( **=** ) dans la liste déroulante **opérateur** .  
  
6.  Cliquez sur le bouton expression en regard du champ **valeur** , cliquez sur **paramètres** dans la zone **catégorie** , puis double-cliquez `productid` dans la zone **valeurs** . Le champ **Définir l’expression pour : Valeur** doit maintenant contenir une expression semblable à **=Parameters!productid.Value**.  
  
7.  Cliquez sur **OK,** puis de nouveau sur **OK** dans la boîte de dialogue Propriétés du tableau **matriciel** .  
  
8.  Enregistrez le fichier .rdlc.  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a>Pour créer une fonction qui sélectionne les données non filtrées dans la table PurchaseOrdeDetail  
  
1.  Dans l'Explorateur de solutions, développez Default.aspx, puis double-cliquez sur Default.aspx.cs.  
  
2.  Créez une nouvelle fonction qui accepte un paramètre, `productid` , de type entier et retourne un `datatable` objet, puis effectue les opérations suivantes.  
  
    1.  Crée une instance du DataSet, `DataSet2` , qui a été créé à l’étape 2 de la [leçon 4 : définir une connexion de données et une table de données pour le rapport enfant](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Crée une connexion à la base de données SqlServer pour exécuter la requête définie dans la **Leçon 4 : Définir une connexion de données et une table de données pour le rapport enfant**.  
  
    3.  La requête retourne des données non filtrées.  
  
    4.  Remplissez l'instance de DataSet avec des données non filtrées en exécutant la requête.  
  
    5.  Retournez l'objet DataTable `PurchaseOrderDetail`.  
  
         La fonction doit ressembler à celle ci-dessous. (Pour référence uniquement. Vous pouvez suivre le modèle de votre choix pour extraire les données nécessaires pour le rapport enfant.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a>Pour ajouter un gestionnaire d'événements qui lie l'objet DataTable PurchaseOrderDetail au rapport enfant  
  
1.  Ouvrez Default.aspx.  
  
2.  Cliquez avec le bouton droit sur le contrôle ReportViewer, puis cliquez sur **Propriétés.**  
  
3.  Sur la page **Propriétés** , cliquez sur l’icône **événements** .  
  
4.  Double-cliquez sur l’événement d' **extraction** .  
  
     Cette opération permet d'ajouter une section du gestionnaire d'événements dans le code, qui doit ressembler au bloc ci-dessous.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Terminez l'exécution du gestionnaire d'événements. Il doit inclure les fonctionnalités suivantes.  
  
    1.  Extraire la référence d’objet de rapport enfant du paramètre *DrillthroughEventArgs* .  
  
    2.  Appelez la fonction.`GetPurchaseOrderDetail`  
  
    3.  Liez l'objet DataTable `PurchaseOrderDetail` à la source de données correspondante du rapport.  
  
         Le code exécuté du gestionnaire d'événements doit ressembler à ce qui suit.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Enregistrez le fichier .  
  
## <a name="query-filter"></a>Filtre de requête  
 Vous devez effectuer les tâches suivantes pour implémenter un filtre de requête.  
  
-   Créez une fonction qui sélectionne les données filtrées dans la table `PurchaseOrderDetail`.  
  
-   Ajoutez un gestionnaire d'événements qui extrait les valeurs de paramètre et lie l'objet DataTable `PurchaseOrdeDetail` au rapport enfant.  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a>Pour créer une fonction qui sélectionne les données filtrées dans la table PurchaseOrderDetail  
  
1.  Dans l'Explorateur de solutions, développez Default.aspx, puis double-cliquez sur Default.aspx.cs.  
  
2.  Créez une fonction qui accepte un paramètre, `productid`, de type entier et retourne un objet `datatable`, puis procédez comme suit.  
  
    1.  Crée une instance du DataSet, `DataSet2` , qui a été créé à l’étape 2 de la [leçon 4 : définir une connexion de données et une table de données pour le rapport enfant](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Créez une connexion à la base de données SqlServer pour exécuter la requête définie dans la **Leçon 4 : Définir une connexion de données et une table de données pour le rapport enfant**.  
  
    3.  La requête inclut un paramètre, `productid`, pour vérifier que les données retournées sont filtrées en fonction de l'élément `ProductID` sélectionné dans le rapport parent.  
  
    4.  Remplissez l'instance de DataSet avec les données filtrées en exécutant la requête.  
  
    5.  Retournez l'objet DataTable `PurchaseOrderDetail`.  
  
         La fonction doit ressembler à celle ci-dessous. (Pour référence uniquement. Vous pouvez suivre le modèle de votre choix pour extraire les données nécessaires pour le rapport enfant.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a>Pour ajouter un gestionnaire d'événements qui extrait les valeurs de paramètre et lie l'objet DataTable PurchaseOrderDetail au rapport enfant  
  
1.  Ouvrez Default.aspx.  
  
2.  Cliquez avec le bouton droit sur le contrôle ReportViewer, puis cliquez sur **Propriétés**.  
  
3.  Dans le volet **Propriétés** , cliquez sur l’icône **événements** .  
  
4.  Double-cliquez sur l’événement d' **extraction** .  
  
     Cette opération permet d'ajouter une section du gestionnaire d'événements dans le code, qui doit ressembler à ce qui suit.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Terminez l'exécution du gestionnaire d'événements. Il doit inclure la fonctionnalité suivante.  
  
    1.  Extraire la référence d’objet de rapport enfant du paramètre *DrillthroughEventArgs* .  
  
    2.  Obtenez la liste des paramètres de rapport enfant de l'objet de rapport enfant extrait.  
  
    3.  Parcourez la collection du paramètre et récupérez la valeur du paramètre, `ProductID`, passée depuis le rapport parent.  
  
    4.  Appelez la fonction, `GetPurchaseOrderDetail`, puis passez la valeur pour le paramètre `ProductID`.  
  
    5.  Liez le `PurchaseOrderDetail` DataTable à la source de données correspondante du rapport.  
  
         Le code exécuté du gestionnaire d'événements doit ressembler à ce qui suit.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Enregistrez le fichier .  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de créer un filtre de données pour la table de données que vous avez définie pour le rapport enfant. Vous allez à présent générer et exécuter l'application de site Web.  
  
  
