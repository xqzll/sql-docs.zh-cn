---
title: OpenSchema 方法示例 （VC + +） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OpenSchema method [ADO], VC++ example
ms.assetid: 6f3da460-0f49-41e0-999d-a754ec1d887e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 506862694a725e19ecfc893b0ed88d4ad7ca89b0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707232"
---
# <a name="openschema-method-example-vc"></a>OpenSchema 方法示例 (VC++)
此示例使用[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)方法的名称和类型的每个表中显示***Pubs***数据库。  
  
```  
// OpenSchemaMethodExample.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <oleauto.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void OpenSchemaX();  
void OpenSchemaX2();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   OpenSchemaX();  
   OpenSchemaX2();  
   ::CoUninitialize();  
}  
  
void OpenSchemaX() {  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection = NULL;  
   _RecordsetPtr pRstSchema = NULL;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open connection.  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      pConnection->Open (strCnn, "", "", adConnectUnspecified);  
  
      pRstSchema = pConnection->OpenSchema(adSchemaTables);  
  
      while ( !(pRstSchema->EndOfFile) ) {  
         _bstr_t table_name = pRstSchema->Fields->GetItem("TABLE_NAME")->Value;  
  
         printf("Table Name: %s\n",(LPCSTR) table_name);  
  
         _bstr_t table_type = pRstSchema->Fields->GetItem("TABLE_TYPE")->Value;  
  
         printf("Table type: %s\n\n",(LPCSTR) table_type);  
  
         pRstSchema->MoveNext();           
      }  
   }  
   catch (_com_error &e) {  
      // Display errors, if any. Pass connection pointer accessed from the Connection.          
      PrintProviderError(pConnection);  
      PrintComError(e);  
   }  
  
   // Clean up objects before exit.  
   if (pRstSchema)  
      if (pRstSchema->State == adStateOpen)  
         pRstSchema->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
void OpenSchemaX2() {  
   // Define ADO object pointers. Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection2 = NULL;  
   _RecordsetPtr pRstSchema = NULL;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open connection.  
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));  
      pConnection2->Open (strCnn, "", "", adConnectUnspecified);  
  
      // Create a safearray which takes four elements,and pass it as   
      // 2nd parameter in OpenSchema method.  
      SAFEARRAY FAR* psa = NULL;  
      SAFEARRAYBOUND rgsabound;  
      _variant_t  var;  
      _variant_t  Array;  
      rgsabound.lLbound = 0;  
      rgsabound.cElements = 4;  
      psa = SafeArrayCreate(VT_VARIANT, 1, &rgsabound);  
      var.vt = VT_EMPTY;  
  
      long ix;  
      ix = 0;  
      SafeArrayPutElement(psa, &ix, &var);  
  
      ix= 1;  
      SafeArrayPutElement(psa, &ix, &var);  
  
      ix = 2;  
      SafeArrayPutElement(psa, &ix, &var);  
  
      var.vt = VT_BSTR;  
      char * s1 = "VIEW";  
      _bstr_t str = s1;  
      var.bstrVal = str;  
  
      ix = 3;  
      SafeArrayPutElement(psa, &ix, &var);  
  
      Array.vt = VT_ARRAY|VT_VARIANT;  
      Array.parray = psa;    
  
      pRstSchema = pConnection2->OpenSchema(adSchemaTables,&Array);  
  
      while(!(pRstSchema->EndOfFile))  
      {  
         printf("Table Name: %s\n",   
            (LPCSTR) (_bstr_t) pRstSchema->Fields->GetItem("TABLE_NAME")->Value);  
  
         printf("Table type: %s\n\n",  
            (LPCSTR) (_bstr_t) pRstSchema->Fields->GetItem("TABLE_TYPE")->Value);  
  
         pRstSchema->MoveNext();           
      }  
   }    // End Try statement.  
   catch (_com_error &e) {  
      // Display errors, if any. Pass connection pointer accessed from the Connection.  
      PrintProviderError(pConnection2);  
      PrintComError(e);  
   }  
  
   // Clean up objects before exit.  
   if (pRstSchema)  
      if (pRstSchema->State == adStateOpen)  
         pRstSchema->Close();  
   if (pConnection2)  
      if (pConnection2->State == adStateOpen)  
         pConnection2->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print COM errors.   
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [OpenSchema 方法](../../../ado/reference/ado-api/openschema-method.md)
