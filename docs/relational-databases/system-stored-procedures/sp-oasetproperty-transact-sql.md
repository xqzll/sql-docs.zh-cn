---
title: sp_OASetProperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2d3cc319a99c9e1b157e5b6bc06cabea2dd19a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65450064"
---
# <a name="spoasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  将 OLE 对象的属性设置为新值。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>参数  
 *objecttoken*  
 以前创建的 OLE 对象的对象令牌**sp_OACreate**。  
  
 propertyname   
 要设置新值的 OLE 对象的属性名。  
  
 *newvalue*  
 属性的新值，并且必须是适当数据类型的值。  
  
 *index*  
 索引参数。 如果指定，*索引*必须是相应的数据类型的值。  
  
 有些属性包含参数。 这些属性称为索引化属性，相应的参数被称为索引参数。 一个属性可有多个索引参数。  
  
> [!NOTE]  
>  此存储过程的参数按位置（而不是按名称）指定。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或非零数字（失败），是由 OLE 自动化对象返回的 HRESULT 整数值。  
  
 有关 HRESULT 返回代码的详细信息，请参阅[OLE 自动化返回代码和错误信息](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)。  
  
## <a name="permissions"></a>权限  
 要求的成员身份**sysadmin**固定服务器角色或直接在此存储过程的执行权限。 `Ole Automation Procedures` 必须配置**启用**若要使用相关的 OLE 自动化到任何系统过程。  
  
## <a name="examples"></a>示例  
 下面的示例设置`HostName`属性 (先前创建的**SQLServer**对象) 为新值。  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>请参阅  
 [OLE 自动化存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE 自动化脚本示例](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
