---
title: ADO 术语表术语 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6f139965c4235b84c66c460767d5c6d1695b68ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701831"
---
# <a name="ado-glossary-terms"></a>ADO 术语表术语
本主题定义与 ADO 相关的术语。

## <a name="a"></a>A
 绝对 URL 的完全限定 URL，Internet 或 intranet 上指定的资源所在的位置。 另请参阅*URL*并*相对 URL*。

 ActiveX 控件通常具有一个可视元素在设计时或运行的时的自助注册、 进程内 COM 组件。 ActiveX 控件还可以与活动文档容器，如 Microsoft Internet Explorer 进行通信。

 ADISAPI （高级数据 Internet 服务器应用程序编程接口） ISAPI DLL 提供了分析，自动化控制，封送处理记录集，以及 MIME 打包。 ADISAPI 组件的工作方式通过提供由 Internet 信息服务 (IIS) 的 API。 另请参阅*ISAPI*。

 在查询中，如 COUNT、 AVG 或计算表的列中使用的所有行的值的 STDEV 函数的聚合函数。 在编写表达式和编程中，可以使用 SQL 聚合函数 （包括上面列出的三个） 和域聚合函数来确定的各种统计信息。

 别名的备用名称需授予权限的列或表达式中的 SQL SELECT 语句，通常更短或更有意义。 例如，BobSales 是以下 SELECT 语句中的别名："选择作为从 SalesDB BobSales wr Sales"。 可以使用别名将动态分配 DataControl 对象上的控件绑定到的列。

 单元线程处理 COM 线程模型对对象的所有调用都发生在一个线程。 在单元线程处理，COM 同步，并将调用封送。 另请参阅*COMmddefcom*。

 一个将控制返回给调用程序，而无需等待操作完成的操作的异步操作。 操作已完成之前，将继续执行代码。 另请参阅*同步操作*。

## <a name="b"></a>B
 在表中的字段和变量之间的绑定条目的映射。 在 ADO VisualC++扩展中，**记录集**字段映射到 C /C++变量。

 位掩码的数字值适用于与其他数字值，通常为参数中的标志选项或返回值的按位值比较。 通常这种比较通过按位逻辑运算符，如**并**并**或者**在 Visual Basic 中 **&** 并 **&#124;** 在C++。

 例如，ADO **FieldAttributeEnum**值可以使用为位掩码，以确定字段的特性。 假设你想要确定字段是否可更新。 可以使用以下表达式在 Visual Basic 中对此进行测试：`Field.Attributes AND adFldUpdatable`

 如果结果为 TRUE，则可更新字段。

 添加书签，以便用户可以快速导航到它唯一标识行集中的行的标记。

 业务对象执行一组定义的操作，如数据验证或业务规则逻辑的对象。 业务对象通常驻留在中间层上。

 业务规则验证编辑、 登录验证、 数据库查找、 策略和构成开展业务的企业的方式的算法转换的组合。 也称为*业务逻辑*。

## <a name="c"></a>C
 计算表达式的表达式不是常量，但其值取决于其他值。 要计算的计算的表达式必须获取并计算来自其他源，通常在其他字段或行的值。

 章一个来自数据源的行范围的引用。 在 ADO 中，一个章节通常是对另一个引用**记录集**。

 章节列使其可以定义*父-子*关系其中*父*是**记录集**包含章节列和*子*是**记录集**由一章。

 章别名引用的列的别名附加到父级。

 字符集一组字符的映射到其数字值。 例如，Unicode 是集能够对所有已知的字符进行编码，用作全球范围内的字符编码标准的 16 位字符。

 子层次结构关系的依赖端。 子级是具有其上方的另一个节点的层次结构中的节点 （更接近于根）。 另请参阅*子别名*，*父-子关系*，*父*。

 子别名引用子级的别名。 另请参阅*别名*，*子*。

 CLSID （类标识符） 的全局唯一标识符 (UUID)，用于标识 COM 组件。 以便它可以由其他应用程序加载，每个 COM 组件在 Windows 注册表中具有的 CLSID。 另请参阅*ProgID*， *COM*。

 客户端层的逻辑层的分布式系统的通常向用户提供数据以及处理输入用户，有时称为*前端*。 通常情况下，客户端层从基于输入的服务器请求数据，然后设置格式并显示结果。 另请参阅*中间层*，*数据源层*，*分布式应用程序*。

 COM （组件对象模型） 的二进制标准，使对象能够在联网环境中而不考虑开发各个语言或在其所在的计算机上进行互操作。 基于 COM 的技术包括 ActiveX 控件、 自动化和链接和嵌入 (OLE) 对象。 COM 允许对象向其他组件和主机应用程序公开其功能。 它定义了对象如何公开本身和跨进程和跨网络这种公开的工作原理。 COM 还定义了对象的生命周期。

 COM 组件二进制文件-例如.dll、.ocx 和某些.exe 文件-提供对象支持 COM 标准的。 此类文件包含一个或多个类工厂、 COM 类、 注册表项机制、 加载代码等的代码。

 比较运算符比较两个表达式并返回一个布尔值的运算符。

 可能表示为条件参数">"（大于）、"\<"（小于）、"="（等于）"> ="（大于或等于）"< ="（小于或等于）、"<>"（不等于），或"like"（模式匹配）。

 组件的对象，封装数据和代码，并提供了一组明确指定的公开可用的服务。

 复合文件的 COM 实现结构化存储文件。 复合文件将单独的对象存储在一个结构化文件包含两个主要元素： 存储对象和流对象。 它们共同作用，如文件中的文件系统。

 在一个物理文件中绑定在一起的单个文件的数量。 复合文件中的每个单个文件可以访问，就好像在一个物理文件。

 常量不会更改的数值或字符串值。 命名的 ADO 枚举 （枚举常量） 可以使用在代码中而不是实际值，例如， **adUseClient**是的常量值为 3。 (Const adUseClient = 3)。 另请参阅*枚举*。

 游标控制记录导航、 可更新性的数据，以及其他用户对数据库所做的更改的可见性的数据库元素。

