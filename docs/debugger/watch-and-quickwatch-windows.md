---
title: 변수에 조사식 설정 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8cd119ab39939de6562adcb962679874d528283
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929289"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>조사식 창 및 간략 한 조사식을 사용 하 여 변수를 시청 하세요.

디버깅하는 동안 **조사식** 창과 **간략한 조사식**을 사용하여 변수와 표현식을 확인할 수 있습니다. Windows는 디버깅 세션 중에서만 사용할 수 있습니다.

**조사식** windows 디버깅 하는 동안 한 번에 여러 변수를 표시할 수 있습니다. 합니다 **간략 한 조사식** 대화 한 번에 하나의 변수가 표시 및 디버그를 계속 하기 전에 닫아야 합니다.

읽을 하려는 처음 코드를 디버그 하려는 경우 [초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 하 고 [기술 및 도구 디버깅](../debugger/write-better-code-with-visual-studio.md) 이 문서를 진행 하기 전에 합니다.

## <a name="observe-variables-with-a-watch-window"></a>조사식 창 변수 관찰

둘 이상의 열 수 있습니다 **Watch** 창에서 둘 이상의 변수를 확인 하 고는 **조사식** 창.

예를 들어, 값에 조사식을 설정 하려면 `a`, `b`, 및 `c` 다음 코드에서:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. 에 중단점을 설정 합니다 `c = a + b;` 줄의 왼쪽된 여백을 클릭 하 여 선택 **디버그** > **중단점 설정/해제**, 키를 누르거나 **F9**합니다.

1. 녹색을 선택 하 여 디버깅을 시작할 **시작** 화살표 또는 **디버그** > **디버깅 시작**를 누르거나 **F5**합니다. 실행이 중단점에서 일시 중지 합니다.

1. 엽니다는 **조사식** 를 선택 하 여 창 **디버그** > **Windows** > **조사식**  >   **조사식 1**를 누르거나 **Ctrl**+**Alt**+**W** > **1**.

   창 **2**,**3** 또는 **4**를 선택하여 추가 **조사식**창을 열 수 있습니다.

1. 4\.**조사식** 창에서 빈 행을 선택하고 변수 `a`를 입력합니다. `b`와 `c`에 대해서도 동일하게 수행하세요.

   ![변수를 조사할](../debugger/media/watchvariables.png "WatchVariables")

1. 계속 진행하려면 **디버그** > **단계씩**을 선택하거나 **F11**을 눌러 디버깅을 계속하세요. `for` 루프를 반복할 때 **조사식** 창에서 변수 값이 변경됩니다.

>[!NOTE]
>에 대 한 C++ 만
>- 변수 이름 또는 변수 이름을 사용 하는 식의 컨텍스트를 한 정해야 해야 합니다. 컨텍스트 함수, 소스 파일 또는 변수 위치한 모듈입니다. 사용 하 여 컨텍스트를 한 정해야 해야 할 경우는 [컨텍스트 연산자 (C++)](../debugger/context-operator-cpp.md) 구문을 **이름** 에 **조사식** 창입니다.
>
>- 등록 이름 및 변수 이름을 사용 하 여 추가할 수 있습니다  **$ \<등록&nbsp;이름 >** 하거나  **@ \<등록&nbsp;이름 >** 에 **이름** 에 **조사식** 창입니다. 자세한 내용은 [Pseudovariables](../debugger/pseudovariables.md)를 참조하세요.

## <a name="use-expressions-in-a-watch-window"></a>조사식 창에서 식 사용

**조사식** 창에서 디버거가 인식한 유효한 식을 관찰할 수 있습니다.

예를 들어, 이전 섹션의 코드에 대해 **조사식** 창에 `(a + b + c) / 3`을 입력하여 세 가지 값의 평균을 얻을 수 있습니다:

![조사식](../debugger/media/watchexpression.png "조사식")

**조사식** 창에서 식을 평가하는 규칙은 일반적으로 코드 언어의 식을 평가하기 위한 규칙과 동일합니다. 식에 구문 오류가 있으면 코드 편집기와 동일한 컴파일러 오류를 예상합니다. 예를 들어 앞의 식에서 오타가 발생하면 **조사식** 창에서도 오류가 발생합니다:

![식 오류를 시청](../debugger/media/watchexpressionerror.png "식 오류 보기")

아이콘 두 물결선이 있는 원에 나타날 수 있습니다 합니다 **조사식** 창입니다. 이 아이콘은 디버거 잠재적 크로스 스레드 종속성으로 인해 식이 계산 되지 않고 의미 합니다. 코드를 확인할 때 일시적으로 실행 하려면 앱의 다른 스레드에 하는데 앱의 모든 스레드가 중지 일반적으로 중단 모드에 있는 때문입니다. 다른 스레드를 임시로 실행할 수 있습니다. 앱 및 디버거 상태에 예기치 않은 효과가 중단점 및 해당 스레드에서 예외와 같은 이벤트를 무시 될 수 있습니다.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>조사식 창에서 검색

이름, 값 및 형식 열에는 키워드를 검색할 수 있습니다 합니다 **조사식** 검색 표시줄을 사용 하 여 각 창 위에 창입니다. ENTER 키를 눌러 또는 검색을 실행 하려면 화살표 중 하나를 선택 합니다. 진행 중인 검색을 취소 하려면 검색 표시줄에서 "x" 아이콘을 선택 합니다.

찾은 일치 항목을 탐색하려면 왼쪽 및 오른쪽 화살표(각각 Shift + F3 및 F3)를 사용하세요.

![조사식 창에서 검색](../debugger/media/ee-search-watch.png "조사식 창에서 검색")

검색을 다소 철저하게 하려면 **조사식** 창의 상단에 있는 **심층 검색** 드롭다운을 사용하여 중첩된 개체에 대해 검색할 수준을 선택하세요. 

::: moniker-end

### <a name="bkmk_refreshWatch"></a> 조사식 값 새로 고침

식을 계산하는 경우에 새로 고침 아이콘(원형 화살표)이 **조사식** 창에 나타날 수 있습니다. 새로 고침 아이콘은 오류 또는 오래된 값을 나타냅니다.

값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 계산합니다. 그러나 값이 계산되지 않은 이유에 따라 식을 다시 계산하지 못하거나 계산하지 않고자 할 수도 있습니다.

식이 재대로 계산되지 않은 이유를 알아보려면 새로 고침 아이콘 위에 마우스를 올리거나 **값** 열을 참조하세요. 이유는 다음과  같습니다.

- 이전 예에서와 같이 식을 계산할 때 오류가 발생했습니다. 시간 초과가 발생하거나 변수가 범위를 벗어났을 수 있습니다.

- 식에 앱에서 부작용을 유발할 수 있는 함수 호출이 있습니다. [의도하지 않은 식](#bkmk_sideEffects) 문서를 참조하세요.

- 자동 속성 평가 및 암시적 함수 호출을 사용 하는 사용할 수 없습니다.

새로 고침 아이콘 자동 속성 평가 및 암시적 함수 호출 수 없기 때문에 나타나면 선택 하 여 사용할 수 있습니다 **속성 확인 및 기타 암시적 함수 호출** 에서 **도구**   >  **옵션** > **디버깅** > **일반**합니다.

새로 고침 아이콘을 사용 하 여 보여 줍니다.

1. **도구** > **옵션** > **디버깅** > **일반**, 합니다 지우기**속성 확인 및 기타 암시적 함수 호출** 확인란 합니다.

1. 다음 코드를 입력 및 합니다 **Watch** 창에 대 한 조사식 설정는 `list.Count` 속성입니다.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. 디버깅을 시작합니다. 합니다 **조사식** 창에 다음 메시지와 같이 표시 됩니다.

   ![보기 새로 고침](../debugger/media/refreshwatch.png "Watch 새로 고침")

1. 값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거 식을 재평가 합니다.

### <a name="bkmk_sideEffects"></a> 의도 하지 않은 식

일부 식을 계산할 때 변수의 값을 변경 하거나 앱의 상태에 영향을 미칠 수 있습니다. 예를 들어 다음 식을 계산하면 `var1`의 값이 변경됩니다.

```csharp
var1 = var2
```

이 코드에서 발생할 수 있습니다는 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))합니다. 의도 하지 않은 더 어려워질 수 있습니다 디버깅 앱의 작동 방식을 변경 하 여 합니다.

