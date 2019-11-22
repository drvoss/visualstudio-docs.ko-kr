---
title: 'How to: Use the Expression Editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d40cefc3dd47f7f4ad7e8255d8bdc06bc5f1651
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300945"
---
# <a name="how-to-use-the-expression-editor"></a>방법: 식 편집기 사용
식 편집기는 많은 워크플로 활동에서 식을 입력하거나 계산하는 데 사용되는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 컨트롤입니다. 식 편집기는 IntelliSense, 색 지정, ParamInfo, 오류 물결선 등 다양한 기능이 포함된 완벽한 IDE 편집 환경을 제공합니다. 그리고 컴파일러는 입력된 식의 유효성을 검사합니다. 식이 잘못된 경우 오류 아이콘이 표시됩니다. The editor can also be opened as an **Expression Editor** dialog box.

 식이란 인수나 속성에 바인딩된 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 코드 또는 리터럴 값입니다. 식에는 새 값을 생성하기 위해 연산으로 연결되는 변수, 상수, 리터럴, 속성 등의 값 요소가 포함됩니다. 애플리케이션이 C#을 사용하는 프로그램에 있는 경우에도 식은 VB.NET 구문으로 작성됩니다. This means capitalization does not matter, comparison is performed using a single equals (“=”) sign instead of (“==”), the Boolean operators are the words "and" and "or" instead of the symbols "&&" and "&#124;&#124;", and **Nothing** is used instead of **null**. For more information on expressions and operators in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and for some samples, see [Operators and Expressions in Visual Basic](https://go.microsoft.com/fwlink/?LinkId=186818).

 The **Expression Editor** behaves as follows:

- 포커스가 식 편집기에 있지 않을 때는 일반 TextBlock 컨트롤과 비슷하게 보입니다.

- 포커스를 식 편집기에 맞추면 식 편집기 컨트롤처럼 보이고 동작하다가, 포커스를 바꾸면 다시 일반 TextBlock처럼 보입니다.

- 다시 호스트된 Workflow Designer의 식 편집기에 포커스를 맞추면 TextBox처럼 동작하고, 다시 호스트된 워크플로 디자이너에서 포커스를 옮기면 식 편집기가 다시 일반 TextBlock처럼 보입니다.

> [!NOTE]
> 식 편집기용 IntelliSense는 [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서만 사용할 수 있습니다. [!INCLUDE[vs2010](../includes/vs2010-md.md)]과 다시 호스트된 시나리오 모두에서 컴파일러가 입력된 식의 유효성을 검사하고 식이 잘못된 경우 식 편집기에 오류 아이콘이 표시됩니다.

### <a name="using-the-expression-editor"></a>식 편집기 사용

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 새 워크플로 프로젝트 또는 기존 워크플로 프로젝트를 엽니다.

2. 예를 들어 <xref:System.Activities.Statements.Assign> 활동을 워크플로에 추가합니다.

    > [!NOTE]
    > 여러 가지 워크플로 활동에 식 편집기가 있습니다. 식 TextBlock은 변수 디자이너, 인수 디자이너 및 동적 인수 디자이너에도 나타납니다. 예제에서는 <xref:System.Activities.Statements.Assign> 활동을 사용합니다.

3. <xref:System.Activities.Statements.Assign> 활동의 활동 디자이너에서 왼쪽 식 편집기를 클릭합니다.

     The grey watermark strings **\<To>** and **\<Enter a VB Expression>** are the default text strings for expression editors in the <xref:System.Activities.Statements.Assign> activity.

4. 식을 입력합니다. 문자열을 입력할 경우 문자열 앞뒤에 물음표를 붙여야 합니다. 식 인수를 변수에 바인딩하려면 물음표를 제거합니다.

     작업을 마친 뒤 식 편집기 바깥 영역을 선택하여 디자이너의 다른 부분으로 포커스를 옮깁니다. 그러면 앞에서 설명한 것처럼 컴파일러가 식의 유효성을 검사합니다.

     속성 표에서 속성 이름 옆에 있는 줄임표를 클릭하여 식을 입력/편집할 수도 있습니다. This will open the **Expression Editor** as dialog box.

## <a name="see-also"></a>관련 항목:
 <xref:System.Activities.Presentation.View.ExpressionTextBox>