---
title: 'CA1063: IDisposable을 올바르게 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90f218165c0543c1881857191efd202717c6e372
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820892"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable을 올바르게 구현하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 `IDisposable` 올바르게 구현 되지 않았습니다. 이 문제에 대 한 몇 가지 원인은 다음과 같습니다.

- IDisposable은 다시 클래스에서 구현 합니다.

- 마무리 다시 재정의 됩니다.

- Dispose는 재정의 됩니다.

- Dispose () public이 아닙니다 봉인 또는 Dispose를 명명 합니다.

- Dispose (bool) 보호, 가상 또는 봉인 되지 않은 아닙니다.

- Dispose ()는 봉인 되지 않은 형식에서 Dispose(true)을 호출 해야 합니다.

- 봉인 되지 않은 형식에 대 한 Finalize 구현 중 하나 또는 모두 dispose (bool) 또는 사례 클래스 종료자를 호출 하지 않습니다.

  이러한 패턴 중 하나를 위반 하면이 경고가 트리거됩니다.

  봉인 되지 않은 모든 루트 IDisposable 형식 자체 보호 된 가상 void dispose (bool) 메서드를 제공 해야 합니다. Dispose () 호출 Dispose(true) 및 Finalize dispose (false)를 호출 해야 합니다. 봉인 되지 않은 루트 IDisposable 형식을 만들려는 경우 dispose (bool)을 정의 하 고 호출 해야 합니다. 자세한 내용은 [관리 되지 않는 리소스 정리](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) 에 [Framework 디자인 지침](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) .NET Framework 설명서의 섹션입니다.

## <a name="rule-description"></a>규칙 설명
 모든 IDisposable 형식은 Dispose 패턴을 올바르게 구현해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 코드를 검사는 다음과 같은 해결이이 위반이 해결 됩니다.

- 구현 되는 인터페이스 목록에서 IDisposable을 제거 {0} 하 고 대신 기본 클래스 Dispose 구현을 재정의 합니다.

- 형식에서 종료자를 제거 {0}, Dispose (bool disposing)를 재정의 하 고 종료 논리를 코드 경로에서 '삭제'는 false입니다.

- 제거 {0}, Dispose (bool disposing)를 재정의 하 고 dispose 논리가 코드 경로에서 '삭제'가 true입니다.

- 되도록 {0} public로 선언 되 고 봉인 합니다.

- 이름 바꾸기 {0} '삭제'를 public 및 sealed로 선언 되어 있는지 확인 합니다.

- 했는지 {0} 보호, 가상, 선언 및 봉인 되지 않은 합니다.

- 수정 {0} GC 호출 Dispose(true)를 호출 합니다. 현재 개체 인스턴스에 대해 SuppressFinalize ('this' 또는 'Me' in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])를 반환 합니다.

- 수정 {0} dispose (false) 호출을 반환 합니다.

- 봉인 되지 않은 루트 IDisposable 클래스를 작성 하는 경우에 IDisposable의 구현은이 단원의 앞에서 설명한 패턴을 따르는지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="pseudo-code-example"></a>의사 코드 예제
 다음 의사 코드 및 네이티브 리소스를 dispose (bool) 관리를 사용 하는 클래스에서 구현 되는 방법의 일반적인 예제를 제공 합니다.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
