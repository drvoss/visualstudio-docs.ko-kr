---
title: 사용자 지정 데이터 시각화 도우미 만들기 | Microsoft Docs
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564736"
---
# <a name="create-custom-data-visualizers"></a>사용자 지정 데이터 시각화 도우미 만들기
 A *시각화 도우미* 의 일부인는 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 해당 데이터 형식에 적합 한 방식으로 변수나 개체를 표시 하는 디버거 사용자 인터페이스입니다. 예를 들어, HTML 시각화 도우미는 HTML 문자열을 해석 하 고 브라우저 창에는 것과 동일한 결과 표시 합니다. 비트맵 시각화 도우미는 비트맵 구조를 해석 하 고 나타내므로 그래픽을 표시 합니다. 일부 시각화 도우미 뿐만 아니라 데이터를 보고 수정할 수 있습니다.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 디버거에는 6가지 표준 시각화 도우미가 포함되어 있습니다. 텍스트, HTML, XML 및 JSON 시각화 도우미는 문자열 개체에서 작동 합니다. WPF 트리 시각화 도우미를 WPF 개체 시각적 트리의 속성을 표시 합니다. 데이터 집합 시각화 도우미, DataSet, DataView 및 DataTable 개체에 대 한 작동합니다.

더 많은 시각화 도우미 Microsoft, 타사 및 커뮤니티에서 다운로드할 수 있습니다. 또한 사용자 고유의 시각화 도우미를 작성 하 고에 설치할 수 있습니다는 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 디버거.

디버거 시각화 도우미 돋보기 아이콘으로 표시 됩니다 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 아이콘")합니다. 에 있는 아이콘을 선택할 수 있습니다는 **DataTip**, 디버거 **조사식** 창 또는 **간략 한 조사식** 대화 상자에서 선택한 후 해당 개체에 대 한 적절 한 시각화 도우미입니다.

## <a name="write-custom-visualizers"></a>사용자 지정 시각화 도우미 작성

 > [!NOTE]
 > 네이티브 코드에 대 한 사용자 지정 시각화 도우미를 만들려면 참조 된 [SQLite 네이티브 디버거 시각화 도우미](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) 샘플입니다. UWP 및 Windows 8.x 앱에 대 한 사용자 지정 시각화 도우미가 지원 되지 않습니다.

<xref:System.Object> 및 <xref:System.Array>를 제외한 모든 관리 클래스의 개체에 대해 사용자 지정 시각화 도우미를 작성할 수 있습니다.

디버거 시각화 도우미의 아키텍처는 두 부분으로 구성되어 있습니다.

- 합니다 *디버거 쪽* Visual Studio 디버거 내에서 실행 되 고 만들고 시각화 도우미 사용자 인터페이스를 표시 합니다.

- *디버기(debuggee) 쪽* 코드는 Visual Studio가 디버깅하는 프로세스(*디버기*) 내에서 실행됩니다. 데이터 개체 (예: String 개체)를 시각화 하는 디버기 프로세스에 있습니다. 디버기 쪽 만든 사용자 인터페이스에서 표시 하는 디버거 쪽에 개체를 보냅니다.

디버거 쪽에서 데이터 개체를 수신 합니다.는 *개체 공급자* 구현 하는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 인터페이스. 디버기 쪽을 통해 개체를 전송 합니다 *개체 소스*에서 파생 된 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>합니다.

개체 공급자 데이터를 편집할 수 있는 시각화 도우미를 작성할 수 있는 개체 소스에 데이터를 다시 보낼 수도 있습니다. 식 계산기와 개체 소스를 연결할 개체 공급자를 재정의 하는 있습니다.

디버기 쪽과 디버거 쪽을 통해 서로 통신 <xref:System.IO.Stream> 에 개체 데이터를 serialize 하는 메서드를 <xref:System.IO.Stream> 및 deserialize를 <xref:System.IO.Stream> 데이터 개체로 다시 합니다.

형식이 개방형 형식인 경우에 제네릭 형식에 대 한 시각화 도우미를 작성할 수 있습니다. `DebuggerTypeProxy` 특성을 사용하는 경우에도 이 제한은 동일하게 적용됩니다. 자세한 내용은 참조 하세요 [DebuggerTypeProxy 특성 사용](../debugger/using-debuggertypeproxy-attribute.md)합니다.

사용자 지정 시각화 도우미를 작성할 때는 보안 문제를 고려해야 합니다. 참조 [시각화 도우미 보안 고려 사항](../debugger/visualizer-security-considerations.md)합니다.

다음 단계는 시각화 도우미 만들기의 대략적인 개요를 제공합니다. 자세한 내용은 참조 하세요. [연습: 시각화 도우미를 작성 C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) 나 [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)합니다.

### <a name="to-create-the-debugger-side"></a>디버거 쪽 코드를 만들려면

상속 되는 클래스를 만들면 디버거 쪽 시각화 도우미 사용자 인터페이스를 만들려면 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>를 재정의 하 고는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 인터페이스를 표시 하는 방법입니다. 사용할 수 있습니다 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 시각화 도우미에서 Windows forms, 대화 상자 및 컨트롤을 표시 합니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 메서드를 사용하여 디버거 쪽에서 시각화되는 개체를 가져옵니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>에서 상속된 클래스를 만듭니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 메서드를 재정의하여 인터페이스를 표시합니다. 사용 하 여 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 인터페이스에서 Windows forms, 대화 상자 및 컨트롤을 표시 하는 방법입니다.

4. 적용 <xref:System.Diagnostics.DebuggerVisualizerAttribute>를 표시 하는 시각화 도우미를 제공 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>디버기 쪽 코드를 만들려면

디버기 쪽 코드를 사용 하 여 지정할는 <xref:System.Diagnostics.DebuggerVisualizerAttribute>합니다.

1. 시각화 도우미(<xref:System.Diagnostics.DebuggerVisualizerAttribute>)와 개체 소스(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)를 제공하여 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>를 적용합니다. 개체 소스를 생략 하면 시각화 도우미에는 기본 개체 소스가 사용 합니다.

1. 데이터 개체를 표시 하는 것은 물론 편집 시각화 도우미를 수 있도록 하려면 재정의 `TransferData` 또는 `CreateReplacementObject` 메서드에서 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>합니다.

## <a name="see-also"></a>참고자료

- [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)
- [방법: 시각화 도우미 테스트 및 디버그](../debugger/how-to-test-and-debug-a-visualizer.md)
- [시각화 도우미 API 참조](../debugger/visualizer-api-reference.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)