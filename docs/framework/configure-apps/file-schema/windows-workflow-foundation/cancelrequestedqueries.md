---
title: "&lt;cancelRequestedQueries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;cancelRequestedQueries&gt;
代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。  追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。  
  
 如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
## 語法  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
       </workflow>  
   </trackingProfile>  
</tracking>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<cancelRequestedQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|查詢，可用來追蹤由父活動取消子活動的要求。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<workflow\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|包括特定工作流程之所有查詢的組態項目，這個工作流程可由 **activityDefinitionId** 屬性識別。|  
  
## 請參閱  
 [System.ServiceModel.Activities.Tracking.Configuration.CancelRequestQueryElementCollection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.CancelRequestQueryElementCollection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.CancelRequestQuery](assetId:///System.Activities.Tracking.CancelRequestQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)