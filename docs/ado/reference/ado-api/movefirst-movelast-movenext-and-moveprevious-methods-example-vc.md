---
title: 移动记录指针的记录集的示例 （VC + +） |Microsoft Docs
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
- MoveLast method [ADO], VC++ example
- MoveNext method [ADO], VC++ example
- MovePrevious method [ADO], VC++ example
- MoveFirst method [ADO], VC++ example
ms.assetid: 7f8aea7b-9183-4b29-8ac0-a393ed2e8bd5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 60cb539a22a53573d184afe55f612e20e39811eb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707340"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-example-vc"></a>MoveFirst、 MoveLast、 MoveNext 和 MovePrevious 方法示例 （VC + +）
此示例使用[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)， [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)， [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)，以及[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)方法移动记录指针[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)基于提供的命令。 若要运行此示例需要 MoveAny 函数。  
  
## <a name="example"></a>示例  
  
```  
// MoveFirstMoveLastMoveNextSample.cpp  
// compile with: /EHsc  
#include <ole2.h>  
#include <stdio.h>  
  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void MoveFirstX();  
void MoveAny(int intChoice, _RecordsetPtr pRstTemp);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   MoveFirstX();  
   ::CoUninitialize();  
}  
  
void MoveFirstX() {  
   HRESULT hr = S_OK;  
   _RecordsetPtr pRstAuthors = NULL;  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
   _bstr_t strMessage("UPDATE Titles SET Type = "  
      "'psychology' WHERE Type = 'self_help'");  
   int intCommand = 0;  
  
   // Temporary string variable for type conversion for printing.  
   _bstr_t  bstrFName;  
   _bstr_t  bstrLName;  
  
   try {  
      // Open recordset from Authors table.  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
      pRstAuthors->CursorType = adOpenStatic;  
  
      // Use client cursor to enable AbsolutePosition property.  
      pRstAuthors->CursorLocation = adUseClient;  
      pRstAuthors->Open("Authors", strCnn, adOpenStatic, adLockBatchOptimistic, adCmdTable);  
  
      // Show current record information and get user's method choice.  
      while (true) {   // Continuous loop.  
         // Convert variant string to convertable string type.  
         bstrFName = pRstAuthors->Fields->Item["au_fName"]->Value;  
         bstrLName = pRstAuthors->Fields->Item["au_lName"]->Value;  
  
         printf("Name: %s %s\n Record %d of %d\n\n",  
            (LPCSTR) bstrFName,  
            (LPCSTR) bstrLName,  
            pRstAuthors->AbsolutePosition,  
            pRstAuthors->RecordCount);  
         printf("[1 - MoveFirst, 2 - MoveLast, \n");  
         printf(" 3 - MoveNext, 4 - MovePrevious, 5 - Quit]\n");  
  
         scanf_s("%d", &intCommand);  
  
         if ((intCommand < 1) || (intCommand > 4))  
            break;   // Out of range entry exits program loop.  
  
         // Call method based on user's input.  
         MoveAny(intCommand, pRstAuthors);  
      }  
   }  
   catch (_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
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
  
   // Clean up objects before exit.  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
void MoveAny(int intChoice, _RecordsetPtr pRstTemp) {  
   // Use specified method, trapping for BOF and EOF  
   try {  
      switch(intChoice) {  
         case 1:  
            pRstTemp->MoveFirst();  
            break;  
         case 2:  
            pRstTemp->MoveLast();  
            break;  
         case 3:  
            pRstTemp->MoveNext();  
            if (pRstTemp->EndOfFile) {  
               printf("\nAlready at end of recordset!\n");  
               pRstTemp->MoveLast();  
            }    // End If  
            break;  
         case 4:  
            pRstTemp->MovePrevious();  
            if (pRstTemp->BOF) {  
               printf("\nAlready at beginning of recordset!\n");  
               pRstTemp->MoveFirst();  
            }  
            break;  
         default:  
            ;  
      }  
   }  
  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstTemp->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt)  {  
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
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount - 1.  
      for ( long i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, pErr->Description);  
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
  
 输入  
  
```  
5  
```  
  
## <a name="see-also"></a>请参阅  
 [MoveFirst、 MoveLast、 MoveNext 和 MovePrevious 方法 (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
