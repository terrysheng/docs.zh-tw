---
title: Expression Trees
description: Expression Trees
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6ec60b6cdbe29def719f7970dad15fad65902e7
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---

# <a name="expression-trees"></a>Expression Trees

如果您使用過 LINQ，您會有豐富的程式庫使用經驗，其中 `Func` 類型是 API 集合的一部分 (如果您不熟悉 LINQ，則可能需要閱讀 [LINQ 教學課程](linq/index.md)及有關 [Lambda 運算式](lambda-expressions.md)的教學課程，再開始進行本主題)。「運算式樹狀架構」提供與函式引數更豐富的互動。

當您建立 LINQ 查詢時，通常會使用 Lambda 運算式來撰寫函式引數。 在一般 LINQ 查詢中，這些函式引數會轉換成編譯器所建立的委派。 

當您想要有更豐富的互動時，您必須使用「運算式樹狀架構」。
運算式樹狀架構會以您可以查看、修改或執行的結構來表示程式碼。 這些工具可讓您在執行階段操作程式碼。 您可以撰寫程式碼來查看執行中的演算法，或插入新功能。 在更進階的案例中，您可以修改執行中的演算法，甚至將 C# 運算式轉譯為其他格式，以便在其他環境中執行。

您可能已撰寫使用運算式樹狀架構的程式碼。 Entity Framework 的 LINQ API 接受運算式樹狀架構作為 LINQ 查詢運算式模式的引數。
這可讓 [Entity Framework](http://docs.efproject.net/en/latest/) 將以 C# 撰寫的查詢，轉譯為在資料庫引擎中執行的 SQL。 另一個範例是 [Moq](https://github.com/Moq/moq)，這是 .NET 的熱門模擬架構。

本教學課程的其餘章節會探索運算式樹狀架構為何、查看支援運算式樹狀架構的架構類別，並示範如何使用運算式樹狀架構。 您將了解如何讀取運算式樹狀架構、如何建立運算式樹狀架構、如何建立修改後的運算式樹狀架構，以及如何執行由運算式樹狀架構表示的程式碼。 閱讀完後，您將能夠使用這些結構來建立豐富彈性的演算法。
<style type="text/css"> ol { list-style-type: upper-roman; } </style>
1. [說明運算式樹狀架構](expression-trees-explained.md)

    Understand the structure and concepts behind *Expression Trees*.
    
2. [支援運算式樹狀架構的架構類型](expression-classes.md)
    
    了解定義及操作運算式樹狀架構的結構和類別。
    
3. [執行運算式](expression-trees-execution.md)

    了解如何將以 Lambda 運算式表示的運算式樹狀架構轉換成委派，再執行所產生的委派。

4. [解譯運算式](expression-trees-interpreting.md)

    了解如何周遊及查看「運算式樹狀架構」，以了解運算式樹狀架構所表示的程式碼。

5. [建置運算式](expression-trees-building.md)

    了解如何建構運算式樹狀架構的節點，並建立運算式樹狀架構。

6. [轉譯運算式](expression-trees-translating.md)

    了解如何建立修改後的運算式樹狀架構複本，或將運算式樹狀架構轉譯為其他格式。

7. [總結](expression-trees-summary.md)

    檢閱運算式樹狀架構的相關資訊。
    

