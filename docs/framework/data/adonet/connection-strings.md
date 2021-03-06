---
title: "ADO.NET 中的連接字串 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# ADO.NET 中的連接字串
.NET Framework 2.0 導入了使用連接字串的新功能，包括在連接字串產生器 \(Builder\) 類別 \(Class\) 中引入新的關鍵字，這麼做可在執行階段建立有效的連接字串。  
  
 連接字串 \(Connection String\) 包含可當做參數從資料提供者 \(Data Provider\) 傳遞至資料來源的初始化資訊。  此語法會因資料提供者而不同，而且連接字串會在嘗試開啟連接期間進行剖析。  語法錯誤會產生執行階段例外狀況 \(Exception\)，但其他錯誤只會發生在資料來源接收連接資訊之後。  經過驗證後，資料來源便可套用在連接字串中指定的選項並開啟連接。  
  
 連接字串的格式是分號分隔的索引鍵\/值參數組清單：  
  
 `keyword1=value; keyword2=value;`  
  
 關鍵字不區分大小寫，而且索引鍵\/值組之間的空格會被忽略。  不過，依照資料來源的不同，值可能會區分大小寫。  所有包含分號、單引號或雙引號的值，都必須用雙引號括住。  
  
 有效的連接字串語法隨提供者而異，且是從早期的 API \(如 ODBC\) 經過多年不斷發展而來的。  .NET Framework Data Provider for SQL Server \(SqlClient\) 納入了許多舊式語法項目，而且對一般連接字串語法通常都可接受。  連接字串語法項目經常會有同等效力的同義資料表 \(Synonym\)，但某些語法和拼字錯誤可能會導致問題。  例如，"`Integrated Security=true`" 有效，"`IntegratedSecurity=true`" 則會導致錯誤。  此外，在執行階段自未經驗證的使用者輸入所建構的連接字串可能會導致字串插入式攻擊，進而危及資料來源的安全性。  
  
 為了解決這些問題，ADO.NET 2.0 針對每個 .NET Framework 資料提供者導入新的連接字串產生器。  關鍵字會以屬性的方式公開 \(Expose\)，如此就可在將連接字串提交至資料來源之前先驗證字串語法。  
  
## 在本節中  
 [連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。  
  
 [連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 示範如何在組態檔中儲存及擷取連接字串。  
  
 [連接字串語法](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。  
  
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 示範的技術可保護用於連接至資料來源的資訊。  
  
## 請參閱  
 [連接資料來源](../../../../ocs/framework/data/adonet/connecting-to-a-data-source.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)