부작용이 있는 식은 처음 입력할 때이 한 번만 평가 됩니다. 그 후 식 표시에서 회색으로 표시 되는 **조사식** 창 및 추가 평가 사용 하지 않도록 설정 됩니다. 도구 설명 하거나 **값** 칼럼에서 설명 하는 해당 식 부작용을 일으킵니다. 값 옆에 표시 되는 새로 고침 아이콘을 선택 하 여 재평가 할 수 있습니다.

의도 지정 하지 않으려면 하나 방법은 자동 함수 계산을 끄는 것입니다. **도구** > **옵션** > **디버깅** > **일반**합니다 선택취소**속성 확인 및 기타 암시적 함수 호출**합니다.

에 대 한 C# 만 암시적 함수 호출이 나 속성의 계산을 해제 하는 경우 식을 강제로 계산할 수를 추가 하 여는 **ac** 변수에 형식 한정자 **이름** 에 **시청**  창입니다. [C#의 형식 지정자](../debugger/format-specifiers-in-csharp.md)를 참조하세요.

## <a name="bkmk_objectIds"></a> 조사식 창에서 개체 Id를 사용 하 여 (C# 및 Visual Basic)

특정 개체의 동작을 관찰 하려는 경우가 있습니다. 예를 들어, 다음 해당 변수 범위를 벗어난 후 지역 변수에 의해 참조 된 개체를 추적 하는 것이 좋습니다. C# 및 Visual Basic에서 참조 형식의 특정 인스턴스에 대한 개체 ID를 만들고 **조사식** 창 및 중단점 조건에서 사용할 수 있습니다. 개체 ID는 CLR(공용 언어 런타임) 디버깅 서비스에 의해 생성되고 개체와 연결됩니다.

