---
title: Changer un mot de passe utilisateur pour l’authentification SQL Server (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1ed37ded-5671-46a4-b609-eea886dfae20
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c00012746e5995c7954152d1fd6d3e354c94ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702899"
---
# <a name="change-a-sql-server-authentication-user-password-ole-db"></a>Modifier un mot de passe utilisateur d'authentification SQL Server (OLE DB)
  Cet exemple explique comment utiliser OLE DB pour modifier le mot de passe d'un compte d'utilisateur sous Authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez conserver des informations d’identification, vous devez les chiffrer avec l' [API de chiffrement Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Exemple  
 Avant la génération, mettez à jour le code C++ pour spécifier l'ID d'utilisateur, l’ancien mot de passe et le nouveau mot de passe.  
  
 Cette application vous permet de vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut de votre ordinateur. Sur certains systèmes d'exploitation Windows, vous devrez remplacer (localhost) ou (local) par le nom de votre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour vous connecter à une instance nommée, changez la chaîne de connexion de L"(local)" en L"(local)\\\nom", où nom correspond à l’instance nommée. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express est installé dans une instance nommée. Assurez-vous que votre variable d'environnement INCLUDE inclut le répertoire qui contient sqlncli.h.  
  
 Compilez avec ole32.lib oleaut32.lib.  
  
 Pour générer cet exemple, vous aurez besoin d'un compte d'utilisateur d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour lequel vous connaissez le mot de passe. Pour autoriser des comptes de connexion sous l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, cliquez avec le bouton droit sur le nœud Serveur dans l’Explorateur d'objets, puis sélectionnez Propriétés. Sélectionnez Sécurité et activez le mode d’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows. Pour ajouter un compte d'utilisateur sous l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cliquez avec le bouton droit sur le nœud Sécurité dans l’Explorateur d'objets et sélectionnez Ajouter.  
  
 Le serveur sur lequel vous exécutez cet exemple doit avoir au moins une connexion activée pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le serveur doit également autoriser les connexions d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
// compile with: ole32.lib oleaut32.lib  
void InitializeAndEstablishConnection();  
  
#define STATUSDUMP(status)  case status : wprintf(L"status"); break;  
  
#define UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
  
#include <assert.h>  
#include <windows.h>  
#include <stdio.h>  
#include <stddef.h>  
#include <IOSTREAM>  
#include <cguid.h>  
#include <oledb.h>  
#include <oledberr.h>  
  
#include <SQLNCLI.h>  
  
LPMALLOC pMalloc = NULL;  
IDBInitialize * pIDBInitialize = NULL;  
HRESULT hr;  
  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError);  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError, BOOL &has_sql_errors);  
  
int main() {  
   // All the initialization activities in a separate function.  
   InitializeAndEstablishConnection();  
  
   if ( FAILED( pIDBInitialize->Uninitialize() ) )  
      // Uninitialize is not required, but fails if an interface was not released.  
      printf("Problem uninitializing.\n");  
  
   pIDBInitialize->Release();  
   CoUninitialize();  
};  
  