## <a name="d"></a>D
 数据绑定相关联的对象或控件的数据源的应用程序的过程。 与数据源相关联的控件称为*数据绑定控件*。

 数据绑定控件的内容是与数据库中的值相关联。 例如，绑定到一个网格控件**记录集**对象可以是更新时中的行**记录集**进行更新。 当新要检索的值由**记录集**，网格中显示新值。

 数据提供程序公开的 ADO 应用程序的数据的软件直接或通过服务提供程序。 另请参阅服务提供程序。

 数据整理一种方法可使使用正式语法的 (称为**形状语言**) 来定义一个专用**记录集**对象 (称为*调整的记录集*) 的包含不只是数据，但也引用到其他**记录集**对象和/或计算的值基于这些其他**记录集**对象。

 数据源的分布式系统的代表运行 DBMS，例如 SQL Server 数据库的计算机层的逻辑层。 另请参阅*客户端层*，*中间层*，*分布式应用程序*。

 DCOM 的线路协议，使 COM 组件，可以在网络上直接相互通信。 另请参阅*COM*，*组件*。

 DDL （数据定义语言） 定义，而不是操作，数据在 SQL 中的这些语句。 创建或使用 DDL 修改数据库的架构。 例如， **CREATE TABLE**， **CREATE INDEX**，**授予**，以及**撤消**是 SQL DDL 语句。

 默认流式处理文本或二进制流 (由**Stream**对象) 相关联**记录**或**记录集**对象时使用某些 OLE DB 访问接口，例如，用于 Internet 发布的 Microsoft OLE DB 提供程序。 默认流通常包含如 HTML 代码用于网站的根目录的文件的内容。

 分布式应用程序的编写，以便通过网络可以在多台计算机之间划分处理程序。 通常情况下，分布式应用程序划分为演示文稿、 业务逻辑和数据存储层，或*层*。 请参阅客户端层、 中间层和数据源层。

 断开连接记录集 A**记录集**不再具有实时连接到服务器的客户端缓存中的对象。 如果原始数据源需要访问再次出于某种原因，例如，更新数据，必须重新建立连接。 但是，集合、 属性和方法的已断开连接**记录集**仍可访问。

 DML （数据操作语言） 操作，而不是定义数据在 SQL 中的这些语句。 选择并使用 DML 修改数据库中的值。 例如，**插入**，**更新**，**删除**，以及**选择**是 SQL DML 语句。

 文档源提供程序的提供程序管理文件夹和文档的一个特殊类。 表示一个文档时**记录**对象或某个文件夹中的文档由**记录集**对象时，文档源提供程序填充这些对象的一组唯一的字段，描述文档，而不是实际文档本身的特征。 另请参阅资源记录。

 DSN （数据源名称） 用于连接到特定 ODBC 数据库应用程序的信息集合。 ODBC 驱动程序管理器使用此信息来创建与数据库的连接。 在文件 （文件 DSN） 或 Windows 注册表 (machine DSN) 中，可以存储 DSN。

 特定于数据访问接口或游标服务的动态属性的属性。 **属性**自动使用这些填充对象的集合 （"动态"）。 连接到数据源通过特定的数据提供程序之前，对象将具有任何动态属性。 另请参阅数据提供程序、 光标。

