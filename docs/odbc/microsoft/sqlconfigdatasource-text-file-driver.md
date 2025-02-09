---
title: SQLConfigDataSource （文本文件驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1635538f69b313a73a24ab1531f8793c7d98741e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62665253"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource（文本文件驱动程序）
> [!NOTE]  
>  本主题提供了文本文件驱动程序特定信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 **SQLConfigDataSource**函数，用于添加、 修改或删除数据源动态使用下列关键字。  
  
|关键字|Description|  
|-------------|-----------------|  
|CHARACTERSET|对于文本驱动程序中，OEM 或 ANSI。|  
|COLNAMEHEADER|对于文本驱动程序，该值指示第一个记录的数据是否将指定的列名称。 TRUE 或 FALSE。|  
|DEFAULTDIR|所指定的路径的目录。|  
|DESCRIPTION|数据源中的数据说明。<br /><br /> 这将设置为相同的选项**说明**中设置的对话框。|  
|DRIVER|路径规范，以驱动程序 DLL。|  
|DRIVERID|驱动程序的一个整数 ID。 27 （文本）|  
|扩展插件|列出数据源上的文本文件的文件名称扩展。<br /><br /> 这将设置为相同的选项**扩展插件列表**中设置的对话框。|  
|FIL|文件类型的文本|  
|文件类型|文本驱动程序 （文本） 的文件类型。|  
|FORMAT|对于文本驱动程序，可以是 FIXEDLENGTH、 TABDELIMITED、 CSVDELIMITED （逗号分隔） 或 DELIMITED() （通过在括号中指定的特殊字符）。 特殊的字符是一个字符的长度，可以是字符、 十进制或十六进制格式。|  
|MAXSCANROWS|要设置基于现有数据的列的数据类型时进行扫描的行数。<br /><br /> 对于文本驱动程序，您可以输入介于 1 到 32767 之间要扫描; 的行数但是，值将始终默认为 25。 （限制以外的数字将返回错误。）<br /><br /> 这将设置为相同的选项**扫描的行数**中设置的对话框。|  
|READONLY|若要使文件只读的;如果为 FALSE，则若要使文件不是只读的。<br /><br /> 这将设置为相同的选项**Read Only**中设置的对话框。|
