---
title: XML 스키마 탐색기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 550c43532db89132ec4e1b123005ad02ef547414
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198033"
---
# <a name="xml-schema-explorer"></a>XML 스키마 탐색기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 스키마 탐색기는 XSD(XML 스키마 정의 언어) 스키마 작업을 수행할 수 있도록 Microsoft Visual Studio 및 XML 편집기와 통합되었습니다. XML 스키마 파일을 열면 합니다 **스키마 집합** 노드가 XML 스키마 탐색기에 나타납니다. 대상 파일은 물론 `include` 또는 `import` 문에서 참조되는 모든 파일에 대해 포함된 스키마, 가져온 스키마 또는 다시 정의된 스키마도 모두 XML 스키마 탐색기에 나타납니다.  
  
 XML 스키마 탐색기를 사용하면 다음을 수행할 수 있습니다.  
  
- 스키마 집합을 간단히 파악할 수 있습니다.  
  
- 트리를 검색하고 탐색합니다.  
  
- 키워드 및 스키마 관련 검색을 수행합니다. 자세한 내용은 [스키마 집합 검색](../xml-tools/searching-the-schema-set.md)합니다.  
  
- 검색 결과를 그래프 뷰 또는 콘텐츠 모델 뷰에 추가합니다.  
  
- 문서 순서, 유형 또는 이름별로 트리를 정렬할 수 있습니다. 자세한 내용은 [정렬, 필터링 및 그룹화](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)합니다.  
  
- XML 편집기를 열고 XSD 파일의 코드 위치로 이동할 수 있습니다. 자세한 내용은 [XML 편집기와 통합](../xml-tools/integration-with-xml-editor.md)합니다.  
  
- 전역 요소를 위한 샘플 XML을 생성할 수 있습니다.  
  
  XML 스키마 탐색기에서는 트리 뷰를 통해 스키마 집합을 계층적으로 표시합니다. 또한 검색, 필터링, 탐색 및 정렬 기능도 제공합니다. XML 스키마 탐색기에 액세스하려면 다음 중 하나를 수행합니다.  
  
- 있는 경우는 [시작 뷰](../xml-tools/start-view.md)를 클릭 합니다 **XML 스키마 탐색기** 링크.  
  
- 있는 경우는 [그래프 뷰](../xml-tools/graph-view.md) 또는 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md) 및 작업 영역에 노드가 있거나, XML 스키마 탐색기를 선택 하려면 상황에 맞는 메뉴를 사용 합니다.  
  
- XML 스키마 Explorerfrom 선택할 수도 있습니다는 **보기** 메뉴.  
  
- XML 스키마 Explorerfrom는 Visual Basic XML 리터럴.xsd 파일과 연결 된 있는.vb 파일에 액세스할 수 있습니다. XML 스키마 탐색기에서 설정, xml 리터럴에서 XML 노드 또는 XML 네임 스페이스 가져오기에서 마우스 오른쪽 단추로 클릭 하 고, 선택 된 스키마를 확인 합니다 **스키마 탐색기에 표시** 명령입니다. 자세한 내용은 [통합의 XML 리터럴과 XML 스키마 탐색기와](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)합니다.  
  
## <a name="tree-view"></a>트리 뷰  
 XML 스키마 탐색기에서는 미리 컴파일된 스키마 집합 정보를 트리 구조로 표시합니다. 트리 구조는 다음과 같이 구성됩니다.  
  
- 최상위 수준은 스키마 집합 노드입니다.  
  
- 두 번째 수준에는 네임스페이스가 포함됩니다.  
  
- 세 번째 수준에는 파일이 포함됩니다.  
  
- 네 번째 수준에는 전역 노드가 포함됩니다. 여기에는 요소, 그룹, 복합 형식, 단순 형식, 특성, 특성 그룹 및 `include`, `import` 및 `redefine` 문이 포함될 수 있습니다.  
  
  다음은 트리 구조의 예제입니다.  
  
  ![XML 스키마 탐색기](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>선택 및 활성화  
 노드를 강조 표시하고 선택하려면 스키마 탐색기에서 한 번 클릭합니다.  
  
 노드를 활성화 하려면 두 번 클릭 하거나 눌러 **Enter** 노드를 선택 하는 경우.  
  
- 파일이 아직 열려 있지 않은 경우 노드를 활성화하면 이 노드가 정의된 파일이 열리고 파일의 노드가 선택됩니다.  
  
- 파일이 아직 열려 있지 않은 경우 파일 노드를 활성화하면 선택된 파일이 열리고 `<schema>` 노드가 강조 표시됩니다.  
  
- SchemaSet 또는 네임스페이스 노드를 활성화하는 경우에는 아무 작업도 수행되지 않습니다.  
  
## <a name="draging-and-dropping-nodes"></a>노드 끌어서 놓기  
 전역 노드, 파일 노드 및 네임스페이스 노드를 XSD 디자이너 뷰로 끌어서 놓을 수 있습니다. 현재 뷰가 경우는 [시작 뷰](../xml-tools/start-view.md), 열립니다는 노드를 뷰로 끌어 합니다 [그래프 뷰](../xml-tools/graph-view.md)합니다. 현재 뷰가 경우 합니다 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md) 또는 그래프 뷰의 경우 노드를 끌어 놓으면 뷰가 변경 되지 것입니다.  
  
 파일에 있는 모든 전역 노드가 추가 보기에서 파일을 삭제 합니다 [XSD 디자이너 작업 영역](../xml-tools/xml-schema-designer-workspace.md)합니다. 네임스페이스를 뷰에 놓으면 네임스페이스의 모든 전역 노드가 작업 영역에 추가됩니다. 작업 영역은 모든 뷰 간에 공유됩니다.  
  
 로컬 노드 또는 가져오기를 끌어서 놓을 수 없습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
- [스키마 집합 검색](../xml-tools/searching-the-schema-set.md)  
  
- [정렬, 필터링 및 그룹화](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
- [상황에 맞는 메뉴](../xml-tools/context-menus-xml-schema-explorer.md)  
  
- [XML 리터럴과 XML 스키마 탐색기와의 통합](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>참고 항목  
 [방법: XML 스키마 탐색기에서 작업 영역에 노드 추가](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
