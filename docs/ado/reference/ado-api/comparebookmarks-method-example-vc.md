---
title: CompareBookmarks 方法示例 （VC + +） |Microsoft Docs
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
- CompareBookmarks method [ADO], VC++ example
ms.assetid: 24ab3f3a-29c5-4ee1-942e-2634c02d0778
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c806149a6d56547b5336bcbb59455c0cc297088a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698771"
---
# <a name="comparebookmarks-method-example-vc"></a>CompareBookmarks 方法示例 (VC++)
此示例演示[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)方法。 除非某个特定的书签以某种方式是特殊很少需要书签的相关值。  
  
 将指定的随机行[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)派生自***作者***作为搜索的目标表。 然后显示每个行相对于该目标的位置。  
  
```  
// BeginCompareBookmarksCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
#include <time.h>  
#include <stdlib.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void CompareBookMarksX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   CompareBookMarksX();  
   ::CoUninitialize();  
}  
  
void CompareBookMarksX() {  
   HRESULT hr = S_OK;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   // Initialize pointers on define. These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
   _variant_t vTarget;  
   _bstr_t strAns;  
   _bstr_t strTitle;  
   strTitle = "CompareBookmarks Example";  
   try {      
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      pRstAuthors->Open("SELECT * FROM authors ORDER BY au_id", strCnn, adOpenStatic, adLockReadOnly, adCmdText);  
  
      long count = pRstAuthors->RecordCount;  
      printf("Rows in the Recordset = %d\n", count);  
      if (count == 0)   
         exit(1);   // Exit if an empty recordset  
  
      srand( (unsigned)time( NULL ) );   // Randomize  
  
      count = int(rand() % (count-1));   // Get position between 1 and count-1  
      if (!count)   
         count++;  
  
      printf("Randomly chosen row position = %d\n", count);  
      _variant_t vtBookMark = (short)adBookmarkFirst;  
      pRstAuthors->Move(count,vtBookMark);   // Move row to random position  
  
      vTarget = pRstAuthors->Bookmark;   // Remember the mystery row.  
      count = 0;  
      pRstAuthors->MoveFirst();  
  
      while (!(pRstAuthors->EndOfFile)) {   // Loop through recordset  
         long result = pRstAuthors->CompareBookmarks(pRstAuthors->Bookmark, vTarget);  
  
         if (result == adCompareNotEqual)  
            printf("Row %d: Bookmarks are not equal. %d\n", count, result);  
         else if  (result == adCompareNotComparable)   
            printf("Row %d: Bookmarks are not comparable.\n", count);  
         else {  
            switch(result) {  
            case adCompareLessThan:  
               strAns = "less than";  
               break;  
            case adCompareEqual:  
               strAns = "equal to";  
               break;  
            case adCompareGreaterThan:  
               strAns = "greater than";  
               break;  
            default:  
               strAns = "in error comparing to";  
               break;  
            }  
            printf ("Row position  %d  is  %s  the target.\n",  
               count,(LPCSTR)strAns);  
         }  
         count++;  
         pRstAuthors->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
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
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for (long i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, pErr->Description);  
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
 [CompareBookmarks 方法 (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
