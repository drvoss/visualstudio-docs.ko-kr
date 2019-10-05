---
title: 'CA1301: 중복 액셀러레이터 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2e992cfb648b9b7f84032abab2f96d3f7cb410d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686864"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: 중복 액셀러레이터 키를 사용하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식 확장 <xref:System.Windows.Forms.Control?displayProperty=fullName> 리소스 파일에 저장 된 동일한 액세스 키가 있는 두 개 이상의 최상위 컨트롤을 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 액셀러레이터 키라고도 하는 선택키를 사용하면 Alt 키를 사용하여 키보드로 컨트롤에 액세스할 수 있습니다. 여러 컨트롤에 중복되는 선택키가 있으면 선택키의 동작이 제대로 정의되지 않은 경우입니다. 사용자 액세스 키를 사용 하 여 의도 한 컨트롤에 액세스 할 수 있습니다 하 고 대상으로 하는 것과 다른 컨트롤을 사용할 수 있습니다.

 이 규칙의 현재 구현 메뉴 항목을 무시합니다. 그러나 동일한 하위 메뉴에 메뉴 항목에는 동일한 액세스 키 없어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 모든 컨트롤에 대 한 고유한 액세스 키를 정의 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 동일한 액세스 키가 포함 된 간단한 폼을 보여 줍니다. 키 표시 되지 않는; 리소스 파일에 저장 됩니다. 그러나 해당 값이 나타나는 주석 처리 된 out `checkBox.Text` 줄. 중복 액셀러레이터 키의 동작을 교환 하 여 검사할 수는 `checkBox.Text` 줄 주석 처리를 사용 하 여 합니다. 그러나이 경우 예제 생성 하지 않습니다는 경고 규칙에서.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
