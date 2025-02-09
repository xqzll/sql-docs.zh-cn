---
title: 跟踪标志 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- trace flags [SQL Server], about trace flags
- trace flags [SQL Server]
- global trace flags [SQL Server]
- flags [SQL Server]
- session trace flags [SQL Server]
- performance [SQL Server], trace
- debugging [SQL Server], trace flags
ms.assetid: b971b540-1ac2-435b-b191-24399eb88265
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4e366d686bc71d9b4ee391013fedb25e93494c45
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413157"
---
# <a name="dbcc-traceon---trace-flags-transact-sql"></a>DBCC TRACEON - 跟踪标志 (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

跟踪标志用于设置特定服务器特征或更改特定行为。 例如，跟踪标志 3226 是一种常用的启动跟踪标志，可取消显示错误日志中的成功备份消息。 跟踪标志经常用于诊断性能问题或调试存储过程或复杂的计算机系统，但 Microsoft 支持部门还可能建议将它们用于解决会对特定工作负载产生负面影响的行为。  当按照指示使用时，所有记录的跟踪标志和 Microsoft 支持部门推荐的跟踪标志在生产环境中都完全受支持。  请注意，此列表中的跟踪标志在其特定用途方面可能会有一些其他注意事项，因此建议仔细查看此处和/或支持工程师提供的所有建议。 此外，与 SQL Server 中的任何配置更改一样，最好在部署标志之前在非生产环境中全面测试该标志。

## <a name="remarks"></a>Remarks  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，有三种跟踪标志：查询、会话和全局。 查询跟踪标志在特定查询的上下文中处于活动状态。 会话跟踪标志对某个连接有效，且只对该连接可见。 全局跟踪标志在服务器级别上进行设置，对服务器上的每一个连接都可见。 某些标志只能作为全局标志启用，而某些标志在全局或会话作用域都可以启用。  
  
 下列规则适用：  
-   全局跟踪标志必须全局启用。 否则，跟踪标志无效。 建议在启动时通过使用 **-T** 命令行选项来启用全局跟踪标志。 这样可确保跟踪标志在服务器重新启动后保持活动状态。 若要让跟踪标志生效，请重启 SQL Server。 
-   如果跟踪标志有全局、会话或查询作用域，则可以用合适的作用域来启用它。 在会话级别启用的跟踪标志永远不会影响另一个会话，并且当打开会话的 SPID 注销时，该跟踪标志将失效。  
  
使用以下方法之一可将跟踪标志设置为开或关：
-   使用 DBCC TRACEON 和 DBCC TRACEOFF 命令。  
     例如，若要全局启用 2528 跟踪标志，请在使用 [DBCC TRACEON](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) 时使用 -1 参数：`DBCC TRACEON (2528, -1)`。 重新启动服务器时，使用 DBCC TRACEON 启用全局跟踪标志的方法将失效。 若要关闭全局跟踪标志，请在使用 [DBCC TRACEOFF](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md) 时使用 -1 参数。  
-   使用 **-T** 启动选项可以指定跟踪标志在启动期间设置为开。  
     **-T** 启动选项会全局启用跟踪标志。 使用启动选项无法启动会话级别的跟踪标志。 这样可确保跟踪标志在服务器重新启动后保持活动状态。 有关启动选项的详细信息，请参阅 [数据库引擎服务启动选项](../../database-engine/configure-windows/database-engine-service-startup-options.md)。
