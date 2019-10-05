---
title: 가져오지 않은 형식에 대한 IntelliSense 완성
description: '`using` 지시문으로 아직 가져오지 않은 형식에 대해 IntelliSense 완성 기능을 사용하는 방법입니다.'
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312921"
---
# <a name="intellisense-completion-for-unimported-types"></a>가져오지 않은 형식에 대한 IntelliSense 완성

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 가져오지 않은 형식에 대해 IntelliSense 완성 기능 사용

**시기:** 이미 종속성이 있는 형식을 프로젝트에 추가하려고 하는데, import 문이 파일에 아직 추가되지 않은 경우 

**이유:** 파일에 import 문을 수동으로 추가할 필요가 없습니다.

## <a name="how-to"></a>방법

1. 종속성이 있는 형식을 프로젝트에서 사용하기 시작하면 IntelliSense에서 제안을 제공합니다.
2. **Tab** 키를 누릅니다. 

   import 문이 파일에 추가됩니다.

   ![가져오지 않은 형식에 대한 IntelliSense 완성](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
