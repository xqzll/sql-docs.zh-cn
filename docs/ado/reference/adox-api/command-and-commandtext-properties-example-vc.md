---
title: Command 和 CommandText 属性示例 （VC + +） |Microsoft Docs
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
- CommandText property [ADOX], VC++ example
- Command property [ADOX], VC++ example
ms.assetid: 5a007b9a-be11-4fba-96db-6252993f97b8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1aac155aef874303f3281893db021b9492eef289
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703512"
---
# <a name="command-and-commandtext-properties-example-vc"></a>Command 和 CommandText 属性示例 (VC++)
下面的代码演示如何使用[命令](../../../ado/reference/adox-api/command-property-adox.md)属性更新过程的文本。  
  
```  
// BeginCommandTextCpp  
// This sample runs correctly only if procedure 'CustomerById' exists.  
  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void ProcedureTextX();  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL) ) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define ADOX object pointers, initialize pointers. These are in ADOX namespace.  
   _CatalogPtr m_pCatalog = NULL;  
  
   // Define ADODB object pointers.  
   ADODB::_ConnectionPtr m_pCnn = NULL;  
   ADODB::_CommandPtr m_pCommand = NULL;  
  
   try {  
      // Open the Connection  
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));  
      TESTHR(hr = m_pCommand.CreateInstance(__uuidof(ADODB::Command)));  
      m_pCnn->Open("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';", "", "", NULL);  
  
      // Open the catalog  
      m_pCatalog->PutActiveConnection(_variant_t((IDispatch *)m_pCnn));  
  
      // Get the Command  
      m_pCommand = m_pCatalog->Procedures->GetItem("CustomerById")->GetCommand();  
  
      // Update the CommandText  
      m_pCommand->PutCommandText("PARAMETERS [CustId] Text;select "  
         "CustomerId, CompanyName, ContactName "  
         "from Customers where CustomerId = [CustId]");  
      printf("CommandText is updated.\n");  
  
      // Update the Procedure  
      m_pCatalog->Procedures->GetItem("CustomerById")->PutCommand(_variant_t((IDispatch *)m_pCommand));  
      printf("Procedure 'CustomerById' is updated.\n");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in ProcedureTextX...."<< endl;  
   }  
  
   ::CoUninitialize();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Command 属性 (ADOX)](../../../ado/reference/adox-api/command-property-adox.md)
