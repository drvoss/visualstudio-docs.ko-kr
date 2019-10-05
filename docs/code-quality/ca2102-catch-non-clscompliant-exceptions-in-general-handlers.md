---
title: 'CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233007"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하세요.

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> 또는로 표시 되지 않은 어셈블리의 멤버에는를 처리 <xref:System.Exception?displayProperty=fullName> 하는 `RuntimeCompatibility(WrapNonExceptionThrows = false)` catch 블록이 포함 되어 있으며,이 블록에는 바로 다음 일반 catch 블록이 포함 되어 있지 않습니다. 이 규칙은 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 어셈블리를 무시 합니다.

## <a name="rule-description"></a>규칙 설명

를 처리 <xref:System.Exception> 하는 catch 블록은 모든 CLS (공용 언어 사양) 규격 예외를 catch 합니다. 그러나 CLS 규격이 아닌 예외는 catch 하지 않습니다. CLS 규격이 아닌 예외는 네이티브 코드 또는 MSIL (Microsoft 중간 언어) 어셈블러에 의해 생성 된 관리 코드에서 throw 될 수 있습니다. 및 C# [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 컴파일러는 cls 규격이 아닌 예외 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 를 throw 하는 것을 허용 하지 않으며 cls 규격이 아닌 예외를 catch 하지 않습니다. Catch 블록의 의도에서 모든 예외를 처리 하는 경우 다음 일반 catch 블록 구문을 사용 합니다.

- C#: `catch {}`

- C++: `catch(...) {}` 또는`catch(Object^) {}`

처리 되지 않은 CLS 규격이 아닌 예외는 catch 블록에서 이전에 허용 된 사용 권한을 제거할 때 보안 문제가 됩니다. CLS 규격이 아닌 예외가 catch 되지 않으므로 CLS 규격이 아닌 예외를 throw 하는 악의적인 메서드는 상승 된 권한으로 실행할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

모든 예외를 catch 할 때이 규칙 위반 문제를 해결 하려면 일반 catch 블록을 대체 하거나 추가 하거나 어셈블리 `RuntimeCompatibility(WrapNonExceptionThrows = true)`를 표시 합니다. Catch 블록에서 사용 권한을 제거 하는 경우 일반 catch 블록의 기능을 복제 합니다. 모든 예외를 처리할 의도가 아니면 특정 예외 형식을 처리 하는 catch 블록으로 처리 <xref:System.Exception> 하는 catch 블록을 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

Try 블록에 CLS 규격이 아닌 예외를 생성할 수 있는 문이 포함 되지 않은 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 네이티브 코드나 관리 코드는 CLS 규격이 아닌 예외를 throw 할 수 있으므로 try 블록 내의 모든 코드 경로에서 실행할 수 있는 모든 코드에 대 한 지식이 필요 합니다. CLS 규격이 아닌 예외는 공용 언어 런타임에 의해 throw 되지 않습니다.

## <a name="example-1"></a>예제 1

다음 예제에서는 CLS 규격이 아닌 예외를 throw 하는 MSIL 클래스를 보여 줍니다.

```cpp
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

## <a name="example-2"></a>예제 2

다음 예제에서는 규칙을 충족 하는 일반 catch 블록을 포함 하는 메서드를 보여 줍니다.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

위의 예제를 다음과 같이 컴파일합니다.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>관련 규칙

[CA1031: 일반적인 예외 형식을 catch 하지 마십시오.](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>참고 항목

- [예외 및 예외 처리](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe(IL 어셈블러)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [언어 독립성 및 언어 독립적 구성 요소](/dotnet/standard/language-independence-and-language-independent-components)