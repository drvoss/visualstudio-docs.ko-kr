---
title: '연습: 데이터 집합 디자이너에서 DataTable 만들기'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1126117cb1fc26c4f61bfb0f6ed0e19e86ce9323
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564924"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>연습: 데이터 집합 디자이너에서 DataTable 만들기

이 연습을 만드는 방법을 설명를 <xref:System.Data.DataTable> (TableAdapter) 없이 사용 하는 **데이터 집합 디자이너**. Tableadapter를 포함 하는 데이터 테이블을 만드는 방법에 대 한 정보를 참조 하세요 [만들기 및 Tableadapter 구성](../data-tools/create-and-configure-tableadapters.md)합니다.

## <a name="create-a-new-windows-forms-application"></a>새 Windows Forms 애플리케이션 만들기

1. Visual Studio에서에 **파일** 메뉴에서 **새로 만들기** > **프로젝트**합니다.

2. 확장 **Visual C#** 하거나 **Visual Basic** 왼쪽 창에서 선택한 **Windows Desktop**합니다.

3. 가운데 창에서 선택 합니다 **Windows Forms 앱** 형식 프로젝션 합니다.

4. 프로젝트 이름을 **DataTableWalkthrough**를 선택한 후 **확인**합니다.

     합니다 **DataTableWalkthrough** 프로젝트에 추가한 생성 **솔루션 탐색기**합니다.

## <a name="add-a-new-dataset-to-the-application"></a>응용 프로그램에 새 데이터 집합 추가

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. 왼쪽 창에서 선택 **데이터**을 선택한 후 **데이터 집합** 가운데 창에서.

3. **추가**를 선택합니다.

     라는 파일을 추가 하는 visual Studio **DataSet1.xsd** 프로젝트에서 엽니다 합니다 **데이터 집합 디자이너**합니다.

## <a name="add-a-new-datatable-to-the-dataset"></a>데이터 집합에 새 DataTable을 추가 합니다.

1. 끌어서를 **DataTable** 에서 **데이터 집합** 탭의 **도구 상자** 에 **데이터 집합 디자이너**.

     라는 테이블 **DataTable1** 데이터 집합에 추가 됩니다.

2. 제목 표시줄을 누릅니다 **DataTable1** 하 고 이름을 `Music`입니다.

## <a name="add-columns-to-the-datatable"></a>DataTable에 열 추가

1. 마우스 오른쪽 단추로 클릭 합니다 **음악** 테이블입니다. 가리킨 **추가**를 클릭 하 고 **열**합니다.

2. 열 이름을 `SongID`입니다.

3. **속성** 창에서 <xref:System.Data.DataColumn.DataType%2A> 속성을 <xref:System.Int16?displayProperty=fullName>로 설정합니다.

4. 이 프로세스를 반복 하 고 다음 열을 추가 합니다.

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>테이블에 대 한 기본 키 설정

모든 데이터 테이블에 기본 키가 있어야 합니다. 기본 키 데이터 테이블의 특정 레코드를 고유 하 게 식별합니다.

기본 키를 설정 하려면 마우스 오른쪽 단추로 클릭 합니다 **SongID** 열 및 클릭 **기본 키 설정**합니다. 키 아이콘 옆에 표시 되는 **SongID** 열입니다.

## <a name="save-your-project"></a>프로젝트 저장

저장 하는 **DataTableWalkthrough** 프로젝트에 **파일** 메뉴에서 **모두 저장**합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 집합 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)