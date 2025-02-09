---
title: Resync Command 属性-动态 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5acaaa20667ac13f89b41391c1cc1d567eccf580
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711664"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command 属性 - 动态 (ADO)
指定用户提供的命令字符串[重新同步](../../../ado/reference/ado-api/resync-method.md)要刷新中命名的表中的数据的方法问题[唯一表](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)动态属性。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回**字符串**值，该值是一个命令字符串。  
  
## <a name="remarks"></a>备注  
 [记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象是在多个基表上执行联接操作的结果。 取决于受影响的行*AffectRecords*的参数[重新同步](../../../ado/reference/ado-api/resync-method.md)方法。 标准**重新同步**如果执行方法[唯一表](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)并**Resync Command**未设置的属性。  
  
 命令字符串**Resync Command**属性是参数化的命令或存储的过程，用于唯一地标识要刷新的行，并返回单个行，其中包含与行是同一数和列的顺序刷新一次。 命令字符串中包含的参数中每个主键列**唯一表**; 否则为将返回一个运行时错误。 参数会自动填充要刷新的行中的主键值。  
  
 下面是基于 SQL 的两个示例：  
  
 1\) **记录集**定义某一命令：  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 **Resync Command**属性设置为：  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 **唯一表**是*订单*及其主要密钥*OrderID*，参数化。 嵌套的 select 提供以编程方式确保通过原始命令返回的相同数量和顺序的列的简单方法。  
  
 2\) **记录集**由存储过程定义：  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 **重新同步**方法应执行以下存储的过程：  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 **Resync Command**属性设置为：  
  
```  
"{call CustordersResync (?)}"  
```  
  
 再一次**唯一表**是*订单*及其主要密钥*OrderID*，参数化。  
  
 **重新同步命令**动态属性追加到**记录集**对象[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合时[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)属性设置为**adUseClient**。  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
