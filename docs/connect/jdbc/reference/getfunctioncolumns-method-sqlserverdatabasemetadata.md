---
title: getFunctionColumns 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cd4958db78e2e35d29bcc47428295db50f7e5678
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66774632"
---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>getFunctionColumns 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索关于指定目录的系统函数或用户函数参数和返回类型的说明。  
  
## <a name="syntax"></a>语法  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Parameters  
 *catalog*  
  
 一个包含目录名称的字符串  。 如果该名称为空字符串 ""，则结果将包括无目录的函数。 如果此字符串为“null”，目录名称则不可用于搜索  。  
  
 schemaPattern   
  
 一个包含架构名称模式的字符串  。 如果该名称为空字符串 ""，则结果将包括无架构的函数。 如果此字符串为“null”，架构名称则不可用于搜索  。  
  
 functionNamePattern   
  
 一个包含函数名称的字符串  。  
  
 columnNamePattern   
  
 一个包含参数名称的字符串  。  
  
## <a name="return-value"></a>返回值  
 一个 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getFunctionColumns 方法是由 java.sql.DatabaseMetaData 接口中的 getFunctionColumns 方法指定的。  
  
 此方法只返回与指定目录内的指定架构、函数名称和参数名称相匹配的函数和参数。  
  
 结果集中的各行均包括针对参数说明、列说明或返回类型的以下列：  
  
|“属性”|类型|描述|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|函数所在的数据库的名称。|  
|FUNCTION_SCHEM|**String**|函数的架构。|  
|FUNCTION_NAME|**String**|函数的名称。|  
|COLUMN_NAME|**String**|参数或列的名称。|  
|COLUMN_TYPE|**short**|**列的类型。可以为下列值之一：**<br /><br /> functionColumnUnknown (0)：未知类型。<br /><br /> functionColumnIn (1)：输入参数。<br /><br /> functionColumnInOut (2)：输入/输出参数。<br /><br /> functionColumnOut (3)：输出参数。<br /><br /> functionReturn (4)：函数返回值。<br /><br /> functionColumnResult (5)：参数或列是结果集中的列。|  
|DATA_TYPE|**smallint**|来自 Java.sql.Types 的 SQL 数据类型值。|  
|TYPE_NAME|**String**|数据类型的名称。|  
|PRECISION|**int**|有效数字总个数。|  
|LENGTH|**int**|以字节为单位的数据的长度。|  
|SCALE|**short**|小数点右边的数字位数。|  
|RADIX|**short**|数值类型的基数。|  
|NULLABLE|**short**|指示参数或返回值是否可包括 null 值  。<br /><br /> **可以为下列值之一：**<br /><br /> functionNoNulls (0)：不允许为 NULL 值。<br /><br /> functionNullable (1)：允许为 NULL 值。<br /><br /> functionNullableUnknown (2)：未知。|  
|REMARKS|**String**|有关列或参数的注释。|  
|COLUMN_DEF|**String**|列的默认值。<br /><br /> **注意：** 此信息可在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用且特定于 JDBC 驱动程序。|  
|SQL_DATA_TYPE|**smallint**|此列与 DATA_TYPE 列相同，datetime 和 ISO interval 数据类型除外    。<br /><br /> **注意：** 此信息可在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用且特定于 JDBC 驱动程序。|  
|SQL_DATETIME_SUB|**smallint**|如果 SQL_DATA_TYPE 的值为 SQL_DATETIME 或 SQL_INTERVAL，则为 datetime ISO interval 子代码      。 对于数据类型以外**datetime**和 ISO**间隔**，此列为 NULL。<br /><br /> **注意：** 此信息可在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用且特定于 JDBC 驱动程序。|  
|CHAR_OCTET_LENGTH|**int**|基于二进制和字符的最大长度的参数或列。 对于其他数据类型，该值为 NULL。|  
|ORDINAL_POSITION|**int**|对于输入和输出参数，它表示从 1 开始的位置。<br /><br /> 对于结果集列，它指从 1 开始的结果集的列的位置。<br /><br /> 对于返回值，该值为 0。|  
|IS_NULLABLE|**String**|确定参数或列的可为 Null 性。<br /><br /> 可以为下列值之一：<br /><br /> **是**：参数或列可包括 NULL 值。<br /><br /> **否**：参数或列不可包括 NULL 值。<br /><br /> 空字符串 ("")：未知。|  
|SS_TYPE_CATALOG_NAME|**String**|包含用户定义类型 (UDT) 的目录名称。|  
|SS_TYPE_SCHEMA_NAME|**String**|包含用户定义类型 (UDT) 的架构名称。|  
|SS_UDT_CATALOG_NAME|**String**|采用完全限定名称的用户定义类型 (UDT)。|  
|SS_UDT_SCHEMA_NAME|**String**|在其中定义 XML 架构集合名称的目录的名称。 如果找不到目录名称，此变量则会包含一个空字符串。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|在其中定义 XML 架构集合名称的架构的名称。 如果找不到架构名称，则为空字符串。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|XML 架构集合的名称。 如果找不到名称，则为空字符串。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|包含用户定义类型 (UDT) 的目录名称。|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|包含用户定义类型 (UDT) 的架构名称。|  
|SS_DATA_TYPE|**tinyint**|扩展存储过程使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型。<br /><br /> **注意：** 有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 返回的数据类型的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书中的“数据类型 (Transact-SQL)”。|  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
