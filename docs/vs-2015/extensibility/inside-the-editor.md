---
title: 편집기 내부에서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 32
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8dfc751b040bd775c3f55ff7db804c2a16d45d5f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414625"
---
# <a name="inside-the-editor"></a>편집기 기본 사항
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기는 텍스트 보기 및 사용자 인터페이스에서 모델 별도 텍스트 편집기를 유지 하도록 설계 된 다른 하위 시스템의 숫자로 구성 됩니다.  
  
 이 섹션에서는 편집기의 다양 한 측면을 설명합니다.  
  
- [하위 시스템 개요](../extensibility/inside-the-editor.md#overview)  
  
- [텍스트 모델](../extensibility/inside-the-editor.md#textmodel)  
  
- [텍스트 보기](../extensibility/inside-the-editor.md#textview)  
  
  이 섹션에서는 편집기의 기능을 설명합니다.  
  
- [태그 및 분류자](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
- [선의 도구 영역](../extensibility/inside-the-editor.md#adornments)  
  
- [프로젝션](../extensibility/inside-the-editor.md#projection)  
  
- [개요](../extensibility/inside-the-editor.md#outlining)  
  
- [마우스 바인딩](../extensibility/inside-the-editor.md#mousebindings)  
  
- [편집기 작업](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview"></a> 하위 시스템 개요  
  
### <a name="text-model-subsystem"></a>텍스트 모델 하위 시스템  
 텍스트 모델 하위 시스템은 텍스트를 나타내고 해당 조작을 사용 하도록 설정 하는 일을 담당 합니다. 텍스트 모델 하위 시스템 포함을 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 편집기에서 표시 되는 문자 시퀀스를 설명 하는 인터페이스입니다. 이 텍스트 수정, 추적 및 여러 가지 방법으로 조작할 수 있습니다. 텍스트 모델 다음 측면에 대 한 형식을 제공합니다.  
  
- 텍스트 파일을 연결 하 고 읽기 및 쓰기 파일 시스템에서 관리 하는 서비스입니다.  
  
- 차이점 보관용 사용 하는 서비스 개체의 두 시퀀스 간의 최소 차이점이 발견입니다.  
  
- 다른 버퍼에 있는 텍스트의 하위 집합 측면에서 버퍼에 텍스트를 설명 하는 데 사용 되는 시스템입니다.  
  
  텍스트 모델 하위 시스템은 사용자 인터페이스 (UI) 개념의 무료입니다. 예를 들어는 텍스트 서식 지정 또는 텍스트 레이아웃을 처리 하지 않습니다 하 고 텍스트를 사용 하 여 연결할 수 있는 시각적 장식 알지 합니다.  
  
  텍스트 모델 하위 시스템의 공용 형식에 Microsoft.VisualStudio.Text.Data.dll Microsoft.VisualStudio.CoreUtilitiy.dll,.NET Framework 기본 클래스 라이브러리는 Framework MEF (Managed Extensibility)에 의존 하는 포함 됩니다.  
  
### <a name="text-view-subsystem"></a>텍스트 뷰 하위 시스템  
 텍스트 뷰 하위 시스템은 서식 지정 및 텍스트를 표시 하는 일을 담당 합니다. 이 하위 시스템의 형식은 형식을 Windows Presentation Foundation (WPF)를 사용 하는 여부에 따라 두 계층으로 나뉩니다. 가장 중요 한 유형은 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 고 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, 표시 되는 텍스트 줄 집합 캐럿, 선택 및 WPF UI 요소를 사용 하 여 텍스트를 표시 하기 위한 기능을 제어 하는 합니다. 이 하위 시스템은 또한 텍스트 주위에 여백을 표시 영역을 제공 합니다. 이러한 여백, 확장할 수 있으며 다양 한 종류의 콘텐츠 및 시각적 효과 포함할 수 있습니다. 여백에 줄 번호 표시 및 스크롤 막대는 있습니다.  
  
 텍스트 뷰 하위 시스템의 공용 형식 Microsoft.VisualStudio.Text.UI.dll Microsoft.VisualStudio.Text.UI.Wpf.dll에 포함 됩니다. 플랫폼 독립적인 요소를 포함 하는 첫 번째 어셈블리를 하 고 두 번째 WPF 관련 요소를 포함 합니다.  
  
### <a name="classification-subsystem"></a>분류 하위 시스템  
 분류 하위 시스템은 텍스트의 글꼴 속성을 결정 합니다. 분류자를 다른 클래스로, 예를 들어, "키워드" 또는 "comment" 텍스트를 중단합니다. 분류 서식 맵에 관련 된 이러한 클래스 실제 글꼴 속성을 예를 들어 "Blue Consolas 10pt"입니다. 이 정보는 형식을 지정 하 고 텍스트를 렌더링 하는 경우 텍스트 보기에서 사용 됩니다. 태그 지정 텍스트의 범위와 연결 되도록 데이터를 사용 하면이 항목의 뒷부분에 자세히 설명 되어 있습니다.  
  
 분류 하위 시스템의 공용 형식 Microsoft.VisualStudio.Text.Logic.dll에 포함 되어 있으며 Microsoft.VisualStudio.Text.UI.Wpf.dll에 포함 된 분류의 시각적 요소를 상호 작용 합니다.  
  
### <a name="operations-subsystem"></a>작업 하위 시스템  
 작업 하위 시스템 편집기 동작을 정의 합니다. 실행 취소 시스템 및 Visual Studio 편집기 명령에 대 한 구현을 제공합니다.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>자세히 보기 텍스트 모델 및 텍스트 보기  
  
### <a name="textmodel"></a> 텍스트 모델  
 텍스트 모델 하위 시스템 텍스트 형식의 다른 그룹으로 구성 됩니다. 이러한 텍스트 버퍼, 텍스트 스냅숏 및 텍스트 범위를 포함 합니다.  
  
#### <a name="text-buffers-and-text-snapshots"></a>텍스트 버퍼 및 텍스트 스냅숏  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 인터페이스는 인코딩을 사용 하 여 u t F-16을 사용 하 여 인코드된 유니코드 문자 시퀀스로 나타냅니다는 `String` .NET Framework의 형식입니다. 텍스트 버퍼를 파일 시스템 문서로 지속 될 수 있지만 필요 하지 않습니다.  
  
 합니다 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 빈 텍스트 버퍼를 또는 또는 문자열에서 초기화 되는 텍스트 버퍼를 만드는 데 <xref:System.IO.TextReader>합니다. 텍스트 버퍼를 파일 시스템에 유지할 수는 <xref:Microsoft.VisualStudio.Text.ITextDocument>합니다.  
  
 스레드를 호출 하 여 텍스트 버퍼의 소유권을 갖습니다 될 때까지 모든 스레드에서 텍스트 버퍼를 편집할 수 있습니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>합니다. 그런 다음 해당 스레드만 편집을 수행할 수 있습니다.  
  
 텍스트 버퍼의 수명 동안 여러 버전을 거칠 수 있습니다. 버퍼를 편집할 때마다 및 변경할 수 없는 새 버전이 생성 됩니다 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 버퍼의 해당 버전의 내용을 나타냅니다. 텍스트 스냅숏을 변경할 수 없기 때문에 나타내는 텍스트 버퍼 계속 변경 하는 경우에 텍스트 스냅숏으로 제한 없이 모든 스레드에서 액세스할 수 있습니다.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>텍스트 스냅숏 및 스냅숏 줄 텍스트  
 문자 시퀀스 또는 줄의 시퀀스로 텍스트 스냅숏의 콘텐츠를 볼 수 있습니다. 문자와 줄 모두 인덱스 0부터 시작 됩니다. 빈 텍스트 스냅숏을 0 개의 문자 및 빈 줄을 포함합니다. 유효한 유니코드 줄 바꿈 문자 시퀀스를 하거나 시작 또는 버퍼의 끝 줄 구분 됩니다. 줄 바꿈 문자를 텍스트 스냅숏의 명시적으로 표시 됩니다 및 텍스트 스냅숏의 줄 바꿈은 일부만 필요가 동일 합니다.  
  
> [!NOTE]
> Visual Studio 편집기에서 줄 바꿈 문자에 대 한 자세한 내용은 참조 하세요. [인코딩 및 줄 바꿈](../ide/encodings-and-line-breaks.md)합니다.  
  
 텍스트 줄으로 표시 됩니다는 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 개체를 특정 문자 위치 또는 특정 줄 번호에 대 한 텍스트 스냅숏에서 얻을 수 있습니다.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Snapshotpoints가 고 SnapshotSpans, NormalizedSnapshotSpanCollections  
 <xref:Microsoft.VisualStudio.Text.SnapshotPoint> 스냅숏으로의 문자 위치를 나타냅니다. 위치는 0과 스냅숏의 길이 하도록 보장 됩니다. <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 스냅숏에 있는 텍스트 범위를 나타냅니다. 0과 스냅숏의 길이 사이 최종 위치로 보장 됩니다. 합니다 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 집합으로 이루어져 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 동일한 스냅숏에서 개체입니다.  
  
#### <a name="spans-and-normalizedspancollections"></a>범위 및 NormalizedSpanCollections  
 <xref:Microsoft.VisualStudio.Text.Span> 텍스트 스냅숏에 있는 텍스트 범위를 적용할 수 있는 간격을 나타냅니다. 범위는 0을 포함 하 여 모든 위치에서 시작할 수 있도록 스냅숏 위치는 0부터 시작 합니다. 합니다 `End` 범위의 속성은 합계에 해당 `Start` 속성 및 해당 `Length` 속성입니다. A `Span` 으로 인덱싱된 문자를 포함 하지는 `End` 속성입니다. 시작 된 범위를 예를 들어 = 5이 고 길이 = 3에 끝 = 8, 5, 6 및 7 위치에 있는 문자를 포함 하 고 있습니다. 이 범위에 대 한 표기법은 5..8) 합니다.  
  
 두 범위 공통점은 모든 위치에서 끝 위치를 포함 하는 경우 교차 합니다. 따라서 교차 [3, 5) 및 [2, 7)는 [3, 5) 및 교차 [3, 5) 및 [5, 7)는 [5, 5). (있음을 [5, 5)는 빈 범위입니다.)  
  
 두 범위 끝 위치를 제외 하 고 위치 공통적으로 있는 경우 겹칩니다. 빈 범위 되지 다른 범위를 겹치는 및의 두 범위가 겹치기 비어 있지 않습니다.  
  
 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 해당 범위의 시작 속성을 순서 대로 범위 목록이 있습니다. 목록에서 중복 되거나 인접 범위 병합 됩니다. 예를 들어 범위 집합을 지정 [5..9), [0..1), [3..6), 및 [9..10), 정규화 된 목록은 범위 [0..1), [3..10) 합니다.  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit 고 textversion이 텍스트 변경 알림  
 텍스트 버퍼의 내용을 사용 하 여 변경할 수 있습니다는 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체입니다. 이러한 개체를 만드는 (중 하나를 사용 하 여 합니다 `CreateEdit()` 메서드의 <xref:Microsoft.VisualStudio.Text.ITextBuffer>) 텍스트 편집 내용을 구성 된 텍스트 트랜잭션을 시작 합니다. 모든 편집은 일부 문자열 버퍼의 텍스트 범위를 대체 합니다. 트랜잭션이 시작 된 경우 모든 편집 내용을 확인 하 고 좌표 버퍼의 스냅숏을 기준으로 표시 됩니다. <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체가 동일한 트랜잭션에서 다른 편집의 영향을 받는 편집의 좌표를 조정 합니다.  
  
 예를 들어이 문자열을 포함 하는 텍스트 버퍼를 고려 합니다.  
  
```  
abcdefghij  
```  
  
 두 편집에서 범위를 대체 하는 하나의 편집을 포함 하는 트랜잭션이 적용 [2..4) 문자를 사용 하 여 `X` 에서 범위를 대체 하는 두 번째 편집 [6..9) 문자를 사용 하 여 `Y`입니다. 결과이 버퍼:  
  
```  
abXefYj  
```  
  
 첫 번째 편집 내용이 적용 되기 전에 두 번째 편집에 대 한 좌표를 트랜잭션의 시작 부분에서 버퍼의 내용에 대해 계산 된 것입니다.  
  
 버퍼에 변경 내용을 적용 하면를 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체를 호출 하 여 커밋됩니다 해당 `Apply()` 메서드. 하나 이상의 비어 있지 않은 편집 되었으면 새 <xref:Microsoft.VisualStudio.Text.ITextVersion> 만들어지면 새 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 만들어지면 하나의 `Changed` 이벤트가 발생 합니다. 모든 텍스트 버전이 다른 텍스트 스냅숏입니다. 텍스트 스냅숏으로 편집 트랜잭션이, 후 텍스트 버퍼의 전체 상태 나타내지만 텍스트 버전에서에서 변경 된 사항만 하나의 스냅숏만 다음에 대해 설명 합니다. 일반적으로 텍스트 스냅숏은 한 번 사용 하며 텍스트 버전 일정 시간 동안 활성 상태로 유지 해야 하는 동안 다음 삭제 합니다.  
  
 텍스트 버전을 포함 한 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>합니다. 이 컬렉션의 변경 내용을 설명 합니다.는 스냅숏을 적용 되 면 후속 스냅숏이 생성 됩니다. 모든 <xref:Microsoft.VisualStudio.Text.ITextChange> 컬렉션의 변경, 대체 문자열 및 대체 문자열의 문자 위치를 포함 합니다. 기본 삽입을 위해 대체 문자열이 비어 및 기본 삭제에 대 한 대체 문자열이 비어 있습니다. 정규화 된 컬렉션은 항상 `null` 텍스트 버퍼의 가장 최근 버전에 대 한 합니다.  
  
 하나의 <xref:Microsoft.VisualStudio.Text.ITextEdit> 언제 든 지는 텍스트 버퍼 개체를 인스턴스화할 수 있습니다 하 고 모든 텍스트 편집 (소유권을 요구 한) 경우 텍스트 버퍼를 소유 하는 스레드에서 수행 해야 합니다. 텍스트 편집을 호출 하 여 중단 될 수 있습니다 해당 `Cancel` 메서드 또는 해당 `Dispose` 메서드.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 해줍니다 `Insert()`, `Delete()`, 및 `Replace()` 와 유사 하는 방법에는 <xref:Microsoft.VisualStudio.Text.ITextEdit> 인터페이스입니다. 이러한 호출 된 것과 동일한 효과가 만들기는 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체는 유사한 호출을 실행 하 고 편집에 적용 합니다.  
  
#### <a name="tracking-points-and-tracking-spans"></a>추적 지점 및 범위를 추적 합니다.  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> 텍스트 버퍼의 문자 위치를 나타냅니다. 이동할 문자의 위치를 발생 시키는 방식으로 버퍼를 편집, 추적 지점을 함께 이동 합니다. 예를 들어 추적 지점 위치를 나타냅니다 10 버퍼 다섯 개의 문자 버퍼의 시작 부분에 삽입 됩니다 하는 경우 추적 지점은 다음 위치를 나타냅니다 15. 해당 동작은에 의해 결정 됩니다 삽입 추적 지점을 가리키는 위치에 정확 하 게 있는 경우 해당 <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, 수 `Positive` 또는 `Negative`합니다. 추적 모드를이 양수인 경우 추적 지점은; 삽입의 끝에 이제는 동일한 문자를 가리키는 경우 추적 모드를 음수 이면 추적 지점의 원래 위치에 삽입 된 첫 번째 문자를 가리킵니다. 추적 지점에서 표시 되는 위치에 있는 문자가 삭제 되 면 추적 지점은 삭제 범위 뒤에 오는 첫 번째 문자로 이동 합니다. 예를 들어 추적 지점 위치 5에 있는 문자가 나타내며 3-6 위치의 문자 삭제를 추적 지점 3 위치의 문자를 참조 합니다.  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 하나만 위치 대신 문자 범위를 나타냅니다. 해당 동작은에 의해 결정 됩니다 해당 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>합니다. 범위 추적 모드를 사용 하는 경우 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 범위 추적 모드를 사용 하는 경우 가장자리;에 삽입 하는 텍스트를 통합 하기 위해 추적 범위 증가 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 추적 범위 가장자리에 삽입 하는 텍스트를 통합 하지 않습니다. 그러나 범위 추적 모드를 사용 하는 경우 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>에 삽입 시작 방향으로 현재 위치를 푸시 경우 범위 추적 모드를 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 삽입이 끝날 때 현재 위치를 푸시합니다.  
  
 속해 있는 텍스트 버퍼의 모든 스냅숏에 대 한 추적 요소의 위치 또는 추적 범위의 범위를 가져올 수 있습니다. 추적 지점 및 추적 범위 모든 스레드에서 안전 하 게 참조할 수 있습니다.  
  
#### <a name="content-types"></a>콘텐츠 형식  
 콘텐츠 유형은 여러 종류의 콘텐츠를 정의 하는 메커니즘입니다. 콘텐츠 형식 "text", "코드" 또는 "binary"와 같은 파일 형식 또는 "xml", "vb" 또는 "c#"와 같은 기술 형식을 수 있습니다. 예를 들어 C# 및 Visual Basic의 경우에 있지만 다른 프로그래밍 언어에는 없는 키워드는 단어 "using"입니다. 따라서이 키워드의 정의 "c#" 및 "vb" 콘텐츠 형식으로 제한 됩니다.  
  
 콘텐츠 형식은 장식 및 편집기의 다른 요소에 대 한 필터로 사용 됩니다. 콘텐츠 형식별; 정의 된 다양 한 편집기 기능 및 확장 지점 예를 들어 텍스트 색은 일반 텍스트 파일, XML 파일 및 Visual Basic 소스 코드 파일에 대 한 다릅니다. 일반적으로 텍스트 버퍼는 만들어질 때 텍스트 버퍼의 콘텐츠 형식을 변경할 수 있습니다는 content-type는 할당 됩니다.  
  
 콘텐츠 형식을 여러-에서 상속할 수 있습니다 다른 콘텐츠 형식입니다. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 여러 기본 형식을 지정 된 콘텐츠 형식의 부모로 지정할 수 있습니다.  
  
 개발자가 자신의 콘텐츠 형식을 정의 업데이트 하 고 사용 하 여 등록할 수는 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>합니다. 사용 하 여 특정 콘텐츠 형식에 대해 다양 한 편집기 기능을 정의할 수 있습니다는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>합니다. 예를 들어, 편집기 여백, 프로그램 및 마우스 처리기 정의할 수 있습니다 특정 콘텐츠 형식을 표시 하는 편집기에만 적용 되도록 합니다.  
  
### <a name="textview"></a> 텍스트 보기  
 모델 보기 컨트롤러 (MVC) 패턴의 뷰 부분 뷰, 스크롤 막대 캐럿 등 그래픽 요소 서식을 텍스트 뷰를 정의 합니다. Visual Studio 편집기의 모든 프레젠테이션 요소는 WPF를 기반으로 합니다.  
  
#### <a name="text-views"></a>텍스트 뷰  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 인터페이스 텍스트 뷰는 플랫폼 독립적인 표현입니다. 창에서 텍스트 문서를 표시 하는 데 주로 사용 됩니다 있지만 해당 데도 사용할 수 있습니다 다른 용도 대 한 예를 들어 도구 설명에 합니다.  
  
 텍스트 뷰는 여러 가지 텍스트 버퍼를 참조합니다. 합니다 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> 속성 참조는 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 이러한 세 가지 다른 텍스트 버퍼를 가리키는 개체: 상위 데이터 수준 버퍼 편집 버퍼 발생 하는 편집 된 버퍼는 visual 버퍼에는 데이터 버퍼 텍스트 보기에 표시 합니다.  
  
 텍스트 기본 텍스트 버퍼에 연결 된 분류자에 따라 형식이 및 텍스트 뷰 자체에 연결 되어 있는 adornment 공급자를 사용 하 여 표시 됩니다.  
  
#### <a name="the-text-view-coordinate-system"></a>텍스트 보기 좌표계  
 텍스트 보기 좌표계 텍스트 보기에서 위치를 지정합니다. 이 좌표 시스템에서 표시 되 고 텍스트의 왼쪽된 가장자리에 해당 하는 x 값 0.0 및 y 값 0.0 되 고 표시 되는 텍스트의 위쪽 가장자리에 해당 합니다. X 좌표 왼쪽에서 오른쪽으로 늘어나고 아래쪽에 위쪽에서 증가 하는 y 좌표입니다.  
  
 뷰포트 (텍스트 창에 표시 되는 텍스트의 일부) 가로로 스크롤할 수 동일한 방식으로 세로로 스크롤 된 대로 합니다. 뷰포트 그리기 화면을 기준으로 이동 되도록 해당 왼쪽된 좌표를 변경 하 여 가로로 스크롤됩니다. 그러나 뷰포트 스크롤할 수 있는 세로로 하면 렌더링된 된 텍스트를 바꿔서는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 이벤트가 발생 합니다.  
  
 좌표계에서 거리가 논리 픽셀에 해당합니다. 텍스트 렌더링 화면 배율 변환 하지 않고 표시 되지 않으면 텍스트 렌더링 좌표 시스템을 하나의 단위로 표시에 1 픽셀에 해당 합니다.  
  
#### <a name="margins"></a>여백  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> 인터페이스는 여백을 나타내는 및 여백 및 해당 크기의 표시 유형 제어할 수 있습니다. "Top", "왼쪽", "오른쪽" 및 "아래" 라고 하며 위쪽, 아래쪽, 왼쪽 또는 보기의 오른쪽 가장자리에 연결 된 미리 정의 된 여백 네 가지가 있습니다. 이러한 여백은 컨테이너 다른 여백과 배치할 수 있습니다. 인터페이스는 여백 크기와 여백의 표시 여부를 반환 하는 메서드를 정의 합니다. 여백은 연결 된 텍스트 보기에 대 한 추가 정보를 제공 하는 시각적 요소입니다. 예를 들어, 줄 번호 여백 텍스트 보기에 대 한 줄 번호를 표시합니다. 문자 모양 여백 UI 요소를 표시합니다.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 만들고 여백의 배치를 처리 하는 인터페이스입니다. 여백이 다른 여백과 기준으로 정렬할 수 있습니다. 우선 순위가 높은 여백은 텍스트 보기에 가까이 위치입니다. 예를 들어 두 왼쪽된 여백, 여백 A 및 B, 여백 및 여백 B에는 여백 보다 낮은 우선 순위를, 여백 B 나타납니다 왼쪽의 여백 1.  
  
#### <a name="the-text-view-host"></a>텍스트 뷰 호스트  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 텍스트 보기 및 보기를 예를 들어, 스크롤 막대와 함께 제공 되는 모든 인접 장식을 인터페이스에 포함 되어 있습니다. 텍스트 뷰 호스트 보기의 테두리에 연결 되어 있는 여백을도 포함 되어 있습니다.  
  
#### <a name="formatted-text"></a>서식 있는 텍스트  
 텍스트 보기에 표시 되는 텍스트 이루어집니다 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 개체입니다. 뷰 텍스트 줄 마다 한 줄의 텍스트 보기에는 텍스트에 해당합니다. 기본 텍스트 버퍼의 긴 줄 수 있습니다 수 부분적으로 가려진 (자동 줄 바꿈을 사용 하지 않는) 하는 경우 또는 여러 텍스트 보기 줄으로 나뉘어집니다. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 인터페이스 메서드 및 매핑 좌표 사이의 문자를 줄으로 연결할 수 있는 도구 영역에 대 한 속성을 포함 합니다.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 개체를 사용 하 여 생성 되는 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 인터페이스입니다. 현재 보기에 표시 되는 텍스트에만 관심이, 서식의 원본을 무시할 수 있습니다. 없는 텍스트 형식의 관심이 있는 경우 (예를 들어 지원 서식 있는 텍스트 잘라내기 및 붙여넣기), 보기에 표시 된 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 텍스트 버퍼의 텍스트 서식 지정을 합니다.  
  
 텍스트 뷰 형식 하나 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 번입니다.  
  
## <a name="editor-features"></a>편집기 기능  
 기능 정의 해당 구현에서 별도 편집기의 기능 설계 됩니다. 편집기에는 이러한 기능이 포함 됩니다.  
  
- 태그 및 분류자  
  
- 선의 도구 영역  
  
- 프로젝션  
  
- 개요  
  
- 마우스 및 키 바인딩  
  
- 작업 및 기본 형식  
  
- IntelliSense  
  
### <a name="tagsandclassifiers"></a> 태그 및 분류자  
 태그는 텍스트 범위와 연관 된 표식입니다. 표현할 수 있습니다 다른 방법으로 예를 들어 텍스트 색, 밑줄, 그래픽 또는 팝업을 사용 하 여 합니다. 분류자는 태그의 한 종류입니다.  
  
 다른 종류의 태그는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 텍스트를 강조 표시 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 개요에 및 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 컴파일 오류에 대 한 합니다.  
  
#### <a name="classification-types"></a>분류 유형  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 인터페이스의 텍스트는 추상 종류는 동등 클래스를 나타냅니다. 분류 유형을 여러-형식에서 상속할 수 다른 분류 합니다. 예를 들어, 프로그래밍 언어 분류 포함 될 수 있습니다 "키워드", "설명" 및 "식별자"는 "코드"에서 상속 합니다. "명사", "동사" 및 "형용사" 모든 "자연어"에서 상속 되 자연어 분류 유형이 포함할 수 있습니다.  
  
#### <a name="classifications"></a>분류  
 분류는 텍스트 범위를 통해 일반적으로 특정 분류 형식의 인스턴스입니다. <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 분류를 나타내는 데 사용 됩니다. 범위를 분류 된이 텍스트 범위를 특정 분류 시스템을 지시 및 텍스트의 특정 범위를 포함 되어 있는 레이블로 생각할 수 있습니다.  
  
#### <a name="classifiers"></a>분류자  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 텍스트 분류의 집합으로 분리 하는 메커니즘입니다. 분류자 특정 콘텐츠 형식에 대해 정의 하 고 특정 텍스트 버퍼에 대해 인스턴스화된 해야 합니다. 클라이언트를 구현 해야 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 텍스트 분류에 참여할 수 있습니다.  
  
#### <a name="classifier-aggregators"></a>분류자 집계  
 분류자 aggregator에 하나의 집합으로 분류 한 텍스트 버퍼에 대 한 모든 분류자를 결합 하는 메커니즘입니다. 예를 들어 C# 분류자와 영어 분류자를 만들 수 분류 C# 파일에서 주석 위에 있습니다. 이 메모를 고려 합니다.  
  
```  
// This method produces a classifier  
```  
  
 C# 분류자를 주석으로 전체 범위 레이블 수 및 영어 분류자 수 분류 "생성"는 "동사" 및 "method"는 "명사"로 합니다. 집계 겹치지 않는 분류의 집합을 생성 하 고 집합의 형식은 모든 기 고물 기반 키를 누릅니다.  
  
 분류자 집계를 분류의 집합으로 텍스트 이므로 분류자 이기도 합니다. 분류자 집계도 있는지 여부를 확인 있습니다 겹치는 사용할 수 있는 분류는 분류 정렬 됩니다. 개별 분류자는 순서에 관계 없이 분류의 집합을 반환할 수 및 겹치는 어떤 방식으로든에서입니다.  
  
#### <a name="classification-formatting-and-text-coloring"></a>분류 서식 지정 및 텍스트 색 지정  
 텍스트 서식 지정은 텍스트 분류에서 기본 제공 되는 기능의 예입니다. 응용 프로그램에서 텍스트 표시를 확인 하려면 텍스트 보기 계층에서 사용 됩니다. 텍스트 서식 지정 영역 WPF 종속 이지만 분류 논리 정의 아닙니다.  
  
 분류 형식은 서식 특정 분류 형식에 대 한 속성의 집합입니다. 이러한 형식을 분류 유형 부모의 형식에서 상속합니다.  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 은 텍스트 서식 속성 집합에 분류 유형에서 맵입니다. 편집기에서 서식 맵에 구현의 분류 형식의 모든 내보내기를 처리합니다.  
  
### <a name="adornments"></a> 선의 도구 영역  
 장식을 글꼴 및 텍스트 보기에 있는 문자의 색을 직접 관련 되지 않은 그래픽 효과입니다. 예를 들어, 다양 한 프로그래밍 언어로 비 컴파일 코드를 표시 하는 데 사용 되는 빨간색 물결선 밑줄이 포함된 adornment, 이며 도구 설명 팝업 장식 됩니다. 선의 도구 영역에서 파생 됩니다 <xref:System.Windows.UIElement> 구현 및 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>합니다. 두 가지 특수 한 유형의 장식 태그는 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, 뷰의 텍스트와 동일한 공간을 차지 하는 선의 도구 영역에 대 한 및 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, 물결선 밑줄에 대 한 합니다.  
  
 포함 된 장식을 서식 있는 텍스트 보기의 일부를 형성 하는 그래픽입니다. 이러한 여러 Z-순서 계층으로 구성 됩니다. 다음과 같이 세 가지 기본 제공 계층을 가지 있습니다: 텍스트, 캐럿, 및를 선택 합니다. 그러나 개발자는 더 많은 레이어를 정의 하 고 각각에 대해 순서 대로 배치 수 있습니다. 장식 포함 된 세 가지는 상대 텍스트 장식 (하는 텍스트를 움직이면 이동 되며 텍스트 삭제 되 면 삭제 됨), (해야 하는 텍스트가 아닌 부분 뷰를 사용 하 여 수행)의 보기 관련 장식 및 소유자 제어 선의 도구 영역 ( 개발자 관리 해야 배치).  
  
 팝업 장식을 위의 예를 들어 도구 설명 텍스트 뷰를 다른 작은 창에 표시 되는 그래픽입니다.  
  
### <a name="projection"></a> Projection  
 프로젝션은 서로 다른 종류의 텍스트를 실제로 저장 되지 않습니다 하지만 대신 다른 텍스트 버퍼에서 텍스트를 결합 하는 텍스트 버퍼를 생성 하기 위한 기술입니다. 예를 들어 다른 두 버퍼에서 텍스트를 연결 하 고 하나의 버퍼에 있는 것 처럼 결과 표시 또는 숨기기 하나의 버퍼에서 텍스트의 부분에 프로젝션 버퍼를 사용할 수 있습니다. 프로젝션 버퍼는 다른 프로젝션 버퍼로 소스 버퍼로 작동할 수 있습니다. 다양 한 방법으로 텍스트를 다시 정렬 하려면 프로젝션을 통해 연관 된 버퍼 집합을 생성할 수 있습니다. (이러한 집합은 라고도 *버퍼 그래프*.) Visual Studio 텍스트 개요 기능을 축소 된 텍스트를 숨기려면 프로젝션 버퍼를 사용 하 여 구현 됩니다 하 고 ASP.NET 페이지에 대 한 Visual Studio 편집기 프로젝션을 사용 하 여 Visual Basic 및 C#과 같은 포함 된 언어를 지원 합니다.  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 사용 하 여 만들어지는 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>합니다. 프로젝션 버퍼는 정렬된 된 시퀀스를 나타내는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 이라고 하는 개체 *소스 범위*합니다. 이러한 범위 콘텐츠의 문자 시퀀스로 표시 됩니다. 소스 범위 그려지는 텍스트 버퍼 라고 *버퍼를 원본*합니다. 일반 텍스트 버퍼에서 다른는 알아야 할 클라이언트 프로젝션 버퍼에 없습니다.  
  
 프로젝션 버퍼가 소스 버퍼의 텍스트 변경 이벤트를 수신합니다. 원본에 있는 텍스트 변경 내용에 걸쳐 있는 프로젝션 버퍼 자체 좌표로 변경 된 텍스트 좌표를 매핑하고 해당 텍스트 변경 이벤트를 발생 시킵니다. 예를 들어, 이러한 내용이 들어 있는 소스 버퍼를 A와 B는 것이 좋습니다.  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 프로젝션 버퍼 P 하나 모든 버퍼를 및 모든 B 버퍼에는 다른 두 텍스트 범위에서 형식이 P에 다음 내용이 포함:  
  
```  
P: ABCDEvwxyz  
```  
  
 경우 부분 문자열 `xy` 버퍼 P 7 및 8 위치의 문자 삭제 된 이벤트를 발생 시킵니다. 그런 다음 버퍼 B에서에서 삭제 됩니다.  
  
 프로젝션 버퍼를 직접 편집할 수도 있습니다. 적절 한 원본 버퍼에 대 한 편집 내용을 전파 합니다. 예를 들어 문자열 버퍼 P 6 ("v" 문자가의 원래 위치) 위치에 삽입 하는 경우 삽입 위치 1 B 버퍼에 전파 됩니다.  
  
 프로젝션 버퍼에 기여 하는 소스 범위에 제한이 있습니다. 소스 범위는 겹치지 않을 수 있습니다. 프로젝션 버퍼의 위치에 모든 소스 버퍼의 둘 이상의 위치에 매핑할 수 없습니다 및 소스 버퍼의 위치를 프로젝션 버퍼에 둘 이상의 위치에 매핑할 수 없습니다. 소스 버퍼 관계 없는 circularities 허용 됩니다.  
  
 이벤트는 소스 집합 프로젝션 버퍼 변경 하 고 변경 내용을 원본 집합에 걸쳐 있는 경우 버퍼링 하는 경우에 발생 합니다.  
  
 생략 버퍼는 프로젝션 버퍼의 특별 한 합니다. 개요 및 확장 하 고 텍스트 블록을 축소 하는 작업에 주로 사용 됩니다. 생략 버퍼 하나만 소스 버퍼를 기준으로 하며 elision 버퍼에 범위 해야 동일한 순서 대로 지정 소스 버퍼의 순서 대로 수행 됩니다.  
  
##### <a name="the-buffer-graph"></a>버퍼 그래프  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 인터페이스 매핑을 프로젝션 버퍼의 그래프에서 사용 하도록 설정 합니다. 모든 텍스트 버퍼 및 프로젝션 버퍼는 언어 컴파일러에서 생성 되는 추상 구문 트리 마찬가지로 방향성된 비순환 그래프에서 수집 됩니다. 그래프는 모든 텍스트 버퍼 수 있는 상위 버퍼에 의해 정의 됩니다. 버퍼 그래프 위쪽 버퍼를 소스 버퍼를 지정 된 지점 또는 범위 소스 버퍼의 집합에 상위 버퍼의 범위에서 매핑할 수 있습니다. 마찬가지로, 점을 매핑할 하거나 소스 버퍼에서 최상위 버퍼 지점까지를 포괄 수 있습니다. 버퍼 그래프를 사용 하 여 만들어진 여 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>입니다.  
  
##### <a name="events-and-projection-buffers"></a>이벤트 및 프로젝션 버퍼  
 프로젝션 버퍼 수정 되 면 수정 작업에 종속 된 버퍼에 프로젝션 버퍼에서 전송 됩니다. 모든 버퍼가 수정 되 면 버퍼 변경 이벤트가 발생 하는 가장 안쪽 버퍼를 사용 하 여 시작 합니다.  
  
### <a name="outlining"></a> 개요  
 개요를 확장 하거나 다양 한 텍스트 뷰에서 텍스트 블록을 축소할 수 있습니다. 종류로 란 개요의 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, 장식을 정의 된 방식으로 동일한 합니다. <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 확장 하거나 축소할 수 있는 텍스트 영역을 정의 하는 태그입니다. 개요를 사용 하려면 가져와야는 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> 가져오려는 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>합니다. 개요 관리자 열거를 축소 하 고 다른 블록으로 표시 되는 확장 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 개체 및 그에 따라 이벤트를 발생 시킵니다.  
  
### <a name="mousebindings"></a> 마우스 바인딩  
 마우스 바인딩을 다른 명령 마우스 움직임을 연결합니다. 마우스 바인딩을 사용 하 여 정의 되는 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, 키 바인딩을 사용 하 여 정의 됩니다는 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>합니다. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 자동으로 모든 바인딩은 인스턴스화하고 뷰에서 마우스 이벤트에 연결 합니다.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> 여러 마우스 이벤트에 대 한 전처리 및 후 처리 이벤트 처리기를 포함 하는 인터페이스입니다. 이벤트 중 하나가 핸들을의 메서드 중 일부를 재정의할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>합니다.  
  
### <a name="editoroperations"></a> 편집기 작업  
 편집기 작업 스크립팅 편집기 또는 기타 목적을 위해 상호 작용을 자동화 하 사용할 수 있습니다. 가져올 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 액세스 작업에 지정 된 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다. 그런 다음 선택 항목을 수정, 보기를 스크롤하거나, 보기의 다른 부분에 캐럿을 이동 하려면 이러한 개체를 사용할 수 있습니다.  
  
### <a name="intellisense"></a> IntelliSense  
 IntelliSense 문 완성, 시그니처 도움말 (매개 변수 정보 라고도 함), 요약 정보 및 전구를 지원합니다.  
  
 문 완성 팝업 메서드 이름, XML 요소 및 다른 코드 또는 태그 요소에 대 한 잠재적인 완성 목록을 제공합니다. 일반적으로 사용자 제스처는 완료 세션을 호출합니다. 세션 잠재적인 완성 목록을 표시 하 고 사용자 수 하나를 선택 하거나 목록 해제 합니다. 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 만들고 트리거하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>합니다. 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 계산 된 <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 세션에 대 한 완성 항목의 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)   
 [편집기 가져오기](../extensibility/editor-imports.md)
