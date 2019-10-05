---
title: Windows Forms 애플리케이션에서 조회 테이블 만들기
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 782f5b422058d1564bde04251a92d95145f6edf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567278"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms 애플리케이션에서 조회 테이블 만들기

용어 *조회 테이블* 두 관련된 데이터 테이블에 바인딩되는 컨트롤에 설명 합니다. 이러한 조회 컨트롤에는 두 번째 테이블에서 선택한 값을 기준으로 첫 번째 테이블의 데이터를에서 표시 합니다.

부모 테이블의 기본 노드 드래그 하 여 조회 테이블을 만들 수 있습니다 (에서 합니다 [데이터 소스 창](add-new-data-sources.md#data-sources-window)) 관련된 자식 테이블의 열에 이미 바인딩되어 있는 폼의 컨트롤입니다.

예를 들어 테이블을 `Orders` 판매 데이터베이스에서. 각 레코드는 `Orders` 테이블에는 `CustomerID`, 고객 주문을 나타내는입니다. 합니다 `CustomerID` 에서 고객 레코드를 가리키는 외래 키를 `Customers` 테이블입니다. 이 시나리오를 확장 하는 `Orders` 테이블에 **데이터 원본** 창 주 노드를 설정 하 고 **세부 정보**합니다. 그런 다음 설정 합니다 `CustomerID` 사용할 열을를 <xref:System.Windows.Forms.ComboBox> (또는 조회 바인딩을 지 원하는 다른 컨트롤) 끌어서를 `Orders` 노드를 폼으로 합니다. 마지막으로 끌어를 `Customers` 관련된 열에 바인딩되는 컨트롤 노드-이 경우는 <xref:System.Windows.Forms.ComboBox> 바인딩할를 `CustomerID` 열입니다.

## <a name="to-databind-a-lookup-control"></a>데이터 바인딩에 조회 컨트롤

1. 열린 프로젝트를 사용 하 여 열을 **데이터 원본** 선택 하 여 창 **보기** > **다른 Windows** > **데이터 원본을**.

    > [!NOTE]
    > 조회 테이블 두 관련된 테이블 또는 개체에서 사용할 수 있어야 합니다 **데이터 원본** 창입니다. 자세한 내용은 [데이터 집합의 관계](relationships-in-datasets.md)합니다.

2. 노드를 확장 합니다 **데이터 원본** 부모 테이블 및 모든 해당 열 및 관련된 자식 테이블의 모든 열 표시 될 때까지 창입니다.

    > [!NOTE]
    > 자식 테이블 노드는 부모 테이블의 확장 가능한 자식 노드로 표시 되는 노드입니다.

3. 자식 테이블의 놓기 형식을 변경 **세부 정보** 를 선택 하 여 **세부 정보** 자식 테이블의 노드의 컨트롤 목록에서. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

4. 노드 두 테이블 간의 관계를 찾습니다 (의 `CustomerID` 이전 예에서 노드). 해당 드롭 유형을 변경를 <xref:System.Windows.Forms.ComboBox> 를 선택 하 여 **ComboBox** 컨트롤 목록에서.

5. 기본 자식 테이블 노드를 끌어 합니다 **데이터 원본** 창에서 폼으로 합니다.

     데이터 바인딩된 컨트롤 (설명이 포함 된 레이블로) 도구 스트립 (<xref:System.Windows.Forms.BindingNavigator>) 폼에 나타납니다. A [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md)를 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)를 <xref:System.Windows.Forms.BindingSource>, 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

6. 이제에서 기본 부모 테이블 노드를 끕니다 합니다 **데이터 원본** 조회 컨트롤에 직접 창 (의 <xref:System.Windows.Forms.ComboBox>).

     이제 조회 바인딩은 설정 됩니다. 컨트롤에 설정 된 특정 속성에 대해 다음 표를 참조 하세요.

    |속성|설정 설명|
    |--------------| - |
    |**DataSource**|Visual Studio는 사용자가 컨트롤로 끌어 온 테이블에 대해 작성된 <xref:System.Windows.Forms.BindingSource>로 이 속성을 설정합니다. 컨트롤을 만들 때 작성된 <xref:System.Windows.Forms.BindingSource>가 아닙니다.<br /><br /> 조정 해야 할 경우 설정 된 <xref:System.Windows.Forms.BindingSource> 표시 하려는 열이 있는 테이블의 합니다.|
    |**DisplayMember**|Visual Studio는 컨트롤로 끄는 테이블에 대해 문자열 데이터 형식을 포함하는 기본 키 다음의 첫 번째 열로 이 속성을 설정합니다.<br /><br /> 조정 해야 하는 경우 표시 하려는 열 이름으로 설정 합니다.|
    |**ValueMember**|Visual Studio는 이 속성을 기본 키에 포함되는 첫 번째 열로 설정하거나 키가 정의되어 있지 않으면 테이블의 첫 번째 열로 설정합니다.<br /><br /> 조정 해야 하는 경우 표시 하려는 열이 있는 테이블의 기본 키로 설정 합니다.|
    |**SelectedValue**|Visual Studio에서 삭제할 원래 열으로이 속성을 설정 합니다 **데이터 원본** 창입니다.<br /><br /> 조정 해야 하는 경우 관련된 테이블의 외래 키 열으로 설정 합니다.|

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)