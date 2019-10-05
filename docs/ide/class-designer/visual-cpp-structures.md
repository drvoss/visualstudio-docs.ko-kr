---
title: 클래스 디자이너의 Visual C++ 구조체
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8e81ee25e081a324a8520317fa57a1314ccd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975036"
---
# <a name="visual-c-structures-in-class-designer"></a>클래스 디자이너의 Visual C++ 구조체

**클래스 디자이너**는 `struct` 키워드로 선언된 C++ 구조체를 지원합니다. 예를 들면 다음과 같습니다.

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

`struct` 형식을 사용하는 방법에 대한 자세한 내용은 [구조체](/cpp/cpp/struct-cpp)를 참조하세요.

레이블이 **구조체**를 읽고 둥근 모서리 대신 사각형 모서리를 갖고 있다는 점을 제외하고, 클래스 다이어그램에서 C++ 구조체 모양은 클래스 모양처럼 보이고 실제 그러한 작용을 합니다.

|코드 요소|클래스 디자이너 보기|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> 구조체|

## <a name="see-also"></a>참고 항목

- [Visual C++ 코드 작업](working-with-visual-cpp-code.md)
- [클래스 및 구조체](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)