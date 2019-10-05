---
title: MSBuild 모범 사례 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ad0bd131251259b375a4300807825205da2c6ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931487"
---
# <a name="msbuild-best-practices"></a>MSBuild 모범 사례
MSBuild 스크립트를 작성할 때는 다음 모범 사례를 따르는 것이 좋습니다.

- 기본 속성 값은 명령줄에서 기본값을 재정의할 수 있는 속성을 선언하는 대신 `Condition` 특성을 사용하여 처리하는 것이 가장 효율적입니다. 예를 들어 다음과 같은 코드를 사용합니다.

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- 항목을 선택할 때는 와일드카드를 사용하지 않습니다. 대신 파일을 명시적으로 지정합니다. 이렇게 하면 파일을 추가하거나 삭제할 때 발생할 수 있는 오류를 보다 쉽게 추적할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [고급 개념](../msbuild/msbuild-advanced-concepts.md)
