---
title: '오류: 혼합 모드 디버깅 프로세스는 Microsoft.NET Framework 4를 사용 하는 경우에 지원 됩니다 x64 이상 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745435"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>오류: x64 프로세스용 혼합 모드 디버깅은 Microsoft .NET Framework 4 이상을 사용할 때만 지원됩니다.
64 비트 프로세스의 혼합된 네이티브 및 관리 코드를 디버깅 하려면.NET Framework 버전 4 있어야 합니다. 4 이전의.NET Framework 버전을 사용 하 여 64 비트 프로세스의 혼합 모드 디버깅이 지원 되지 않습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 다음 단계 중 하나를 수행합니다.

  - .NET Framework 4 버전으로 업그레이드 합니다.

  - 디버깅을 위해 32비트 버전의 애플리케이션을 빌드합니다.

## <a name="see-also"></a>참고 항목
- [Remote Debugging](../debugger/remote-debugging.md)