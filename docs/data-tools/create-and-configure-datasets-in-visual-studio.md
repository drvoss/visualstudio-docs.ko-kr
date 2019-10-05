---
title: 데이터 세트 만들기 및 구성
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 41a7a699506853d6891c7d7b66fef4082814c06a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460615"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>방법: Visual Studio에서 데이터 세트 만들기 및 구성

데이터 집합은 데이터베이스에서 데이터를 메모리에 저장 하 고 사용 하도록 설정 하려면 변경 내용 추적을 지 원하는 개체 집합을 만들기, 읽기, 업데이트 및 삭제 (CRUD) 작업 항상 데이터베이스에 연결할 필요가 없이 해당 데이터에 있습니다. 데이터 집합은 간단한 용으로 설계 된 *데이터 폼* 비즈니스 응용 프로그램입니다. 새 응용 프로그램에 대 한 Entity Framework를 사용 하 여 저장 하 고 메모리에서 데이터를 모델링 하는 것이 좋습니다. 데이터 집합을 사용 하려면 데이터베이스 개념에 대 한 기본 지식이 있어야 합니다.

형식화 된 만들 수 있습니다 <xref:System.Data.DataSet> 를 사용 하 여 디자인 타임에 Visual Studio에서 클래스를 **데이터 소스 구성 마법사**합니다. 프로그래밍 방식으로 데이터 집합을 만드는 방법에 대 한 정보를 참조 하세요 [데이터 집합 (ADO.NET) 만들기](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)합니다.

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>데이터 소스 구성 마법사를 사용 하 여 새 데이터 집합을 만들려면

1. Visual Studio에서 프로젝트를 열고 선택한 **프로젝트** > **새 데이터 소스 추가** 시작 하는 **데이터 소스 구성 마법사**합니다.

2. 연결에서는 데이터 원본 유형을 선택 합니다.

     ![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)

3. 데이터베이스 또는 데이터 집합에 대 한 데이터 원본으로 사용할 데이터베이스를 선택 합니다.

     ![데이터 원본에 대 한 연결 선택](../data-tools/media/data-source-choose-a-connection.png)

4. 테이블 (또는 개별 열), 저장 프로시저, 함수 및 데이터 집합 표시 하려는 데이터베이스에서 뷰를 선택 합니다.

     ![데이터베이스 개체 선택](../data-tools/media/raddata-chose-objects.png)

5. **마침**을 클릭합니다.

   데이터 집합에 노드로 나타납니다 **솔루션 탐색기**합니다.

   ![솔루션 탐색기에서 데이터 집합](../data-tools/media/dataset-in-solution-explorer.png)

6. 데이터 집합 노드를 클릭 **솔루션 탐색기** 에서 데이터 집합을 열려고 합니다 **데이터 집합 디자이너**합니다. 데이터 집합의 각 테이블에 연결 된 `TableAdapter` 맨 아래에 표시 되는 개체입니다. 테이블 어댑터는 데이터 집합 및 필요에 따라 데이터베이스에 명령을 보내는 데 사용 됩니다.

   ![데이터 세트 디자이너](../data-tools/media/dataset-designer.png)

7. 데이터베이스에 정의 된 대로 테이블을 연결 하는 관계 선이 테이블 관계를 나타냅니다. 기본적으로 데이터베이스의 외래 키 제약 조건 업데이트로 관계를 표현 하 고 none으로 설정 하는 규칙을 삭제 합니다. 일반적으로 원하는 것입니다. 그러나 줄을 표시를 클릭 하면 합니다 **관계** 대화 상자에서 계층적 업데이트의 동작을 변경할 수 있습니다. 자세한 내용은 [데이터 집합의 관계](../data-tools/relationships-in-datasets.md) 하 고 [계층적 업데이트](../data-tools/hierarchical-update.md)합니다.

     ![데이터 집합 관계 대화 상자](../data-tools/media/raddata-relation-dialog.png)

8. 테이블, 테이블 어댑터 또는 테이블의 열 이름에서 해당 속성을 보려면 클릭 합니다 **속성** 창입니다. 여기에서 값의 일부를 수정할 수 있습니다. 원본 데이터베이스가 아닌 데이터 집합을 수정 하면 기억 하십시오.

     ![데이터 집합 열 속성](../data-tools/media/dataset-column-properties.png)

9. 데이터 집합에 새 테이블이 나 테이블 어댑터를 추가 하거나 기존 테이블 어댑터에 대 한 새 쿼리를 추가 하거나 해당 항목을 끌어 테이블 간에 새 관계를 지정할 수 있습니다 합니다 **도구 상자** 탭 합니다. 이 탭을 표시 하는 경우는 **데이터 집합 디자이너** 포커스가 있습니다.

     ![데이터 집합 도구](../data-tools/media/raddata-dataset-toolbox.png)

다음으로, 다음 데이터 집합을 채우는 방법을 지정 하는 것이 좋습니다. 사용 합니다 **TableAdapter 구성 마법사**합니다. 자세한 내용은 [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)합니다.

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>데이터베이스 테이블 또는 다른 개체를 기존 데이터 집합 추가

이 절차에는 먼저 데이터 집합을 만드는 데는 동일한 데이터베이스에서 테이블을 추가 하는 방법을 보여 줍니다.

1. 데이터 집합 노드를 클릭 **솔루션 탐색기** 상태로 전환 하는 **데이터 집합 디자이너** 에 포커스입니다.

2. 클릭 합니다 **데이터 원본** 탭의 형식 또는 Visual Studio의 왼쪽된 여백 **데이터 원본** 검색 상자에 합니다.

3. 데이터 집합 노드를 마우스 오른쪽 단추로 누르고 **마법사를 사용 하 여 데이터 소스 구성**합니다.

     ![데이터 원본 상황에 맞는 메뉴](../data-tools/media/data-source-context-menu.png)

4. 마법사를 사용 하 여 추가 테이블, 저장된 프로시저 또는 데이터 집합에 추가할 다른 데이터베이스 개체를 지정 합니다.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>데이터 집합에 독립 실행형 데이터 테이블을 추가 합니다.

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다.

2. 끌어서를 <xref:System.Data.DataTable> 에서 클래스를 **데이터 집합** 탭의 **도구 상자** 에 **데이터 집합 디자이너**.

3. 데이터 테이블을 정의 하는 열을 추가 합니다. 선택한 테이블을 마우스 오른쪽 단추로 클릭 **추가** > **열**합니다. 사용 된 **속성** 필요한 경우 데이터 형식의 열 및 키를 설정 하는 창입니다.

독립 실행형 테이블 구현 해야 `Fill` 독립 실행형 테이블에는 논리를 데이터로 채울 수 있습니다. 독립 실행형 데이터 테이블을 채우는 방법은 [DataAdapter에서 DataSet 채우기](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
- [데이터 집합에서의 관계](../data-tools/relationships-in-datasets.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)
- [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)