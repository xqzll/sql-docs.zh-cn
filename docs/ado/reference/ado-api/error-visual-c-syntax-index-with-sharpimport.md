---
title: '错误 (VisualC++使用 #import 语法索引) |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'Error collection [ADO], Visual C++ syntax index with #import'
ms.assetid: 1ee59754-59c8-48e2-a4fb-242fa788c1f9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a1b4172efbccf5fb86ce1c8251c8a3d0bd4c400b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697996"
---
# <a name="error-visual-c-syntax-index-with-import"></a>错误 (VisualC++使用 #import 语法索引)
## <a name="properties"></a>属性  
  
```  
_bstr_t GetDescription( );  
__declspec(property(get=GetDescription)) _bstr_t Description;  
  
long GetHelpContext( );  
__declspec(property(get=GetHelpContext)) long HelpContext;  
  
_bstr_t GetHelpFile( );  
__declspec(property(get=GetHelpFile)) _bstr_t HelpFile;  
  
long GetNativeError( );  
__declspec(property(get=GetNativeError)) long NativeError;  
  
long GetNumber( );  
__declspec(property(get=GetNumber)) long Number;  
  
_bstr_t GetSource( );  
__declspec(property(get=GetSource)) _bstr_t Source;  
  
_bstr_t GetSQLState( );  
__declspec(property(get=GetSQLState)) _bstr_t SQLState;  
```  
  
## <a name="see-also"></a>请参阅  
 [错误对象](../../../ado/reference/ado-api/error-object.md)
