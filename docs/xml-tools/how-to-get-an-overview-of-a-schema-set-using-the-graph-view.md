---
title: 'XML 스키마 디자이너: 그래프 뷰를 사용 하 여 스키마 집합 개요'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a0fc62a0d6dfe772a550f33cafa02bc5bc1bf3
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432165"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>방법: 그래프 뷰를 사용 하 여 설정 하는 스키마 개요

이 항목에서는 사용 하는 방법을 설명 합니다 [그래프 뷰](../xml-tools/graph-view.md) 스키마 집합 및 노드 간 관계에 있는 노드의 상위 수준 보기를 확인 합니다.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면

1. 새 XML 스키마 파일을 만들고 파일을 *Relationships.xsd*합니다.

2. 클릭 합니다 **기본 XML 스키마 파일 표시 및 편집을 사용 하 여 XML 편집기** 시작 보기의 링크입니다.

3. XML 스키마 샘플 코드를 복사 [샘플 XML 스키마: 관계](../xml-tools/sample-xsd-file-relationships.md) 붙여 넣어 기본적으로 새 XSD 파일에 추가 된 코드를 바꿉니다.

4. XML 편집기에서 아무 곳 이나 마우스 오른쪽 단추로 누르고 **뷰 디자이너**합니다.

5. 그래프 뷰를 선택 합니다 **XSD 도구 모음**합니다.

6. 선택 **스키마 집합** 에서 노드를 **XML 스키마 탐색기** 노드가 그래프 뷰의 디자인 화면으로 끌어서 합니다. 모든 전역 노드 및 관계가 설정된 노드를 연결하는 화살표를 볼 수 있어야 합니다.

     ![그래프 뷰](../xml-tools/media/relationshipingraphview.gif)

7. 디자인 화면의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.

8. Rick-디자인 화면에 요소 노드를 클릭 **샘플 XML 생성** 에 XML 인스턴스 문서를 참조 하세요.