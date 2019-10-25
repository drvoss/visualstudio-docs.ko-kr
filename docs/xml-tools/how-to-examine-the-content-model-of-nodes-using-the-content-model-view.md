---
title: XML 스키마 디자이너에서 콘텐츠 모델 뷰를 사용 하 여 노드 검사
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c109d167534dc969ae34c55d16f2ee55e34fe3aa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645893"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>방법: 콘텐츠 모델 뷰를 사용 하 여 노드의 콘텐츠 모델 검사

이 항목에서는 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md)를 사용 하 여 노드를 탐색 하는 방법에 대해 설명 합니다.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면

1. 새 XML 스키마 파일을 만듭니다.

2. **Xml 편집기를 사용 하 여 시작 뷰에서 기본 Xml 스키마 파일 보기 및 편집을** 클릭 합니다.

3. [샘플 xml 스키마: 구매 주문 스키마](../xml-tools/sample-xsd-file-purchase-order-schema.md) 에서 xml 스키마 샘플 코드를 복사 하 고 붙여넣어 새 XSD 파일에 추가 된 코드를 기본적으로 바꿉니다.

4. XML 편집기에서 `purchaseOrder` 요소를 마우스 오른쪽 단추로 클릭 하 고 **Xml 탐색기에 표시**를 선택 하 여 스키마 탐색기에서 `purchaseOrder` 요소를 선택 합니다.

5. XML 탐색기에서 `purchaseOrder`을 마우스 오른쪽 단추로 클릭 하 고 **콘텐츠 모델 뷰에서 표시**를 선택 합니다.

     콘텐츠 모델 뷰는 해당 디자인 화면에 `purchaseOrder` 요소를 표시합니다.

6. 각 노드를 두 번 클릭하거나 각 노드 오른쪽에 있는 양방향 화살표를 클릭하여 `shipTo`, `billTo` 및 `items` 노드를 확장합니다.

     이제 `purchaseOrder` 요소의 노드가 확장되고 요소의 콘텐츠 모델을 볼 수 있습니다.

7. `purchaseOrder` 요소 아래의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.

8. XSD 도구 모음에서 **설명서 표시** 단추를 클릭 하 여 설명서를 설정/해제 합니다. 또한 디자인 화면을 마우스 오른쪽 단추로 클릭하여 설명서를 표시하거나 숨길 수 있습니다.

9. @No__t_0 노드를 마우스 오른쪽 단추로 클릭 하 고 **샘플 Xml 생성** 을 선택 하 여 xml 인스턴스 문서를 확인 합니다.
