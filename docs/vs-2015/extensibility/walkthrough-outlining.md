---
title: '연습: 개요 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201963"
---
# <a name="walkthrough-outlining"></a>연습: 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개요 확장 또는 축소 하려는 텍스트 영역의 종류를 정의 하 여 같은 언어 기반 기능을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 영역을 정의할 수 있습니다 또는 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 지역 정의 해당 형식에만 적용할 수 또는 지역 정의 기존 콘텐츠 형식 (예: "text")에 적용할 수 있습니다. 이 연습에서는 정의 개요 영역을 표시 하는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>MEF(Managed Extensibility Framework) 프로젝트 만들기  
  
#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면  
  
1. VSIX 프로젝트를 만듭니다. 솔루션의 이름을 `OutlineRegionTest`로 지정합니다.  
  
2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3. 기존 클래스 파일을 삭제합니다.  
  
## <a name="implementing-an-outlining-tagger"></a>개요는 태거 구현  
 태그의 종류별로 개요 영역 표시 됩니다 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). 이 태그는 표준 동작 개요를 제공 합니다. 윤곽선이 있는 영역을 확장 하거나 축소할 수 있습니다. 확장 된 경우 확장 된 영역 세로 선 경계선은 개요 영역이 축소 된 경우에 더하기 또는 빼기 기호 표시 됩니다.  
  
 다음 단계에서는 구분 되는 모든 지역에 대 한 개요 영역을 만들 수 있는 한 태거를 정의 하는 방법을 보여 "[" 및 "]"입니다.  
  
#### <a name="to-implement-an-outlining-tagger"></a>개요는 태거를 구현 하려면  
  
1. 클래스 파일을 추가하고 이름을 `OutliningTagger`로 지정합니다.  
  
2. 다음 네임 스페이스를 가져옵니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. 라는 클래스를 만듭니다 `OutliningTagger`를 구현 하도록 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. 텍스트 버퍼 및 스냅숏 추적 하 고 집합 개요 영역으로 태그를 지정 해야 하는 줄을 누적 할 일부 필드를 추가 합니다. 이 코드 개요 영역을 나타내는 (나중으로 정의 됨)를 지역 개체의 목록이 포함 됩니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. 버퍼를 구문 분석 하 고 이벤트 처리기를 추가 하는 추가 필드를 초기화 하는 태거 생성자는 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트입니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 태그를 인스턴스화하는 메서드를 포함 합니다. 이 가정에서 범위를 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 메서드에 전달 된이 하지 않을 경우 인접은입니다. 이 메서드는 각 개요 영역에 대 한 새 태그 범위를 인스턴스화합니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. 선언 된 `TagsChanged` 이벤트 처리기입니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. 추가 된 `BufferChanged` 에 응답 하는 이벤트 처리기 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 텍스트 버퍼를 구문 분석 하 여 이벤트입니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. 버퍼를 구문 분석 하는 메서드를 추가 합니다. 여기에 제공 된 예제 으로만입니다. 동기적으로 버퍼 중첩된 개요 영역에 구문 분석합니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. 다음 도우미 메서드 1은 맨 왼쪽 중괄호 쌍, 개요 수준을 나타내는 정수를 가져옵니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. 다음 도우미 메서드 (이 항목의 뒷부분에 정의 된) 영역을 SnapshotSpan 변환 됩니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. 다음 코드는 으로만입니다. 줄 번호 및 개요 영역을 그리고 (있는 경우)는 부모 영역에 대 한 참조의 시작 오프셋을 포함 하는 PartialRegion 클래스를 정의 합니다. 이 통해 설정 하기 위해 파서가 개요 영역을 중첩 합니다. 파생된 영역 클래스 개요 영역 끝의 줄 번호에 대 한 참조를 포함합니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>태거 공급자 구현  
 태거 프로그램에 대 한 태거 공급자를 내보내야 합니다. 태거 공급자를 만듭니다는 `OutliningTagger` "text" 콘텐츠 형식 또는 다른 반환 버퍼는 `OutliningTagger` 버퍼 이미 있는 경우.  
  
#### <a name="to-implement-a-tagger-provider"></a>태거 공급자를 구현 하려면  
  
1. 라는 클래스를 만듭니다 `OutliningTaggerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ContentType 및 TagType 특성을 사용 하 여 내보내야 합니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. 구현 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 메서드를 추가 하 여는 `OutliningTagger` 버퍼의 속성입니다.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 OutlineRegionTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>빌드 및 OutlineRegionTest 솔루션 테스트  
  
1. 솔루션을 빌드합니다.  
  
2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3. 텍스트 파일을 만듭니다. 여는 중괄호와 닫는 중괄호를 포함 하는 일부 텍스트를 입력 합니다.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. 두 중괄호를 포함 하는 개요 영역 없어야 합니다. 개요 영역 축소를 여는 중괄호의 왼쪽에 빼기 기호를 클릭 해야 합니다. 경우 영역을 축소 줄임표 기호 (...) 축소 된 영역 및 텍스트가 포함 된 팝업의 왼쪽에 나타납니다 **가리킨 항목 텍스트** 줄임표 위로 포인터를 이동 하면 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