> [!NOTE]
> 개체 Id는 가비지 수집 되지 않도록에서 개체를 방해 하지는 약한 참조를 만듭니다. 현재 디버깅 세션에 대해서만 유효합니다.

다음 코드에서를 `MakePerson()` 메서드를 만듭니다를 `Person` 지역 변수를 사용 하 여:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

이름을 확인 하려면를 `Person` 에 `DoSomething()` 메서드에 대 한 참조를 추가할 수 있습니다 합니다 `Person` 에 개체 ID를 **조사식** 창.

1. 후 코드에서 중단점을 설정 합니다 `Person` 개체가 생성 되었습니다.

1. 디버깅을 시작합니다.

1. 실행이 중단점에서 일시 중지, 열립니다는 **지역** 를 선택 하 여 창 **디버그** > **Windows** > **지역**.

1. 에 **지역** 창에서 마우스 오른쪽 단추로 클릭는 `Person` 변수와 선택 **개체 ID 만들기**합니다.

   달러 기호 표시 됩니다 ( **$** ) 더하기 숫자가 합니다 **지역** 창이 되 고 개체 id입니다.

1. 개체의 ID를 추가 합니다 **Watch** 개체 ID를 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 창 **조사식 추가**합니다.

1. 다른 중단점을 설정 합니다 `DoSomething()` 메서드.

1. 디버깅을 계속합니다. 실행에 일시 중지 하는 경우는 `DoSomething()` 메서드를 **조사식** 창에 표시 됩니다는 `Person` 개체.

   > [!NOTE]
   > 개체의 속성을 표시 하려는 경우 `Person.Name`를 선택 하 여 속성 평가 사용 해야 합니다 **도구** > **옵션**  >   **디버깅** > **일반** > **속성 확인 및 기타 암시적 함수 호출**합니다.

## <a name="dynamic-view-and-the-watch-window"></a>동적 뷰 및 조사식 창

