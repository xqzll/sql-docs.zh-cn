---
title: VisualC++扩展插件示例 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions example
ms.assetid: 9739c278-582c-402b-a158-7f68a1b2c293
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 76be5e7c1dd88cb15c9f32db818aa63606f0ba7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701352"
---
# <a name="visual-c-extensions-example"></a>Visual C++ 扩展示例
此程序说明如何从字段中检索和转换为 C 值 /C++变量。  
  
 此示例还会利用的"智能指针，"它会自动处理调用的特定于 COM 的详细信息`QueryInterface`和引用计数**IADORecordBinding**接口。  
  
 没有智能指针的情况下将代码：  
  
```cpp
IADORecordBinding   *picRs = NULL;  
...  
TESTHR(pRs->QueryInterface(  
          __uuidof(IADORecordBinding), (LPVOID*)&picRs));  
...  
if (picRs) picRs->Release();  
```  
  
 使用智能指针派生`IADORecordBindingPtr`类型从`IADORecordBinding`接口使用此语句：  
  
```cpp
_COM_SMARTPTR_TYPEDEF(IADORecordBinding, __uuidof(IADORecordBinding));  
```  
  
 并实例化此类的指针：  
  
```cpp
IADORecordBindingPtr picRs(pRs);  
```  
  
 因为视觉对象C++扩展通过实现**记录集**对象，智能指针构造函数`picRs`，采用 _`RecordsetPtr`指针， `pRs`。 构造函数调用`QueryInterface`使用`pRs`若要查找`IADORecordBinding`接口。  
  
```cpp
// Visual_Cpp_Extensions_Example.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <icrsint.h>  
_COM_SMARTPTR_TYPEDEF(IADORecordBinding, __uuidof(IADORecordBinding));  
  
inline void TESTHR(HRESULT _hr) { if FAILED(_hr) _com_issue_error(_hr); }  
  
class CCustomRs : public CADORecordBinding {  
   BEGIN_ADO_BINDING(CCustomRs)  
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_ch_fname, sizeof(m_ch_fname), m_ul_fnameStatus, false)  
      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_ch_lname, sizeof(m_ch_lname), m_ul_lnameStatus, false)  
   END_ADO_BINDING()  
  
public:  
   CHAR m_ch_fname[22];  
   CHAR m_ch_lname[32];  
   ULONG m_ul_fnameStatus;  
   ULONG m_ul_lnameStatus;  
};  
  
int main() {  
   ::CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      CCustomRs rs;  
      IADORecordBindingPtr picRs(pRs);  
  
      pRs->Open(L"SELECT * FROM Employee ORDER BY lname", L"dsn=DataPubs;Trusted_Connection=yes;", adOpenStatic, adLockOptimistic, adCmdText);  
  
      TESTHR(picRs->BindToRecordset(&rs));  
  
      while (!pRs->EndOfFile) {  
         // Process data in the CCustomRs C++ instance variables.  
         printf("Name = %s %s\n",  
            (rs.m_ul_fnameStatus == adFldOK ? rs.m_ch_fname: "<Error>"),   
            (rs.m_ul_lnameStatus == adFldOK ? rs.m_ch_lname: "<Error>") );  
  
         // Move to the next row of the Recordset.   Fields in the new row will   
         // automatically be placed in the CCustomRs C++ instance variables.  
  
         pRs->MoveNext();  
      }  
   }  
   catch (_com_error &e ) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Meaning = %s\n", e.ErrorMessage());  
      printf("Source = %s\n", (LPCSTR) e.Source());  
      printf("Description = %s\n", (LPCSTR) e.Description());  
   }  
   ::CoUninitialize();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [使用视觉对象C++扩展](../../../ado/guide/appendixes/using-visual-c-extensions.md)   
 [Visual C++ 扩展标头](../../../ado/guide/appendixes/visual-c-extensions-header.md)
