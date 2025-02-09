---
title: getCrossReference 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCrossReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2fc70ed3e449840793dbd32e4d2014031256f3bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66763008"
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>getCrossReference 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索给定外键表中的外键列的说明，该外键表引用给定主键表的主键列。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>Parameters  
 cat1   
  
 一个包含具有主键的表的目录名称的字符串  。  
  
 schem1   
  
 一个包含具有主键的表的构架名称的字符串  。  
  
 *tab1*  
  
 一个包含具有主键的表的表名称的字符串  。  
  
 cat2   
  
 一个包含具有外键的表的目录名称的字符串  。  
  
 schem2   
  
 一个包含具有外键的表的架构名称的字符串  。  
  
 tab2   
  
 一个包含具有外键的表的表名称的字符串  。  
  
## <a name="return-value"></a>返回值  
 一个 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getCrossReference 方法由 java.sql.DatabaseMetaData 接口中的 getCrossReference 方法指定。  
  
 由 getCrossReference 方法返回的结果集将包含以下信息：  
  
|“属性”|类型|描述|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|包含主键表的目录名称。|  
|PKTABLE_SCHEM|**String**|主键表的架构名称。|  
|PKTABLE_NAME|**String**|主键表的名称。|  
|PKCOLUMN_NAME|**String**|主键的列名称。|  
|FKTABLE_CAT|**String**|包含外键表的目录名称。|  
|FKTABLE_SCHEM|**String**|外键表的架构名称。|  
|FKTABLE_NAME|**String**|外键表的名称。|  
|FKCOLUMN_NAME|**String**|外键的列名称。|  
|KEY_SEQ|**short**|多列主键中列的序列号。|  
|UPDATE_RULE|**short**|SQL 操作为更新时对外键应用的操作。 可以为下列值之一：<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|SQL 操作为删除时对外键应用的操作。 可以为下列值之一：<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|外键的名称。|  
|PK_NAME|**String**|主键的名称。|  
|DEFERRABILITY|**short**|指示对外键约束的计算是否可以延迟到提交时。 可以为下列值之一：<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  有关 getCrossReference 方法返回的数据的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书中的“sp_fkeys (Transact-SQL)”。  
  
## <a name="example"></a>示例  
 以下示例演示了如何使用 getCrossReference 方法返回有关 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 示例数据库中 Person.Contact 和 HumanResources.Employee 表之间的主键和外键关系的信息。  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
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
  
  
