---
title: 옵션, 텍스트 편집기, C-C++, 실험적 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297850"
---
# <a name="options-text-editor-cc-experimental"></a>옵션, 텍스트 편집기, C/C++, 실험적
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이러한 옵션을 변경하면 C 또는 C++에서 프로그래밍할 때 IntelliSense 및 검색 데이터베이스 관련 동작을 변경할 수 있습니다.

 이 페이지에 액세스하려면 왼쪽 창의 **옵션** 대화 상자에서 **텍스트 편집기**를 확장하고 **C/C++** 를 확장한 다음 **실험적**을 선택합니다.

 이러한 기능은 Visual Studio 2015 업데이트 1 RC 설치에서 사용할 수 있습니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.

## <a name="browsingnavigation"></a>검색/탐색
 **Enable New Database Engine** This should automatically speed up database population and make all database operations faster (with no loss in accuracy) for operations such as **Go To Definition** and **Find All References**. 변경 내용을 적용하려면 솔루션을 닫았다가 다시 열면 됩니다. Visual Studio를 다시 시작할 필요가 없습니다.

## <a name="intellisense"></a>IntelliSense
 **Member List Dot-To-Arrow** Replaces '.' with '->' when applicable for Member List.

## <a name="refactoring"></a>Refactoring
 **Enable Extract Function** Extract selected code to its own function and replace code with a call to the new function. 이 기능에 액세스하려면 선택한 코드를 마우스 오른쪽 단추로 클릭하고 **빠른 작업**을 선택하거나, 간단히 기본 바로 가기인 Ctrl+.[Ctrl+점]을 누릅니다.

 **Enable Change Signature** Add, reorder, and delete parameters of a function and propagate the changes to all call sites. 이 기능에 액세스하려면 모든 함수 사용을 마우스 오른쪽 단추로 클릭하고 **빠른 작업**을 선택하거나, 간단히 기본 바로 가기 Ctrl+.[Ctrl+점]을 누릅니다.

## <a name="text-editor"></a>텍스트 편집기
 **Enable Expand Scopes** If enabled, you can surround selected text with curly braces by typing '{' into the text editor.

 **Enable Expand Precedence** If enabled, you can surround selected text with parentheses by typing '(' into the text editor.

 Visual Studio 갤러리의 추가 텍스트 편집기 기능은 [여기](https://go.microsoft.com/fwlink/?LinkId=692016)에서 목록을 참조하세요. 예제는 [C++ 빠른 조치 방법](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)(영문)이며, 다음을 지원합니다.

- **누락된 #include 추가** - 코드의 알 수 없는 기호에 대해 관련 #include를 제안합니다.

- **네임스페이스/정규화 기호를 사용하여 추가** - 네임스페이스를 제외하고 이전 항목과 유사합니다.

- **누락된 세미콜론 추가**

- **MSDN 도움말** - MSDN에서 오류 메시지를 검색합니다.

  물결선을 가리켜서 전구를 표시하거나 기본 바로 가기 키 Ctrl+.(Ctrl+점)을 사용할 수 있습니다. 바로 가기 키의 경우 특정 오류나 토큰에 캐럿을 배치할 필요가 없으며 오류와 같은 줄에 있기만 하면 해당 줄의 모든 항목에 대한 제안을 호출할 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md) [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
