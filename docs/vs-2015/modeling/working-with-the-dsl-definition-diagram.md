---
title: DSL 정의 다이어그램 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd4b15fb7c0f1cbc0630779ecef0373977bb2056
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694217"
---
# <a name="working-with-the-dsl-definition-diagram"></a>DSL 정의 다이어그램 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다이어그램을 [!INCLUDE[dsl](../includes/dsl-md.md)] 정의 도메인별 언어 정의 대 한 중요 한 도구입니다. 도메인 모델에 요소를 추가하고 다이어그램에 대해 관계를 정의할 수 있으며 보다 읽기 쉽도록 다이어그램의 레이아웃을 수정할 수 있습니다.  
  
## <a name="the-layout-of-the-diagram"></a>다이어그램 레이아웃  
 합니다 [!INCLUDE[dsl](../includes/dsl-md.md)] 정의 다이어그램에는 두 개의 파티션이 합니다 **클래스 및 관계** 파티션 및 **다이어그램 요소** 파티션 합니다. 합니다 **클래스 및 관계** 도메인 클래스, 도메인 관계 및 상속 파티션을 표시 합니다. 합니다 **다이어그램 요소** 파티션 모양 클래스, 연결선 클래스, 스윔 레인 클래스 및 생성 된 디자이너 다이어그램이 표시 됩니다.  
  
 도메인 클래스의 여러 위치에 나타날 수 있습니다 합니다 **클래스 및 관계** 파티션 합니다. 도메인 클래스 정의는 다른 도메인 클래스의 기본 클래스인 경우 상속 트리를 표시하고 포함/참조 관계의 소스인 경우에는 관계 트리를 표시합니다. 포함 또는 참조 관계의 대상으로는 도메인 클래스 자리 표시자가 표시됩니다. 기본적으로 자리 표시자 요소가 사용 하 여 표시 되는 **도메인 속성** 구획을 축소 합니다. 상속 또는 포함/참조 관계는 표시하지 않습니다.  
  
 아래쪽 부분에 나타나는 도메인 클래스에 추가 합니다 **클래스 및 관계** 파티션 합니다. 포함 또는 참조 관계를 추가하면 소스 도메인 클래스 오른쪽 아래에 관계가 그려집니다.  
  
 도메인 클래스와 관계를 추가할 때는 특정 도메인 클래스를 찾기가 어려울 수도 있습니다. 마우스 오른쪽 단추로 클릭 하 여 도메인 클래스를 찾을 수 있습니다 합니다 **DSL 탐색기** 클릭 한 다음 **다이어그램에서 찾기**합니다.  
  
 다음 섹션에서는 보다 쉽게 읽을 수 있도록 다이어그램의 모양을 변경하는 방법을 설명합니다.  
  
## <a name="copying-elements"></a>요소 복사  
 DSL 정의 다이어그램의 요소에 대해 복사, 잘라내기 및 붙여넣기를 사용할 수 있습니다.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>다이어그램 확대/축소  
 있습니다 수 확대 또는 축소 다이어그램에서 사용 하 여 합니다 **DSL 디자이너** 확대/축소 수준을 설정 하려면 도구 모음입니다.  
  
## <a name="hiding-map-lines"></a>지도 선 숨기기  
 지도 선은 도메인 클래스 또는 도메인 관계와 해당 클래스/관계가 매핑되는 모양 또는 연결선 간에 그려지는 선입니다. 클릭 하 여 지도 선을 숨길 수는 **지도 선 표시** 단추를 **DSL 디자이너** 도구 모음입니다. 선을 표시하려면 단추를 다시 클릭합니다.  
  
## <a name="changing-the-diagram-layout"></a>다이어그램 레이아웃 변경  
 레이아웃을 변경할 수는 **클래스 및 관계** 같이 분할 합니다.  
  
### <a name="expandcollapse"></a>확장/축소  
 마우스 오른쪽 단추로 클릭 하 여 도메인 클래스 또는 모양을 나타내는 구획 모양 요소 크기를 줄일 수 있습니다 **축소**합니다. 이 숨깁니다 합니다 **도메인 속성** 도형의 구획입니다. 표시할 합니다 **도메인 속성** 구획을 다시 셰이프를 마우스 오른쪽 단추로 클릭 하 고 클릭 **확장**합니다.  
  
### <a name="move-updown"></a>위/아래로 이동  
 요소를 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 파티션에 도메인 클래스 또는 다이어그램 요소를 위로 또는 아래로 이동할 수 있습니다 **위로 이동** 하거나 **아래로 이동**합니다. 포함 또는 참조 관계의 대상으로 표시된 자리 표시자 요소를 이동하면 관계도 함께 이동됩니다.  
  
### <a name="expandcollapse-relationships-tree"></a>관계 트리 확장/축소  
 다른 도메인 클래스와 포함 또는 참조 관계에서 원본 역할을 담당 하는 도메인 클래스, 하는 경우 도메인 클래스 정의 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 관계를 숨길 수 있습니다 **관계 트리 축소**합니다. 관계를 표시 하려면 정의 요소를 마우스 오른쪽 단추로 클릭 하 고 클릭 **관계 트리 확장**합니다.  
  
### <a name="expandcollapse-inheritance-tree"></a>상속 트리 확장/축소  
 도메인 클래스가 다른 도메인 클래스의 기본 클래스 이면 도메인 클래스 정의 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 상속 트리를 숨길 수 있습니다 **상속 트리 축소**합니다. 상속 트리를 표시 하려면 정의 요소를 마우스 오른쪽 단추로 클릭 하 고 클릭 **상속 트리 확장**합니다.  
  
### <a name="bring-tree-here"></a>여기로 트리 가져오기  
 자리 표시자 도메인 클래스를 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 다이어그램을 통합할 수 있습니다 **여기로 트리 가져오기**합니다. 그러면 자리 표시자 도메인 클래스가 정의 요소가 되고 상속 및 관계 트리가 표시됩니다. 이전 정의 요소는 관계의 대상이거나 상속 관계의 자식인 경우 자리 표시자 요소가 되고 그렇지 않으면 사라집니다.  
  
### <a name="split-tree"></a>트리 분할  
 표시 하는 도메인 클래스 정의 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 상속 또는 관계 트리를 분할할 수 있습니다 **트리 분할**합니다. 그러면 정의 요소가 자리 표시자 요소가 되고 정의 도메인 클래스는 상속 및 관계 트리와 함께 파티션 아래쪽에 표시됩니다.  
  
### <a name="show-as-class"></a>Show As Class  
 도메인 관계에서 관계가 파생 하거나 경우 다른 도메인 관계를 사용 하 여 포함 또는 참조 관계에 표시할 수 있습니다 관계를 클래스로 관계를 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 **클래스로 표시** . 관계 방향으로 표시할지를 **도메인 속성** 구획과 상속 및 관계 트리가 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
