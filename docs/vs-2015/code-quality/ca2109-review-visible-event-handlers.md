---
title: 'CA2109: 표시 되는 이벤트 처리기를 검토 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9cdf4777aa9ec0222656ac02376c5343d2138c0d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687380"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: 표시되는 이벤트 처리기를 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 public 또는 protected 이벤트 처리 메서드를 발견했습니다.

## <a name="rule-description"></a>규칙 설명
 외부에 표시 되는 이벤트 처리 메서드를 검토 해야 하는 보안 문제를 표시 합니다.

 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다. 처리기와 이벤트 시그니처가 일치으로 모든 이벤트에 노출 된 메서드를 호출 하는 대리자 형식, 이벤트 처리기를 추가할 수 있습니다. 이벤트 모든 코드에 의해 잠재적으로 발생할 수 있습니다 및 신뢰할 수 있는 시스템 코드는 단추 클릭과 같은 사용자 작업에 대 한 응답에서으로 자주 발생 합니다. 보안 검사는 이벤트 처리 메서드를 추가 해도 코드 메서드를 호출 하는 이벤트 처리기를 등록 합니다.

 요청은 이벤트 처리기에서 호출 되는 메서드를 안정적으로 보호 수 없습니다. 도움말을 요구 하는 보안 코드를 신뢰할 수 없는 호출자에서 호출 스택의 호출자를 검사 하 여 보호 합니다. 이벤트 처리기의 메서드를 실행 하는 경우 이벤트에 이벤트 처리기를 추가 하는 코드를 반드시 호출 스택에 있는 나타나지 않습니다. 따라서 호출 스택 수만 항상 신뢰할 수 있는 호출자가 이벤트 처리기 메서드가 호출 되 면 합니다. 그러면 요청이 성공 하려면 이벤트 처리기 메서드에서 수행 됩니다. 또한 메서드가 호출 될 때 요청 된 권한이 어설션 될 수도 있습니다. 이 규칙 위반 문제를 해결 하지 위험이 이러한 이유로, 이벤트 처리 메서드를 검토 한 후 평가할 수만 있습니다. 코드를 검토할 때는 다음 사항을 고려 하십시오.

- 이벤트 처리기는 위험한 또는 사용 권한 어설션 비관리 코드 권한 숨기기 등 악용 하는 작업을 수행 하나요?

- 언제 든 지만 항상 실행할 수 있기 때문에 코드에서 보안 위협을 이란 스택에 있는 호출자를 신뢰할 수 있는?

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 메서드를 검토 하 고 다음 평가:

- 만들 수는 이벤트 처리 메서드에서 public이 아닌?

- 이벤트 처리기에서 모든 위험한 기능을 이동할 수 있나요?

- 보안 요청을 적용 하는 경우이 다른 방법으로 수행할 있습니다?

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 코드에 보안 위험이 없습니다 되도록 신중 하 게 보안을 검토 한 후에이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 코드는 악성 코드가 악용할 수 있습니다 하는 이벤트 처리 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [보안 요청](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
