---
title: 클래스 디자이너의 Visual C++ 열거형
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f31f153183d0cdd809bd9dde9187ade32b20ddd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975023"
---
# <a name="visual-c-enumerations-in-class-designer"></a>클래스 디자이너의 Visual C++ 열거형

**클래스 디자이너**는 C++ `enum` 및 범위가 지정된 `enum class` 형식을 지원합니다. 예를 들면 다음과 같습니다.

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

클래스 다이어그램의 C++ 열거형 도형은 레이블이 **Enum** 또는 **Enum 클래스**로 표시되고, 파란색이 아니라 분홍색이며, 왼쪽 및 위쪽 여백에 색이 지정된 테두리가 있다는 점을 제외하고 구조체 도형과 모양 및 기능이 유사합니다. 열거형 도형과 구조체 도형에는 사각형 모서리가 있습니다.

`enum` 형식을 사용하는 방법에 대한 자세한 내용은 [열거형](/cpp/cpp/enumerations-cpp)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual C++ 코드 작업](working-with-visual-cpp-code.md)
- [열거형](/cpp/cpp/enumerations-cpp)