void InitializeAndEstablishConnection() {  
   IDBProperties * pIDBProperties = NULL;  
   const ULONG nInitProps = 4;  
   DBPROP InitProperties[nInitProps];  
   const ULONG nSSInitProps = 1;  
   DBPROP SSInitProperties[nSSInitProps];  
  
   const ULONG nPropSet = 2;  
   DBPROPSET rgInitPropSet[nPropSet];  
  
   // Initialize the COM library.  
   CoInitialize(NULL);  
   CoGetMalloc(1, &pMalloc);  
  
   CLSID clsid;  
   CLSIDFromProgID(L"SQLNCLI11", &clsid);  
  
   // Obtain access to the SQLOLEDB provider.  
   hr = CoCreateInstance( clsid, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void **) &pIDBInitialize);  
   if (FAILED(hr))  
      printf("Failed in CoCreateInstance().\n");  
  
   // Initialize the property values needed to establish the connection.  
   for (int i = 0; i < nInitProps; i++)  
      VariantInit(&InitProperties[i].vValue);  
  
   // Specify database name.  
   InitProperties[0].dwPropertyID = DBPROP_INIT_CATALOG;  
   InitProperties[0].vValue.vt = VT_BSTR;  
   // Change the following line to use any database on your server  
   InitProperties[0].vValue.bstrVal = SysAllocString(L"master");  
   InitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid = DB_NULLID;  
  
   InitProperties[1].dwPropertyID = DBPROP_AUTH_USERID;  
   InitProperties[1].vValue.vt = VT_BSTR;  
   // Modify the following line to add the user ID of a SQL Server Authentication account on your server  
   InitProperties[1].vValue.bstrVal = SysAllocString(L"");  
   InitProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid = DB_NULLID;  
  
   InitProperties[2].dwPropertyID = DBPROP_AUTH_PASSWORD;  
   InitProperties[2].vValue.vt = VT_BSTR;  
   // Modify the following line to add the new SQL Server Authentication password  
   InitProperties[2].vValue.bstrVal = SysAllocString(L"");  
   InitProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid = DB_NULLID;  
  
   InitProperties[3].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   InitProperties[3].vValue.vt = VT_BSTR;  
   InitProperties[3].vValue.bstrVal = SysAllocString(L"(local)");  
   InitProperties[3].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid = DB_NULLID;  
  
   SSInitProperties[0].dwPropertyID = SSPROP_AUTH_OLD_PASSWORD;  
   SSInitProperties[0].vValue.vt = VT_BSTR;  
   // Modify the following line to specify the existing SQL Server Authentication password  
   SSInitProperties[0].vValue.bstrVal = SysAllocString(L"");  
   SSInitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   SSInitProperties[0].colid = DB_NULLID;  
  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties = nInitProps;  
   rgInitPropSet[0].rgProperties = InitProperties;  
  
   rgInitPropSet[1].guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
   rgInitPropSet[1].cProperties = nSSInitProps;  
   rgInitPropSet[1].rgProperties = SSInitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface( IID_IDBProperties, (void **)&pIDBProperties);  
  
   if (FAILED(hr))  
      printf("Failed to obtain IDBProperties interface.\n");  
  
   hr = pIDBProperties->SetProperties( nPropSet, rgInitPropSet);  
  
   if (FAILED(hr))  
      printf("Failed to set initialization properties.\n");  
  
   pIDBProperties->Release();  
  
   // establish connection to the data source.  
   DWORD now = GetTickCount();  
  
   if ( FAILED(pIDBInitialize->Initialize()) ) {  
      printf("Problem in initializing.\n");  
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
   }  
  
   DWORD tookms = GetTickCount() - now;  
   printf("Connection took %d ms.\n", tookms);  
}  
  
// DumpErrorInfo queries SQLOLEDB error interfaces, retrieving available status  
// or error information. This version is called when SQL Server errors are not expected.  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError) {  
   BOOL has_sql_errors;  
   DumpErrorInfo (pObjectWithError, IID_InterfaceWithError, has_sql_errors);  
}  
  