## <a name="e"></a>E
 命名常量的枚举的列表。 枚举的值不需要是唯一的。 但是每个值的名称必须在其中定义枚举的作用域内唯一。 在 ADO 中，枚举用于数字参数和返回值，将含义添加到的 ADO 代码并避免开发人员的数字值 （这可能会更改版本之间的差异）。 例如，若要打开一个静态**记录集**，使用**adOpenStatic**枚举值： `Recordset.Open ,,adOpenStatic`

 ョ 嘿 *枚举的常数*。 另请参阅*常量*。

 事件由一个对象，可以为其编写代码以响应识别的操作。 命令执行、 事务完成、 记录集导航和数据更新，以及其他操作可以生成事件。 另请参阅*事件处理程序*。

 事件处理程序的事件处理程序是一个事件发生时执行的代码。 另请参阅事件。

## <a name="h"></a>H
 管理的常见和相对简单的条件或操作，例如错误恢复或数据管理的一个处理程序例程。

 分层记录集 A**记录集**，其中包含另一个**记录集**。 另请参阅数据整理一章。

 有关详细信息，请参阅[访问分层记录集的行](../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)。

 通常，层次结构的层次结构是具有 top 的排名的结构级别和从属级别。 在 ADO 中，层次结构**记录集**用于表示一条记录和一个章节的父-子关系。 在 ADO 中，还**记录**并**Stream**对象可用于访问文件夹和文档等的分层树状结构。 ADO MD 还包括**层次结构**对象来表示 OLAP 多维数据集中的维度级别之间的关系。 另请参阅分层记录集，父-子关系、 章节和树。

## <a name="i-l"></a>I-L
 ISAPI （Internet 服务器应用程序编程接口） 的组用于 Internet 服务器，如运行 Microsoft® Internet 信息服务 (IIS) 的 Windows NT® Server/Windows 2000 服务器的函数。

 键列或表中的列，用于唯一标识某行;通常用于索引表。

## <a name="m"></a>M
 跨线程或进程边界封送的打包、 发送，和解接口方法参数的过程。

 中间层在分布式系统中的用户界面或 Web 客户端与数据库之间的逻辑层。 这通常是业务对象进行实例化的位置。 中间层是业务规则和函数，生成，并对其接收的信息进行操作的集合。 它们通过业务规则，通常情况下，可以更改，因此封装到物理上独立于应用程序逻辑本身的组件实现此目的。 也称为*应用程序服务器层*。 另请参阅分布式应用程序、 客户端层、 数据源层。

 MIME （多用途 Internet 邮件扩展） Internet 协议最初开发以允许跨异类网络、 计算机和电子邮件环境的丰富内容的电子邮件消息交换。 在实践中，MIME 也已采用并通过非邮件应用程序扩展。

 MIME 是一种标准，允许单独发布和在 Internet 上读取二进制数据。 具有二进制数据的文件的标头包含数据; 的 MIME 的类型这会通知客户端程序 (Web 浏览器和邮件包，例如)，它们将需要以不同方式处理的数据不是它们处理直接提供的文本。 例如，包含 JPEG 图的 Web 文档的标头包含特定于 JPEG 文件格式的 MIME 类型。 如果有的话，这允许浏览器以显示其 JPEG 查看器中，使用该文件。

