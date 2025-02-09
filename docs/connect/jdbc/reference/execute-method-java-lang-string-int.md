---
title: execute 方法 (java.lang.String，int[]) |Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d4ae744a27156a59c926f2181ca9aec1146e8cd7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801657"
---
# <a name="execute-method-javalangstring-int"></a>execute 方法 (java.lang.String, int[])

  运行可返回多项结果的给定的 SQL 语句，并向 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 发出信号以指明给定数组中指定的自动生成的键应对检索可用。

## <a name="syntax"></a>语法

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Parameters
*sql*

包含 SQL 语句的 String  。

columnIndexes 

一组 int 数组，指示应该可用的自动生成的键的列索引  。

## <a name="return-value"></a>返回值
如果第一个结果为一个结果集，则为“true”  。 否则为 **false**。
  
## <a name="exceptions"></a>异常
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
此执行方法是由 java.sql.Statement 接口中的执行方法指定的。

## <a name="see-also"></a>另请参阅

[执行方法&#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement 成员](./sqlserverstatement-members.md)

[SQLServerStatement 类](./sqlserverstatement-class.md)
