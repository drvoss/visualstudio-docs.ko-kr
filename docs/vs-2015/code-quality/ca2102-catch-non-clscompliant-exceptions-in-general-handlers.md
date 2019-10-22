---
title: 'CA2102: 일반 처리기에서 비 CLSCompliant 예외를 Catch 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051b59183a761477476269480ecdf83ccbf0cb37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652170"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|범주|Microsoft.Security|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 @No__t_0로 표시 되지 않았거나 `RuntimeCompatibility(WrapNonExceptionThrows = false)`로 표시 되어 있고 <xref:System.Exception?displayProperty=fullName>를 처리 하는 catch 블록을 포함 하는 어셈블리의 멤버 이며 바로 다음 일반 catch 블록을 포함 하지 않습니다. 이 규칙은 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 어셈블리를 무시 합니다.

## <a name="rule-description"></a>규칙 설명
 @No__t_0를 처리 하는 catch 블록은 CLS (공용 언어 사양) 규격 예외를 모두 catch 합니다. 그러나 CLS 규격이 아닌 예외는 catch 하지 않습니다. CLS 규격이 아닌 예외는 네이티브 코드 또는 MSIL (Microsoft 중간 언어) 어셈블러에 의해 생성 된 관리 코드에서 throw 될 수 있습니다. C# 및 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 컴파일러는 cls 규격이 아닌 예외를 throw 하는 것을 허용 하지 않으며 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]는 cls 규격이 아닌 예외를 catch 하지 않습니다. Catch 블록의 의도에서 모든 예외를 처리 하는 경우 다음 일반 catch 블록 구문을 사용 합니다.

- C#: `catch {}`

- C++: `catch(...) {}` 또는 `catch(Object^) {}`

  처리 되지 않은 CLS 규격이 아닌 예외는 catch 블록에서 이전에 허용 된 사용 권한을 제거할 때 보안 문제가 됩니다. CLS 규격이 아닌 예외가 catch 되지 않으므로 CLS 규격이 아닌 예외를 throw 하는 악의적인 메서드는 상승 된 권한으로 실행할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 모든 예외를 catch 할 때이 규칙 위반 문제를 해결 하려면 일반 catch 블록을 대체 하거나 추가 하거나 어셈블리 `RuntimeCompatibility(WrapNonExceptionThrows = true)` 표시 합니다. Catch 블록에서 사용 권한을 제거 하는 경우 일반 catch 블록의 기능을 복제 합니다. 모든 예외를 처리할 의도가 아닌 경우 <xref:System.Exception>를 처리 하는 catch 블록을 특정 예외 형식을 처리 하는 catch 블록으로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 Try 블록에 CLS 규격이 아닌 예외를 생성할 수 있는 문이 포함 되지 않은 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 네이티브 코드나 관리 코드는 CLS 규격이 아닌 예외를 throw 할 수 있으므로 try 블록 내의 모든 코드 경로에서 실행할 수 있는 모든 코드에 대 한 지식이 필요 합니다. CLS 규격이 아닌 예외는 공용 언어 런타임에 의해 throw 되지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 CLS 규격이 아닌 예외를 throw 하는 MSIL 클래스를 보여 줍니다.

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하는 일반 catch 블록을 포함 하는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 위의 예제를 다음과 같이 컴파일합니다.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>관련 규칙
 [CA1031: 일반적인 예외 형식을 catch하지 마십시오.](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>관련 항목:
 [예외 및 예외 처리](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm (IL 어셈블러)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [보안 검사 재정의](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
