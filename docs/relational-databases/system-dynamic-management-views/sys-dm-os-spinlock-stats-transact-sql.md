---
title: sys.dm_os_spinlock_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats
- sys.dm_os_spinlock_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_spinlock_stats dynamic management view
author: bluefooted
ms.author: pamela
ms.reviewer: maghan
manager: amitban
ms.openlocfilehash: e302eadaa559674482911904678cc8aa4cbd2577
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826601"
---
# <a name="sysdmosspinlockstats-transact-sql"></a>sys.dm_os_spinlock_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回有关所有按类型整理的旋转锁等待的信息。  
  

|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(256)**|旋转锁类型的名称。|  
|冲突|**bigint**|一个线程尝试获取调节锁并被阻止，因为另一个在当前线程的次数保存自旋锁。|  
|旋转|**bigint**|一个线程的次数尝试获得旋转锁时执行一个循环。|  
|spins_per_collision|**real**|每个冲突的数量的比率。|  
|sleep_time|**bigint**|以毫秒为单位，线程处于休眠状态发生退避算法时所用的时间量。|  
|几率|**int**|时间"旋转"一个线程获取调节锁将失败并产生了计划程序数。|  


## <a name="permissions"></a>权限  
上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高级层，需要`VIEW DATABASE STATE`数据库中的权限。 上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]标准版和基本层，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。    
  
## <a name="remarks"></a>备注  
 
 sys.dm_os_spinlock_stats 可以用于标识的旋转锁争用源。 在某些情况下，您可能能够解决或减少旋转锁争用。 但是，在某些情况下可能需要与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户支持服务部门联系。  
  
 您可以使用重置的 sys.dm_os_spinlock_stats 内容`DBCC SQLPERF`，如下所示：  
  
```  
DBCC SQLPERF ('sys.dm_os_spinlock_stats', CLEAR);  
GO  
```  
  
 这将使所有计数器重置为 0。  
  
> [!NOTE]  
>  如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新启动，则这些统计信息不会持久化。 自从上次统计信息重置以来，或自从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动以来，所有数据都是累积的。  
  
## <a name="spinlocks"></a>自旋锁  
 自旋锁是时间的轻量同步对象用于序列化对短时间通常拥有该数据结构的访问。 当一个线程尝试访问受另一个线程拥有该旋转锁的资源时，线程将执行一个循环，或"旋转"并再次尝试访问资源，而不立即使用闩锁或其他资源在生成计划程序请等待。 该线程将继续的旋转直到资源可用，或在循环完成，此时该线程将生成计划程序，并返回到可运行队列。 这种做法有助于减少过多的线程上下文切换，但如果旋转锁争用较高，可能会观察到大量的 CPU 使用率。
   
 下表包含一些最常见的旋转锁类型的简短说明。  
  
