---
title: "使用 SqlDependency 來偵測變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 使用 SqlDependency 來偵測變更
您可以將 <xref:System.Data.SqlClient.SqlDependency> 物件與 <xref:System.Data.SqlClient.SqlCommand> 產生關聯，以便偵測查詢結果與原始擷取結果不同的時間。  此外，您也可以指派委派 \(Delegate\) 給 `OnChange` 事件，而此事件將在相關聯命令的結果變更時引發。  您必須先將 <xref:System.Data.SqlClient.SqlDependency> 與此命令產生關聯，然後再執行此命令。  <xref:System.Data.SqlClient.SqlDependency> 的 `HasChanges` 屬性也可用來判斷自從上次擷取資料以來，查詢結果是否已經變更。  
  
## 安全性考量  
 相依性基礎結構會仰賴呼叫 <xref:System.Data.SqlClient.SqlDependency.Start%2A> 時所開啟的 <xref:System.Data.SqlClient.SqlConnection>，以便接收指定命令之基礎資料已經變更的通知。  讓用戶端啟始呼叫 `SqlDependency.Start` 的功能是透過使用 <xref:System.Data.SqlClient.SqlClientPermission> 和程式碼存取安全性屬性來控制的。  如需詳細資訊，請參閱[啟用查詢通知](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)與[程式碼存取安全性和 ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)。  
  
### 範例  
 下列步驟將說明如何宣告相依性、執行命令，並在結果集變更時接收通知：  
  
1.  啟始伺服器的 `SqlDependency` 連接。  
  
2.  建立要連接至伺服器的 <xref:System.Data.SqlClient.SqlConnection> 和 <xref:System.Data.SqlClient.SqlCommand> 物件，並定義 Transact\-SQL 陳述式。  
  
3.  建立新的 `SqlDependency` 物件，或使用現有的物件，並將它繫結至 `SqlCommand` 物件。  如此便可在內部建立 <xref:System.Data.Sql.SqlNotificationRequest> 物件，並視需要將其繫結至命令物件。  此通知要求包含可唯一識別此 `SqlDependency` 物件的內部識別項。  此外，它也會啟動用戶端接聽程式 \(Listener\) \(如果尚未作用中的話\)。  
  
4.  訂閱 `SqlDependency` 物件之 `OnChange` 事件的事件處理常式。  
  
5.  使用 `SqlCommand` 物件的任何 `Execute` 方法來執行命令。  因為命令已繫結至通知物件，所以伺服器知道它必須產生通知，並且佇列資訊將指向相依性佇列。  
  
6.  停止伺服器的 `SqlDependency` 連接。  
  
 如果任何使用者隨後變更基礎資料，Microsoft SQL Server 就會偵測到針對此類變更暫止的通知存在，並發佈通知，而該通知可透過呼叫 `SqlDependency.Start` 所建立的基礎 `SqlConnection` 來進行處理並轉送給用戶端。  用戶端接聽程式會接收到無效訊息。  然後，用戶端接聽程式會找出相關聯的 `SqlDependency` 物件並引發 `OnChange` 事件。  
  
 下列程式碼片段會顯示您應該用來建立範例應用程式的設計模式。  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the refence in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## 請參閱  
 [SQL Server 中的查詢通知](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)