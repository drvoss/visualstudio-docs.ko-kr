---
title: 'CA1900: 값 형식 필드는 이식 가능 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97a83bf4ba71d0adc71fdb96d4e1c865358c08e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203097"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: 값 형식 필드는 이식 가능해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 최신 설명서를 참조 하세요. [CA1900: 값 형식 필드는 이식 가능 해야](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)합니다.  
  
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|범주|Microsoft.Portability|  
|변경 수준|주요-어셈블리 외부의 필드를 볼 수 있는 경우입니다.<br /><br /> 주요 변경 아님-필드 어셈블리 외부에서 볼 수 없는 경우|  
  
## <a name="cause"></a>원인  
 이 규칙은 명시적 레이아웃을 사용 하 여 선언 된 구조체가 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 올바르게 맞춰지는지 검사 합니다. IA-64 정렬 되지 않은 메모리에 액세스 하 고이 위반을 수정 하지 않으면 프로세스 충돌 허용 하지 않습니다.  
  
## <a name="rule-description"></a>규칙 설명  
 64 비트 운영 체제에서 충돌 불일치 필드를 포함 하는 명시적 레이아웃이 있는 구조체입니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 8 바이트 보다 작은 모든 필드는 해당 크기의 배수에 오프셋 및 필드는 8 바이트에 있어야 합니다. 또는 더 8의 배수가 되는 오프셋 있어야 합니다. 다른 솔루션을 사용 하는 것 `LayoutKind.Sequential` 대신 `LayoutKind.Explicit`적절 한 경우.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 오류가 발생 하는 경우에이 경고를 표시 하지 않습니다.