|旋转锁类型|描述|  
|-----------------|-----------------|  
|ABR|仅限内部使用。|
|ADB_CACHE|仅限内部使用。|
|ALLOC_CACHES_HASH|仅限内部使用。|
|APPENDONLY_STORAGE|仅限内部使用。|
|APRC_BACK_OFF_STATS|仅限内部使用。|
|APRC_EVENT_LIST|仅限内部使用。|
|APRC_QUEUE_LIST|仅限内部使用。|
|APRC_VALIDATION_QUEUE_LIST|仅限内部使用。|
|ASYNC_OP_ADMIN_CLIENT_REGISTRATION_LIST|仅限内部使用。|
|ASYNC_OP_ADMIN_WORK_REGISTRATION_HASH_TABLE|仅限内部使用。|
|ASYNCSTATSLIST|仅限内部使用。|
|BACKUP|仅限内部使用。|
|BACKUP_COPY_CONTEXT|仅限内部使用。|
|BACKUP_CTX|仅限内部使用。|
|BASE_XACT_HASH|仅限内部使用。|
|BLOCKER_ENUM|仅限内部使用。|
|BPREPARTITION|仅限内部使用。|
|BPWORKFILE|仅限内部使用。|
|BUF_HASH|仅限内部使用。|
|BUF_LINK|仅限内部使用。|
|BUF_WRITE_LOG|仅限内部使用。|
|CACHEOBJ_DBG|仅限内部使用。|
|CHANNELFORCECLOSEMANAGER|仅限内部使用。|
|CHECK_AGGREGATE_STATE|仅限内部使用。|
|CLR_HOSTTASK|仅限内部使用。|
|CLR_SPIN_LOCK|仅限内部使用。|
|CMED_DATABASE|仅限内部使用。|
|CMED_HASH_SET|仅限内部使用。|
|COLUMNDATASETSESSIONLIST|仅限内部使用。|
|COLUMNSTORE_HASHTABLE|仅限内部使用。|
|COLUMNSTOREBUILDSTATE_LIST|仅限内部使用。|
|COM_INIT|仅限内部使用。|
|可提交|仅限内部使用。|
|COMPPLAN_SKELETON|仅限内部使用。|
|CONNECTION_MANAGER|仅限内部使用。|
|连接|仅限内部使用。|
|CSIBUILDMEM|仅限内部使用。|
|CURSOR|仅限内部使用。|
|CURSQL|仅限内部使用。|
|DATAPORTCONSUMER|仅限内部使用。|
|DATAPORTSOURCEINFOCREDIT|仅限内部使用。|
|DATAPORTSOURCEINFOQUEUE|仅限内部使用。|
|DATASET_FREELIST|仅限内部使用。|
|DBCC_CHECK|仅限内部使用。|
|DBSEEDING_OPERATION|仅限内部使用。|
|DBT_HASH|仅限内部使用。|
|DBT_IO_LIST|仅限内部使用。|
|将数据库表|控制对包含该数据库的属性的 SQL Server 中的每个数据库的内存中数据结构的访问。 请参阅[这篇文章](https://techcommunity.microsoft.com/t5/SQL-Server/Improving-Concurrency-Scalability-of-SQL-Server-workload-by/ba-p/384789)有关详细信息。 |
|DEFERRED_WF_EXT_DROP|仅限内部使用。|
|DEK_INSTANCE|仅限内部使用。|
|DELAYED_PARTITIONED_STACK|仅限内部使用。|
|DELETEBITMAP|仅限内部使用。|
|DIAG_MANAGER|仅限内部使用。|
|DIAG_OBJECT|仅限内部使用。|
|DIGEST_CACHE|仅限内部使用。|
|DINPBUF|仅限内部使用。|
|DIRECTLOGCONSUMER|仅限内部使用。|
|DP_LIST|控制对具有启用了间接检查点的数据库的脏页列表的访问。 请参阅[这篇文章](https://techcommunity.microsoft.com/t5/SQL-Server/Indirect-Checkpoint-and-tempdb-8211-the-good-the-bad-and-the-non/ba-p/385510)有关详细信息。|
|DROP|仅限内部使用。|
|DROP_TEMPO|仅限内部使用。|
|DROPPED_ALLOC_UNIT|仅限内部使用。|
|DTC_HASHTABLE|仅限内部使用。|
|DTT_LIST|仅限内部使用。|
|ENDD_LIST|仅限内部使用。|
|EXT_CACHE|仅限内部使用。|
|EXTENT_ACTIVATION|仅限内部使用。|
|FABRIC_DB_MGR_PTR|仅限内部使用。|
|FABRIC_LOG_MANAGEMENT_INPUT_VALUE|仅限内部使用。|
|FABRIC_REPLICA_TRANSPORT|仅限内部使用。|
|FABRIC_TVF_DATA_CONSUMER_LIST|仅限内部使用。|
|FABRIC_TVF_LOAD_LIB|仅限内部使用。|
|FCB_REPLICA_SYNC|仅限内部使用。|
|FGCB_PRP_FILL|仅限内部使用。|
|FILE_HANDLE_CACHE|仅限内部使用。|
|FILE_TABLE|仅限内部使用。|
|FILESTREAM_CHUNKER|仅限内部使用。|
|FREE_SPACE_CACHE_ENTRY|仅限内部使用。|
|FS_CONTAINER_LIST_WITH_DELETE|仅限内部使用。|
|FS_DELETED_FOLDER_CLEANUP|仅限内部使用。|
|FSAGENT|仅限内部使用。|
|FSGHOST_STATUS|仅限内部使用。|
|FT_INIT|仅限内部使用。|
|GHOST_FREE|仅限内部使用。|
|GHOST_HASH|仅限内部使用。|
|GLOBAL_SCHEDULER_LIST|仅限内部使用。|
|GLOBAL_TRACE_FLAGS|仅限内部使用。|
|GLOBALTRANS|仅限内部使用。|
|GROUP_COMMIT_FEEDBACK_LOOP|仅限内部使用。|
|GUARDIAN|仅限内部使用。|
|HADR_AGH_X_ACCESS|仅限内部使用。|
|HADR_AR_CONTROLLER_COLLECTION|仅限内部使用。|
|HADR_AR_DB_MGR|仅限内部使用。|
|HADR_AR_TRANSPORT|仅限内部使用。|
|HADR_COMPRESSION_MGR_POOL|仅限内部使用。|
|HADR_FABRIC_FACTORY|仅限内部使用。|
|HADR_PRIORITY_QUEUE|仅限内部使用。|
|HADR_TRANSPORT_CONTROL|仅限内部使用。|
|HADR_TRANSPORT_LIST|仅限内部使用。|
|HADRSEEDINGLIST|仅限内部使用。|
|HOBT_DROPPED|仅限内部使用。|
|HOBT_HASH|仅限内部使用。|
|HTTP|仅限内部使用。|
|HTTP_CONNCACHE|仅限内部使用。|
|HTTP_ENDPOINT|仅限内部使用。|
|IDENTITY|仅限内部使用。|
|INDEX_CREATE|仅限内部使用。|
|IO_DISPENSER_PAUSE|仅限内部使用。|
|IO_RG_VOLUME_HASHTABLE|仅限内部使用。|
|IOREQ|仅限内部使用。|
|ISSRESOURCE|仅限内部使用。|
|KTM_ENLISTMENT|仅限内部使用。|
|LANG_RES_LOAD|仅限内部使用。|
|LIVE_TARGET_TVF|仅限内部使用。|
|LOCK_FREE_LIST|仅限内部使用。|
|LOCK_HASH|保护对将被持有的锁有关的信息存储在数据库中的锁管理器哈希表的访问。 请参阅[这篇文章](https://support.microsoft.com/kb/2926217)有关详细信息。|
|LOCK_NOTIFICATION|仅限内部使用。|
|LOCK_RESOURCE_ID|仅限内部使用。|
|LOCK_RW_ABTX_HASH_SET|仅限内部使用。|
|LOCK_RW_AGDB_HEALTH_DIAG|仅限内部使用。|
|LOCK_RW_CMED_HASH_SET|仅限内部使用。|
|LOCK_RW_DPT_TABLE|仅限内部使用。|
|LOCK_RW_IN_ROW_TRACKER|仅限内部使用。|
|LOCK_RW_LOGIN_RATE_STATS|仅限内部使用。|
|LOCK_RW_PVS_PAGE_TRACKER|仅限内部使用。|
|LOCK_RW_RBIO_REQ|仅限内部使用。|
|LOCK_RW_SECURITY_CACHE|仅限内部使用。|
|LOCK_RW_TEST|仅限内部使用。|
|LOCK_RW_WPR_BUCKET|仅限内部使用。|
|LOCK_SORT_STREAM|仅限内部使用。|
|LOCK_SQLSATELLITE_MESSAGE|仅限内部使用。|
|LOG_CONSOLIDATION|仅限内部使用。|
|LOG_RG_GOVERNOR|仅限内部使用。|
|LOGCACHE_ACCESS|仅限内部使用。|
|LOGFLUSHQ|仅限内部使用。|
|LOGIOSEQ|仅限内部使用。|
|LOGIOSEQMAPPENDINGMESSAGEQUEUE|仅限内部使用。|
|LOGLC|仅限内部使用。|
|LOGLFM|仅限内部使用。|
|LOGON_TRIGGER_CACHE|仅限内部使用。|
|LOGPOOL_HASHBUCKET|仅限内部使用。|
|LOGPOOL_REFCOUNTEDOBJECT|仅限内部使用。|
|LOGPOOL_SHAREDCACHEBUFFER|仅限内部使用。|
|LOGPOOL_SIZEPERRESOURCEPOOL|仅限内部使用。|
|LPE_BATCH|仅限内部使用。|
|LPE_SESSION|仅限内部使用。|
|LPE_SXTP|仅限内部使用。|
|LSID|仅限内部使用。|
|LSLIST|仅限内部使用。|
|LSNREFLIST|仅限内部使用。|
|LSS_SYNC_DTC|仅限内部使用。|
|MD_CHANGE_NOTIFICATION|仅限内部使用。|
|MDB_REMOTE_BATCH_STATS_HASH_TABLE|仅限内部使用。|
|MDB_REMOTE_SESSION_HASH_TABLE|仅限内部使用。|
|MEM_MGR|仅限内部使用。|
|MGR_CACHE|仅限内部使用。|
|MIGRATION_BUF_LIST|仅限内部使用。|
|NETCONN_ADDRESS|仅限内部使用。|
|ONDEMAND_TASK|仅限内部使用。|
|ONE_PROC_SIM_NODE_CONTEXT|仅限内部使用。|
|ONE_PROC_SIM_NODE_CONTEXT_LIST|仅限内部使用。|
|ONE_PROC_SIM_REPLICA_CONTEXT|仅限内部使用。|
|ONE_PROC_SIM_SERVICE_PARTITION|仅限内部使用。|
|OPT_IDX_MISS_ID|仅限内部使用。|
|OPT_IDX_MISS_KEY|仅限内部使用。|
|OPT_IDX_STATS|仅限内部使用。|
|OPT_INFO_MGR|仅限内部使用。|
|PAGE_WORKITEMLIST|仅限内部使用。|
|PAGECOPIER|仅限内部使用。|
|PARALLELREDOCACHE|仅限内部使用。|
|PARTITIONED_HEAP_FREE_LIST|仅限内部使用。|
|PROGRESS_REPORT|仅限内部使用。|
|QE_SHUTDOWN|仅限内部使用。|
|QSCAN_CACHE|仅限内部使用。|
|QUERY_EXEC_STATS|仅限内部使用。|
|QUERY_STORE_ASYNC_PERSIST|仅限内部使用。|
|QUERY_STORE_ASYNC_QUEUE_TLIST|仅限内部使用。|
|QUERY_STORE_CAPTURE_POLICY_INTERVAL|仅限内部使用。|
|QUERY_STORE_CAPTURE_POLICY_STATS|仅限内部使用。|
|QUERY_STORE_CAPTURE_POLICY_THRESHOLD|仅限内部使用。|
|QUERY_STORE_CURRENT_INTERVAL|仅限内部使用。|
|QUERY_STORE_HT_CACHE|仅限内部使用。|
|QUERY_STORE_LIST|仅限内部使用。|
|QUERY_STORE_PLAN_COMP_AGG|仅限内部使用。|
|QUERY_STORE_PLAN_LIST|仅限内部使用。|
|QUERY_STORE_READ_ONLY_FLAGS|仅限内部使用。|
|QUERY_STORE_SELF_AGG|仅限内部使用。|
|QUERY_STORE_STMT_COMP_AGG|仅限内部使用。|
|QUERYEXEC|仅限内部使用。|
|QUERYSCAN|仅限内部使用。|
|RANGE_GENERATION|仅限内部使用。|
|READ_AHEAD|仅限内部使用。|
|REDOMGRSTATE|仅限内部使用。|
|REMOTE_SESSION_CACHE|仅限内部使用。|
|REMOTEBLOCKIO|仅限内部使用。|
|REMOTEOP|仅限内部使用。|
|REPL_LOGREADER_HISTORY_CACHE|仅限内部使用。|
|REPL_LOGREADER_PERDB_HISTORY_CACHE|仅限内部使用。|
|RESMANAGER|仅限内部使用。|
|资源|仅限内部使用。|
|RESQUEUE|仅限内部使用。|
|RFS_THREAD_QUEUE|仅限内部使用。|
|RG_TIMER|仅限内部使用。|
|ROWGROUP_VERSIONS|仅限内部使用。|
|RPCCHANNELPOOL|仅限内部使用。|
|RPCPACKAGE|仅限内部使用。|
|RPCREQUESTORCONTEXT|仅限内部使用。|
|RWLOCK_LAST|仅限内部使用。|
|SATELLITE_CONNECTION|仅限内部使用。|
|SBS_CLIENT_ENDPOINTS|仅限内部使用。|
|SBS_CLIENT_REQUESTS|仅限内部使用。|
|SBS_DISPATCH|仅限内部使用。|
|SBS_PENDING|仅限内部使用。|
|SBS_SERVER_XACT_TASK_PROXY|仅限内部使用。|
|SBS_TRANSPORT|仅限内部使用。|
|SBS_UCS_DISPATCH|仅限内部使用。|
|安全|仅限内部使用。|
|SECURITY_CACHE|仅限内部使用。|
|SECURITY_FEDAUTH_AAD_BECWSCONNS|仅限内部使用。|
|SEMANTIC_TICACHE|仅限内部使用。|
|SEQUENCED_OBJECT|仅限内部使用。|
|SEQUEUE_SIZED_THREADSAFE|仅限内部使用。|
|SESSION_KILLER|仅限内部使用。|
|SESSION_MANAGER|仅限内部使用。|
|SESSION_SEC_CONTEXT|仅限内部使用。|
|SETRANGE_SYNC|仅限内部使用。|
|SHARABLE_SESSION_OBJECTS|仅限内部使用。|
|SLO_INFO_LIST|仅限内部使用。|
|SNI|仅限内部使用。|
|SNI_NODE_PENDING_IO_QUEUE|仅限内部使用。|
|SOAPSESSIONS|仅限内部使用。|
|SOS_ABORT_TASK|仅限内部使用。|
|SOS_ACTIVEDESCRIPTOR|仅限内部使用。|
|SOS_BLOCKALLOCPARTIALLIST|仅限内部使用。|
|SOS_BLOCKDESCRIPTORBUCKET|仅限内部使用。|
|SOS_CACHESTORE|同步对 SQL Server 中计划缓存或临时表缓存等的各种内存中缓存的访问。 此旋转锁类型上的大量争用可能意味着许多不同的事物，具体取决于特定缓存争用情况。 请联系[!INCLUDE[msCoName](../../includes/msconame-md.md)]客户支持服务，以帮助解决此旋转锁类型。 |
|SOS_CACHESTORE_CLOCK|仅限内部使用。|
|SOS_CLOCKALG_INTERNODE_SYNC|仅限内部使用。|
|SOS_DEBUG_HOOK|仅限内部使用。|
|SOS_DESCDATABUFFERLIST|仅限内部使用。|
|SOS_LARGEPAGE_ALLOCATOR|仅限内部使用。|
|SOS_MINITHREAD|仅限内部使用。|
|SOS_NODE|仅限内部使用。|
|SOS_OBJECT_POOL|仅限内部使用。|
|SOS_OBJECT_STORE|仅限内部使用。|
|SOS_OOM_CHECK|仅限内部使用。|
|SOS_PHYS_PAGE_CACHE|仅限内部使用。|
|SOS_RESOURCE_CLERK_LIST|仅限内部使用。|
|SOS_RINGBUFFER_RECORD|仅限内部使用。|
|SOS_RW|仅限内部使用。|
|SOS_SATELLITE_USER_POOL|仅限内部使用。|
|SOS_SCHEDULER|仅限内部使用。|
|SOS_SELIST_SIZED_SLOCK|仅限内部使用。|
|SOS_SUSPEND_QUEUE|仅限内部使用。|
|SOS_SYSTHREAD|仅限内部使用。|
|SOS_SYSTHREAD_DISPATCHER|仅限内部使用。|
|SOS_TASK|仅限内部使用。|
|SOS_TLIST|仅限内部使用。|
|SOS_VM_LOW|仅限内部使用。|
|SOS_WAIT_STATS|仅限内部使用。|
|SOS_WAITABLE_ADDRESS_HASHBUCKET|仅限内部使用。|
|SPIN_EVENT_MUTEX|仅限内部使用。|
|SPL_DISPATCHER_LIST|仅限内部使用。|
|SPL_DISPATCHER_QUEUE|仅限内部使用。|
|SPL_NONYIELD_ANALYSIS|仅限内部使用。|
|SPL_QUERY_STORE_CTX_INITIALIZED|仅限内部使用。|
|SPL_QUERY_STORE_EXEC_STATS_AGG|仅限内部使用。|
|SPL_QUERY_STORE_EXEC_STATS_READ|仅限内部使用。|
|SPL_QUERY_STORE_STATS_COOKIE_CACHE|仅限内部使用。|
|SPL_SOS_DISPATCHER|仅限内部使用。|
|SPL_TDS_PKT_QUEUE|仅限内部使用。|
|SPL_XE_BUFFER_MGR|仅限内部使用。|
|SPL_XE_DISPATCHER_QUEUE|仅限内部使用。|
|SPL_XE_NOTIFICATION_CALLBACK_LIST|仅限内部使用。|
|SPL_XE_SESSION_EVENT_MGR|仅限内部使用。|
|SPL_XE_SESSION_MGR|仅限内部使用。|
|SPL_XE_SESSION_TARGET_MGR|仅限内部使用。|
|SPT_PROFILE|仅限内部使用。|
|SQL_MGR|仅限内部使用。|
|SQL_NORM|仅限内部使用。|
|SQLTRACE_FILE_BUFFER|仅限内部使用。|
|SRVPROC|仅限内部使用。|
|STACK_HASHER|仅限内部使用。|
|SUBLATCH|仅限内部使用。|
|SUBPDESC|仅限内部使用。|
|SUBPDESC_LIST|仅限内部使用。|
|SVC_BROKER_CTRL|仅限内部使用。|
|SVC_BROKER_DEBUG_LIST|仅限内部使用。|
|SVC_BROKER_LIST|仅限内部使用。|
|SVC_BROKER_OBJECT|仅限内部使用。|
|SYNCPOINT_RESOURCE|仅限内部使用。|
|TaskElapsedExecutionMonitor|仅限内部使用。|
|TDS_TVP|仅限内部使用。|
|TESTTEAM|仅限内部使用。|
|TESTTEAMEXPONENTIAL|仅限内部使用。|
|TESTTEAMEXPONENTIALTASTAS|仅限内部使用。|
|TESTTEAMTASTAS|仅限内部使用。|
|TMP_SESS_KEY|仅限内部使用。|
|TSQL_DEBUG|仅限内部使用。|
|TXFRM_REPL|仅限内部使用。|
|VDI_OPERATION|仅限内部使用。|
|WINFAB_REPORT_FAULT|仅限内部使用。|
|WRITE_PAGE_RECORDER|仅限内部使用。|
|X_PACKET_LIST|仅限内部使用。|
|X_PIPE|仅限内部使用。|
|X_PIPE_DEMAND|仅限内部使用。|
|X_PORT|仅限内部使用。|
|XACT_LOCK_INFO|仅限内部使用。|
|XACT_LOCKINFO_TASK|仅限内部使用。|
|XACT_WORKSPACE|仅限内部使用。|
|XCB|仅限内部使用。|
|XCB_FREE_LIST|仅限内部使用。|
|XCB_HASH|仅限内部使用。|
|XCHNG_TRACE|仅限内部使用。|
|XDES|仅限内部使用。|
|XDES_HASH|仅限内部使用。|
|XDESMGR|仅限内部使用。|
|XDESTABLELIST|仅限内部使用。|
|XE_RATE_LIMITER_STRETCHDB|仅限内部使用。|
|XE_SESSION_STORAGE|仅限内部使用。|
|XID_ARRAY|仅限内部使用。|
|XIO_BLOCKLIST|仅限内部使用。|
|XIO_REQSTR|仅限内部使用。|
|XIO_SEQNUMBUMP|仅限内部使用。|
|XIOSTATS|仅限内部使用。|
|XTP_RT_DATA_LIST|仅限内部使用。|
|XTS_MGR|仅限内部使用。|
|XVB_CSN|仅限内部使用。|
|XVB_LIST|仅限内部使用。|
 

  
## <a name="see-also"></a>请参阅  
 
 [DBCC SQLPERF (Transact-SQL)](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [与 SQL Server 操作系统相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  

 [何时 SQL Server 中的较高的驱动程序的 CPU 使用率是旋转锁？](https://techcommunity.microsoft.com/t5/SQL-Server-Support/When-is-Spinlock-a-Significant-Driver-of-CPU-utilization-in-SQL/ba-p/530142)

 [诊断和解决 SQL Server 上的旋转锁争用](https://www.microsoft.com/download/details.aspx?id=26666)
  
  


