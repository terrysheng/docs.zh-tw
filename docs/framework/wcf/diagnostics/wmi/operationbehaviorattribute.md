---
title: "OperationBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## 語法  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## 方法  
 OperationBehaviorAttribute 類別並未定義任何方法。  
  
## 屬性  
 OperationBehaviorAttribute 類別具有下列屬性：  
  
### AutoDisposeParameters  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 參數自動處置功能的狀態。  
  
### Impersonation  
 資料型別：字串  
  
 存取類型：唯讀  
  
 表示作業支援的呼叫端模擬等級。  
  
### ReleaseInstanceMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 表示在作業引動過程當中要回收物件的時機。  
  
### TransactionAutoComplete  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 表示未發生未處理的例外狀況時是否要自動認可目前的交易。  
  
### TransactionScopeRequired  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 表示作業是否需要交易。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.OperationBehaviorAttribute>