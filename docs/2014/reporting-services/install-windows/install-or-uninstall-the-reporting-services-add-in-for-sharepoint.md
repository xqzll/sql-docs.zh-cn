---
title: 安装或卸载 Reporting Services 外接程序的 SharePoint （SharePoint 2010 和 SharePoint 2013） |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0da7d391c5dc564129f1504e2100a6c47dcb000b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108822"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>安装或卸载用于 SharePoint 的 Reporting Services 外接程序（SharePoint 2010 和 SharePoint 2013）
  在 SharePoint 服务器上运行用于 SharePoint 产品的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序安装包 (rsSharePoint.msi)，以在 SharePoint 部署中启用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。 这些功能包括 Power View、一个报表查看器 Web 部件、一个 URL 代理端点、一些内容类型和一些应用程序页，使用它们可以创建、查看及管理 SharePoint 站点上的报表、报表模型、数据源和其他报表服务器内容。 用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序是在 SharePoint 模式下运行的报表服务器的必需组件。 可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导或通过从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能包下载 rsSharePoint.msi 来安装此外接程序。 有关外接程序和下载页的版本列表，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **本主题内容：**  
  
-   [先决条件](#bkmk_prereq)  
  
-   [外接程序安装什么？](#bkmk_whatinstalled)  
  
-   [安装方法概述](#bkmk_3ways_to_install)  
  
-   [外接程序使用安装文件 rsSharePoint.msi 安装](#bkmk_install_rssharepoint)  
  
    -   [仅文件安装](#bkmk_files_only_installation)  
  
-   [如何删除 Reporting Services 外接程序](#bkmk_remove_addin)  
  
-   [如何从命令行修复 rssharepoint.msi](#bkmk_repair)  
  
-   [安装程序日志文件](#bkmk_logfiles)  
  
-   [升级](#bkmk_upgrade)  
  
-   [RsCustomAction.exe](#bkmk_rscustomaction)  
  
##  <a name="bkmk_prereq"></a> 先决条件  
 将报表服务器与 SharePoint 产品的实例集成需要若干步骤，安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序是其中的一步。 有关针对使用 SharePoint 模式全套要求的详细信息，请参阅 [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)。 有关安装和配置的详细信息[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，请参阅[安装 Reporting Services SharePoint 模式适用于 SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)。  
  
-   如果将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 与具有多个 Web 前端应用程序的 SharePoint 场集成，则将该外接程序安装到场中每台具有 Web 服务器前端的计算机上。 仅对将要用于访问报表服务器内容的 Web 前端执行此操作。  
  
-   若要安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，您必须是计算机上的管理员。 例如，如果要在命令提示符下运行 rsSharePoint.msi，应使用“以管理员身份运行”  选项用管理员权限打开命令提示符。  
  
-   若要安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，您必须是 SharePoint 场 Administrators 组的成员。  
  
-   您必须是网站集管理员才能激活 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成功能。  
  
-   有关的示例部署使用外接程序的关系图，请参阅[在 SharePoint 中的 SQL Server BI 功能的部署拓扑](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。  
  
##  <a name="bkmk_whatinstalled"></a> 外接程序安装执行哪些操作？  
 外接程序安装过程由两个阶段组成，完成标准安装时将自动完成这两个阶段：  
  
-   第一个阶段是将文件安装到适当的文件夹。 这些文件夹是 SharePoint 部署的标准文件夹。 要安装的文件之一是 rsCustomAction.exe。  
  
-   安装的第二个阶段是运行一组自定义操作以便向 SharePoint 注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件。 从 rsCustomAction.exe 运行这些自定义操作。 在整个两个安装阶段都完成后，该 exe 将被删除。 您可以运行“仅文件”  安装，在安装结束时不运行 rsCustomAction.exe 并且该文件将保留在驱动器上。  
  
## <a name="the-reporting-services-installation-order"></a>Reporting Services 安装顺序  
 外接程序可在安装 SharePoint 之前安装，也可在安装 SharePoint 之后安装。 此外接程序遵循 SharePoint 预部署标准，将文件安装到 SharePoint 安装所用的位置中。  
  
> [!NOTE]  
>  在安装 SharePoint 产品之前安装外接程序的好处是：当新的服务器添加到场后，SharePoint 场会配置并激活 Reporting Services 外接程序。  
  
 **SharePoint 2010**  
  
-   SharePoint 2010 产品准备工具安装 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 包括 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能所需的外接程序的新版本。  
  
     如果您运行 SharePoint 产品准备工具，仍需要安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。  
  
-   如果您是第一次安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本，则在运行 SharePoint 产品准备工具时，将会看到以下对话框，指示该准备工具未安装该外接程序的较旧版本，因为已检测到了较新版本。 这是预期行为  
  
     ![已安装 SSRS 外接程序。](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "已安装 SSRS 外接程序。")  
  
 **SharePoint 2013**  
  
 SharePoint 20103 产品准备工具的功能**不**安装[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用于 SharePoint 产品外接程序。  
  
##  <a name="bkmk_3ways_to_install"></a> 安装方法概述  
 使用以下两种方法之一可以安装用于 SharePoint 产品的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序：  
  
-   **安装向导：** ![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")的新增功能[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]外, 接程序可以安装通过[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安装向导。 在向导的“功能选择”  页上，选择“用于 SharePoint 产品的 Reporting Services 外接程序”  。  
  
-   **rsSharepoint.msi:** 外接程序可从安装介质直接安装或下载并安装。 rsSharepoint.msi 同时支持图形用户界面和命令行安装。 您必须以管理员权限来运行 .msi：首先使用提升权限打开命令提示符，然后从命令行运行 rsSharepoint.msi。 有关如何下载外接程序的详细信息，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。  
  
    > [!NOTE]  
    >  如果你将 **/q** 开关用于无提示命令行安装，将不显示最终用户许可协议。 对此软件的使用受到许可协议控制并且由您负责遵守该许可协议，而与安装方法无关。  
  
##  <a name="bkmk_install_rssharepoint"></a> 使用安装文件 rsSharePoint.msi 安装外接程序  
 本节介绍如何通过运行 .msi 安装向导或命令行安装，直接安装 rssharepoint.msi。 如果您使用 SQL Server 安装向导安装了该外接程序，则无需执行这些步骤。  
  
 您可以通过运行以下命令，看到命令行开关的完整列表：  
  
```  
Rssharepoint.msi /?  
```  
  
1.  下载安装程序 (`rsSharepoint.msi`) 为[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]外接程序。 有关如何下载外接程序的详细信息，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。  
  
2.  以管理员身份运行 `rsSharepoint.msi` 以启动安装向导。 向导将显示“欢迎”页、软件许可条款和注册信息页。 安装程序将在以下路径下创建文件夹，并将文件复制到该文件夹中：  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`  
  
     或  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`  
  
3.  在 SharePoint 管理中心配置报表服务器设置和功能激活。 . 有关安装和配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的详细信息，请参阅 [安装用于 SharePoint 2010 的 Reporting Services SharePoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)。  
  
###  <a name="bkmk_files_only_installation"></a> “仅文件”安装  
 若要安装文件但跳过自定义操作安装阶段，则可以从命令行中使用 SKIPCA 选项来运行 rssharepoint.msi：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行下面的命令：  
  
    ```  
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1  
    ```  
  
 安装用户界面将打开并正常运行，`rsCustomAction.exe` 文件将安装。 但是，该 .exe 将不会在安装结束时运行，并且在安装完成后 `rsCustomAction.exe` 将保留在计算机中。  
  
### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>使用两步骤安装解决安装问题或安装内容类型  
 如果安装期间出现错误或文档库设置中不显示 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 内容类型，可以从命令行分两个步骤运行安装程序：  
  
1.  使用管理员权限  打开命令提示符，根据前一节中所述运行仅文件安装。  
  
2.  运行自定义操作可执行文件：  
  
    1.  导航到包含文件 `rsCustomAction.exe` 的文件夹。 此文件通过外接程序的“仅文件”安装复制到您的计算机。 `rsCustomAction.exe` 中位于 **%temp%** 目录。 要导航到此文件，请从命令提示符键入以下信息：  
  
         **CD %temp%** 。  
  
         该文件应位于： **\Users\\<你的姓名\>\AppData\Local\Temp**  
  
    2.  键入下列命令。 完成该配置步骤需要几分钟时间。 在此过程中，将重新启动 W3SVC 服务。 在程序复制文件、注册组件和运行 SharePoint 产品配置向导时，将显示若干状态消息。  
  
        ```  
        rsCustomAction.exe /i  
        ```  
  
    3.  更改生效所需的时间可能因您的服务器环境而异。 您还可以运行 **iisreset** 以强制实施更快的更新。  
  
### <a name="quiet-installation-for-scripting"></a>用于脚本撰写的静默安装  
 你可以使用 /q 或 /quiet 开关，进行不显示任何对话框或警告的“静默”安装   。 如果您想要编写外接程序安装的脚本，静默安装将很有用。  
  
> [!NOTE]  
>  如果你将 **/q** 开关用于无提示命令行安装，将不显示最终用户许可协议。 对此软件的使用受到许可协议控制并且由您负责遵守该许可协议，而与安装方法无关。  
  
 执行静默安装：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行下面的命令：  
  
    ```  
    Msiexec.exe /i rsSharePoint.msi /q  
    ```  
  
##  <a name="bkmk_remove_addin"></a> 如何删除 Reporting Services 外接程序  
 可以从 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows 控制面板或命令行卸载用于 SharePoint 产品的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 外接程序。  
  
1.  使用控制面板将在当前计算机上完全卸载文件， **并且** 将从 SharePoint 场中删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能。 删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能后，您将不再能查看和更新报表。  
  
2.  使用命令行方法卸载外接程序时，您可以使用 LocalOnly 参数仅从本地计算机删除外接程序文件，场中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能将保持不变。  
  
 卸载外接程序会删除用于在报表服务器上处理报表的服务器集成功能。 它还将从 SharePoint 管理中心删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 页和其他自定义 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 页。 您可能还想删除在受影响的 SharePoint 站点上不再使用的所有报表和其他报表服务器项。 在删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序后，它们不会再运行。  
  
 若要卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，必须使 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 安装仍处于运行状态。 如果先卸载 SharePoint 2010，则必须重新安装该产品才能卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序。  
  
 卸载外接程序的步骤与卸载独立服务器和服务器场的步骤相同。 安装程序将删除在安装过程中添加的程序文件和所有配置设置。  
  
 卸载外接程序将不删除以下内容：  
  
-   为用于访问 SharePoint 配置和内容数据库的报表服务器服务帐户创建的登录名。 必须从用于承载 SharePoint 数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中删除报表服务器服务帐户的所有登录名。  
  
-   为报表用户创建的权限或组。 如果创建了自定义权限级别或 SharePoint 组来授予访问报表服务器功能的权限，则应撤销不再需要的任何权限。  
  
-   上载到 SharePoint 库的数据文件，包括报表定义 (.rdl)、共享数据源 (.rsds) 和已发布报表项 (.rsc) 文件。 不会删除这些文件，但它们将不再运行。 必须手动删除这些文件。  
  
-   安装程序将不删除报表服务器数据库，也不修改用于集成操作的报表服务器实例。  
  
### <a name="to-uninstall-from-windows-control-panel"></a>从 Windows 控制面板卸载  
 从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 控制面板启动向导并删除外接程序：  
  
1.  在控制面板的 **“程序”** 中，选择 **“卸载程序”** 。  
  
2.  选择“用于 SharePoint 的 Microsoft SQL Server RS 外接程序”  。 还可以从命令提示符运行不带开关的 **rssharepoint.msi** 来启动卸载向导。  
  
3.  单击 **“删除”** 。  
  
### <a name="uninstall-from-the-command-line"></a>从命令行卸载  
 从命令行卸载外接程序：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行以下命令：  
  
    ```  
    msiexec.exe /uninstall rsSharePoint.msi  
    ```  
  
3.  您将看到一个确认消息框。 单击 **“是”** 。  
  
### <a name="uninstall-the-add-in-from-the-local-server-only"></a>仅从本地服务器卸载外接程序  
 卸载外接程序的以前方法会从场中删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能和对象。 如果具有多服务器场且只想从本地计算机卸载外接程序而使 SharePoint 场正常工作，请执行以下步骤：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行下面的命令：  
  
    ```  
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1  
    ```  
  
 这将从 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件并且删除文件，但仅限本地计算机。  
  
 如果您想要从 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能，但在磁盘上保留这些文件以供以后使用，请执行以下步骤：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行下面的命令：  
  
    ```  
    rsCustomAction.exe /p  
    ```  
  
 上述步骤假定您使用 SkipCA=1 完成了 .msi 安装并且 rscusstomaction.exe 可用。 有关详细信息，请参阅描述仅文件安装的部分。  
  
##  <a name="bkmk_repair"></a> 如何从命令行修复 rssharepoint.msi  
 若要使用命令行修复或卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，请执行以下步骤：  
  
1.  使用 **管理员权限**打开命令提示符。  
  
2.  运行下面的命令：  
  
    ```  
    msiexec.exe /f rssharepoint.msi  
    ```  
  
##  <a name="bkmk_logfiles"></a> 安装日志文件  
 安装程序在运行期间，会为安装 **外接程序的用户将相应信息记录到** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件夹下的一个日志文件中。 例如，**c:\Users\\<用户名\>\AppData\Local\Temp**。此文件名为 **RS_SP_\<number>.log**，例如，**RS_SP_0.log**。 日志中的每个错误都以字符串“SSRSCustomActionError”开头。  
  
> [!NOTE]  
>  AppData 是 Windows 操作系统中隐藏的文件夹。 您可能需要修改您的 Windows 资源管理器的文件夹设置，以便可以看到隐藏的文件和文件夹。  
  
#### <a name="view-a-log-file-with-windows-notepad"></a>使用 Windows 记事本查看日志文件  
  
1.  下面的命令将更改命令提示符路径，列出 rs 日志文件，然后使用 Windows 记事本打开这些文件之一：  
  
    ```  
    cd %temp%  
    ```  
  
    ```  
    Dir rs_sp*.log  
    ```  
  
    ```  
    notepad rs_sp_3.log  
    ```  
  
#### <a name="view-a-log-file-with-powershell"></a>使用 PowerShell 查看日志文件  
  
1.  从 SharePoint Management Shell 键入以下命令，以便从该文件中返回包含“ssrscustomactionerror”的行的筛选后列表：  
  
    ```  
    Get-content -path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
    ```  
  
2.  输出将类似于以下内容：  
  
     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`。  
  
##  <a name="bkmk_upgrade"></a> 升级  
 如果具有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序的现有安装，则可以升级到当前版本。 外接程序安装程序将检测现有版本并提示您确认是否更新。 将显示如下的消息：  
  
 在你的系统上检测到此产品的较低版本。  是否要升级现有安装？  
  
 如果确认更新，则旧版本的外接程序将被删除，然后安装新版本。  
  
 请注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序不能识别实例。 一台计算机上只能有一个外接程序实例。 不能并行运行不同版本和当前版本。  
  
##  <a name="bkmk_rscustomaction"></a> RsCustomAction.exe  
 下表概述了 rscustomaction.exe 的各个开关：  
  
|开关|Description|  
|------------|-----------------|  
|i|安装自定义操作。 这将在 SharePoint 中注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件。 并且将重新启动 W3SVCservice。|  
|r|Repair|  
|u|卸载。 这将从整个 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件，但在磁盘上保留文件。 并且将重新启动 W3SVCservice。|  
|p|本地卸载。 这将仅从本地计算机撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件。 文件将保留在磁盘上。 并且将重新启动 W3SVCservice。|  
|t|仅限 SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005。 此开关测试报表服务器与报表服务器数据库之间是否具有有效的连接。|  
  
## <a name="configuring-reporting-services"></a>配置 Reporting Services  
 在所有所需计算机上都安装了外接程序之后，您需要从 SharePoint 管理中心来配置报表服务器。 所需步骤取决于安装不同技术的顺序。 有关详细信息，请参阅[安装 Reporting Services SharePoint 模式适用于 SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)并[Reporting Services 报表服务器&#40;SharePoint 模式&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
  
## <a name="see-also"></a>请参阅  
 [安装用于 SharePoint 2010 的 Reporting Services SharePoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)   
 [Reporting Services 报表服务器（SharePoint 模式）](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
  
  
