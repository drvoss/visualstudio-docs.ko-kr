---
title: 작업 영역에 XML 스키마 집합 검색 결과 노드 추가
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be024ac139d2b420f56b14158afd33ae5b7e917d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646027"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>방법: 작업 영역에 스키마 집합 검색 결과 노드 추가

이 항목에서는 작업 영역에서 키워드 검색의 결과로 **XML 스키마 탐색기** 에서 강조 표시 되는 노드를 추가 하는 방법에 대해 설명 합니다.

> [!NOTE]
> 전역 노드만 [작업 영역](../xml-tools/xml-schema-designer-workspace.md)에 추가할 수 있습니다.

이 예에서는 샘플 [구매 주문 스키마](../xml-tools/sample-xsd-file-purchase-order-schema.md)를 사용 합니다.

## <a name="to-add-schema-set-result-nodes"></a>스키마 집합 결과 노드를 추가하려면

1. [방법: XSD 스키마 파일 만들기 및 편집](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)의 단계를 따릅니다.

2. [XML 탐색기](../xml-tools/xml-schema-explorer.md) 도구 모음의 검색 텍스트 상자에 "purchaseOrder"를 입력 하 고 검색 단추를 클릭 합니다.

     ![XML 스키마 탐색기 키워드 검색](../xml-tools/media/schemaexplorersearch.gif)

     검색 결과가 **XML 스키마 탐색기** 에서 강조 표시 되 고 세로 스크롤 막대에 틱으로 표시 됩니다.

3. 요약 결과 창에서 **작업 영역에 선택한 노드 추가** 단추를 클릭 하 여 작업 영역에 검색 결과를 추가 합니다.

     ![XML 스키마 탐색기 검색 결과](../xml-tools/media/schemaexplorersearchresult.gif)

     [그래프 뷰의](../xml-tools/graph-view.md)디자인 화면에서 `purchaseOrder` 노드와 `PurchaseOrderType` 노드가 서로 옆에 표시 됩니다. 이 두 노드는 서로 관련되어 있으므로(`purchaseOrder` 요소가 `PurchaseOrderType` 형식임) 두 노드 사이에 화살표가 그려집니다.