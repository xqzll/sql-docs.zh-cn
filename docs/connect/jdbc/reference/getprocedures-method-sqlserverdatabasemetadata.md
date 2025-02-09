---
title: getProcedures 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 66c9a8b0-dc4c-4cbb-8004-c7157368cab4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6e374dd44d25a40953662cada81f6cc3d949f97c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771097"
---
# <a name="getprocedures-method-sqlserverdatabasemetadata"></a>getProcedures 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索在给定目录、架构或存储过程名称模式中可用的存储过程的说明。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.ResultSet getProcedures(java.lang.String sCatalog,  
                                        java.lang.String sSchema,  
                                        java.lang.String proc)  
```  
  
#### <a name="parameters"></a>Parameters  
 sCatalog   
  
 一个包含目录名称的字符串  。 对此参数提供 Null 值指示无需使用目录名称。  
  
 sSchema   
  
 一个包含架构名称模式的字符串  。 对此参数提供 Null 值指示无需使用架构名称。  
  
 *proc*  
  
 一个包含过程名称模式的字符串  。  
  
## <a name="return-value"></a>返回值  
 一个 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getProcedures 方法由 java.sql.DatabaseMetaData 接口中的 getProcedures 方法指定。  
  
 由 getProcedures 方法返回的结果集将包含以下信息：  
  
|“属性”|类型|描述|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|指定的存储过程所在数据库的名称。|  
|PROCEDURE_SCHEM|**String**|存储过程的架构。|  
|PROCEDURE_NAME|**String**|存储过程的名称。|  
|NUM_INPUT_PARAMS|**int**|保留以供将来使用，当前返回 -1 值。|  
|NUM_OUTPUT_PARAMS|**int**|保留以供将来使用，当前返回 -1 值。|  
|NUM_RESULT_SETS|**int**|保留以供将来使用，当前返回 -1 值。|  
|REMARKS|**String**|过程列的说明。<br /><br /> <br /><br /> **注意：** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不会为此列返回值。|  
|PROCEDURE_TYPE|**smallint**|存储过程的类型。 可以为下列值之一：<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
> [!NOTE]  
>  有关 getProcedures 方法返回的数据的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书中的“sp_stored_procedures (Transact-SQL)”。  
  
## <a name="example"></a>示例  
 以下示例演示了如何使用 getProcedures 方法返回有关 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 示例数据库中的 uspGetBillOfMaterials 存储过程的信息。  
  
```  
public static void executeGetProcedures(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedures(null, null, "uspGetBillOfMaterials");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
