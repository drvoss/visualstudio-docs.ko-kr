---
title: 'CA2115: GC를 호출 합니다. KeepAlive 네이티브 리소스를 사용 하는 경우 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c035c05480279012fba1101c3a60b020d34b1890
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687334"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 종료자를 사용 하 여 형식에 선언 된 메서드 참조를 <xref:System.IntPtr?displayProperty=fullName> 또는 <xref:System.UIntPtr?displayProperty=fullName> 필드를 호출 하지 않습니다 하지만 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 관리 되는 코드에 대 한 참조가 더 이상 없으면 가비지 수집에서 개체를 종료 합니다. 개체에 대 한 관리 되지 않는 참조는 가비지 수집을 방지 하지 않습니다. 이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.

 이 규칙이 있다고 가정 <xref:System.IntPtr> 고 <xref:System.UIntPtr> 필드는 관리 되지 않는 리소스에 대 한 포인터를 저장 합니다. 관리 되지 않는 리소스를 해제 하는 종료자의 목적은 이기 때문에 종료 자가 포인터 필드에서 가리키는 관리 되지 않는 리소스를 해제 합니다 규칙을 가정 합니다. 이 규칙은 또한 메서드를 비관리 코드에 관리 되지 않는 리소스를 전달 하려면 포인터 필드를 참조 하 고는 가정 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면에 대 한 호출을 추가 <xref:System.GC.KeepAlive%2A> 메서드를 현재 인스턴스를 전달 합니다 (`this` 에서 C# 및 C++) 인수로 합니다. 가비지 컬렉션에서 개체 보호 되어야 합니다는 코드의 마지막 줄 다음 호출을 배치 합니다. 호출 직후 <xref:System.GC.KeepAlive%2A>, 개체 다시 비율은 가비지 컬렉션에 대 한 준비를 관리 되는 참조가 없는 가정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙은 거짓 긍정을 야기할 수 있는 몇 가지 사항을 가정 합니다. 안전 하 게 하는 경우이 규칙에서 경고를 무시할 수 있습니다.

- 종료자의 콘텐츠를 해제 하지 않는 합니다 <xref:System.IntPtr> 또는 <xref:System.UIntPtr> 메서드에서 참조 되는 필드입니다.

- 메서드를 통과 하지 못한 합니다 <xref:System.IntPtr> 또는 <xref:System.UIntPtr> 비관리 코드로 필드입니다.

  신중 하 게 제외 하기 전에 다른 메시지를 검토 합니다. 이 규칙 재현 하 고 디버그 하기 어려운 오류를 감지 합니다.

## <a name="example"></a>예제
 다음 예제에서 `BadMethod`에는 `GC.KeepAlive`에 대한 호출이 포함되지 않으므로 규칙을 위반합니다. `GoodMethod` 수정 된 코드를 포함합니다.

> [!NOTE]
> 이 예제는 의사 코드입니다. 코드가 컴파일되고 실행되더라도 관리되지 않는 리소스가 생성 또는 해제되지 않으므로 경고가 발생하지 않습니다.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
