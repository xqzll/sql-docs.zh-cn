---
title: 不受支持的 Visual FoxPro 命令和函数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], commands and functions
- functions [ODBC], Visual FoxPro
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro commands and functions
- FoxPro ODBC driver
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6b69c8bf15b4d56872c4030725638e4b61571e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633367"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>不支持的 Visual FoxPro 命令和函数（Visual FoxPro ODBC 驱动程序）
下表列出了 FoxPro 命令和函数，不受 Visual FoxPro ODBC 驱动程序，但支持的 Microsoft® Visual FoxPro®。  
  
 如果应用程序与数据交互的规则、 触发器、 默认值，或存储的过程调用这些 Visual FoxPro 命令或函数，该驱动程序可以生成一个错误。  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>不受支持的 Visual FoxPro 命令和函数  
  
||||  
|-|-|-|  
|#DEFINE...#UNDEF|#IF...#ENDIF 预处理器指令|#IFDEF &#124; #IFNDEF|  
|#INCLUDE 预处理器指令|::范围解析运算符|! 命令 (请参阅运行&#124;！ 命令中）|  
|? &#124; ?? Command|??? Command|\ &#124; \\\ 命令|  
|@ ...框命令|@ ...类命令|@ ...清除命令|  
|@ ...编辑-编辑框命令|@ ...填充命令|@ ...GET|  
|@ ...菜单命令|@ ...提示命令|@ ...说出命令|  
|@ ...滚动命令|@ ...若要命令||  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|接受命令|用于类 （） 函数|激活菜单命令|  
|激活弹出菜单命令|激活屏幕命令|激活窗口命令|  
|ActivateCell 方法|添加类命令|ADIR （） 函数|  
|AFONT （） 函数|AINSTANCE （） 函数|可系统内存变量|  
|AMEMBERS （） 函数|ANSITOOEM （） 函数|APRINTERS （） 函数|  
|ASELOBJ( ) Function|帮助命令||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|栏 （） 函数|BARCOUNT （） 函数|BARPROMPT （） 函数|  
|_BEAUTIFY 系统内存变量|_BOX 系统内存变量|浏览命令|  
|_BROWSER 系统内存变量|生成的应用程序命令|生成的 EXE 命令|  
|生成项目命令|_BUILDER 系统内存变量||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|_CALCVALUE 系统内存变量|_CLIPTEXT 系统内存变量|_CONVERTER 系统内存变量|  
|_CUROBJ 系统内存变量|调用命令|取消命令|  
|CAPSLOCK （） 函数|CD 命令|更改命令|  
|CHDIR 命令|CHRSAW （） 函数|关闭备注命令|  
|CNTBAR （） 函数|CNTPAD （） 函数|列号 （） 函数|  
|编译命令|编译数据库命令|编译窗体命令|  
|COMPOBJ( ) Function|容器对象|控件对象|  
|复制文件命令|复制备注命令|创建类的命令|  
|创建 CLASSLIB 命令|创建颜色 SET 命令|创建命令|  
|创建连接的命令|创建数据库的命令|创建窗体的命令|  
|从命令创建|创建标签命令|创建菜单命令|  
|创建项目命令|创建查询命令|创建报表的命令|  
|创建屏幕命令|创建视图的 SQL 命令|创建触发器命令|  
|创建视图命令|CREATEOBJECT （） 函数|CURDIR （） 函数|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|_DBLCLICK 系统内存变量|_DIARYDATE 系统内存变量|DBSETPROP( ) Function|  
|DDE 函数|停用菜单命令|停用弹出项命令|  
|停用窗口命令|声明的 DLL 命令|声明命令|  
|定义命令栏|定义框命令|定义类命令|  
|定义菜单命令|定义板命令|定义弹出窗口命令|  
|定义窗口命令|删除连接命令|删除数据库命令|  
|删除文件命令|删除触发器命令|删除视图命令|  
|DIR 命令|目录命令|显示命令|  
|显示连接命令|显示数据库命令|显示的 DLL 命令|  
|显示文件命令|显示内存命令|显示对象命令|  
|显示过程命令|显示状态命令|显示结构命令|  
|显示表命令|显示视图命令|窗体命令|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|编辑命令|错误命令||  
|清除命令|外部命令|导出命令|  
|弹出命令|弹出页命令||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|_FOXDOC 系统内存变量|_FOXGRAPH 系统内存变量|FEOF （） 函数|  
|FCLOSE （） 函数|FCREATE （） 函数|FGETS （） 函数|  
|FERROR( ) Function|FFLUSH （） 函数|FKLABEL （） 函数|  
|文件管理器命令|查找命令|FOPEN （） 函数|  
|FKMAX （） 函数|FONTMETRIC （） 函数|FSEEK （） 函数|  
|FPUTS （） 函数|FREAD （） 函数||  
|FWRITE （） 函数|FCHSIZE （） 函数||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|_GENGRAPH 系统内存变量|_GENMENU 系统内存变量|_GENPD 系统内存变量|  
|_GENSCRN 系统内存变量|_GENXTAB 系统内存变量|GETBAR （） 函数|  
|GETCOLOR （） 函数|GETDIR （） 函数|GETEXPR 命令|  
|GETFILE （） 函数|GETFONT （） 函数|GETOBJECT （） 函数|  
|GETPAD （） 函数|GETPICT （） 函数|GETPRINTER （） 函数|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|帮助命令|隐藏菜单命令|隐藏弹出项命令|  
|隐藏窗口命令|家庭 （） 函数||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS （） 函数|导入命令|输入的命令|  
|对命令的索引|INKEY （） 函数|ISCOLOR （） 函数|  
|插入命令|INSMODE （） 函数||  
|ISMOUSE （） 函数|（_i） 系统内存变量||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|加入命令|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|键盘命令|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|_LMARGIN 系统内存变量|标签命令|LASTKEY （） 函数|  
|LINENO （） 函数|列表命令|列出连接命令|  
|装载命令|LOCFILE （） 函数||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL （） 函数|MD 命令|菜单命令|  
|内存 （） 函数|菜单命令|MKDIR 命令|  
|菜单 （） 函数|MESSAGEBOX （） 函数|修改连接命令|  
|修改类命令|修改命令的命令|修改窗体命令|  
|修改数据库命令|修改文件命令|修改备注命令|  
|修改常规命令|修改标签命令|修改项目命令|  
|修改的菜单命令|修改过程命令|修改屏幕命令|  
|修改查询命令|修改报表命令|修改窗口命令|  
|修改结构命令|修改视图命令|移动窗口命令|  
|鼠标命令|移动弹出窗口命令|MROW （） 函数|  
|MRKBAR （） 函数|MRKPAD （） 函数||  
|MWINDOW （） 函数|MDOWN （） 函数||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NUMLOCK （） 函数|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM （） 函数|OBJTOCLIENT （） 函数|ON 命令栏|  
|OEMTOANSI （） 函数|APLABOUT 命令|ON 退出菜单命令|  
|转义命令|在上栏退出命令|在键 = 命令|  
|ON 退出板命令|ON 退出弹出项命令|ON 板命令|  
|有关密钥的标签命令|MACHELP 命令|在所选内容栏命令|  
|页面命令|READERROR 命令|选择弹出窗口命令|  
|选择菜单命令|在所选内容填充命令||  
|关闭命令|OBJVAR （） 函数||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|_PADVANCE 系统内存变量|_PAGENO 系统内存变量|_PBPAGE 系统内存变量|  
|_PCOLNO 系统内存变量|_PCOPIES 系统内存变量|_PDRIVER 系统内存变量|  
|_PDSETUP 系统内存变量|_PECODE 系统内存变量|_PEJECT 系统内存变量|  
|_PEPAGE 系统内存变量|_PLENGTH 系统内存变量|_PLINENO 系统内存变量|  
|_PLOFFSET 系统内存变量|_PPITCH 系统内存变量|_PQUALITY 系统内存变量|  
|_PRETEXT 系统内存变量|_PSCODE 系统内存变量|_PSPACING 系统内存变量|  
|_PWAIT 系统内存变量|PACK 数据库命令|板 （） 函数|  
|PCOL （） 函数|PEMSTATUS （） 函数|播放宏命令|  
|弹出项命令|弹出菜单命令|POP 弹出项命令|  
|弹出窗口 （） 函数|打印作业...ENDPRINTJOB 命令|PRINTSTATUS （） 函数|  
|PRMBAR （） 函数|PRMPAD （） 函数|提示 （） 函数|  
|PROW （） 函数|PRTINFO （） 函数|推送键命令|  
|推送菜单命令|推送弹出项命令|PUTFILE （） 函数|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|QUIT 命令|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|_RMARGIN 系统内存变量|远程桌面命令|READKEY （） 函数|  
|读取命令|读取菜单命令|发布栏命令|  
|REFRESH() 函数|重新索引命令|发布库命令|  
|发布 CLASSLIB 命令|发布命令|发布面板命令|  
|发布菜单命令|发布模块命令|发布 WINDOWS 命令|  
|发布弹出项命令|发布过程命令|重命名命令|  
|删除类命令|重命名类命令|重命名视图命令|  
|重命名连接命令|重命名表命令|从命令还原|  
|报表命令|再次查询 （） 函数|还原窗口命令|  
|还原宏命令|还原屏幕命令|RGBSCHEME （） 函数|  
|RESUME 命令|RGB （） 函数|RUN &#124; ! Command|  
|RMDIR 命令|ROW （） 函数||  
|RUNSCRIPT 命令|RDLEVEL （） 函数||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|将宏命令保存|保存屏幕命令|将保存到命令|  
|保存 WINDOWS 命令|方案 （） 函数|SCOLS （） 函数|  
|滚动命令|_SCREEN 系统内存变量|SET 命令|  
|设置备用命令|SET ANSI 命令|SET APLABOUT 命令|  
|设置自动保存命令|SET 钟形命令|设置闪烁命令|  
|设置边框命令|SET BRSTATUS 命令|SET CLASSLIB 命令|  
|SET 清除命令|设置时钟命令|设置颜色的命令|  
|设置颜色的方案命令|设置颜色集命令|设置颜色以命令|  
|设置兼容命令|设置确认命令|设置控制台命令|  
|集 CPCOMPILE|集 CPDIALOG|设置货币命令|  
|设置游标命令|SET DATASESSION 命令|设置调试命令|  
|SET 小数命令|组分隔符命令|设置开发命令|  
|设置设备命令|设置显示命令|SET DOHISTORY 命令|  
|SET 回显命令|设置转义命令|设置格式命令|  
|SET 函数命令|设置标题命令|设置帮助命令|  
|SET HELPFILTER 命令|设置强度命令|设置项命令|  
|SET KEYCOMP 命令|SET LOGERRORS 命令|SET MACDESKTOP 命令|  
|SET MACHELP 命令|SET MACKEY 命令|设置边距命令|  
|设置标记的命令|设置标记以命令|SET MEMOWIDTH 命令|  
|设置消息命令|设置鼠标命令|SET 里程表命令|  
|SET OLEOBJECT 命令|SET 调色板命令|SET PDSETUP 命令|  
|设置点命令|设置打印机命令|SET READBORDER 命令|  
|设置刷新命令|设置资源命令|设置安全命令|  
|设置计分板命令|SET 秒命令|组分隔符命令|  
|设置阴影命令|组跳过的命令|SET 空间命令|  
|设置状态命令|设置状态栏命令|设置步骤命令|  
|SET 粘滞命令|SET SYSFORMATS 命令|SET SYSMENU 命令|  
|SET 对话命令|SET TEXTMERGE 命令|SET TEXTMERGE 分隔符命令|  
|SET 主题命令|SET 主题 ID 命令|SET TRBETWEEN 命令|  
|SET TYPEAHEAD 命令|设置视图命令|设置窗口中的备注命令|  
|SET XCMDFILE 命令|_SHELL 系统内存变量|显示 GET 命令|  
|显示获取命令|显示菜单命令|显示对象命令|  
|显示弹出项命令|显示窗口命令|弹出窗口大小命令|  
|大小窗口命令|SKPBAR （） 函数|SKPPAD （） 函数|  
|SOUNDEX （） 函数|_SPELLCHK 系统内存变量|SQL 函数|  
|SROWS （） 函数|_STARTUP 系统内存变量|暂停命令|  
|除 SYS(2011) SYS() 函数|SYSMETRIC （） 函数||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TABS 系统内存变量|文本...ENDTEXT 命令|TXTWIDTH （） 函数|  
|转换 （） 函数|_TRANSPORT 系统内存变量||  
|TYPE 命令|_THROTTLE 系统内存变量||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|更新 （） 函数|使用命令||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|验证数据库命令|VARREAD （） 函数|版本 （） 函数|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|（_w） 系统内存变量|_WIZARD 系统内存变量|WCHILD （） 函数|  
|等待命令|WBORDER （） 函数|WFONT （） 函数|  
|WCOLS （） 函数|WEXIST （） 函数|WLROW （） 函数|  
|使用...ENDWITH 命令|WLAST （） 函数|WONTOP （） 函数|  
|WMAXIMUM （） 函数|WLCOL （） 函数|WREAD （） 函数|  
|WOUTPUT （） 函数|WMINIMUM （） 函数|WVISIBLE （） 函数|  
|WPARENT （） 函数|WTITLE （） 函数||  
|WROWS （） 函数|_WRAP 系统内存变量||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|缩放窗口命令|||
