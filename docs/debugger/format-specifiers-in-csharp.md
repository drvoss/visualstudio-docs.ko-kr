---
title: 형식 지정자는 디버거에서 (C#) | Microsoft Docs
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: caaf36e286f1bdc664ebdbb10e3baf7ed28183e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849830"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Visual Studio 디버거에서의 C#의 형식 지정자
값이 표시 하는 형식을 변경할 수 있습니다 합니다 **조사식** 형식 지정자를 사용 하 여 창입니다. 형식 지정자를 사용할 수도 있습니다는 **직접 실행** 창 합니다 **명령** 창에서 [추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), 및 소스 창. 를 일시 중지 하면 해당 창에 식의 결과에 표시 됩니다는 [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) 지정 된 형식으로 표시 합니다.

형식 지정자를 사용 하려면 변수 식 뒤에 쉼표와 적절 한 지정자를 입력 합니다.

## <a name="set-format-specifiers"></a>집합 형식 지정자
다음 예제 코드를 사용 하겠습니다.

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

추가 합니다 `my_var1` 변수를 합니다 **조사식** 디버깅 하는 동안 창 **디버그** > **Windows** > **보기**  >  **조사식 1**합니다. 그런 다음 변수를 마우스 오른쪽 단추로 클릭 하 고 선택 **16 진수 표시**합니다. 이제는 **조사식** 창 값이 0x0065 표시 합니다. 이 값을 16 진수 정수 대신 10 진수 정수를 표시 하는 10 진수 서식 지정자를 추가 **, d** 에 **이름** 변수 이름 뒤에 열입니다. 합니다 **값** 열이 표시 됩니다 **101**합니다.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

볼 수 있으며 값에 쉼표 (,)를 추가 하 여 사용할 수 있는 형식 지정자 목록에서 선택 합니다 **조사식** 창입니다. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>형식 지정자
다음 표에서 C# 형식 지정자는 Visual Studio 디버거에 대 한 합니다.

|지정자|형식|원래 조사식 값|표시|
|---------------|------------|--------------------------|--------------|
|ac|암시적 속성 확인 및 암시적 함수 호출이 해제 된 경우 유용할 수 있는 식의 평가 강제 합니다.|메시지 “사용자가 암시적 함수 실행을 해제했습니다.”|\<value>|
|일|10진수 정수|0x0065|101|
|dynamic|동적 뷰를 사용하여 지정된 개체를 표시합니다.|동적 뷰를 포함하여 개체의 모든 멤버를 표시합니다.|동적 뷰만 표시합니다.|
|h|16진수 정수|61541|0x0000F065|
|nq|따옴표 없는 문자열|"My String"|My String|
|nse|형식이 아니라 동작을 지정합니다. "파생 작업이 없습니다."를 사용 하 여 식을 계산합니다. 식을 해석할 수 없습니다 (예: 함수 호출)를 평가 하 여 해결할 수 있습니다를 대신 오류가 표시 됩니다.|N/A|N/A|
|hidden|모든 public 멤버 및 public이 아닌 멤버를 표시합니다.|공용 멤버를 표시합니다.|모든 멤버를 표시합니다.|
|raw|항목을 원시 항목 노드에 나타나는 대로 표시합니다. 프록시 개체에만 사용할 수 있습니다.|사전\<T >|raw 뷰\<T >|
|results|IEnumerable 또는 IEnumerable을 구현 하는 형식의 변수와 함께 사용할\<T >를 일반적으로 쿼리 식의 결과입니다. 쿼리 결과가 포함된 멤버만 표시합니다.|모든 멤버 표시|쿼리 조건에 맞는 멤버 표시|

## <a name="see-also"></a>참고자료
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [자동 및 지역 창](../debugger/autos-and-locals-windows.md)
