---
title: 매개 변수 리팩터링 생성
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329062"
---
# <a name="generate-parameter"></a>매개 변수 생성

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 자동으로 메서드 매개 변수 생성

**시기:** 현재 컨텍스트에 없는 변수를 메서드에서 참조하여 오류가 표시되는 경우. 코드 수정으로 매개 변수를 생성할 수 있습니다. 

**이유:** 컨텍스트를 유지하면서 메서드 시그니처를 빠르게 수정할 수 있습니다.

## <a name="how-to"></a>방법

1. 변수 이름에 커서를 놓고 **Ctrl**+ **.** 을 누릅니다. **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
1. **매개 변수 생성**을 선택합니다.

   ![매개 변수 생성](media/generate-parameter.png) 

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
