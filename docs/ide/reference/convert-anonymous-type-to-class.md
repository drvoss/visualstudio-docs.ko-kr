---
title: 익명 형식을 클래스로 변환
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f29e31fb87d8b18e7f5a46d16f90217ee08d51f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968539"
---
# <a name="convert-anonymous-type-to-class"></a>익명 형식을 클래스로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 익명 형식을 클래스로 변환합니다.

**시기:** 클래스에서 계속 빌드하려는 익명 형식이 있습니다.

**이유:** 익명 형식은 로컬에서만 사용하는 경우에 유용합니다. 코드가 증가함에 따라 클래스로 승격시키는 쉬운 방법이 있습니다.

## <a name="how-to"></a>방법

1. 익명 형식으로 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![익명 형식을 클래스로 변환](media/convert-anon-to-class.png)

2. **Enter**를 눌러 리팩터링을 수락합니다.

   ![익명 형식을 허용하는 클래스로 변환](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
