---
title: Xml 편집기와 XML 스키마의 통합
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9df2d97a6ff68299ab70545683970188eb1bfea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601777"
---
# <a name="integration-with-xml-editor"></a>XML 편집기와의 통합

Xml 스키마 디자이너는 XML 편집기와 통합 됩니다. XML 편집기에서 XSD 파일을 수정 하면 변경 내용이 [Xml 스키마 탐색기](../xml-tools/xml-schema-explorer.md)에 반영 됩니다. [그래프 뷰](../xml-tools/graph-view.md) 또는 [콘텐츠 모델 뷰가](../xml-tools/content-model-view.md) 열린 경우에도 변경 내용이 반영 됩니다. 다음과 같은 방법으로 XML 스키마 디자이너와 XML 편집기 사이를 탐색할 수 있습니다.

- XML 편집기에서 노드를 마우스 오른쪽 단추로 클릭 하 고 **Xml 스키마 탐색기에 표시**를 선택 합니다.

- 그래프 뷰 및 **XML 스키마 탐색기**에서 노드를 두 번 클릭 하거나 노드를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 선택 합니다. 콘텐츠 모델 뷰에서 노드를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 선택 합니다.

다음 스크린샷은 **Xml 스키마 탐색기**에서 열린 xml 스키마를 보여 줍니다. **XML 스키마 탐색기** 에 스키마 집합이 트리 뷰로 표시 됩니다. Xml 편집기에서는 **Xml 스키마 탐색기**에서 현재 활성 상태인 노드의 텍스트 뷰를 표시 합니다.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

XML 편집기와 그래픽 디자이너의 코드를 나란히 표시 하는 것이 유용한 경우도 있습니다. 두 파일을 동시에 보려면 XML 편집기의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **디자이너 보기**를 선택 합니다. Visual Studio 창 메뉴에서 **새 가로 또는 세로 탭 그룹**을 선택 합니다.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>참조

- [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)