---
title: '방법: 그래프 뷰를 사용 하 여 스키마 집합 개요 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f6f264427e10cbe444cab8a5208e86866635ed17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150740"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>방법: 그래프 뷰를 사용하여 스키마 집합의 개요 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 사용 하는 방법을 설명 합니다 [그래프 뷰](../xml-tools/graph-view.md) 스키마 집합 및 노드 간 관계에 있는 노드의 상위 수준 보기를 확인 합니다.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면  
  
1. 새 XML 스키마 파일을 만들고 파일을 Relationships.xsd로 저장합니다.  
  
2. 클릭 합니다 **보고 기본 XML 스키마 파일을 편집 하려면 XML 편집기를 사용 하 여** 시작 보기의 링크입니다.  
  
3. XML 스키마 샘플 코드를 복사 [샘플 XML 스키마: 관계](../xml-tools/sample-xsd-file-relationships.md) 붙여 넣어 기본적으로 새 XSD 파일에 추가 된 코드를 바꿉니다.  
  
4. XML 편집기에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 **뷰 디자이너**합니다.  
  
5. XSD 도구 모음에서 그래프 뷰를 선택합니다.  
  
6. 선택 **스키마 집합** 노드 XML 스키마 탐색기 및 노드 끌어서 그래프 뷰의 화면을 디자인 합니다. 모든 전역 노드 및 관계가 설정된 노드를 연결하는 화살표를 볼 수 있어야 합니다.  
  
     ![그래프 뷰로](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7. 디자인 화면의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.  
  
8. Rick 디자인 화면에서 모든 요소 노드를 클릭 **샘플 XML 생성** 에 XML 인스턴스 문서를 참조 하세요.
