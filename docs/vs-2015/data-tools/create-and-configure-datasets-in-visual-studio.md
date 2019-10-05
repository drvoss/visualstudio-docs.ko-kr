---
title: 데이터 세트 만들기 및 구성
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6864708d3e60898b32ba07b14939a5c3e31d897e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705128"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio에서 데이터 세트 만들기 및 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *데이터 집합* 데이터베이스에서 데이터를 메모리에 저장 하 고 사용 하도록 설정 하려면 변경 내용 추적을 지 원하는 개체의 집합이 만들기, 읽기, 업데이트 및 삭제 (CRUD) 작업 항상 데이터베이스에 연결할 필요가 없이 해당 데이터에 있습니다. 데이터 집합은 간단한 용으로 설계 된 *데이터 폼* 비즈니스 응용 프로그램입니다. 새 응용 프로그램에 대 한 Entity Framework를 사용 하 여 저장 하 고 메모리에서 데이터를 모델링 하는 것이 좋습니다. 데이터 집합을 사용 하려면 데이터베이스 개념에 대 한 기본 지식이 있어야 합니다.

 형식화 된 만든 <xref:System.Data.DataSet> 를 사용 하 여 디자인 타임에 Visual Studio에서 클래스를 **데이터 소스 구성 마법사**합니다. 프로그래밍 방식으로 데이터 집합을 만드는 방법에 대 한 정보를 참조 하세요 [데이터 집합 만들기](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)합니다.

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>데이터 소스 구성 마법사를 사용 하 여 새 데이터 집합을 만들려면

1. 에 **프로젝트** 메뉴에서 클릭 **새 데이터 소스 추가** 시작 하는 **데이터 소스 구성 마법사**합니다.

2. 에 연결 하는 데이터 원본의 유형을 선택 합니다.

     ![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png "데이터 소스 구성 마법사")

3. 데이터베이스에 대 한 데이터베이스 또는 데이터 집합에 대 한 데이터 원본으로 사용할 데이터베이스를 선택 합니다.

     ![데이터 원본에 대 한 연결 선택](../data-tools/media/data-source-choose-a-connection.png "데이터 원본에 대 한 연결 선택")

4. 테이블 (또는 개별 열), 저장 프로시저, 함수 및 데이터 집합 표시 하려는 데이터베이스에서 뷰를 선택 합니다.

     ![데이터베이스 개체 선택](../data-tools/media/raddata-chose-objects.png "raddata 선택한 개체")

5. **마침**을 클릭합니다.

6. 데이터 집합에 노드로 나타납니다 **솔루션 탐색기**:

     ![솔루션 탐색기에서 데이터 집합](../data-tools/media/dataset-in-solution-explorer.png "솔루션 탐색기에서 데이터 집합")

     해당 노드를 클릭 하 고 데이터 집합에 표시 된 **데이터 집합 디자이너**합니다. 데이터 집합의 각 테이블에는 맨 아래에 표시 되는 연결 된 TableAdapter 개체를 참고 합니다. 테이블 어댑터는 데이터 집합 및 필요에 따라 데이터베이스에 명령을 보내는 데 사용 됩니다.

     ![DataSet Designer](../data-tools/media/dataset-designer.png "DataSet Designer")

7. 데이터베이스에 정의 된 대로 테이블을 연결 하는 관계 선이 테이블 관계를 나타냅니다. 기본적으로 데이터베이스의 외래 키 제약 조건 업데이트로 관계를 표현 하 고 none으로 설정 하는 규칙을 삭제 합니다. 일반적으로 원하는 것입니다. 그러나 줄을 표시를 클릭 하면 합니다 **관계** 대화 상자에서 계층적 업데이트의 동작을 변경할 수 있습니다. 자세한 내용은 [데이터 집합의 관계](../data-tools/relationships-in-datasets.md) 하 고 [계층적 업데이트](../data-tools/hierarchical-update.md)합니다.

     ![데이터 집합 관계 대화](../data-tools/media/raddata-relation-dialog.png "raddata 관계 대화 상자")

8. 테이블, 테이블 어댑터 또는 테이블의 열 이름에서 해당 속성을 보려면 클릭 합니다 **속성** 창입니다. 여기에서 값의 일부를 수정할 수 있습니다. 원본 데이터베이스가 아닌 데이터 집합을 수정 하면 기억 하십시오.

     ![데이터 집합 열 속성](../data-tools/media/dataset-column-properties.png "데이터 집합 열 속성")

9. 데이터 집합에 새 테이블이 나 테이블 어댑터를 추가 하거나 기존 테이블 어댑터에 대 한 새 쿼리를 추가 하거나 해당 항목을 끌어 테이블 간에 새 관계를 지정할 수 있습니다 합니다 **도구 상자** 탭 합니다. 이 탭을 표시 하는 경우는 **데이터 집합 디자이너** 포커스가 있습니다.

     ![데이터 집합 도구 상자](../data-tools/media/raddata-dataset-toolbox.png "raddata 데이터 집합 도구")

10. 다음으로, 아마도 하려는 데이터 집합을 채우는 방법을 지정 합니다. 사용 합니다 **TableAdapter 구성 마법사**합니다. 자세한 내용은 [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md) 합니다.

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>데이터베이스 테이블 또는 다른 개체를 기존 데이터 집합 추가
 이 절차에는 먼저 데이터 집합을 만드는 데는 동일한 데이터베이스에서 테이블을 추가 하는 방법을 보여 줍니다.

1. 데이터 집합 노드를 클릭 **솔루션 탐색기** 으로 포커스를 데이터 집합 디자이너를 가져옵니다.

2. 클릭 합니다 **데이터 원본** Visual Studio의 왼쪽된 여백에 탭 또는 입력 `Data Sources` 에서 **빠른 실행**합니다.

3. 데이터 집합 노드를 마우스 오른쪽 단추로 누르고 **마법사를 사용 하 여 데이터 소스 구성** 합니다.

     ![데이터 원본 상황에 맞는 메뉴](../data-tools/media/data-source-context-menu.png "데이터 원본의 상황에 맞는 메뉴")

4. 마법사를 사용 하 여 추가 테이블, 저장된 프로시저 또는 데이터 집합에 추가할 다른 데이터베이스 개체를 지정 합니다.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>데이터 집합에 독립 실행형 데이터 테이블을 추가 합니다.

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다.

2. 끌어서를 <xref:System.Data.DataTable> 에서 클래스를 **데이터 집합** 탭의 **도구 상자** 에 **데이터 집합 디자이너**.

3. 데이터 테이블을 정의 하는 열을 추가 합니다. 자세한 내용은 [방법: DataTable에 열 추가](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)합니다.

4. 독립 실행형 테이블 구현 해야 `Fill` 독립 실행형 테이블에는 논리를 데이터로 채울 수 있습니다. 독립 실행형 데이터 테이블을 채우는 방법은 [DataAdapter에서 DataSet 채우기](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)합니다.
