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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d4406d1fc30115cc7002da24c71d2274131ce74
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674527"
---
# <a name="options-text-editor-cc-experimental"></a>옵션, 텍스트 편집기, C/C++, 실험적
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이러한 옵션을 변경하면 C 또는 C++에서 프로그래밍할 때 IntelliSense 및 검색 데이터베이스 관련 동작을 변경할 수 있습니다.  
  
 이 페이지에 액세스하려면 왼쪽 창의 **옵션** 대화 상자에서 **텍스트 편집기**를 확장하고 **C/C++** 를 확장한 다음 **실험적**을 선택합니다.  
  
 이러한 기능은 Visual Studio 2015 업데이트 1 RC 설치에서 사용할 수 있습니다.  
  
> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="browsingnavigation"></a>검색/탐색  
 **새 데이터베이스 엔진 사용**  
 자동으로 데이터베이스 채우기 속도가 향상되고 **정의로 이동** 및 **모든 참조 찾기**와 같은 작업에 대한 모든 데이터베이스 작업 속도가 빨라지며 정확도가 손실되지 않습니다. 변경 내용을 적용하려면 솔루션을 닫았다가 다시 열면 됩니다. Visual Studio를 다시 시작할 필요가 없습니다.  
  
## <a name="intellisense"></a>IntelliSense  
 **멤버 목록 점-화살표**  
 멤버 목록에 적합한 경우 '.'을 '->'로 바꿉니다.  
  
## <a name="refactoring"></a>리팩터링  
 **함수 추출 사용**  
 선택한 코드를 자체 함수로 추출하고 코드를 새 함수 호출로 바꿉니다. 이 기능에 액세스하려면 선택한 코드를 마우스 오른쪽 단추로 클릭하고 **빠른 작업**을 선택하거나, 간단히 기본 바로 가기인 Ctrl+.[Ctrl+점]을 누릅니다.  
  
 **시그니처 변경 사용**  
 함수의 매개 변수를 추가하고, 순서를 바꾸고, 삭제하며 변경 내용을 모든 호출 사이트에 전파합니다. 이 기능에 액세스하려면 모든 함수 사용을 마우스 오른쪽 단추로 클릭하고 **빠른 작업**을 선택하거나, 간단히 기본 바로 가기 Ctrl+.[Ctrl+점]을 누릅니다.  
  
## <a name="text-editor"></a>텍스트 편집기  
 **범위 확장 사용**  
 사용하도록 설정한 경우 텍스트 편집기에 '{'를 입력하면 선택한 텍스트를 중괄호로 둘러쌀 수 있습니다.  
  
 **우선 순위 확장 사용**  
 사용하도록 설정한 경우 텍스트 편집기에 '('를 입력하면 선택한 텍스트를 괄호로 둘러쌀 수 있습니다.  
  
 Visual Studio 갤러리의 추가 텍스트 편집기 기능은 [여기](http://go.microsoft.com/fwlink/?LinkId=692016)에서 목록을 참조하세요. 예제는 [C++ 빠른 조치 방법](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)(영문)이며, 다음을 지원합니다.  
  
- **누락된 #include 추가** - 코드의 알 수 없는 기호에 대해 관련 #include를 제안합니다.  
  
- **네임스페이스/정규화 기호를 사용하여 추가** - 네임스페이스를 제외하고 이전 항목과 유사합니다.  
  
- **누락된 세미콜론 추가**  
  
- **MSDN 도움말** - MSDN에서 오류 메시지를 검색합니다.  
  
  물결선을 가리켜서 전구를 표시하거나 기본 바로 가기 키 Ctrl+.(Ctrl+점)을 사용할 수 있습니다. 바로 가기 키의 경우 특정 오류나 토큰에 캐럿을 배치할 필요가 없으며 오류와 같은 줄에 있기만 하면 해당 줄의 모든 항목에 대한 제안을 호출할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [언어별 편집기 옵션 설정](../../ide/reference/setting-language-specific-editor-options.md)   
 [C++에서의 리팩터링(VC 블로그)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
