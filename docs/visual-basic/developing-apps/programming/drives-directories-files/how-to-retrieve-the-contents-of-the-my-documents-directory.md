---
title: "如何：在 Visual Basic 中擷取 [我的文件] 目錄的內容 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 39e1d8b4d7e613bf245769816ef24a7787f41e04
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>如何：在 Visual Basic 中擷取我的文件目錄的內容
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> 物件可以用來讀取許多 [所有使用者] 目錄，例如 [我的文件] 或 [桌面]。  
  
### <a name="to-read-from-the-my-documents-folder"></a>讀取 [我的文件] 資料夾  
  
-   使用 `ReadAllText` 方法，讀取特定目錄中每個檔案的文字。 下列程式碼指定目錄和檔案，然後使用 `ReadAllText` 將它們讀入名為 `patients` 的字串。  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
