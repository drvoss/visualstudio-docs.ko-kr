---
title: '연습: 개요 | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df269c3018d850ed2d5ae7435b82eb4f3aee4e1a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320618"
---
# <a name="walkthrough-outlining"></a>연습: 개요
개요 확장 또는 축소 하려는 텍스트 영역의 종류를 정의 하 여 같은 언어 기반 기능을 설정 합니다. 언어 서비스의 컨텍스트에서 영역을 정의 또는 하거나 정의할 수 있습니다 고유한 파일 이름 확장명 및 콘텐츠 유형 및 영역 정의 해당 형식에만 적용할 지역 정의 기존 콘텐츠 형식 (예: "text")를 적용 합니다. 이 연습에서는 정의 개요 영역을 표시 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 있습니다 다운로드 센터에서 Visual Studio SDK를 설치 하지 마세요. Visual Studio 설치에서 선택적 기능으로 포함 되어 있습니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Framework MEF (Managed Extensibility) 프로젝트 만들기

### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. VSIX 프로젝트를 만듭니다. 솔루션의 이름을 `OutlineRegionTest`로 지정합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-an-outlining-tagger"></a>개요는 태거 구현
 태그의 종류별로 개요 영역 표시 됩니다 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). 이 태그는 표준 동작 개요를 제공 합니다. 윤곽선이 있는 영역을 확장 하거나 축소할 수 있습니다. 윤곽선이 있는 지역에 더하기 기호 표시 됩니다 ( **+** ) 축소 된 경우 또는 빼기 기호 ( **-** )를 확장 하 고 확장 된 영역 세로 선 경계선은입니다.

 다음 단계를 대괄호를 구분 하는 모든 지역에 대 한 개요 영역을 만들 수 있는 한 태거를 정의 하는 방법을 보여 줍니다 ( **[** 하십시오 **]** ).

### <a name="to-implement-an-outlining-tagger"></a>개요는 태거를 구현 하려면

1. 클래스 파일을 추가하고 이름을 `OutliningTagger`로 지정합니다.

2. 다음 네임 스페이스를 가져옵니다.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 라는 클래스를 만듭니다 `OutliningTagger`를 구현 하도록 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 텍스트 버퍼 및 스냅숏 추적 하 고 집합 개요 영역으로 태그를 지정 해야 하는 줄을 누적 할 일부 필드를 추가 합니다. 이 코드 개요 영역을 나타내는 (나중으로 정의 됨)를 지역 개체의 목록이 포함 됩니다.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 버퍼를 구문 분석 하 고 이벤트 처리기를 추가 하는 추가 필드를 초기화 하는 태거 생성자는 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트입니다.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 태그를 인스턴스화하는 메서드를 포함 합니다. 이 예에서는 가정에서 범위를 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 메서드에 전달 된 항상 없을 경우 인접은. 이 메서드는 각 개요 영역에 대 한 새 태그 범위를 인스턴스화합니다.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 선언 된 `TagsChanged` 이벤트 처리기입니다.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 추가 된 `BufferChanged` 에 응답 하는 이벤트 처리기 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 텍스트 버퍼를 구문 분석 하 여 이벤트입니다.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 버퍼를 구문 분석 하는 메서드를 추가 합니다. 여기에 제공 된 예제 으로만입니다. 동기적으로 버퍼 중첩된 개요 영역에 구문 분석합니다.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 다음 도우미 메서드 1은 맨 왼쪽 중괄호 쌍, 개요 수준을 나타내는 정수를 가져옵니다.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 다음 도우미 메서드 (이 문서의 뒷부분에 정의 된) 영역을 SnapshotSpan 변환 됩니다.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 다음 코드는 으로만입니다. 줄 번호 및 개요 영역을 및 부모 영역 (있는 경우)에 대 한 참조의 시작 오프셋을 포함 하는 PartialRegion 클래스를 정의 합니다. 이 코드 개요 영역을 중첩 설정 하는 파서를 수 있습니다. 파생된 영역 클래스 개요 영역 끝의 줄 번호에 대 한 참조를 포함합니다.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>태거 공급자 구현
 태거 프로그램에 대 한 태거 공급자를 내보냅니다. 태거 공급자를 만듭니다는 `OutliningTagger` "text" 콘텐츠 형식 또는 다른 반환 버퍼는 `OutliningTagger` 버퍼 이미 있는 경우.

### <a name="to-implement-a-tagger-provider"></a>태거 공급자를 구현 하려면

1. 라는 클래스를 만듭니다 `OutliningTaggerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ContentType 및 TagType 특성을 사용 하 여 내보내야 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 구현 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 메서드를 추가 하 여는 `OutliningTagger` 버퍼의 속성입니다.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>빌드 및 코드를 테스트 합니다.
 이 코드를 테스트 하려면 OutlineRegionTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>빌드 및 OutlineRegionTest 솔루션 테스트

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스를 시작 됩니다.

3. 텍스트 파일을 만듭니다. 여는 괄호와 닫는 괄호를 포함 하는 일부 텍스트를 입력 합니다.

    ```
    [
       Hello
    ]
    ```

4. 양쪽 대괄호를 포함 하는 개요 영역 없어야 합니다. 개요 영역을 축소 하 고 여는 중괄호의 왼쪽에 빼기 기호를 클릭 해야 합니다. 경우 영역을 축소 줄임표 기호 ( *...* ) 축소 된 영역 및 텍스트가 포함 된 팝업의 왼쪽에 나타날 **가리킨 항목 텍스트** 줄임표 위로 포인터를 이동 하면 표시 됩니다.

## <a name="see-also"></a>참고자료
- [연습: 파일 이름 확장명에 콘텐츠 형식 링크](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)