---
title: sp_OAGetProperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAGetProperty_TSQL
- sp_OAGetProperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAGetProperty
ms.assetid: 240eeeb9-6d8b-4930-b912-1d273ca0ab38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6611998b8aa22242693ec5d44bf842671a777c98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65449724"
---
# <a name="spoagetproperty-transact-sql"></a>sp_OAGetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  获取 OLE 对象的属性值。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_OAGetProperty objecttoken , propertyname   
    [ , propertyvalue OUTPUT ]  
    [ , index...]   
```  
  
## <a name="arguments"></a>参数  
 *objecttoken*  
 通过使用先前创建的 OLE 对象的对象令牌**sp_OACreate**。  
  
 propertyname   
 要返回的 OLE 对象的属性名。  
  
 *propertyvalue* **输出**  
 返回的属性值。 如果指定此参数，则必须是相应数据类型的局部变量。  
  
 如果属性返回 OLE 对象， *propertyvalue*必须是数据类型的本地变量**int**。一个对象标记标记存储在本地变量，此对象令牌可用于其他 OLE 自动化存储过程。  
  
 如果属性返回单个值，指定的局部变量*propertyvalue*，返回属性值在本地变量中; 或者不指定*propertyvalue*，它将返回向客户端作为单列、 单行结果集的属性值。  
  
 如果此属性返回一个数组，如果*propertyvalue*指定，则设置为 NULL。  
  
 如果*propertyvalue*指定，但该属性不返回一个值，就会出错。 如果属性返回二维以上的数组，也将出现错误。  
  
 *index*  
 索引参数。 如果指定，*索引*必须是相应的数据类型的值。  
  
 有些属性包含参数。 这些属性称为索引化属性，相应的参数被称为索引参数。 一个属性可有多个索引参数。  
  
> [!NOTE]  
>  此存储过程的参数按位置（而不是按名称）指定。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或非零数字（失败），是由 OLE 自动化对象返回的 HRESULT 整数值。  
  
 有关 HRESULT 返回代码的详细信息，请参阅[OLE 自动化返回代码和错误信息](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)。  
  
## <a name="result-sets"></a>结果集  
 如果属性返回一维或二维数组，那么该数组将作为结果集返回给客户端：  
  
-   一维数组作为单行结果集返回给客户端，其中的列数与数组中的元素数相等。 换言之，该数组以列的形式返回。  
  
-   二维数组作为结果集返回给客户端，其中的列数与数组第一维中的元素数相同，行数与数组第二维中的元素数相同。 换言之，该数组以（列、行）的形式返回。  
  
 当属性返回值或方法返回值是一个数组， **sp_OAGetProperty**或**sp_OAMethod**结果集返回到客户端。 （方法输出参数不能是数组。这些过程可扫描数组中的所有数据值，以确定用于结果集中各列的相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型和数据长度。 对于某个特定的列，这些过程将使用显示该列中的所有数据值所需要的数据类型和长度。  
  
 如果一列中的所有数据值具有相同的数据类型，此数据类型将用于整个列。 当列中的数据值为其他数据类型时，将基于下表选择整个列的数据类型。  
  
||ssNoversion|FLOAT|money|DATETIME|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>备注  
 此外可以使用**sp_OAMethod**获取属性值。  
  
## <a name="permissions"></a>权限  
 要求的成员身份**sysadmin**固定服务器角色或直接在此存储过程的执行权限。 `Ole Automation Procedures` 必须配置**启用**若要使用相关的 OLE 自动化到任何系统过程。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-a-local-variable"></a>A. 使用局部变量  
 下面的示例获取`HostName`属性 (先前创建的**SQLServer**对象) 并将其存储在本地变量。  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAGetProperty @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END  
PRINT @property;  
```  
  
### <a name="b-using-a-result-set"></a>B. 使用结果集  
 下面的示例获取`HostName`属性 (先前创建的**SQLServer**对象)，并返回到客户端作为结果集。  
  
```  
EXEC @hr = sp_OAGetProperty @object, 'HostName';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>请参阅  
 [OLE 自动化存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE 自动化脚本示例](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
