---
title: 보고서 매크로 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c92424275a1dff69863b81fbf8567fbc4b84499
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905557"
---
# <a name="macros-for-reporting"></a>보고서 매크로
디버깅을 사용할 수 있습니다 합니다 **_RPTn** 하 고 **_RPTFn** crtdbg에서 정의 된 매크로 합니다. 사용을 대체 하려면 H `printf` 문입니다. 에 inclose 필요가 **#ifdef**s, 사용 중인 버전에서 자동으로 사라집니다 때문에 빌드에서 **_DEBUG** 정의 되어 있지 않습니다.

|매크로|설명|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|메시지 문자열과 0을 네 개의 인수로 출력합니다. _RPT1부터 **_RPT4**까지는 메시지 문자열이 인수에 대해 printf 스타일의 서식 문자열로 사용됩니다.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|**_RPTn**과 같지만 이러한 매크로는 해당 매크로가 있는 파일 이름과 줄 번호도 출력합니다.|

 다음 예제를 참조하세요.

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 이 코드는 `someVar`과 `otherVar`의 값을 **stdout**로 출력합니다. 다음 `_RPTF2` 호출을 사용하여 동일한 값과 파일 이름, 줄 번호를 보고할 수 있습니다.

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

특정 응용 프로그램을 디버그 C 런타임 라이브러리를 사용 하 여 제공 된 매크로가 제공 하지 않는 보고 해야 함을 확인할 수 있습니다. 이러한 경우에 대 한 고유한 요구 사항에 맞게 특별히 디자인 된 매크로 작성할 수 있습니다. 예를 들어 헤더 파일 중 하나에서 다음과 같은 코드를 포함하여 **ALERT_IF2** 매크로를 정의할 수 있습니다.

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 한 번 호출 **ALERT_IF2** 의 모든 기능을 수행할 수는 **printf** 코드:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 더 많거나 적은 다른 대상 정보를 보고 하는 사용자 지정 매크로 쉽게 변경할 수 있습니다. 디버깅 요구 진화 함에 따라이 방법은 특히 유용 합니다.

## <a name="see-also"></a>참고 항목
- [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)
