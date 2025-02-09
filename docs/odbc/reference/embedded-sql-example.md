---
title: 嵌入式 SQL 示例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eeab20c5385b02a874908cc941c1c69910efa228
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536664"
---
# <a name="embedded-sql-example"></a>嵌入式 SQL 示例
下面的代码是一个简单嵌入式的 SQL 的程序，用 c 语言编写该程序说明了很多，但不是全部的嵌入式 SQL 技术。 该程序提示用户输入订单号、 检索的客户数量、 销售人员和订单的状态，并在屏幕上显示检索到的信息。  
  
```cpp  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 请注意有关此程序的以下信息：  
  
-   **托管变量**括起来的一个部分中声明的主机变量**开始声明一节**并**结尾声明部分**关键字。 每个主机变量名称作为前缀的嵌入式 SQL 语句中出现时冒号 （:）。 冒号允许使用预编译器来区分主机变量和数据库对象，如表和列，具有相同的名称。  
  
-   **数据类型**DBMS 和主机语言支持的数据类型会大不相同。 这会影响主机变量，因为它们发挥双重作用。 一方面，主机变量是程序变量，声明和操作主机语言语句。 但是，它们用于嵌入的 SQL 语句中检索数据库数据。 如果没有主机语言类型的 DBMS 数据类型相对应，DBMS 将会自动转换数据。 但是，由于每个 DBMS 具有其自己的规则和转换过程与关联的特性，主机变量类型必须慎重选择。  
  
-   **错误处理**DBMS 向应用程序通过 SQL 通信区域中或 SQLCA 报告运行时错误。 在前面的代码示例中，第一个嵌入的 SQL 语句是包括 SQLCA。 这将告知预编译器，若要在程序中包括 SQLCA 结构。 这是必需的只要该程序将处理返回的 DBMS 错误。 WHENEVER...GOTO 语句告知预编译器生成错误时的特定标签的分支发生的错误处理代码。  
  
-   **单一实例选择**用来返回数据的语句是一个单独的 SELECT 语句; 也就是说，它返回单个行的数据。 因此，代码示例不声明或使用游标。
