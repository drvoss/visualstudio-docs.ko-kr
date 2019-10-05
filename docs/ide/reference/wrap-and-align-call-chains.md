---
title: 호출 체인 래핑 및 맞춤
description: 메서드 호출의 체인을 래핑하고 맞추는 방법에 대해 알아봅니다.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620015"
---
# <a name="wrap-and-align-call-chains"></a>호출 체인 래핑 및 맞춤

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 메서드 호출의 체인을 래핑 및 맞출 수 있습니다.

**시기:** 하나의 문에 여러 메서드 호출로 구성된 긴 체인이 있습니다.

**이유:** 사용자 기본 설정에 따라 래핑하거나 들여쓰기할 때 긴 목록을 읽기가 더 쉽습니다.

## <a name="how-to"></a>방법

1. 호출 체인에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. 리팩터링을 수락하려면 **호출 체인 래핑** 또는 **호출 체인 래핑 및 맞춤**을 선택합니다.

   ![호출 체인 래핑 및 맞춤](media/wrap-call-chain.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
