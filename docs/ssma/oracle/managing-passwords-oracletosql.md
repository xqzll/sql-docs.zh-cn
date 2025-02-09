---
title: 管理密码 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: c6b99dfd27655894456a1b0957c8c42f31819e1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62795737"
---
# <a name="managing-passwords-oracletosql"></a>管理密码 (OracleToSQL)
本部分是如何确保数据库密码和导入或导出跨服务器的过程：  
  
1.  保护密码  
  
2.  导出或导入加密的密码  
  
## <a name="securing-password"></a>保护密码  
SSMA 允许你保护你的数据库的密码。  
  
使用以下过程来实现安全的连接：  
  
指定一个有效的密码，使用以下三种方法之一：  
  
1.  **清除文本：** 在密码节点的值属性中键入数据库密码。 服务器连接文件的脚本文件的服务器部分中的服务器定义节点下找到它。  
  
    密码以明文形式是不安全的。 因此，您将遇到以下警告消息中的控制台输出： *"服务器&lt;服务器 id&gt;密码是提供不安全的明文形式 SSMA 控制台应用程序提供了一个选项来保护通过加密的密码，请参阅-securepassword 选项 SSMA 帮助文件中的详细信息信息。*  
  
    **加密的密码：** 在这种情况下，指定的密码，在本地计算机中 ProtectedStorage.ssma 以加密形式存储。  
  
    -   **保护密码**  
  
        -   执行`SSMAforOracleConsole.exe`与`-securepassword`，并在命令行传递包含中的服务器定义部分的密码节点的连接或脚本文件的服务器添加开关。  
  
        -   在提示符下，要求用户输入数据库密码并确认它。  
  
            服务器定义 id 和其相应的加密的密码存储在本地计算机上的文件  
            
            示例 1：  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            示例 2：
            
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **删除加密的密码**  
  
        执行`SSMAforOracleConsole.exe`与`-securepassword`和`-remove`开关在命令行传递的服务器 id，以从本地计算机上存在受保护的存储文件中删除加密的密码。  
        
        例如：  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **列出其密码进行加密的服务器 Id**  
  
        执行`SSMAforOracleConsole.exe`与`-securepassword`和`-list`切换通过在命令行列出了其密码已加密的服务器 id。  
  
        例如：  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  在脚本或服务器连接文件中提及的明文密码将优先于受保护的文件中的加密密码。  
    > 2.  在服务器连接文件或脚本文件的服务器部分中存在没有密码时或者如果它不在固定在本地计算机上，控制台将提示您输入的密码。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>导出或导入加密的密码  
SSMA 控制台应用程序，可将加密的数据库密码在本地计算机上的文件中存在导出为受保护的文件，反之亦然。 它有助于使加密的密码机独立。 导出功能读取服务器 id 和密码从本地保护的存储，并将信息保存在加密文件。 提示用户为受保护的文件输入密码。 请确保输入的密码是 8 个字符长度或详细信息。 不同的计算机上，此受保护的文件是可移植的。 导入功能从受保护的文件读取服务器 id 和密码信息。 用户提示输入密码的受保护文件，并将信息追加到受保护的本地存储。  
  
例如：  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
例如：  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>请参阅  
[执行 SSMA 控制台 (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
