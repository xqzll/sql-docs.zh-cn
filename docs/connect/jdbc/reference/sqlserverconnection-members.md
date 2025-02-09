---
title: SQLServerConnection 成员 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4612b0762d8a0d619a19b61b8bb10ef6a68d1ba0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803082"
---
# <a name="sqlserverconnection-members"></a>SQLServerConnection 成员
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  下表列出由 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 类公开的成员。  
  
## <a name="constructors"></a>构造函数  
 无。  
  
## <a name="fields"></a>字段  
  
|“属性”|描述|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|用来指定快照事务隔离级别。|  
  
## <a name="inherited-fields"></a>继承的字段  
  
|类继承自：|描述|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE、TRANSACTION_READ_COMMITTED、TRANSACTION_READ_UNCOMMITTED、TRANSACTION_REPEATABLE_READ、 TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>方法  
  
|“属性”|描述|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|清除所报告的有关此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的所有警告。|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|立即释放此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的数据库和 JDBC 资源，而非等待它们自动释放。|  
|[closeUnreferencedPreparedStatementHandles](../../../connect/jdbc/reference/closeunreferencedpreparedstatementhandles-method-sqlserverconnection.md)|强制取消-准备的任何未完成丢弃准备的语句执行请求。| 
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|让自上次提交或回滚后的所有更改都成为永久性更改，并释放当前由此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象保留的任何数据库锁。|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|创建**java.sql.Blob**对象不包含任何数据。|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|创建**java.sql.Clob**对象不包含任何数据。|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|创建**java.sql.NClob**对象不包含任何数据。|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|创建用于将 SQL 语句发送到数据库的 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 对象。|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|创建**java.sql.SQLXML**对象不包含任何数据。|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|检索此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的当前自动提交模式。|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|检索此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的当前目录名称。|  
|[getClientConnectionID 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|无论最新连接尝试成功还是失败，都获取该尝试的连接 ID。|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|检索有关 JDBC 驱动程序支持的客户端信息属性信息。|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverconnection.md)|返回的值**disableStatementPooling**连接属性。 此设置控制是否启用语句池或不适用于此连接。|
|[getDiscardedServerPreparedStatementCount](../../../connect/jdbc/reference/getdiscardedserverpreparedstatementcount-method-sqlserverconnection.md)|返回当前未处理的已准备语句撤消操作。|
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|返回的值**enablePrepareOnFirstPreparedStatementCall**连接属性。|
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|检索使用此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象创建的 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的当前可保持性。|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|检索包含有关数据库元数据的 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 对象，对此数据库而言，此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象表示一项连接。|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|返回的值**serverPreparedStatementDiscardThreshold**连接属性。|  
|[getStatementHandleCacheEntryCount](../../../connect/jdbc/reference/getstatementhandlecacheentrycount-method-sqlserverconnection.md)|返回当前的共用预定义的语句句柄数。|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverconnection.md)|返回此连接的已准备的语句缓存的大小。|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|检索此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的当前事务隔离级别。|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|检索与此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象关联的 Map 对象。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|检索调用此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象时报告的第一个警告。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|指示此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象是否已关闭。|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|指示此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象是否处于只读模式。|  
|[isStatementPoolingEnabled](../../../connect/jdbc/reference/isstatementpoolingenabled-method-sqlserverconnection.md)|返回是否启用语句池或不适用于此连接。|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|指示此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象是否已关闭以及是否仍然有效。|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|将给定的 SQL 语句转换为数据库服务器的本机 SQL 语法。|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|创建用于调用数据库存储过程的 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) 对象。|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|创建用于将参数化的 SQL 语句发送到数据库的 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 对象。|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|从当前事务中删除指定的 [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) 对象。|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|撤消在当前事务中所做的所有更改并释放当前由此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象保留的任何数据库锁。|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|将此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的自动提交模式设置为给定状态。|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|设置指定的目录名称，以选择在其中使用此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的数据库的子空间。|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|设置客户端信息属性的值。|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverconnection.md)|设置为 true 或 false 的语句池。|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|指定新值的**enablePrepareOnFirstPreparedStatementCall**连接属性。|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|将使用此 [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) 对象创建的 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的可保持性更改为给定可保持性。|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|将此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象设置为只读模式，以此作为 JDBC 驱动程序启用数据库优化的提示。|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|在当前事务中创建未命名的保存点，并返回代表它的新 [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) 对象。|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|设置新值**serverPreparedStatementDiscardThreshold**连接属性。|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverconnection.md)|设置用于此连接的已准备的语句缓存的大小。|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|尝试将此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的事务隔离级别更改为给定级别。|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|安装给定的 TypeMap 对象，作为此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的类型映射。|  
  
## <a name="inherited-methods"></a>继承的方法  
  
|类继承自：|方法|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.lang.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
