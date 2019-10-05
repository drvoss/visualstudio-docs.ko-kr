---
title: 'CA2232: Mark Windows Forms 진입점을 STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e8b7242fcd82db1a0cfb82cf6cd6df5a9f75084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435422"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 어셈블리 참조를 <xref:System.Windows.Forms> 네임 스페이스 및 해당 진입점으로 표시 되지 않으면를 <xref:System.STAThreadAttribute?displayProperty=fullName> 특성입니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.STAThreadAttribute> COM 스레딩 모델이 응용 프로그램에 대 한 단일 스레드 아파트 임을 나타냅니다. 이 특성은 Windows Forms을 사용하는 애플리케이션의 진입점에 있어야 합니다. 이 특성을 생략하면 Windows 구성 요소가 제대로 작동하지 않을 수 있습니다. 특성이 없는 경우 응용 프로그램에 Windows Forms에 대 한 지원 되지 않는 다중 스레드 아파트 모델을 사용 합니다.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 응용 프로그램 프레임 워크를 사용 하는 프로젝트는 표시 하지 않아도 합니다 **Main** STAThread 사용 하 여 메서드. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 컴파일러가 자동으로 수행 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 추가 <xref:System.STAThreadAttribute> 진입점에 특성입니다. 경우는 <xref:System.MTAThreadAttribute?displayProperty=fullName> 특성이 있는 경우 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 .NET Compact framework 개발 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다는 <xref:System.STAThreadAttribute> 특성이 불필요 하 고 지원 되지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는의 올바른 사용법을 보여 주는 <xref:System.STAThreadAttribute>합니다.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
