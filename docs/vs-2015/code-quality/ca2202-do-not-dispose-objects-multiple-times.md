---
title: 'CA2202: 개체가 여러 번 삭제 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3dfe606e3083c937db3ba3d1e6cd49d34bace853
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697979"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: 개체를 여러 번 삭제하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 구현에 대 한 여러 호출을 일으킬 수 있는 코드 경로 포함 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 또는 Dispose와 같은 이와 동등한 동일한 개체에서 일부 형식의 close () 메서드.

## <a name="rule-description"></a>규칙 설명
 잘못 구현 <xref:System.IDisposable.Dispose%2A> 메서드 예외를 throw 하지 않고 여러 번 호출할 수 있습니다. 그러나이 보장 되지 않습니다 및 생성 되지 않도록 하는 <xref:System.ObjectDisposedException?displayProperty=fullName> 호출 하지 않아야 <xref:System.IDisposable.Dispose%2A> 개체에 대 한 번 이상.

## <a name="related-rules"></a>관련된 규칙
 [CA2000: 범위를 벗어나기 전에 개체를 삭제 합니다.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 코드 경로 관계 없이 구현을 변경 <xref:System.IDisposable.Dispose%2A> 개체에 대 한 번만 호출 됩니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 경우에 <xref:System.IDisposable.Dispose%2A> 개체를 여러 번 안전 하 게 호출할 수 알려져 구현은 나중에 변경 될 수 있습니다.

## <a name="example"></a>예제
 중첩 `using` 문 (`Using` Visual basic에서) 위반 CA2202 경고를 발생할 수 있습니다. 경우 중첩 내부 IDisposable 리소스 `using` 문 외부의 리소스를 포함 `using` 문에서 `Dispose` 중첩 된 리소스의 메서드가 포함 된 리소스를 해제 합니다. 이러한 상황이 발생 하는 경우는 `Dispose` 외부 메서드의 `using` 문을 두 번째로 해당 리소스를 삭제 하려고 합니다.

 다음 예에서 <xref:System.IO.Stream> 외부에서 만든 개체의 Dispose 메서드에서 문을 사용 하 여 내부 끝날 때 해제 됩니다 문을 사용 하는 <xref:System.IO.StreamWriter> 포함 된 개체는 `stream` 개체. 외부의 끝 `using` 문에서 `stream` 개체가 해제 되는 두 번째 시간입니다. 두 번째 릴리스 CA2202에 위반 됩니다.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>예제
 이 문제를 해결 하려면 사용을 `try` / `finally` 외부 대신 블록 `using` 문입니다. 에 `finally` 차단 되어 있는지 확인 합니다는 `stream` 리소스 null이 아닙니다.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
