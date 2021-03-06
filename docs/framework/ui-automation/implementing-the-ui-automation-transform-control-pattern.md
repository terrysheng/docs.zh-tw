---
title: "Implementing the UI Automation Transform Control Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control patterns, Transform"
  - "Transform control pattern"
  - "UI Automation, Transform control pattern"
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: 14
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 14
---
# Implementing the UI Automation Transform Control Pattern
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題簡介實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 的方針和慣例，包括屬性、方法和事件的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.TransformPattern> 控制項模式用來支援可在二維空間內移動、調整大小或旋轉的控制項。 如需實作此控制項模式的控制項範例，請參閱[Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 實作方針和慣例  
 實作轉換控制項模式時，請注意下列方針和慣例：  
  
-   此控制項模式的支援不限於桌面上的物件。 若容器物件的子項可以自由在容器的範圍內移動、調整大小或旋轉，則這些子項也必須支援此控制項模式。  
  
-   如果物件最後在螢幕上的位置完全在其容器的座標以外，而鍵盤或滑鼠存取不到的話，就無法移動、調整大小或旋轉物件 \(例如，最上層的視窗移離螢幕，或是子物件移到容器檢視區範圍以外的地方\)。 在這種情況下，物件會放置到最接近所要求螢幕座標的地方，其上方或左方座標會覆寫成容器範圍內的座標。  
  
-   針對多監視器系統，若物件移動、調整大小或旋轉後的位置完全超出合併桌面螢幕座標的範圍，物件就會移至主要監視器上最接近所要求座標的位置。  
  
-   所有參數和屬性值都是絕對值，不受地區設定影響。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## ITransformProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 的必要屬性和方法。  
  
|必要成員|成員類型|備註|  
|----------|----------|--------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|方法|無|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|方法|無|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|方法|無|  
  
 此控制項模式沒有任何相關聯的事件。  
  
<a name="Exceptions"></a>   
## 例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|------------|--------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -   如果 <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> 為 false。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -   如果 <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> 為 false。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -   如果 <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> 為 false。|  
  
## 請參閱  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)