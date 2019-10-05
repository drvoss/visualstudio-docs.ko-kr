---
title: 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa8fbfd8837fb35617b79089fffd11ea3b8d2e93
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444538"
---
# <a name="refactoring-c"></a>리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

리팩터링 하는 것은 코드의 외부 동작을 변경 하지 않고 코드의 내부 구조를 변경 하 여 작성 한 후 코드를 개선의 프로세스입니다.  
  
 Visual C#의 리팩터링 명령을 제공 합니다 **Refactoring** 메뉴:  
  
- [메서드 추출 리팩터링(C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
- [이름 바꾸기 리팩터링(C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
- [필드 캡슐화 리팩터링(C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
- [인터페이스 추출 리팩터링(C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
- [매개 변수 제거 리팩터링(C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
- [매개 변수 다시 정렬 리팩터링(C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>다중 프로젝트 리팩터링  
 Visual Studio 프로젝트에서 동일한 솔루션에 대 한 다중 프로젝트 리팩터링 지원 합니다. 모든 파일에 대 한 참조를 수정 하는 리팩터링 작업은 동일한 언어의 모든 프로젝트에서 해당 참조를 수정 합니다. 이 대 한 프로젝트 간 참조는 작동합니다. 예를 들어, 클래스 라이브러리 형식의 이름을 바꾸면 클래스 라이브러리를 참조 하는 콘솔 응용 프로그램을 사용 하는 경우 (사용 하는 `Rename` 리팩터링 작업), 콘솔 응용 프로그램에 있는 클래스 라이브러리 형식에 대 한 참조도 업데이트 됩니다.  
  
## <a name="changes-preview"></a>변경 내용 미리 보기  
 많은 리팩터링 작업 코드에서 변경 내용을 커밋하기 전에 리팩터링 작업을 수행 하는 모든 참조 변경 내용 검토 수 있는 기회를 제공 합니다. 이러한 리팩터링 작업에 대 한는 **참조 변경 내용 미리 보기** 옵션 리팩터링 대화 상자에 표시 됩니다. 이 옵션을 선택 하 고 리팩터링 작업을 수락 후 합니다 **미리 보기 변경 대화 상자** 나타납니다. 다음에 유의 합니다 **변경 내용 미리 보기** 대화 상자에는 두 개의 뷰가 있습니다. 리팩터링 작업으로 인해 모든 참조 업데이트를 사용 하 여 코드 아래 표시 됩니다. 키를 눌러 **취소할** 에 **변경 내용 미리 보기** 대화 상자에는 리팩터링 작업을 중지 되 고 코드는 변경 되지 것입니다.  
  
## <a name="refactoring-warnings"></a>경고를 리팩터링  
 컴파일러에서 프로그램을 완벽 하 게 이해 되지 않은 경우 리팩터링 엔진에서는 적절 한 모든 참조를 업데이트 하지 않을 수 있습니다 수 경고 대화 상자가 표시 됩니다. 또한이 경고 대화 상자에서 코드를 미리 볼 수 있는 기회를 제공 합니다 **변경 내용 미리 보기** 변경 내용을 커밋하기 전에 대화 상자.  
  
> [!NOTE]
> 메서드는 구문 오류 (빨간색 물결선 밑줄이 있는 IDE을 나타냄)를 포함 한 다음 리팩터링 엔진은 해당 메서드 내에서 요소에 대 한 참조를 업데이트 되지 않습니다. 아래 예제에서는이 동작을 보여 줍니다.  
  
 기본적으로 실행 하는 경우 참조를 미리 보지 않고 리팩터링 작업을 변경 프로그램에 컴파일 오류가 검색 되 고 개발 환경에이 경고 대화 상자가 표시 됩니다.  
  
 리팩터링 작업을 실행 하는 경우 **참조 변경 미리 보기** 사용 하도록 설정 하 고 프로그램에 컴파일 오류가 검색 되는 개발 환경 아래쪽에 다음과 같은 경고 메시지가 표시 됩니다는 **변경 내용 미리 보기** 대화 상자를 표시 하는 대신 합니다 **리팩터링 경고** 대화 상자:  
  
 **프로젝트 또는 해당 종속성 중 하나가 현재 작성 되지 않습니다. 참조를 업데이트할 수 있습니다.**  
  
 이 리팩터링 경고에만 제공 됩니다 제공 하는 리팩터링 작업을 **참조 변경 미리 보기** 옵션입니다.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>오류 허용 리팩터링 및 결과 확인  
 리팩터링 하는 것은 허용 되는 오류입니다. 즉, 빌드할 수 없는 프로젝트의 리팩터링을 수행할 수 있습니다. 그러나 이러한 경우 리팩터링 하는 프로세스 수 참조를 업데이트 하지 모호한 올바르게 합니다.  
  
 합니다 **확인 결과** 대화 상자 알릴 수 리팩터링 엔진에서 컴파일 오류 또는 검색 리팩터링 작업을 인해 코드 참조가 된 다른 항목에 바인딩하는 경우 원래 (다시 바인딩 문제)에 바인딩됩니다.  
  
 켜려면 확인 결과 기능을는 **도구** 메뉴에서 클릭 **옵션**합니다. 에 **옵션** 대화 상자에서 **텍스트 편집기**를 차례로 확장 **C#** 합니다. 클릭 **고급** 선택 합니다 **리팩터링 결과 확인** 확인란 합니다.  
  
 합니다 **확인 결과** 대화 상자에서는 두 종류의 문제를 다시 바인딩 간의 차이 구별 합니다.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>정의 해당 이름이 바뀐된 기호를 더 이상 참조  
 이러한 종류의 다시 바인딩 문제는 이름이 바뀐된 기호에 대 한 참조를 더 이상 참조 하는 경우에 발생 합니다. 예를 들어, 다음 코드를 고려하세요.  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 사용 하 여 리팩터링 이름 바꾸기 `a` 에 `b`,이 대화 상자가 나타납니다. 이름이 바뀐된 변수의에 대 한 참조 `a` 필드에 바인딩하는 대신 생성자에 전달 되는 매개 변수에 바인딩됩니다.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>정의 해당 이름이 바뀐된 기호 되는 참조  
 이러한 종류의 다시 바인딩 문제에는 이름이 바뀐된 기호 참조를 참조 하지 않았던 바꾼 기호 이제를 가리키지 때 발생 합니다. 예를 들어, 다음 코드를 고려하세요.  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 사용 하 여 리팩터링 이름 바꾸기 `OtherMethod` 에 `Method`,이 대화 상자가 나타납니다. 에 대 한 참조 `Main` 이제 받아들이는 오버 로드 된 메서드를 참조는 `int` 받아들이는 오버 로드 된 메서드 대신 매개 변수는 `object` 매개 변수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [C# 용 Visual Studio 개발 환경 사용](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [방법: C# 리팩터링 코드 조각 복원](../ide/how-to-restore-csharp-refactoring-snippets.md)