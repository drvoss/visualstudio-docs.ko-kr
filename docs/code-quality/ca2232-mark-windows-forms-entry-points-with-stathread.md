---
title: 'CA2232: Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230765"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
어셈블리가 <xref:System.Windows.Forms> 네임 스페이스를 참조 하 고 해당 진입점이 <xref:System.STAThreadAttribute?displayProperty=fullName> 특성으로 표시 되어 있지 않습니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.STAThreadAttribute>응용 프로그램에 대 한 COM 스레딩 모델이 단일 스레드 아파트 임을 나타냅니다. 이 특성은 Windows Forms을 사용하는 애플리케이션의 진입점에 있어야 합니다. 이 특성을 생략하면 Windows 구성 요소가 제대로 작동하지 않을 수 있습니다. 특성이 없는 경우 응용 프로그램은 Windows Forms에 대해 지원 되지 않는 다중 스레드 아파트 모델을 사용 합니다.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]응용 프로그램 프레임 워크를 사용 하는 프로젝트는 **Main** 메서드를 STAThread로 표시할 필요가 없습니다. 컴파일러 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 는 자동으로이를 수행 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 진입점에 <xref:System.STAThreadAttribute> 특성을 추가 합니다. <xref:System.MTAThreadAttribute?displayProperty=fullName> 특성이 있는 경우 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
.NET Compact Framework에 대해 개발 하는 경우에는이 규칙에서 경고를 표시 하지 않아도 됩니다. 특성은 <xref:System.STAThreadAttribute> 필요 하지 않으며 지원 되지 않습니다.

## <a name="example"></a>예제
다음 예에서는의 <xref:System.STAThreadAttribute>올바른 사용법을 보여 줍니다.

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]