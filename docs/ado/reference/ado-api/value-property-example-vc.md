---
title: 值属性示例 （VC + +） |Microsoft Docs
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
- Value property [ADO], VC++ example
ms.assetid: 2a104245-56df-44f3-b9b7-b3d18643d57b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2d879720ed3ee338adcf4bf5b9d6feb5d54e28de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710294"
---
# <a name="value-property-example-vc"></a>Value 属性示例 (VC++)
此示例演示[值](../../../ado/reference/ado-api/value-property-ado.md)具有属性[字段](../../../ado/reference/ado-api/field-object.md)并[属性](../../../ado/reference/ado-api/property-object-ado.md)按显示字段和属性值的对象的***员工***表。  
  
```  
// BeginValueCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void ValueX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   ValueX();  
   ::CoUninitialize();  
}  
  
void ValueX() {  
   HRESULT  hr = S_OK;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   // Define ADO object pointers. Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstEmployees = NULL;  
   FieldsPtr pFldLoop = NULL;  
   PropertiesPtr pPrpLoop = NULL;  
   _variant_t vtIndex;  
   vtIndex.vt = VT_I2;  
  
   try {  
      // Open recordset with data from Employee table.  
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));  
      pRstEmployees->Open ("employee", strCnn , adOpenForwardOnly, adLockReadOnly, adCmdTable);  
  
      printf("Field values in rstEmployees\n\n");  
  
      // Enumerate the Fields collection of the Employees table.  
      pFldLoop = pRstEmployees->GetFields();    
  
      for (int intFields = 0 ; intFields < (int)pFldLoop->GetCount() ; intFields++) {  
         vtIndex.iVal = intFields;  
  
         // Because Value is the default property of a Field object,the use of   
         // the actual keyword here is optional.  
         printf(" %s = %s\n\n" ,  
            (LPCSTR) pFldLoop->GetItem(vtIndex)->GetName(),  
            (LPCSTR) (_bstr_t) pFldLoop->GetItem(vtIndex)->Value);  
      }  
  
      printf("Property values in rstEmployees\n\n");  
  
      // Enumerate the Properties collection of the Recordset object.  
      pPrpLoop = pRstEmployees->GetProperties();  
      int intLine = 0;  
  
      for (int intProperties = 0 ; intProperties < (int)pPrpLoop->GetCount() ; intProperties++) {  
         vtIndex.iVal = intProperties;  
  
         // Because Value is the default property of a Property object,  
         // the use of the actual keyword here is optional.  
         _variant_t propValue = pPrpLoop->GetItem(vtIndex)->Value;  
         switch(propValue.vt) {  
  
         case (VT_BOOL):  
            if(propValue.boolVal)  
               printf(" %s = True\n\n", (LPCSTR) pPrpLoop->GetItem(vtIndex)->GetName());  
            else  
               printf(" %s = False\n\n", (LPCSTR) pPrpLoop->GetItem(vtIndex)->GetName());  
            break;  
  
         case (VT_I4):  
            printf(" %s = %d\n\n", (LPCSTR) pPrpLoop->GetItem(vtIndex)->GetName(),  
               pPrpLoop->GetItem(vtIndex)->Value.lVal);  
            break;  
  
         case (VT_EMPTY):  
            printf(" %s = \n\n", (LPCSTR) pPrpLoop->GetItem(vtIndex)->GetName());  
            break;  
  
         default:  
            break;  
         }  
      }  
   }  
   catch (_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstEmployees->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstEmployees)  
      if (pRstEmployees->State == adStateOpen)  
         pRstEmployees->Close();  
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
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.  
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [字段对象](../../../ado/reference/ado-api/field-object.md)   
 [属性对象 (ADO)](../../../ado/reference/ado-api/property-object-ado.md)   
 [Value 属性 (ADO)](../../../ado/reference/ado-api/value-property-ado.md)
