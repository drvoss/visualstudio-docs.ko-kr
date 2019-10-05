---
title: 'CA2001: 문제가 있는 메서드를 호출 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26f50580c8d29e24b25a9dad520a81d22a3dfc0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189066"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: 문제가 있는 메서드는 호출하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|범주|Microsoft.Reliability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.

## <a name="rule-description"></a>규칙 설명
 불필요 하 고 잠재적으로 위험한 메서드를 호출 하지 마세요.

 이 규칙 위반 멤버 다음 방법 중 하나를 호출할 때 발생 합니다.

|메서드|설명|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC를 호출 합니다. 수집 응용 프로그램 성능에 크게 영향을 줄 수 있으며 거의 필요 합니다. 자세한 내용은 참조는 [Rico Mariani의 Performance Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) MSDN에서 블로그 항목입니다.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend 및 Thread.Resume가 사용 되지 않으며 예기치 않은 동작  다른 클래스를 사용 합니다 <xref:System.Threading> 네임 스페이스와 같은 <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, 및 <xref:System.Threading.Semaphore> 스레드를 동기화 하거나 리소스를 보호 합니다.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle 메서드 유효 하지 않은 핸들을 반환할 수 있으므로 보안 위험이 발생 합니다. 참조를 <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> 하며 <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> DangerousGetHandle 메서드를 안전 하 게 사용 하는 방법에 대 한 자세한 내용은 합니다.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|이러한 메서드는 예기치 않은 위치에서 어셈블리를 로드할 수 있습니다. 예를 들어, Suzanne Cook의.NET CLR 정보 블로그 게시물을 참조 [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) 하 고 [바인딩 컨텍스트 선택](http://go.microsoft.com/fwlink/?LinkId=164451) 어셈블리를 로드 하는 방법에 대 한 자세한 내용은 MSDN 웹 사이트입니다.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|사용자 코드를 관리 되는 프로세스 실행을 시작 시간, 하기가 너무 늦게 CoSetProxyBlanket를 안정적으로 호출 합니다. CLR (공용 언어 런타임) 사용자 P/Invoke 성공 하지 못하게 할 수 있는 초기화 작업을 수행 합니다.<br /><br /> 에 관리 되는 응용 프로그램에 대 한 CoSetProxyBlanket 호출 하는 경우 네이티브 코드를 사용 하 여 프로세스를 시작 하는 것이 좋습니다 (C++) 실행 파일, 네이티브 코드에서 CoSetProxyBlanket 호출 하 고 다음 프로세스에서 관리 코드 응용 프로그램을 시작 합니다. (해야 런타임 버전 번호를 지정 합니다.)|

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제거 하거나 대체 위험이 나 문제가 있는 메서드를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 문제가 있는 메서드에 대 한 대안이 사용할 경우에이 규칙에서 메시지를 표시 해야 합니다.

## <a name="see-also"></a>참고 항목
 [안정성 경고](../code-quality/reliability-warnings.md)