// DumpErrorInfo queries SQLOLEDB error interfaces, retrieving available status   
// or error information. This version is called when an SQL Server error could occur.  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError, BOOL &has_sql_errors ) {  
   // Interfaces used in the example.  
   IErrorInfo * pIErrorInfoAll = NULL;  
   IErrorInfo * pIErrorInfoRecord = NULL;  
   IErrorRecords * pIErrorRecords = NULL;  
   ISupportErrorInfo * pISupportErrorInfo = NULL;  
   ISQLErrorInfo * pISQLErrorInfo = NULL;  
   ISQLServerErrorInfo * pISQLServerErrorInfo = NULL;  
  
   // Number of error records.  
   ULONG nRecs;  
   ULONG nRec;  
  
   // Basic error information from GetBasicErrorInfo.  
   ERRORINFO errorinfo;  
  
   // IErrorInfo values.  
   BSTR bstrDescription;  
   BSTR bstrSource;  
  
   // ISQLErrorInfo parameters.  
   BSTR bstrSQLSTATE;  
   LONG lNativeError;  
  
   // ISQLServerErrorInfo parameter pointers.  
   SSERRORINFO * pSSErrorInfo = NULL;  
   OLECHAR * pSSErrorStrings = NULL;  
  
   // Hard-code an English (United States) locale for the example.  
   DWORD MYLOCALEID = 0x0409;  
  
   has_sql_errors = 0;  
  
   // Only ask for error information if the interface supports it.  
   if (FAILED(pObjectWithError->QueryInterface(IID_ISupportErrorInfo, (void**) &pISupportErrorInfo)))     
      wprintf(L"SupportErrorErrorInfo interface not supported\n");  
   else if (FAILED(pISupportErrorInfo->InterfaceSupportsErrorInfo(IID_InterfaceWithError)))     
      wprintf(L"InterfaceWithError interface not supported\n");  
  
   // Do not test the return of GetErrorInfo. It can succeed and return  
   // a NULL pointer in pIErrorInfoAll. Simply test the pointer.  
   GetErrorInfo(0, &pIErrorInfoAll);  
  
   // Test to see if it's a valid OLE DB IErrorInfo interface exposing a list of records.  
   if (pIErrorInfoAll != NULL)  {  
      if (SUCCEEDED(pIErrorInfoAll->QueryInterface(IID_IErrorRecords, (void**) &pIErrorRecords))) {  
         pIErrorRecords->GetRecordCount(&nRecs);  
  
         // Within each record, retrieve information from each of the defined interfaces.  
         for (nRec = 0; nRec < nRecs; nRec++) {  
            ULONG errorno = nRecs - nRec - 1;  
            // From IErrorRecords, get the HRESULT and a reference to the ISQLErrorInfo interface.  
            pIErrorRecords->GetBasicErrorInfo(errorno, &errorinfo);  
            pIErrorRecords->GetCustomErrorObject(errorno,IID_ISQLErrorInfo, (IUnknown**) &pISQLErrorInfo);  
  
            // Display the HRESULT, then use the ISQLErrorInfo.  
            wprintf(L"HRESULT:\t%#X\n", errorinfo.hrError);  
  
            if (pISQLErrorInfo != NULL) {  
               pISQLErrorInfo->GetSQLInfo(&bstrSQLSTATE, &lNativeError);  
               // Display SQLSTATE and native error values.  
               wprintf(L"SQLSTATE:\t%s\nNative Error:\t%ld\n", bstrSQLSTATE, lNativeError);  
  
               // SysFree BSTR references.  
               SysFreeString(bstrSQLSTATE);  
  
               // Get the ISQLServerErrorInfo interface from  
               // ISQLErrorInfo before releasing the reference.  
               pISQLErrorInfo->QueryInterface(IID_ISQLServerErrorInfo, (void**) &pISQLServerErrorInfo);  
  
               pISQLErrorInfo->Release();  
            }  
  
            // Test to ensure the reference is valid, then get error information from ISQLServerErrorInfo.  
            if (pISQLServerErrorInfo != NULL) {  
               pISQLServerErrorInfo->GetErrorInfo(&pSSErrorInfo, &pSSErrorStrings);  
  
               // ISQLServerErrorInfo::GetErrorInfo succeeds even when it  
               // has nothing to return. Test the pointers before using.  
               if (pSSErrorInfo) {  
                  // Display the state and severity from the returned  
                  // information. The error message comes from  
                  // IErrorInfo::GetDescription.  
                  wprintf(L"Error state:\t%d\nSeverity:\t%d\n", pSSErrorInfo->bState, pSSErrorInfo->bClass);  
                  wprintf(L"Procedure:\t%s\nLine:\t%d\n", pSSErrorInfo->pwszProcedure, pSSErrorInfo->wLineNumber);  
  
                  has_sql_errors++;  
  
                  // IMalloc::Free needed to release references on returned values.  
                  pMalloc->Free(pSSErrorStrings);  
                  pMalloc->Free(pSSErrorInfo);  
               }  
  
               pISQLServerErrorInfo->Release();  
            }  
  
            if (SUCCEEDED(pIErrorRecords->GetErrorInfo(errno, MYLOCALEID, &pIErrorInfoRecord))) {  
               // Get the source and description (error message) from the record's IErrorInfo.  
               pIErrorInfoRecord->GetSource(&bstrSource);  
               pIErrorInfoRecord->GetDescription(&bstrDescription);  
  
               if (bstrSource != NULL) {  
                  wprintf(L"Source:\t\t%s\n", bstrSource);  
                  SysFreeString(bstrSource);  
               }  
  
               if (bstrDescription != NULL) {  
                  wprintf(L"Error message:\t%s\n", bstrDescription);  
                  SysFreeString(bstrDescription);  
               }  
  
               pIErrorInfoRecord->Release();  
            }  
         }  
  
         pIErrorRecords->Release();  
      }  
      else {  
         // IErrorInfo is valid; get the source and  
         // description to see what it is.  
         pIErrorInfoAll->GetSource(&bstrSource);  
         pIErrorInfoAll->GetDescription(&bstrDescription);  
  
         if (bstrSource != NULL) {  
            wprintf(L"Source:\t\t%s\n", bstrSource);  
            SysFreeString(bstrSource);  
         }  
  
         if (bstrDescription != NULL) {  
            wprintf(L"Error message:\t%s\n", bstrDescription);  
            SysFreeString(bstrDescription);  
         }  
      }  
  
      pIErrorInfoAll->Release();  
   }  
   else  
      wprintf(L"GetErrorInfo failed.\n");  
  
   if (pISupportErrorInfo != NULL)  
      pISupportErrorInfo->Release();  
}  
```  
  
  
