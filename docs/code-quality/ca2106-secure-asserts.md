---
title: 'CA2106: 어설션을 안전하게 보호하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4495dcbe951edd3e7eaa3b6ff0d2432bc0a7751
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232883"
---
# <a name="ca2106-secure-asserts"></a>CA2106: 어설션을 안전하게 보호하세요.

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|범주|Microsoft.Security|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
메서드는 권한을 어설션 하 고 호출자에 대해 보안 검사를 수행 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다. 보안 스택 워크는 보안 권한이 어설션 될 때 중지 됩니다. 호출자에 대 한 검사를 수행 하지 않고 권한을 어설션하는 경우 호출자는 권한을 사용 하 여 간접적으로 코드를 실행할 수 있습니다. 보안 검사를 사용 하지 않는 어설션은 어설션이 유해한 방식으로 사용 될 수 없는 경우에 허용 됩니다. 호출 하는 코드가 무해 하거나 사용자가 호출 하는 코드에 임의의 정보를 전달할 수 없는 경우 어설션이 무해 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 메서드 또는 해당 선언 형식에 보안 요청을 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
신중한 보안 검토 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [보안 코딩 지침](/dotnet/standard/security/secure-coding-guidelines)