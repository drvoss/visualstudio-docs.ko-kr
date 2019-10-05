---
title: 옵션, 텍스트 편집기, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dc4d918f3eae9088e2b36b7bebbb69ce130e26d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674147"
---
# <a name="options-text-editor-c-intellisense"></a>옵션, 텍스트 편집기, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**IntelliSense** 속성 페이지를 사용하여 Visual C#용 IntelliSense의 동작에 영향을 주는 설정을 수정합니다. **도구** 메뉴에서 **옵션**을 클릭하고, **텍스트 편집기** 폴더에서 **C#** 을 클릭하고 나서, **IntelliSense**를 클릭하여 **IntelliSense** 속성 페이지에 액세스할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
 **IntelliSense** 속성 페이지에는 다음 속성이 포함되어 있습니다.  
  
## <a name="completion-lists"></a>완성 목록  
 **문자가 입력된 후 완성 목록 표시**  
 이 옵션을 선택하면 입력하기 시작할 때 IntelliSense에서 자동으로 완성 목록을 표시합니다. 이 옵션을 선택하지 않으면 IntelliSense 완성은 **IntelliSense** 메뉴를 선택하거나 CTRL+SPACE를 눌러 사용할 수 있습니다.  
  
 **완성 목록에 키워드 배치**  
 이 옵션을 선택하면 IntelliSense에서는 C# 키워드(예: [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690))를 완성 목록에 추가합니다.  
  
 **완성 목록에 코드 조각 배치**  
 이 옵션을 선택하면 IntelliSense에서는 C# 코드 조각의 별칭을 완성 목록에 추가합니다. 코드 조각 별칭이 키워드(예: [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690))와 같은 경우 키워드는 바로 가기로 대체됩니다. 자세한 내용은 [Visual C# 코드 조각](../../ide/visual-csharp-code-snippets.md)을 참조하세요.  
  
## <a name="selection-in-completion-lists"></a>완성 목록의 선택  
 **다음 문자를 입력하면 커밋됨:**  
 문자가 입력된 후 완성 목록에서 선택된 항목에 대해 IntelliSense 자동 완성을 실행하는 모든 문자를 지정합니다.  
  
 **스페이스바를 누르면 커밋됨**  
 완성 목록에서 선택된 항목에 대해 IntelliSense 자동 완성을 실행하기 위해 스페이스바를 누르는 작업을 포함하도록 지정합니다.  
  
 **단어를 모두 입력한 후 Enter 키를 누르면 새 줄 추가**  
 완성 목록에 입력할 모든 문자를 입력하고 나서 Enter 키를 누르면 새 줄이 자동으로 생성되고 커서가 새 줄로 이동하도록 지정합니다.  
  
 예를 들어 `else`를 입력하고 Enter 키를 누르면 편집기에 다음과 같이 표시됩니다.  
  
 `else`  
  
 `|`(커서 위치)  
  
 그러나 `el`만 입력하고 Enter 키를 누르면 편집기에 다음과 같이 표시됩니다.  
  
 `else|`(커서 위치)  
  
## <a name="intellisense-member-selection"></a>IntelliSense 멤버 선택  
 **가장 최근에 사용한 멤버 미리 선택**  
 이 옵션을 선택하면 IntelliSense에서는 IDE(통합 개발 환경)의 현재 세션 중에 개체 이름 자동 완성을 위해 팝업 [멤버 목록] 상자에서 최근에 선택한 멤버를 미리 선택합니다. 가장 최근에 사용한 멤버의 기록은 IDE의 각 세션 사이에서 지워집니다. 자세한 내용은 [가장 최근에 사용한 멤버를 위한 IntelliSense](../../misc/intellisense-for-most-recently-used-members.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML 문서 주석](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [IntelliSense 사용](../../ide/using-intellisense.md)
