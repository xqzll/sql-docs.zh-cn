---
title: SQLPostInstallerError 函数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac7fb545938a0ec5f212e9c0da867fbea5db4817
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536616"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError 函数
**符合性**  
 版本引入了：ODBC 3.0  
  
 **摘要**  
 **SQLPostInstallerError**提供了有关报告错误的驱动程序或转换器安装程序库的机制**ConfigDriver**， **ConfigDSN**，并**ConfigTranslator**到安装程序错误队列的函数。 应用程序不使用此 API;它们使用**SQLInstallerError**检索错误。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>参数  
 *fErrorCode*  
 [输入]安装程序错误代码。  
  
 *szErrorMsg*  
 [输入]错误消息文本。  
  
## <a name="returns"></a>返回  
 SQL_SUCCESS 或 SQL_ERROR。  
  
## <a name="diagnostics"></a>诊断  
 **SQLPostInstallerError**不会为其自身发送错误值。 如果错误已成功发布到安装程序错误队列 (检索，则可以使用**SQLInstallerError**)，将返回 SQL_SUCCESS。 将返回 SQL_ERROR，如果中的值*dwErrorCode*参数不是指定的安装程序错误代码之一。  
  
## <a name="related-functions"></a>相关函数  
  
|有关信息|请参阅|  
|---------------------------|---------|  
|添加、 修改或删除驱动程序|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|添加、 修改或删除数据源|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|翻译选项设置|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
