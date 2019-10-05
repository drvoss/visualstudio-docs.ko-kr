---
title: WPF 애플리케이션에서 조회 테이블 만들기
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1631f1b93f79c21914f990620f7e0047c301163f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567821"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF 애플리케이션에서 조회 테이블 만들기

용어 *조회 표* (라고도 *조회 바인딩을*) 다른 테이블의 외래 키 필드의 값을 기반으로 하는 하나의 데이터 테이블의에서 정보를 표시 하는 컨트롤에 설명 합니다. 부모 테이블의 기본 노드 드래그 하 여 조회 테이블을 만들 수도 있고 개체를 **데이터 원본** 열 또는 관련된 자식 테이블의 속성에 이미 바인딩된 컨트롤을 창입니다.

예를 들어 테이블을 `Orders` 판매 데이터베이스에서. 각 레코드는 `Orders` 테이블에는 `CustomerID` 고객 주문을 나타내는입니다. 합니다 `CustomerID` 에서 고객 레코드를 가리키는 외래 키를 `Customers` 테이블입니다. 주문 목록을 표시 하는 경우는 `Orders` 대신 실제 고객 이름을 표시 하려는 테이블을 `CustomerID`입니다. 고객 이름 이므로 `Customers` 고객 이름을 표시 하는 조회 테이블을 생성 해야 하는 테이블입니다. 조회 테이블 사용 시 합니다 `CustomerID` 값을 `Orders` 관계를 탐색 기록 하 고 고객 이름을 반환 합니다.

## <a name="to-create-a-lookup-table"></a>조회 테이블을 만들려면

1. 프로젝트에 관련 된 데이터를 사용 하 여 데이터 원본의 다음 유형 중 하나를 추가 합니다.

    - 데이터 집합 또는 엔터티 데이터 모델입니다.

    - WCF 데이터 서비스에서 WCF 서비스 또는 웹 서비스입니다. 자세한 내용은 [방법: 서비스의 데이터에 연결](../data-tools/how-to-connect-to-data-in-a-service.md)을 참조하세요.

    - 개체. 자세한 내용은 [Visual Studio에서 개체를 바인딩할](bind-objects-in-visual-studio.md)합니다.

    > [!NOTE]
    > 조회 테이블을 만들려면 먼저 프로젝트에 대 한 데이터 원본으로 두 개의 관련된 테이블이 나 개체가 존재 해야 합니다.

2. 열기는 **WPF 디자이너**, 디자이너 항목에 대 한 유효한 놓기 대상 컨테이너가 포함 되어 있는지 확인 합니다 **데이터 원본** 창입니다.

     유효한 놓기 대상에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)합니다.

3. **데이터** 메뉴에서 **데이터 원본 표시**를 클릭하여 **데이터 원본** 창을 엽니다.

4. 노드를 확장 합니다 **데이터 원본** 창에서 부모 테이블 또는 개체와 관련 된 자식 테이블 또는 개체 표시 될 때까지 합니다.

    > [!NOTE]
    > 관련된 자식 테이블 또는 개체는 부모 테이블 또는 개체를 확장할 수 있는 자식 노드로 표시 되는 노드입니다.

5. 자식 노드에 대 한 드롭다운 메뉴를 클릭 하 고 선택 **세부 정보**합니다.

6. 자식 노드를 확장 합니다.

7. 자식 노드를 자식 및 부모 데이터를 연결 하는 항목에 대 한 드롭다운 메뉴를 클릭 합니다. (이 앞의 예제에는 **CustomerID** 노드.) 조회 바인딩을 지 원하는 컨트롤의 다음 형식 중 하나를 선택 합니다.

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > 경우는 **ListBox** 하거나 **ListView** 컨트롤이 없으면 목록에서 목록에 이러한 컨트롤을 추가할 수 있습니다. 정보를 참조 하세요 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

    - 파생 되는 모든 사용자 지정 컨트롤 <xref:System.Windows.Controls.Primitives.Selector>합니다.

        > [!NOTE]
        > 사용자 지정 컨트롤의 컨트롤 목록에 추가 하는 방법에 대 한 정보 항목에 대해 선택할 수는 **데이터 원본** 창 참조 [데이터 소스 창에 사용자 지정 컨트롤을 추가할](../data-tools/add-custom-controls-to-the-data-sources-window.md)합니다.

8. 자식 노드를 끌어 합니다 **데이터 원본** WPF 디자이너에서 컨테이너 창. (앞의 예제에서 자식 노드는 합니다 **주문** 노드.)

     Visual Studio는 각 항목을 끌면에 대 한 새 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. XAML도 새 추가 <xref:System.Windows.Data.CollectionViewSource> 자식 테이블이 나 개체를 놓기 대상의 리소스에 대 한 합니다. 일부 데이터 원본의 경우 Visual Studio 테이블 또는 개체 데이터를 로드 하는 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)합니다.

9. 부모 노드를 끌어 합니다 **데이터 원본** 앞에서 만든 조회 바인딩 컨트롤에 창. (앞의 예제에서 부모 노드인 합니다 **고객** 노드).

     Visual Studio 조회 바인딩을 구성 하는 컨트롤에 일부 속성을 설정 합니다. 다음 표에서 Visual Studio를 수정 하는 속성을 보여 줍니다. 경우 필요에 따라 변경할 수 있습니다는 XAML 또는 이러한 속성을 **속성** 창입니다.

    |속성|설정 설명|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|이 속성에는 컬렉션 또는 컨트롤에 표시 되는 데이터를 가져오는 데 사용 되는 바인딩을 지정 합니다. 이 속성을 설정 하는 visual Studio는 <xref:System.Windows.Data.CollectionViewSource> 컨트롤을 끌어 부모 데이터에 대 한 합니다.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|이 속성을 컨트롤에 표시 되는 데이터 항목의 경로 지정 합니다. Visual Studio를 사용 하면 첫 번째 열 또는 부모 데이터의 속성에이 속성을 설정 하는 문자열 데이터 형식을 갖는 키 후 합니다.<br /><br /> 부모 데이터에 다른 열 또는 속성을 표시 하려는 경우이 속성을 다른 속성의 경로를 변경 합니다.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 디자이너에 끌어 자식 데이터의 속성에이 속성에 바인딩합니다. 부모 데이터에 외래 키입니다.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio의 경로 열 또는 외래 키를 부모 데이터는 자식 데이터의 속성에이 속성을 설정 합니다.|

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF 응용 프로그램에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md)
- [연습: WPF 애플리케이션에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md)