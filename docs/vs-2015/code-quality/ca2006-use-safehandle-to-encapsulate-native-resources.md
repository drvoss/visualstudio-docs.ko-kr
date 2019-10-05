---
title: 'CA2006: 네이티브 리소스를 캡슐화 하기 위해 SafeHandle 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcf385263eba5a6012097f43b49e7a75166bad42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154407"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle을 사용하여 네이티브 리소스를 캡슐화하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|범주|Microsoft.Reliability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 관리 코드는 <xref:System.IntPtr> 네이티브 리소스에 액세스할 수 있습니다.

## <a name="rule-description"></a>규칙 설명
 사용 `IntPtr` 관리 코드에서 잠재적인 보안 및 안정성 문제를 나타낼 수 있습니다. 모든 용도 `IntPtr` 결정에 검토 해야 합니다 있는지 여부를 사용을 <xref:System.Runtime.InteropServices.SafeHandle> , 유사한 기술을 대신에서 필요 합니다. 경우 문제가 발생 합니다는 `IntPtr` 일부 네이티브 리소스, 메모리, 파일 핸들, 또는 관리 코드를 고유한 것으로 간주 됩니다 소켓을 나타냅니다. 관리 코드 리소스를 소유 하는 경우 이렇게 하지 않으면 리소스 누수 될 때문에 연결 된 네이티브 리소스를 해제도 해야 합니다.

 이러한 시나리오에서는 보안 이나 안정성도 문제가 있습니다 다중 스레드 액세스 하도록 허용 된 경우는 `IntPtr` 와 나타내는 리소스를 해제 하는 방법의 `IntPtr` 제공 됩니다. 이러한 문제는 재활용 포함 된 `IntPtr` 리소스 릴리스 중에 리소스의 동시 사용 하 여 다른 스레드에서 값입니다. 이 경합 상태는 스레드와 읽거나 쓸 수 잘못 된 리소스와 연결 된 데이터를 발생할 수 있습니다. 예를 들어, 형식으로 운영 체제 핸들을 저장 하는 경우는 `IntPtr` 사용자가 모두 호출할 수 있습니다 **닫기** 다른 메서드와 동시에 일종의 동기화 하지 않고 해당 핸들을 사용 하는 코드에 핸들 재활용 및 문제가 발생 했습니다.

 이 핸들 재활용 문제 데이터 손상 및 대부분의 경우 보안 취약점이 발생할 수 있습니다. `SafeHandle` 및 해당 형제 클래스 <xref:System.Runtime.InteropServices.CriticalHandle> 이러한 스레딩 문제를 피할 수 있도록 리소스에 대 한 네이티브 핸들을 캡슐화 하는 메커니즘을 제공 합니다. 또한 사용할 수 있습니다 `SafeHandle` 및 해당 형제 클래스 `CriticalHandle` 문제에 대 한 다른 스레딩, 예를 들어, 기본 메서드 호출에 대해 네이티브 핸들의 복사본이 포함 된 관리 되는 개체의 수명을 제어 합니다. 이런 경우를 제거할 수도 있습니다에 대 한 호출 `GC.KeepAlive`합니다. 사용 하는 경우 발생 하는 성능 오버 헤드가 성공적인 `SafeHandle` 와 그 정도 약간 `CriticalHandle`를 신중 하 게 디자인 자주 줄일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 변환 `IntPtr` 사용량과 `SafeHandle` 네이티브 리소스에 대 한 액세스를 안전 하 게 관리할 수 있습니다. 참조 된 <xref:System.Runtime.InteropServices.SafeHandle> 예제에 대 한 참조 항목입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 경고를 억제 하면 안 됩니다.

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable>
