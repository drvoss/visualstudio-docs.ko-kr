---
title: 'CA2000: 범위를 벗어나기 전에 개체를 삭제 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 975e1eee68911f8d9d0942e73275fcf521979772
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681496"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|범주|Microsoft.Reliability|  
|변경 수준|주요 변경 아님|  
  
## <a name="cause"></a>원인  
 로컬 개체는 <xref:System.IDisposable> 형식 생성 되지만 개체에 대 한 모든 참조가 범위를 벗어나기 전에 개체 삭제 되지 않습니다.  
  
## <a name="rule-description"></a>규칙 설명  
 모든 참조가 범위를 벗어나기 전에 삭제 가능한 개체를 명시적으로 삭제 되지 않습니다, 경우 개체는 가비지 수집기에서 개체의 종료자를 실행 하는 경우 임의의 시점에 삭제 됩니다. 종료자 수 없게 하는 예외적인 이벤트가 발생할 수 있으므로 실행에서 개체의 개체를 명시적으로 삭제 해야 대신 합니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 이 규칙 위반 문제를 해결 하려면 호출 <xref:System.IDisposable.Dispose%2A> 모든 참조가 범위를 벗어나기 전에 개체에 있습니다.  
  
 사용할 수 있는 참고 합니다 `using` 문 (`Using` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])를 구현 하는 개체를 래핑하 `IDisposable`합니다. 이 방식으로 래핑된 개체를 닫으면 자동으로 삭제 됩니다는 `using` 블록입니다.  
  
 다음은 상황에 따라 여기서는 문을 사용 하 여 IDisposable 개체를 보호 하는 데 충분 하지 않습니다 및 되려면 CA2000 발생할 수 있습니다.  
  
- 개체가 사용 하 여을 외부 try/finally 블록에 생성 되는 필요한 삭제 가능한 개체를 반환 합니다. 블록입니다.  
  
- 삭제 가능한 개체의 멤버를 초기화 하지 말아야 사용 하 여 생성자에 문의 합니다.  
  
- 한 가지 예외 처리기로만 보호 되는 생성자를 중첩 합니다. 예를 들면 다음과 같습니다.  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     CA2000 닫히지 않음 FileStream 개체 StreamReader 개체 생성에서 오류가 발생할 수 있기 때문에 발생 하도록 하면 됩니다.  
  
- 동적 개체는 IDisposable 개체의 Dispose 패턴을 구현 하는 섀도 개체를 사용 해야 합니다.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 `Dispose`와 같은 <xref:System.IO.Stream.Close%2A>를 호출하는 개체에 대해 메서드를 호출하지 않은 경우나 경고를 발생시킨 메서드가 사용자의 개체를 래핑하는 IDisposable 개체를 반환하는 경우 이 규칙에서 경고를 표시해야 합니다.  
  
## <a name="related-rules"></a>관련된 규칙  
 [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: 개체가 여러 번 삭제 하지 마십시오](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>예제  
 삭제 가능한 개체를 반환 하는 메서드를 구현 하는 catch 블록 없이 try/finally 블록 사용 하 여 개체가 삭제 되 고 있는지 확인 합니다. Try/finally 블록을 사용 하 여 오류 지점에서 발생 하 여 해당 개체가 삭제 되는지 확인 하는 예외를 허용 합니다.  
  
 OpenPort1 메서드에서 SomeMethod 위한 호출 또는 ISerializable SerialPort 개체 열기 호출이 실패할 수 있습니다. 이 구현에서 CA2000 경고가 발생 합니다.  
  
 OpenPort2 메서드 두 SerialPort 개체에는 null이 선언 된 및로 설정:  
  
- `tempPort`에 테스트 메서드 작업을 수행 하는 데 사용 됩니다.  
  
- `port`메서드의 반환 값에 사용 됩니다.  
  
  합니다 `tempPort` 생성 되 고 열을 `try` 블록 및 기타 필요한 동일한 작업을 수행 `try` 블록입니다. 끝에 `try` 열린된 포트 블록에 할당 되는 `port` 반환 되는 개체 및 `tempPort` 개체로 설정 됩니다 `null`합니다.  
  
  합니다 `finally` 의 값을 확인 하는 블록 `tempPort`합니다. Null 인 경우 메서드는 작업이 실패 하 고 `tempPort` 모든 리소스가 해제 되도록 닫혀 있습니다. 반환 된 포트 개체는 작업이 실패 한 경우 null 됩니다 메서드의 작업이 성공한 경우 열려 있는 SerialPort 개체를 포함 됩니다.  
  
  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>예제  
 기본적으로 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 컴파일러 오버플로 검사 하는 모든 산술 연산자를 포함 합니다. 모든 Visual Basic 산술 연산은 throw 할 수 있습니다 따라서는 <xref:System.OverflowException>합니다. 이 규칙 CA2000 등에서 예기치 않은 위반이 발생할 수 있습니다. 예를 들어, 다음 CreateReader1 함수는 Visual Basic 컴파일러를 표시 하 고 삭제할 필요가 StreamReader를 발생 시키는 예외를 throw 할 수 있는 추가 대 한 지침을 확인 하는 오버플로 때문에 CA2000 위반을 생성 합니다.  
  
 이 해결 하려면 프로젝트에서 Visual Basic 컴파일러에서 오버플로 검사를 내보내는 것을 비활성화할 수 있습니다 하거나 다음 CreateReader2 함수와 같이 코드를 수정할 수 있습니다.  
  
 오버플로 검사 해제 내보내기를 사용 하지 않으려면 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 **속성**합니다. 클릭 **컴파일할**, 클릭 **고급 컴파일 옵션**를 확인 하 고 **정수 오버플로 검사 해제**합니다.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.IDisposable>   
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)