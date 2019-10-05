---
title: '워크플로 디자이너-방법: 식 편집기 사용'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce46f1db900aa5c37b49a1cc228290d7d99d29a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949541"
---
# <a name="how-to-use-the-expression-editor"></a>방법: 식 편집기 사용

식 편집기에는 많은 워크플로 활동에서 입력 하 고 식을 평가 하는 데 사용 되는 워크플로 디자이너 컨트롤입니다. 식 편집기에서는 완전 한 IDE 편집 환경을, IntelliSense, 색 지정, ParamInfo, 오류 물결선 등입니다. 컴파일러는 입력 된 식의 유효성을 검사 합니다. 식이 잘못된 경우 오류 아이콘이 표시됩니다. 편집기로 열 수도 있습니다는 **식 편집기** 대화 상자.

식이란 인수나 속성에 바인딩된 Visual Basic 코드 또는 리터럴 값입니다. 새 값을 생성 하기 위해 연산으로 결합 되는 값 요소 (예: 변수, 상수, 리터럴, 속성)를 포함 합니다. 애플리케이션이 C#을 사용하는 프로그램에 있는 경우에도 식은 VB.NET 구문으로 작성됩니다. 즉, 대/소문자에 상관 없이 단일 등호를 사용 하 여 비교가 수행 됩니다 ("=" 대신 "= =")을 로그인, 부울 연산자는 단어 "및" 및 "or" 기호 대신 "& &" 및 "| |", 및 **Nothing** 는 대신 **null**합니다. Visual Basic의 식 및 연산자에 대 한 자세한 내용은 및 일부 샘플에 대 한 참조 [Visual Basic의 연산자 및 식](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))합니다.

합니다 **식 편집기** 다음과 같이 동작 합니다.

- 포커스가 식 편집기에 있지 않을 때는 일반 TextBlock 컨트롤과 비슷하게 보입니다.

- 포커스를 식 편집기에 맞추면 식 편집기 컨트롤처럼 보이고 동작하다가, 포커스를 잃은 후 식 편집기 찾습니다 일반 TextBlock 처럼 다시 합니다.

- 다시 호스트된 Workflow Designer의 식 편집기에 포커스를 맞추면 TextBox처럼 동작하고, 다시 호스트된 워크플로 디자이너에서 포커스를 옮기면 식 편집기가 다시 일반 TextBlock처럼 보입니다.

> [!NOTE]
> 식 편집기 용 IntelliSense는 Visual Studio 내 에서만 사용할 수 있습니다. Visual Studio 및 재 호스트 된 시나리오에서 컴파일러의 유효성을 검사 식 입력 후 식이 올바르지 않으면 식 편집기 오류 아이콘을 표시 합니다.

## <a name="use-the-expression-editor"></a>식 편집기 사용

1. Visual Studio에서 새 또는 기존 워크플로 프로젝트를 엽니다.

2. 예를 들어 <xref:System.Activities.Statements.Assign> 활동을 워크플로에 추가합니다.

    > [!NOTE]
    > 여러 가지 워크플로 활동에 식 편집기가 있습니다. 식 TextBlock은 변수 디자이너, 인수 디자이너 및 동적 인수 디자이너에도 나타납니다. 예제에서는 <xref:System.Activities.Statements.Assign> 활동을 사용합니다.

3. <xref:System.Activities.Statements.Assign> 활동의 활동 디자이너에서 왼쪽 식 편집기를 클릭합니다.

     회색 워터 마크 문자열  **\<에 >** 하 고  **\<VB 식 입력 >** 는 기본 텍스트 문자열에서 식 편집기에 대 한는 <xref:System.Activities.Statements.Assign> 활동.

4. 식을 입력합니다. 문자열을 입력할 경우 문자열 앞뒤에 물음표를 붙여야 합니다. 식 인수를 변수에 바인딩하려면 물음표를 제거합니다.

     완료 되 면 디자이너의 다른 부분으로 포커스를 식 편집기 바깥 영역을 선택 합니다. 초점이 옮겨지고 컴파일러에서 앞에서 설명한 대로 식의 유효성을 검사 합니다.

     입력 하거나 식을 편집 하는 다른 방법은 속성 표에서 속성 이름 옆의 줄임표를 클릭 하는 것입니다. 줄임표를 선택 하면 열립니다는 **식 편집기** 대화 상자.

## <a name="see-also"></a>참고자료

- <xref:System.Activities.Presentation.View.ExpressionTextBox>