-   在查询级别，通过使用 QUERYTRACEON [查询提示](https://support.microsoft.com/kb/2801413)。 QUERYTRACEON 选项只能用于上表中所述的查询优化器跟踪标志。
  
使用 `DBCC TRACESTATUS` 命令确定哪些跟踪标志当前是活动的。

## <a name="trace-flags"></a>跟踪标志

  
下表列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中可用的跟踪标志，并进行了说明。
 
> [!NOTE]
> 特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中引入了一些跟踪标志。 有关适用版本的详细信息，请参阅与特定跟踪标志关联的 Microsoft 支持文章。

> [!IMPORTANT]
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未来版本可能不支持跟踪标志行为。 
  
|跟踪标志|描述|  
|---|---|
|**139**| 当在兼容性级别较低的数据库上，针对特定数据类型分析兼容性级别 130 中引入的改进型精度和转换逻辑时，在 [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)、[DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md) 和 [DBCC CHECKCONSTRAINTS](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md) 等 DBCC 检查命令的作用域中强制执行正确的转换语义。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/4010261)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] RTM CU3、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 及更高内部版本。<br /><br />警告  ：不应在生产环境中连续启用跟踪标志 139，该标志只能用于执行此 [Microsoft 支持文章](https://support.microsoft.com/help/4010261)中所述的数据库验证检查。 应在完成验证检查后立即禁用它。<br /><br />**作用域**：仅全局|
|**174**|在 64 位系统上将 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]计划缓存桶计数从 40,009 增加到 160,001。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3026083)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：仅全局|
|**176**|在为包含已计算分区依据列的表联机重新生成分区时，启用修复以解决错误。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3213683)。<br /><br />**作用域**：全局或会话|
|**205**|当由于自动更新统计信息而重新编译依赖于统计信息的存储过程时，向错误日志提交报告。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/195565)。<br /><br />**作用域**：仅全局|
|**260**|打印有关扩展存储过程动态链接库 (DLL) 的版本控制信息。 有关 **GetXpVersion()** 的详细信息，请参阅[创建扩展存储过程](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)。<br /><br />**作用域：** 全局或会话|
|**272**|在服务器意外重新启动或故障转移到辅助服务器的情况下，禁用标识预分配以避免标识列的值出现差异。 请注意，标识缓存用于提高具有标识列的表的 INSERT 性能。<br /><br />注意：  从 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 开始，若要在数据库级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 IDENTITY_CACHE 选项。<br /><br />**作用域**：仅全局|
|**460**|将数据截断消息 ID [8152](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-8000-to-8999) 替换为消息 ID [2628](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-2000-to-2999)。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/4468101)。<br /><br />自 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4 起，若要在数据库级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 VERBOSE_TRUNCATION_WARNINGS 选项。<br /><br />**注意：** 此跟踪标志适用于 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU12 及更高内部版本。<br /><br />**注意：** 从数据库兼容性级别 150 开始，消息 ID 2628 为默认设置，此跟踪标志无效。<br /><br />**作用域**：全局或会话|
|**610**|控制对索引表进行的以最低限度记录的插入。 从 SQL Server 2016 开始，不需要此跟踪标志，因为对索引表默认启用了最低限度记录。 在 SQL Server 2016 中，当大容量加载操作导致分配一个新页面时，如果符合最低限度记录的其他所有先决条件，则会以最低限度记录按顺序填充该新页面的所有行。 为了维护索引顺序而插入到现有页面中的行（不分配新页面）仍以完整方式记录，这与在加载过程中由于页面拆分而移动的行一样。 为索引启用 ALLOW_PAGE_LOCKS（默认启用）以便让最低限度记录操作正常工作也很重要，因为在分配期间会获取页锁，从而仅记录页面或盘区分配。有关详细信息，请参阅[数据加载性能指南](https://msdn.microsoft.com/library/dd425070.aspx)。<br /><br />**作用域**：全局或会话|
|**634**|禁用背景列存储压缩任务。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定期运行元组发动机后台任务，对含有未压缩数据的列存储索引行组进行压缩，每次压缩一个这种行组。<br /><br />列存储压缩可提高查询性能，但也会占用系统资源。 通过用跟踪标志 634 禁用后台压缩任务，然后随时显式调用 ALTER INDEX...REORGANIZE 或 ALTER INDEX...REBUILD，可以手动控制列存储压缩计时。<br /><br />**作用域：** 仅全局|
|**652**|禁用页面预提取扫描。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：全局或会话|
|**661**|禁用虚影记录删除进程。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：仅全局|
|**692**|将数据大容量加载到堆或聚集索引时禁用快速插入。 从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，默认情况下会启用快速插入，以便在数据库处于简单或大容量日志恢复模式时，利用最低限度记录来优化插入新页面的记录的插入性能。 启用快速插入后，每个大容量加载批次都会绕过现有盘区的分配查找获得新盘区，从而提供可用空间来优化插入性能。<br /><br /> 启用快速插入后，批次较小的大容量加载会导致对象占用的未用空间增加，因此建议每次都使用较大的批次，以便完全填充盘区。 如果增加批次大小不可行，此跟踪标记可以帮助减少以性能为代价保留的未用空间。 <br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] RTM 及更高内部版本。<br /><br />**作用域**：全局或会话|
|**715**|为没有非聚集索引的堆中的大容量加载操作启用表锁。 启用此跟踪标志时，大容量加载操作会在将数据大容量复制到表中时获取大容量更新锁（BU 锁）。 大容量更新锁（BU 锁）允许多个线程将数据并发地大容量加载到同一表中，同时防止其他不进行数据大容量加载的进程访问该表。<br /><br />该行为与以下行为类似：用户在执行大容量加载时显式指定 TABLOCK 提示，或为给定表启用大容量加载的 sp_tableoption 表锁。 但是，启用此跟踪标志后，该行为将变成默认行为，无需进行任何查询或数据库更改。<br /><br />**作用域：** 全局或会话|
|**834**|对缓冲池、列存储和内存中表使用大型页分配。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3210239)。<br /><br />**注意：** 启用时，大型页内存模型会在实例启动时预分配所有 SQLOS 内存，并且不会将该内存返回到操作系统。<br /><br />**注意：** 如果正在使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的列存储索引功能，则不建议启用跟踪标志 834。<br /><br />**作用域**：仅全局|
|**845**|当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务帐户启用了“锁定内存页”特权时，启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 标准 SKU 上的锁定页。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/970070)以及[“服务器内存”服务器配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md#lock-pages-in-memory-lpim)文档页。<br /><br />注意：  从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，将为标准 SKU 默认启用此行为，并且不得使用跟踪标志 845。<br /><br />**作用域**：仅全局|
|**902**|安装累积更新或 Service Pack 时不执行数据库升级脚本。 如果在脚本升级模式下遇到错误，建议联系 Microsoft SQL 客户服务和支持 (CSS) 获取进一步指导。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2163980)。<br /><br />警告  ：此跟踪标志用于在脚本升级模式下对失败更新进行故障排除，不支持在生产环境中连续运行该标志。 需要成功执行数据库升级脚本才能完整安装累积更新和 Service Pack。 不这样做可能会导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例出现意外问题。<br /><br />**作用域**：仅全局|
|**1117**|当文件组中的某个文件达到自动增长阈值时，文件组中的所有文件都会增长。<br /><br />注意：  从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由 ALTER DATABASE 的 AUTOGROW_SINGLE_FILE 和 AUTOGROW_ALL_FILES 选项控制，跟踪标志 1117 不再有效。 有关详细信息，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)。<br /><br />**作用域：** 仅全局|
|**1118**|删除服务器上的大多数单页分配，以减少 SGAM 页上的争用。 创建新对象后，默认情况下，将从不同的盘区（混合区）分配前 8 页。 此后，如果需要更多的页，将从相同的片区（统一区）分配进行分配。 SGAM 页用于跟踪这些混合区，因此发生大量混合页分配时，可能会很快成为瓶颈。 创建新对象时，此跟踪标志从相同的片区分配所有 8 页，以最大限度降低扫描 SGAM 页的需求。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/328551)。<br /><br />注意：  从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由 ALTER DATABASE 的 SET MIXED_PAGE_ALLOCATION 选项控制，跟踪标志 1118 不再有效。 有关详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)。<br /><br />**作用域：** 仅全局|  
|**1204**|返回参与死锁的锁的资源和类型，以及受影响的当前命令。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/832524)。<br /><br />**作用域：** 仅全局|  
|**1211**|基于内存不足或基于锁数禁用锁升级。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]不会将行锁或页锁升级到表锁。<br /><br />使用此跟踪标志可生成过多的锁数目。 这样会降低[!INCLUDE[ssDE](../../includes/ssde-md.md)]的性能，或因为内存不足而导致 1204 错误（无法分配锁资源）。<br /><br />如果同时设置了跟踪标志 1211 和 1224，则 1211 优先于 1224。 但是，由于在所有情况下（甚至在内存紧张的情况下）跟踪标志 1211 都禁止升级，因此建议使用 1224。 这有助于在使用多个锁时避免“锁不足”错误。<br /><br />**作用域**：全局或会话|  
|**1222**|以不符合任何 XSD 架构的 XML 格式，返回参与死锁的锁的资源和类型，以及受影响的当前命令。<br /><br />**作用域**：仅全局|  
|**1224**|基于锁数禁用锁升级。 但是，内存不足仍可激活锁升级。 如果锁对象使用的内存量超出下列条件之一，[!INCLUDE[ssDE](../../includes/ssde-md.md)]会将行锁或页锁升级为表（或分区）锁：<br /><ul><li>[!INCLUDE[ssDE](../../includes/ssde-md.md)]占用的 40% 的内存。 只有在 sp_configure 的 **locks** 参数设置为 0 时，这才适用。 <li>使用 sp_configure 的 locks 参数配置的锁内存的 40%  。 有关详细信息，请参阅 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</li></ul><br />如果同时设置了跟踪标志 1211 和 1224，则 1211 优先于 1224。 但是，由于在所有情况下（甚至在内存紧张的情况下）跟踪标志 1211 都禁止升级，因此建议使用 1224。 这有助于在使用多个锁时避免“锁不足”错误。<br /><br />注意：  也可以使用 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) 语句的 LOCK_ESCALATION 选项控制到表级或 HoBT 级粒度的锁升级。<br /><br />**作用域：** 全局或会话|
|**1236**|启用数据库锁分区。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2926217)。<br /><br />注意：  从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP3 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 开始，此行为由引擎控制，跟踪标志 1236 不再有效。<br /><br />**作用域**：仅全局|
|**1237**|允许 ALTER PARTITION FUNCTION 语句遵从用户定义的当前会话死锁优先级，而不是成为默认情况下可能的死锁牺牲品。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/4025261)。<br /><br />注意：  从 [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] 和数据库[兼容性级别](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md) 140 开始，该行为变成默认行为，跟踪标志 1237 不再有效。<br /><br />**作用域**：全局、会话或查询|
|**1260**|禁用计划程序监视器转储。<br /><br />**作用域**：仅全局|   
|**1448**|甚至在异步辅助数据库不确认接受更改的情况下，也使复制日志读取器前移。 甚至在此跟踪标志启用的情况下，日志读取器也始终等待同步辅助数据库。 日志读取器将不会超过同步辅助数据库的最小确认。 此跟踪标志应用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，而不仅是可用性组、可用性数据库或日志读取器实例。 应用会立即生效，无需重新启动。 此跟踪标志可提前激活或在同步辅助数据库失败时激活。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/937041)。<br /><br />**作用域**：仅全局|   
|**1462**|对异步可用性组禁用日志流压缩。 默认情况下，对异步可用性组启用此功能，以优化网络带宽。 有关详细信息，请参阅 [Tune compression for availability group](../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md)（调整可用性组的压缩）。<br /><br />**作用域**：仅全局| 
|**1800**|在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Always On 和日志传送环境中，当主副本和次要副本日志文件使用扇区大小不同的磁盘时，启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 优化。 只需在符合以下条件的 SQL Server 实例上启用此跟踪标志：事务日志文件驻留在扇区大小为 512 字节的磁盘上。 **无**需在扇区大小为 4k 的磁盘上启用。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3009974)。<br /><br />**作用域：** 仅全局|
|**2301**|启用高级决策支持优化。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：全局、会话和查询|
|**2312**|允许将查询优化器基数估计模型设置为 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本，而不考虑数据库兼容性级别。 有关详细信息，请参阅 [Microsoft 支持文章](https://support.microsoft.com/kb/2801413)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'FORCE_DEFAULT_CARDINALITY_ESTIMATION' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />**作用域**：全局、会话或查询| 
|**2335**|导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在查询优化期间假定有固定数量的内存可用。 它不限制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 授予用来执行查询的内存。 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置的内存仍将由数据缓存、查询执行和其他使用者使用。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2413549)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话或查询|
|**2340**|导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在生成计划时不对优化的嵌套循环联接使用排序操作（批排序）。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2009160)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'DISABLE_OPTIMIZED_NESTED_LOOP' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话或查询|
|**2371**|将固定自动更新统计信息阈值更改为动态自动更新统计信息阈值。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2754171)。<br /><br />注意：  从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，在低于 130 的[数据库兼容性级别](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)下，此行为由引擎控制，跟踪标志 2371 不再有效。<br /><br />**作用域**：仅全局|
|**2389**|为升序键启用自动生成的快速统计信息（直方图修正）。 如果设置了跟踪标志 2389，并且将前导统计信息列标记为升序，则会在查询编译时调整用于估计基数的直方图。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2801413)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />注意：  此跟踪标志不适用于 CE 版本 120 或更高版本。 请改用跟踪标志 4139。<br /><br />**作用域**：全局、会话或查询|
|**2390**|为升序键或未知键启用自动生成的快速统计信息（直方图修正）。 如果设置了跟踪标志 2390，并且将前导统计信息列标记为升序或未知，则会在查询编译时调整用于估计基数的直方图。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2801413)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />注意：  此跟踪标志不适用于 CE 版本 120 或更高版本。 请改用跟踪标志 4139。<br /><br />**作用域**：全局、会话或查询|
|**2422**|当超过 Resource Governor REQUEST_MAX_CPU_TIME_SEC 配置设置的最长时间时，允许 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]中止请求。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/4038419)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 及更高内部版本。<br /><br />**作用域**：全局|
|**2430**|启用备用锁类清除。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2754301)。<br /><br />**作用域**：仅全局| 
|**2451**|在 sys.dm_exec_query_plan_stats 中启用最后一个实际执行计划的等效项。<br /><br />**注意：** 此跟踪标志适用于 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4 及更高版本。<br /><br />**注意：** 自 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.5 起，若要在数据库级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 LAST_QUERY_PLAN_STATS 选项。<br /><br />**作用域**：仅全局|  
|**2453**|当足够数量的行发生更改时，允许表变量触发重新编译。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2952444)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话或查询|
|**2467**|启用备用并行工作线程分配策略（基于哪个节点具有最少分配的线程）。 有关详细信息，请参阅[并行查询处理](../../relational-databases/query-processing-architecture-guide.md#parallel-query-processing)。 请参阅[配置最大工作线程服务器配置选项](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)，了解有关配置最大工作线程服务器选项的信息。<br /><br />注意：  并行查询度 (DOP) 必须适用于要使用的此备用策略的单个节点，或改为使用默认线程分配策略。 使用跟踪标志时，不建议执行指定 DOP 多于单个节点中的计划程序数的查询，因为这会干扰指定 DOP 低于或等于单个节点中的计划程序数的查询。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：仅全局|
|**2469**|为已分区列存储索引中的 `INSERT INTO ... SELECT` 启用备用 Exchange。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3204769)。<br /><br />**作用域**：全局、会话或查询|
|**2528**|禁用 DBCC CHECKDB、DBCC CHECKFILEGROUP 和 DBCC CHECKTABLE 执行的对象并行检查。 默认情况下，并行度由查询处理器自动确定。 最大并行度的配置就像并行查询的最大并行度一样。 有关详细信息，请参阅 [配置 max degree of parallelism 服务器配置选项](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)。<br /><br />注意：  通常应启用（默认设置）并行 DBCC 检查。 查询处理器会对 DBCC CHECKDB 检查的每个表或每批表重新求值并自动调整并行度。<br /><br />典型的使用场景为：系统管理员知道在 DBCC CHECKDB 完成之前服务器负载会增加，因此选择手动减少或禁用并行操作，以便增加与其他用户工作负载的并发。 但是，禁用 DBCC CHECKDB 中的并行检查会延长其完成时间。<br /><br />注意：  如果使用 TABLOCK 选项执行 DBCC CHECKDB 并禁用并行操作，则可能会将表锁定较长时间。<br /><br />注意：  从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 开始，可以在语句中使用 MAXDOP 选项来覆盖 sp_configure 的 max degree of parallelism 配置选项。<br /><br />**作用域**：全局或会话|
|**2549**|运行 DBCC CHECKDB 命令，该命令假定每个数据库文件均位于唯一的磁盘驱动器上。 DBCC CHECKDB 命令根据唯一磁盘驱动器跨所有数据库文件生成一个待读取页面内部列表。 此逻辑根据每个文件的物理文件名的驱动器号确定唯一磁盘驱动器。<br /><br />注意：  除非知道每个文件都基于唯一的物理磁盘，否则不要使用此跟踪标志。<br /><br />注意：  尽管此跟踪标志改进了以使用 PHYSICAL_ONLY 选项为目标的 DBCC CHECKDB 命令的性能，但一些用户可能还是看不到性能有任何改进。 虽然此跟踪标志可以改善磁盘 I/O 资源的使用情况，但磁盘资源的基本性能可能会限制 DBCC CHECKDB 命令的整体性能。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2634571)。<br /><br />**作用域**：仅全局| 
|**2562**|无论数据库中有多少个索引，都以单个“批次”运行 DBCC CHECKDB 命令。 默认情况下，DBCC CHECKDB 命令会尝试通过以下方式最大限度地减少 tempdb 资源：限制使用“批次”概念生成的索引或“事实”的数量。 此跟踪标志强制在一个批次中执行所有处理。<br /><br />使用此跟踪标志的一个效果是 tempdb 的空间需求可能会增加。 Tempdb 可能会增长到 DBCC CHECKDB 命令正在处理的用户数据库的 5% 或更多。<br /><br />注意：  尽管此跟踪标志改进了以使用 PHYSICAL_ONLY 选项为目标的 DBCC CHECKDB 命令的性能，但一些用户可能还是看不到性能有任何改进。 虽然此跟踪标志可以改善磁盘 I/O 资源的使用情况，但磁盘资源的基本性能可能会限制 DBCC CHECKDB 命令的整体性能。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2634571)。<br /><br />**作用域**：仅全局|
|**2566**|在未指定 DATA_PURITY 选项的情况下，运行 DBCC CHECKDB 命令而不检查数据纯度。<br /><br />注意：  默认情况下将启用列值完整性检查，并且不需要使用 DATA_PURITY 选项。 对于从 SQL Server 的早期版本升级的数据库，默认情况下不启用列值检查，直到 DBCC CHECKDB WITH DATA_PURITY 已在数据库中正确运行至少一次为止。 然后，DBCC CHECKDB 将默认检查列值完整性。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/945770)。<br /><br />**作用域**：仅全局|
|**3023**|启用 CHECKSUM 选项作为 BACKUP 命令的默认选项。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2656988)。<br /><br />注意：  从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 开始，可通过设置 backup checksum default 配置选项来控制此行为  。 有关详细信息，请参阅 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。<br /><br />**作用域**：全局和会话|
|**3042**|绕过默认的备份压缩预先分配算法，以便允许备份文件仅根据需要增长以达到其最终大小。 如果您需要仅分配压缩的备份所需的实际大小以便节约空间，则此跟踪标志将很有用。 使用此跟踪标志可能会导致轻微的性能损失（在备份操作期间损失可能会增加）。 有关预先分配算法的详细信息，请参阅[备份压缩 (SQL Server)](../../relational-databases/backup-restore/backup-compression-sql-server.md)。<br /><br />**作用域**：仅全局|
|**3051**|允许将“SQL Server 备份到 URL”记录到特定的错误日志文件中。 有关详细信息，请参阅 [SQL Server 备份到 URL 最佳实践和故障排除](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)。<br /><br />**作用域**：仅全局|  
|**3205**|默认情况下，如果磁带机支持硬件压缩，则 DUMP 或 BACKUP 语句会使用该功能。 利用此跟踪标志，可以禁用磁带机的硬件压缩。 此选项在您需要与不支持压缩的其他站点或磁带机交换磁带时很有用。<br /><br />**作用域**：全局或会话|  
|**3226**|默认情况下，每个成功的备份操作都会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中添加一个条目。 如果非常频繁地创建日志备份，这些成功消息会迅速累积，从而产生一个巨大的错误日志，使查找其他消息变得非常困难。<br /><br />使用这一跟踪标志，可以取消这些日志条目。 如果您频繁地运行日志备份，并且没有任何脚本依赖于这些条目，则这种做法非常有用。<br /><br />**作用域**：仅全局|   
|**3427**|在 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 或 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 中，如果多个将数据插入临时表的连续事务占用的 CPU 比在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中时更多，则启用修复来解决问题。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/3216543)<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU2 及更高内部版本。 从 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 开始，此跟踪标志不再有效。<br /><br />**作用域**：仅全局|  
|**3459**|禁用并行重做。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/3200975)和 [Microsoft 支持文章](https://support.microsoft.com/help/4101554)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 和 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]。<br /><br />**作用域**：仅全局| 
|**3468**|禁用 TempDB 上的[间接检查点](https://docs.microsoft.com/sql/relational-databases/logs/database-checkpoints-sql-server?view=sql-server-2017#IndirectChkpt)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU5、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1 及更高内部版本。<br /><br />**作用域**：仅全局|  
|**3608**|禁止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动启动和恢复除 **master** 数据库之外的任何数据库。 如果已启动要求使用 **tempdb** 的活动，则会恢复 **model**，并创建 **tempdb**。 在访问数据库时将启动并恢复其他数据库。 可能无法运行某些功能，如快照隔离和读提交快照。 用于[移动系统数据库](../../relational-databases/databases/move-system-databases.md)和[移动用户数据库](../../relational-databases/databases/move-user-databases.md).<br /><br />注意：  请不要在正常操作中使用。<br /><br />**作用域**：仅全局|   
|**3625**|通过使用“\*\*\*\*\*\*”屏蔽某些错误消息的参数，限制返回给不是 sysadmin 固定服务器角色成员的用户的信息量。 这可以帮助阻止披露敏感信息。<br /><br />**作用域**：仅全局|  
|**3656**|若安装了适用于 Windows 的调试工具，在堆栈转储上启用符号解析。 有关详细信息，请参阅 [Microsoft 白皮书](https://www.microsoft.com/download/details.aspx?id=26666)。<br /><br />警告：  这是调试跟踪标志，不用于生产环境。<br /><br />**作用域**：全局和会话|
|**4136**|除非使用 OPTION(RECOMPILE)、WITH RECOMPILE 或 OPTIMIZE FOR \<value>，否则禁用参数探查。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/980653)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，若要在数据库级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 PARAMETER_SNIFFING 选项。<br /><br />若要在查询级别完成此操作，请添加 OPTIMIZE FOR UNKNOWN [查询提示](../../t-sql/queries/hints-transact-sql-query.md)。 从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，在查询级别完成此操作的另一种方法是添加 USE HINT 'DISABLE_PARAMETER_SNIFFING' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局或会话|  
|**4137**|在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和更早版本的查询优化器基数估计模型下估计筛选器的 AND 谓词以说明相关性时，导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用最小选择性生成一个计划。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2658214)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请在使用旧版 CE 时添加 USE HINT 'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />注意：  此跟踪标志不适用于 CE 版本 120 或更高版本。 请改用跟踪标志 9471。<br /><br />**作用域**：全局、会话或查询| 
|**4138**|导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成一个计划，该计划不对包含 TOP、OPTION (FAST N)、IN 或 EXISTS 关键字的查询使用行目标调整。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2667211)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'DISABLE_OPTIMIZER_ROWGOAL' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话或查询| 
|**4139**|无论键列处于什么状态，均启用自动生成的快速统计信息（直方图修正）。 如果设置了跟踪标志 4139，则无论前导统计信息列处于什么状态（升序、降序或静止），都会在查询编译时调整用于估计基数的直方图。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2952101)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />注意：  此跟踪标志不适用于 CE 版本 70。 请改用跟踪标志 2389 和 2390。<br /><br />**作用域**：全局、会话或查询|
|**4199**|<a name="4199"></a>启用在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 累积更新和 Service Pack 中发布的查询优化器 (QO) 修补程序。<br /><br />默认情况下会在给定产品版本的最新数据库[兼容性级别](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)下启用对早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所做的 QO 更改，但不启用跟踪标志 4199。<br /><br />下表总结了使用特定数据库兼容性级别和跟踪标志 4199 时的行为。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/974006)。<br /><br /><table border="1" frame="void" width="550"><tr valign="middle" align="center"><td>**数据库兼容性级别**</td><td>**TF 4199**</td><td>**来自以前的数据库兼容性级别的 QO 更改**</td><td>**当前版本后期 RTM 的 QO 更改**</td></tr><tr valign="middle" align="center"><td rowspan="2">**100 至 120**</td><td>Off</td><td>禁用</td><td>禁用</td></tr><tr valign="middle" align="center"><td>On</td><td>已启用</td><td>已启用</td></tr><tr valign="middle" align="center"><td rowspan="2">**130**</td><td>Off</td><td>已启用</td><td>禁用</td></tr><tr valign="middle" align="center"><td>On</td><td>已启用</td><td>已启用</td></tr><tr valign="middle" align="center"><td rowspan="2">**140**</td><td>Off</td><td>已启用</td><td>禁用</td></tr><tr valign="middle" align="center"><td>On</td><td>已启用</td><td>已启用</td></tr><tr valign="middle" align="center"><td rowspan="2">150 </td><td>Off</td><td>已启用</td><td>禁用</td></tr><tr valign="middle" align="center"><td>On</td><td>已启用</td><td>已启用</td></tr></table><br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，若要在查询级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 QUERY_OPTIMIZER_HOTFIXES 选项。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'ENABLE_QUERY_OPTIMIZER_HOTFIXES' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />**作用域**：全局、会话或查询|
|**4610**|将存储缓存条目的哈希表的大小增加 8 倍。 与跟踪标志 4618 一起使用时，TokenAndPermUserStore 缓存存储中的条目数增加到 8,192 个。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/959823)。<br /><br />**作用域：** 仅全局|
|**4616**|使应用程序角色可以看到服务器级元数据。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，应用程序角色无法访问自身数据库以外的元数据，因为应用程序角色与服务器级别主体不相关联。 这是对早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的行为的更改。 设置此全局标志将禁用新的限制，并允许应用程序角色访问服务器级元数据。<br /><br />**作用域**：仅全局|
|**4618**|将 TokenAndPermUserStore 缓存存储中的条目数限制为 1,024 个。 与跟踪标志 4610 一起使用时，TokenAndPermUserStore 缓存存储中的条目数增加到 8,192 个。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/959823)。<br /><br />**作用域：** 仅全局|
|**5004**|暂停 TDE 加密扫描，并导致加密扫描工作线程退出而不执行任何操作。 数据库将继续处于加密状态（正在加密）。 若要恢复重新加密扫描，请禁用跟踪标志 5004 并运行 ALTER DATABASE <database_name> SET ENCRYPTION ON。 <br /><br />**作用域：** 仅全局|
|**6498**|当有足够的可用内存时，允许多个大型查询编译访问大型网关。 它基于 80% 的 SQL Server 目标内存，并且允许每 25 GB 内存有一个大型查询编译。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3024815)。<br /><br />注意：  从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 和 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由引擎控制，跟踪标志 6498 不再有效。<br /><br />**作用域**：仅全局|
|**6527**|禁止在 CLR 集成中第一次发生内存不足异常时生成内存转储。 默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 CLR 中第一次发生内存不足异常时会生成小内存转储。 该跟踪标志的行为如下所示：<br /><ul><li>如果用作一个启动跟踪标志，则永远不生成内存转储。 但是，如果使用了其他跟踪标志，则可能会生成内存转储。 <li>如果在正在运行的服务器上启用此跟踪标志，则从此时开始不会自动生成内存转储。 但是，如果已经由于 CLR 中的内存不足异常生成了内存转储，则此跟踪标志将没有任何效果。</li></ul><br />**作用域**：仅全局|
|**6532**|在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，针对空间数据类型提高查询操作的性能。 根据配置、查询类型和对象的不同，性能提升程度将有所不同。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3107399)。<br /><br />注意：  从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由引擎控制，跟踪标志 6532 不再有效。<br /><br />**作用域**：全局和会话|
|**6533**|在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，针对空间数据类型提高查询操作的性能。 根据配置、查询类型和对象的不同，性能提升程度将有所不同。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3107399)。<br /><br />注意：  从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由引擎控制，跟踪标志 6533 不再有效。<br /><br />**作用域**：全局和会话| 
|**6534**|在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 和 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 中，针对空间数据类型提高查询操作的性能。 根据配置、查询类型和对象的不同，性能提升程度将有所不同。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3107399)。<br /><br />**作用域**：仅全局|
|**7314**|使用 OLE DB 提供程序将精度/确定位数未知的 NUMBER 值强制视为双精度值。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3051993)。<br /><br />**作用域**：全局和会话|  
|**7412**|启用轻型查询执行统计信息分析基础结构。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3170113)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 及更高内部版本。 从 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 开始，此跟踪标志将不起作用，因为默认情况下启用轻量分析。<br /><br />**作用域**：仅全局|
|**7471**|为单个表上的不同统计信息启用多个 [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) 并发运行。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3156157)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 及更高内部版本。<br /><br />**作用域**：仅全局|
|**7745**|强制查询存储在数据库关闭时不将数据刷新到磁盘。<br /><br />注意：  使用此跟踪可能会导致先前未刷新到磁盘的查询存储数据在关闭时丢失。 关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，可以使用 SHUTDOWN WITH NOWAIT 命令强制立即关闭，而不是使用此跟踪标志。<br /><br />**作用域**：仅全局|
|**7752**|启用查询存储的异步加载。<br /><br />**注意：** 如果 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] 遇到大量与查询存储同步加载（数据库恢复期间的默认行为）相关的 QDS_LOADDB 等待，则使用此跟踪标志。<br /><br />**作用域**：仅全局|
|**7806**|在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]上启用专用管理员连接 (DAC)。 默认情况下，在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 上不保留 DAC 资源。 有关详细信息，请参阅 [用于数据库管理员的诊断连接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。<br /><br />**作用域**：仅全局|  
|**8011**|为资源监视器禁用环形缓冲区。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：全局和会话|
|**8012**|为计划程序禁用环形缓冲区。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：仅全局|
|**8015**|禁用自动检测和 NUMA 设置。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2813214)。<br /><br />**作用域**：仅全局|
|**8018**|禁用异常环形缓冲区。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：仅全局|
|**8019**|为异常环形缓冲区禁用堆栈集合。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：仅全局|
|**8020**|禁用工作集监视。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />**作用域**：仅全局|
|**8032**|将缓存限制参数还原为 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]RTM 设置，此设置通常允许更大的缓存。 当频繁重复使用的缓存条目不适合缓存时，以及当 [“针对即席工作负荷进行优化”服务器配置选项](../../database-engine/configure-windows/optimize-for-ad-hoc-workloads-server-configuration-option.md) 未能解决与计划缓存相关的问题时，请使用此设置。<br /><br />警告  ：如果大缓存使较少的内存可用于其他内存消耗者（如缓冲池），则跟踪标志 8032 可能导致性能较差。<br /><br />**作用域**：仅全局|   
|**8048**|将 NUMA 分区内存对象转换为 CPU 分区内存对象。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2809338)。<br /><br />**注意：** 从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 和 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为是动态的，由引擎控制。<br /><br />**作用域**：仅全局|  
|**8075**|在 64 位 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 上收到内存页分配错误时，减少 [VAS](../../relational-databases/memory-management-architecture-guide.md#changes-to-memory-management-starting-2012-11x-gm) 片段。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3074434)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3。 从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由引擎控制，跟踪标志 8075 不再有效。<br /><br />**作用域**：仅全局|
|**8079**|允许 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 询问硬件布局，并在报告每个 NUMA 节点 8 个或更多 CPU 的系统上自动配置 Soft-NUMA。 自动 Soft-NUMA 行为可识别超线程（HT/逻辑处理器）。 通过提高侦听器数、缩放和网络与加密功能，其他节点的分区和创建会缩放后台处理。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2。 从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，此行为由引擎控制，跟踪标志 8079 不再有效。<br /><br />**作用域**：仅全局| 
|**8207**|允许事务复制和 CDC 的 singleton 更新。 对订阅服务器的更新可以作为 DELETE 和 INSERT 对复制。 这可能不符合业务规则的要求，如激发 UPDATE 触发器。 使用跟踪标志 8207 时，对只影响一行的唯一列的更新（单一实例更新）将作为 UPDATE 而非作为 DELETE 或 INSERT 对进行复制。 如果该更新影响具有唯一约束的列或影响多个行，则仍将该更新作为 DELETE 或 INSERT 对进行复制。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/302341)。<br /><br />**作用域**：仅全局|
|**8721**|在执行自动更新统计信息时向错误日志提交报告。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/195565)。<br /><br />**作用域**：仅全局|
|**8744**|为嵌套循环运算符禁用预提取。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/920093)。<br /><br />注意：  当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行包含嵌套循环运算符的计划时，错误地使用此跟踪标志可能会导致额外的物理读取。<br /><br />**作用域**：全局和会话|
|**9024**|将全局日志池内存对象转换为 NUMA 节点分区内存对象。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/2809338)。<br /><br />注意：  从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP3 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 开始，此行为由引擎控制，跟踪标志 9024 不再有效。<br /><br />**作用域**：仅全局|
|**9347**|禁用 Sort 运算符的批处理模式。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 引入了新的批处理模式 Sort 运算符，可以提高许多分析查询的性能。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3172787)。<br /><br />**作用域**：全局、会话或查询|
|**9349**|禁用 Top N Sort 运算符的批处理模式。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 引入了新的批处理模式 top sort 运算符，可以提高许多分析查询的性能。<br /><br />**作用域**：全局、会话或查询|
|**9389**|为批处理模式运算符启用额外动态内存授予。 如果查询未获取所需的所有内存，则会将数据溢出到 tempdb，从而导致额外的 I/O 并可能影响查询性能。 如果启用动态内存授予跟踪标志，批处理模式运算符可能会要求提供更多内存，如果有更多内存可用，则会避免溢出到 tempdb。 有关详细信息，请参阅[内存管理体系结构指南](../../relational-databases/memory-management-architecture-guide.md#effects-of-min-memory-per-query)中的“min memory per query 的影响”部分  。<br /><br />**作用域**：全局或会话| 
|**9398**|禁用[自适应联接](../../relational-databases/performance/intelligent-query-processing.md#batch-mode-adaptive-joins)运算符，在扫描第一个输入后可延迟选择[哈希联接或嵌套循环联接](../../relational-databases/performance/joins.md)方法，如 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 中引入的那样。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/4099126)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话和查询|
|**9453**|禁用批处理模式执行。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/help/4016902)。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域：** 全局、会话和查询|
|**9471**|在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的查询优化器基数估计模型下，导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用最小选择性为单表筛选器生成一个计划。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />注意：  此跟踪标志不适用于 CE 版本 70。 请改用跟踪标志 4137。<br /><br />**作用域**：全局、会话或查询| 
|**9476**|在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的查询优化器基数估计模型下，导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用简单包含假设而非默认的基本包含假设来生成计划。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3189675)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />注意：  请确保在将此选项引入生产环境之前，先对其进行全面测试。<br /><br />**作用域**：全局、会话或查询| 
|**9481**|允许将查询优化器基数估计模型设置为 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更早版本，而不考虑数据库兼容性级别。 有关详细信息，请参阅 [Microsoft 支持文章](https://support.microsoft.com/kb/2801413)。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 开始，若要在数据库级别完成此操作，请参阅 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 中的 LEGACY_CARDINALITY_ESTIMATION 选项。<br /><br />从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，若要在查询级别完成此操作，请添加 USE HINT 'FORCE_LEGACY_CARDINALITY_ESTIMATION' [查询提示](../../t-sql/queries/hints-transact-sql-query.md)，而不是使用此跟踪标志。<br /><br />**作用域**：全局、会话或查询|  
|**9485**|对 DBCC SHOW_STATISTICS 禁用 SELECT 权限。<br /><br />**作用域**：仅全局|
|**9488**|<a name="9488"></a>当使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的查询优化器基数估计模型时，将表值函数的固定估计值设置为默认值 1（对应于 [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)] 及更早版本的查询优化器基数估计模型下的默认值）。<br /><br />**作用域**：全局、会话或查询|
|**9495**|在 INSERT...SELECT 操作的插入过程中禁用并行，它适用于用户表和临时表。 有关详细信息，请参阅 [Microsoft 支持文章](https://support.microsoft.com/kb/3180087)<br /><br />**作用域**：全局或会话| 
|**9567**|对自动种子设定过程中的 Always On 可用性组启用数据流压缩。 在自动种子设定过程中，压缩可大幅缩短传输时间，并且将增加处理器上的负载。 有关详细信息，请参阅[自动初始化 Always On 可用性组](../../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md)和[调整可用性组的压缩](../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md)。<br /><br />**作用域**：全局或会话|
|**9571**|禁用可用性组自动设定种子到默认数据库路径。 有关详细信息，请参阅[磁盘布局](../../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md)。<br /><br />**作用域**：全局或会话| 
|**9591**|在 Always On 可用性组中禁用日志块压缩。 在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，日志块压缩是用于同步副本和异步副本的默认行为。 在 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 中，压缩仅用于异步副本。 <br /><br />**作用域**：全局或会话|
|**9592**|对同步可用性组启用日志流压缩。 默认情况下，对同步可用性组禁用此功能，因为压缩会增加延迟。 有关详细信息，请参阅 [Tune compression for availability group](../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md)（调整可用性组的压缩）。<br /><br />**作用域**：全局或会话| 
|**9929**|将每个内存中检查点文件都缩减为 1 MB。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/3147012)。<br /><br />**作用域**：仅全局|  
|**9939**|在 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 中，允许在引用内存优化表或表变量的 DML 操作中并行计划和并行扫描内存优化表和表变量，前提是它们不是 DML 操作的目标。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/4013877)。<br /><br />注意：  如果还显式启用了跟踪标志 4199，则不需要使用跟踪标志 9939。<br /><br />**作用域**：全局、会话或查询|   
|**10204**|在列存储索引重组期间禁用合并/重新压缩。 在 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 中，当重组列存储索引时，会有一个新功能将所有小型压缩行组自动合并为较大的压缩行组，并重新压缩具有大量已删除行的所有行组。<br /><br />注意：  跟踪标志 10204 不适用于对内存优化表创建的列存储索引。<br /><br />**作用域**：全局或会话|   
|**10316**|允许对[内部内存优化暂存时态表](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)创建除默认索引之外的附加索引。 如果有特定的查询模式，其中包含未被默认索引覆盖的列，则可以考虑添加附加索引。<br /><br />注意：  内存优化表的经系统版本控制的时态表旨在提供较高的事务吞吐量。 请注意，创建附加索引可能会为更新或删除当前表中的行的 DML 操作带来开销。 如果使用附加索引，应力求在时态查询的性能和额外的 DML 开销之间找到适当的平衡点。<br /><br />**作用域**：全局或会话|
|**11023**|对于未将采样率显式指定为 [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) 语句一部分的所有后续统计信息更新，禁止使用上一个持续采样率。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/4039284)。<br /><br />**作用域**：全局或会话|    
|**11024**|当任何分区的修改计数超过本地[阈值](../../relational-databases/statistics/statistics.md#AutoUpdateStats)时，允许触发统计信息的自动更新。 有关详细信息，请参阅此 [Microsoft 支持文章](https://support.microsoft.com/kb/4041811)。<br /><br />注意：  此跟踪标志适用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 及更高内部版本。<br /><br />**作用域**：全局或会话| 
  

  
## <a name="examples"></a>示例  
 以下示例使用 DBCC TRACEON 针对服务器级别的所有会话将跟踪标志 3205 设置为开。  
  
```sql  
DBCC TRACEON (3205,-1);  
```

对于特定查询，可以启用由跟踪标志 4199 和 4137 控制的所有影响计划的修补程序。
  
```sql
SELECT x FROM correlated WHERE f1 = 0 AND f2 = 1 OPTION (QUERYTRACEON 4199, QUERYTRACEON 4137)
``` 
 
## <a name="see-also"></a>另请参阅  
[数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DBCC INPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
[DBCC OUTPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-outputbuffer-transact-sql.md)  
[DBCC TRACEOFF (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACEON (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)  
[DBCC TRACESTATUS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)  
[EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)  
[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
[SET NOCOUNT (Transact-SQL)](../../t-sql/statements/set-nocount-transact-sql.md)  
[ALTER DATABASE SET 选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
[查询提示 (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)