일부 스크립팅 언어 (예: JavaScript 또는 Python)를 사용 하 여 동적 또는 [오리](https://en.wikipedia.org/wiki/Duck_typing) 입력 및.NET 4.0 이상 버전에서 일반 디버깅 창을 관찰 하기 어려운 개체를 지원 합니다.

합니다 **조사식** 구현 하는 형식에서 생성 되는 동적 개체로 이러한 개체를 표시 하는 창은 <xref:System.Dynamic.IDynamicMetaObjectProvider> 인터페이스입니다. 동적 개체 노드 동적 개체의 동적 멤버를 표시 하지만 멤버 값을 편집할 수 없습니다.

새로 고치려면 **동적 뷰** 값을 선택 합니다 [새로 고침 아이콘](#bkmk_refreshWatch) 동적 개체 노드 옆에 있습니다.

만 표시할 합니다 **동적 뷰** 개체에 대 한 추가 **동적** 형식 지정자의 동적 개체 이름 뒤의 **조사식** 창:

- C#의 경우: `ObjectName, dynamic`
- Visual Basic의 경우: `$dynamic, ObjectName`

>[!NOTE]
>- C# 디버거에서 값을 자동으로 다시 평가 하지 합니다 **동적 뷰** 코드의 다음 줄으로 진행 하는 경우.
>- Visual Basic 디버거 식을 통해 추가 자동으로 새로 고치는 **동적 뷰**합니다.
>- **동적 뷰**의 멤버를 평가하면 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 발생할 수 있습니다.

**새 조사식을 삽입할 변수는 개체를 동적 개체:**

1. 자식을 마우스 오른쪽 단추로 클릭 한 **동적 뷰**합니다.
1. 선택할 **조사식 추가**합니다. 합니다 `object.name` 됩니다 `((dynamic) object).name` 새 나타나고 **조사식** 창입니다.

추가 디버거는 **동적 뷰** 개체의 자식 노드를 **자동** 창. 열려는 합니다 **자동** 창에서 디버그 하는 동안 **디버그** > **Windows** > **자동**합니다.

**동적 뷰** 또한 COM 개체에 대 한 디버깅을 개선 합니다. 디버거에 래핑된 COM 개체를 가져옵니다 하는 경우 **System.__ComObject**에서 추가 **동적 뷰** 개체에 대 한 노드.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>단일 변수 또는 간략 한 조사식을 사용 하 여 식 관찰

사용할 수 있습니다 **간략 한 조사식** 단일 변수를 관찰할 수 있습니다.

예를 들어, 다음 코드에 대 한

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

관찰 하는 `a` 변수

1. `a = a + b;` 줄에 중단점을 설정합니다.

1. 디버깅을 시작합니다. 실행이 중단점에서 일시 중지 합니다.

1. 변수 선택 `a` 코드에서입니다.

1. 선택 **디버그** > **간략 한 조사식**, 키를 눌러 **Shift**+**F9**, 마우스 선택 **간략 한 조사식**합니다.

   합니다 **간략 한 조사식** 대화 상자가 나타납니다. `a` 변수가 합니다 **식** 사용 하 여 상자를 **값** 의 **1**합니다.

   ![간략 한 조사식 변수](../debugger/media/quickwatchvariable.png "간략 한 조사식 변수")

1. 변수를 사용 하 여 식을 평가 하는 식을 입력와 같은 `a + b` 에 **식** 상자에서 선택한 **다시 평가**합니다.

   ![조사식](../debugger/media/quickwatchexpression.png "조사식")

1. 변수 또는 식에 추가할 **간략 한 조사식** 에 **조사식** 창에서 **조사식 추가**합니다.

1. 선택 **닫습니다** 닫으려면 합니다 **간략 한 조사식** 창입니다. (**간략 한 조사식** 는 모달 대화 상자 이므로 열려으로 디버깅을 계속할 수 없습니다.)

1. 디버깅을 계속합니다. 변수를 확인할 수 있습니다 합니다 **조사식** 창입니다.

## <a name="see-also"></a>참고자료
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [디버깅 소개](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
