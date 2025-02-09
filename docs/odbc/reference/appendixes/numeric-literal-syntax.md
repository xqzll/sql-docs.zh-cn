---
title: 数字文本语法 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181287"
---
# <a name="numeric-literal-syntax"></a>数值语法
以下语法用于 ODBC 中的数字文本：  
  
 *numeric-literal* ::= *signed-numeric-literal &#124; unsigned-numeric-literal*  
  
 *signed-numeric-literal* ::= [*sign*] *unsigned-numeric-literal*  
  
 *unsigned-numeric-literal* ::= *exact-numeric-literal &#124; approximate-numeric-literal*  
  
 *exact-numeric-literal* ::= *unsigned-integer* [*period*[*unsigned-integer*]] *&#124;period unsigned-integer*  
  
 *sign* ::= *plus-sign &#124; minus-sign*  
  
 *approximate-numeric-literal* ::= *mantissa E exponent*  
  
 *mantissa* ::= *exact-numeric-literal*  
  
 *exponent* ::= *signed-integer*  
  
 *signed-integer* ::= [*sign*] *unsigned-integer*  
  
 *unsigned-integer* ::= *digit...*  
  
 *plus-sign* ::= *+*  
  
 *minus-sign* ::= -  
  
 *digit* ::= 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *段*:: =。
