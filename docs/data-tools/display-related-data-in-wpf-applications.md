---
title: WPF 애플리케이션에서 관련 데이터 표시
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da6f276e714c816ea9b3c1b735ad50f31ffdc3c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567073"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF 애플리케이션에서 관련 데이터 표시

일부 응용 프로그램에서 여러 테이블 또는 부모-자식 관계에서 서로 관련 된 엔터티를 함께 제공 되는 데이터로 작업 하는 것이 좋습니다. 예를 들어 고객을 표시 하는 표를 표시 하려면 수는 `Customers` 테이블입니다. 사용자가 특정 고객을 선택 하면 다른 표의 관련에서 해당 고객의 주문을 `Orders` 테이블입니다.

항목을 끌어 관련된 데이터를 표시 하는 데이터 바인딩된 컨트롤을 만들 수 있습니다 합니다 **데이터 원본** 창에서 WPF 디자이너로 합니다.

## <a name="to-create-controls-that-display-related-records"></a>관련된 레코드를 표시 하는 컨트롤을 만들려면

1. **데이터** 메뉴에서 **데이터 원본 표시**를 클릭하여 **데이터 원본** 창을 엽니다.

2. **새 데이터 원본 추가**를 클릭하고 **데이터 원본 구성 마법사** 완료합니다.

3. WPF 디자이너를 열고 디자이너의 항목에 대 한 유효한 놓기 대상 컨테이너가 포함 되어 있는지 확인 합니다 **데이터 원본** 창입니다.

     유효한 놓기 대상에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)합니다.

4. 에 **데이터 원본** 창 부모 테이블을 나타내는 노드를 확장 또는 관계 개체입니다. 부모 테이블 또는 개체에 일 대 다 관계의 "일" 쪽 켜져 있습니다.

5. 부모 노드 (또는 부모 노드에 있는 개별 항목)에서 끌어 합니다 **데이터 원본** 창 디자이너에서 유효한 놓기 대상으로 합니다.

     Visual Studio를 끌 수 있는 각 항목에 대 한 새 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. XAML도 새 추가 <xref:System.Windows.Data.CollectionViewSource> 부모 테이블 또는 개체를 놓기 대상의 리소스에 대 한 합니다. 일부 데이터 원본의 경우 Visual Studio 데이터 부모 테이블이 나 개체를 로드 하는 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)합니다.

6. 에 **데이터 원본** 창 관련된 자식 테이블 또는 개체를 찾습니다. 개체와 관련 된 자식 테이블 데이터의 부모 노드 목록 맨 아래에 확장 가능한 노드로 표시 합니다.

7. 자식 노드 (또는 개별 항목에 자식 노드)에서 끌어 합니다 **데이터 원본** 창 디자이너에서 유효한 놓기 대상으로 합니다.

     Visual Studio의 각 끌면 항목에 대 한 새 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. XAML도 새 추가 <xref:System.Windows.Data.CollectionViewSource> 자식 테이블이 나 개체를 놓기 대상의 리소스에 대 한 합니다. 이 새로운 <xref:System.Windows.Data.CollectionViewSource> 는 부모 테이블 또는 디자이너로 끌어 온 개체의 속성에 바인딩됩니다. 일부 데이터 원본의 경우 Visual Studio 데이터 자식 테이블이 나 개체를 로드 하는 코드를 생성 합니다.

     다음 그림에서는 관련 된 방법을 보여 줍니다 **주문** 목차를 **고객** 테이블에서 데이터 집합에서을 **데이터 원본** 창.

     ![관계를 보여 주는 데이터 소스 창](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF 응용 프로그램에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-wpf-applications.md)