## <a name="n-o"></a>N-O
 节点的分层树状结构中的元素。 节点可以是根或另一个节点的子级。 节点还可以是多个子级的父级。 另请参阅层次结构、 树、 根、 子、 父。

 包含对一个对象的引用的对象变量的变量。 例如，`objCustomObject`是指向类型 CustomObject 的对象的变量：`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC （开放式数据库连接） 的标准编程语言接口用于连接到各种数据源。 这通常是通过控制面板中，可分配的数据源名称 (Dsn) 以使用特定的 ODBC 驱动程序进行访问。

 将数据从各种源使用 com。 公开的接口的 OLE DB 的集 OLE DB 接口提供了在各种信息源中存储的数据进行统一访问的应用程序。 这些接口支持 DBMS 功能适用于数据源，使其能够共享其数据的量。 另请参阅 com。

 乐观锁定的锁定将在其中包含一个或多个记录，包括正在编辑的记录的数据页类型不能供其他用户仅在记录时正在更新通过**更新**方法，但不可用为调用之前和之后**更新**。

 使用乐观锁定时**记录集**与打开对象**LockType**参数或属性设置为**adLockOptimistic**或**adLockBatchOptimistic**。 请参阅悲观锁定。

 订单中的项的数字位置的序号值。 ADO 集合中的第一项的序数值为零 (0)。 下一项是一 （1），依次类推。

## <a name="p"></a>P
 参数化的命令的查询，也可以设置参数值之前执行此命令的命令。 例如，SQL 字符串也可以通过在 SQL 字符串中嵌入参数标记参数化 (通过指定？ 字符)。 然后，应用程序为每个参数指定值，并执行命令。

 父层次结构关系的控制端。 层次结构中父层次结构中具有一个或多个直接位于其下方的子节点。 另请参阅父别名、 父-子关系和子级。

 父别名指的是父级的别名。 请参阅参阅别名和父级。

 在该父级是一个级别更高版本并直接与一个或多个子级关联的层次结构中的父-子关系的关系。 子级是低一个级别，必须有一个父级。 另请参阅父级、 子级。

 包含一个或多个记录，包括正在编辑的记录的页面的保守式锁定的锁定在其中的类型不可向其他用户，以确保将进行了更新。 悲观锁定行为由 OLE DB 访问接口定义。 通常情况下，记录将被锁定时编辑并保持不可用状态，直到**更新**方法完成。

 已启用悲观锁定时**记录集**与打开对象**LockType**参数或属性设置为**adLockPessimistic**。 请参阅乐观锁定。

 共用一种性能优化基于使用的预先分配的资源，如对象或数据库连接的集合。 它是要创建新的资源相比，从池中提取现有的资源效率更高。

 由 COM 应用程序映射到 Windows 注册表 ProgID （编程标识符） 的唯一名称。 ADO 连接的 ProgID 是"ADODB。连接"。 另请参阅 CLSID，com。

 代理提供的参数封送处理的特定于接口的对象和客户端调用运行在不同的执行环境中，例如在另一个线程或另一个进程中的应用程序对象所需的通信。 代理位于与客户端，并与被调用的应用程序对象所在的相应存根进行通信。 另请参阅存根 （stub）。

## <a name="r"></a>R
 相对 URL 的部分限定的 Internet 或 intranet 的位置是相对于指定的绝对 URL 或等效的 ADO 连接对象的一个起始点指定的资源的 URL。 实际上，串联绝对和相对 Url consitute 是完整的 URL。 另请参阅 URL 和绝对 URL。

 远程数据源存在另一台计算机，而不是本地系统上 （其中客户端应用程序运行） 的数据源。

 资源记录中文档的源提供程序，其中包含定义文件和文件夹或文档的说明字段的记录。 文档本身不包含在资源记录，但通常可以通过默认流或包含 URL 的资源记录中的字段来访问。 另请参阅文档源提供程序，默认流，URL。

 数据源，全部具有相同的字段架构中的行的行集的组。 行集可以表示表中的所有或某些字段。 行集还可以表示的查询或联接的两个或多个表创建的虚拟表。 在 ADO 中，由行集**记录集**对象。

## <a name="s"></a>S
 范围限定为一个对象或变量引用的范围或一系列中的视图或表的记录。 例如，可以仅在其中定义的过程中引用本地变量。 公共变量是可从应用程序中的任意位置访问。 对象，如当前数据库中，处于范围内，如果它们在定义的搜索路径。 可以使用许多命令中的范围子句指定记录的范围。

 服务提供程序对服务进行生成和使用数据，封装并增加 ADO 应用程序中的功能的软件。 它不会直接公开数据的提供程序，而不是它提供了一种服务，如查询处理。 服务提供程序可以处理数据提供程序提供数据。 另请参阅数据访问接口。

 调整的记录集 A**记录集**已专门定义其列以包含不只是数据，但也引用 （称为章） 与其他**记录集**对象和/或计算的值基于其他**记录集**对象。

 同级层次结构中位于相同级别的层次结构中任何两个或多个节点。 层次结构中的根节点具有任何同级。

 存储的过程的预编译的代码，例如 SQL 语句和可选控制流语句用一个名称存储并作为一个单元处理的集合。 存储的过程存储在一个数据库;它们可以通过从应用程序一次调用执行，并且允许用户声明的变量、 条件执行和其他功能强大的编程功能。

 存根提供的参数封送处理的特定于接口的对象和所需的应用程序对象接收从客户端运行在不同的执行环境中，如另一个线程上或另一个进程中调用的通信。 存根 （stub） 位于与应用程序对象，并与调用它的客户端所在的相应代理进行通信。 另请参阅代理服务器。

 子节点，请参阅子级。

 同步操作由下一步操作之前完成的代码启动的操作可能会启动。 另请参阅异步操作。

## <a name="t-z"></a>T-Z
 树结构元素 （节点） 之间的分层关系。 树 （根） 的最高级别位于一个节点。 下方根目录中，可以有多个子级。 每个子又可以是其他的子级，因此成树状分支的父级。 包含文档和其他文件夹的文件夹是树状结构的典型示例。 另请参阅层次结构、 节点、 根、 子、 父。

 Web 服务器提供 Web 服务和页面到 intranet 和 Internet 用户的计算机。
