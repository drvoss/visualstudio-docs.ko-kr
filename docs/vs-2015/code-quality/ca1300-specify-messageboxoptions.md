---
title: 'CA1300: MessageBoxOptions를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7d24298821895a8bbbe9d3743556007abe17c72
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686869"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions를 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 호출의 오버 로드는 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 메서드를 사용 하지 않는 한 <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> 인수.

## <a name="rule-description"></a>규칙 설명
 올바르게 오른쪽에서 왼쪽 읽기 순서를 사용 하는 문화권에 대 한 메시지 상자를 표시 하는 <xref:System.Windows.Forms.MessageBoxOptions> 및 <xref:System.Windows.Forms.MessageBoxOptions> 의 멤버는 <xref:System.Windows.Forms.MessageBoxOptions> 열거형에 전달 되어야 합니다는 <xref:System.Windows.Forms.MessageBox.Show%2A> 메서드. 검사는 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> 오른쪽에서 왼쪽 읽기 순서를 사용할지 여부를 확인 하려면 포함 하는 컨트롤의 속성입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 오버 로드를 호출 합니다 <xref:System.Windows.Forms.MessageBox.Show%2A> 사용 하는 메서드를 <xref:System.Windows.Forms.MessageBoxOptions> 인수입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 오른쪽에서 왼쪽 읽기 순서를 사용 하는 문화권에 대 한 코드 라이브러리를 지역화할 수는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 문화권의 읽기 순서에 대 한 적합 한 옵션이 있는 메시지 상자를 표시 하는 메서드를 보여 줍니다. 표시 되지 않는 리소스 파일, 예제를 빌드하려면 필요 합니다. 리소스 파일 없이 예제를 빌드하려면 및 오른쪽에서 왼쪽 기능을 테스트 하려면 예제의 주석을 따르세요.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
