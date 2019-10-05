---
title: 데이터 세트를 채우는 동안 제약 조건 해제
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9aca29de7e9c5a01e0c2caad2c42015cd31b3f75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565188"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>데이터 세트를 채우는 동안 제약 조건 해제

데이터 집합 제약 조건 (예: 외래 키 제약 조건)를 포함 하는 경우 데이터 집합에 대해 수행 되는 작업 순서와 관련 된 오류를 발생 시킬 수 있습니다. 예를 들어, 로드 하기 전에 자식 레코드를 로드와 관련 된 부모 레코드 제약 조건을 위반 및 오류를 발생 시킬 수 있습니다. 자식 레코드를 로드 하는 즉시 제약 조건 관련된 부모 레코드에 대 한 확인 하 고 오류를 발생 시킵니다.

임시 제약 조건 일시 중단을 허용 하는 메커니즘이 경우 자식 테이블에 레코드를 로드 하려고 할 때마다 오류가 발생 됩니다. 또 다른 방법은 데이터 집합의 모든 제약 조건을 일시 중단 된 합니다 <xref:System.Data.DataRow.BeginEdit%2A>, 및 <xref:System.Data.DataRow.EndEdit%2A> 속성입니다.

> [!NOTE]
> 유효성 검사 이벤트 (예를 들어 <xref:System.Data.DataTable.ColumnChanging> 고 <xref:System.Data.DataTable.RowChanging>) 제약 조건을 해제 하는 경우 발생 하지 것입니다.

## <a name="to-suspend-update-constraints-programmatically"></a>제약 조건 업데이트를 프로그래밍 방식으로 일시 중단

- 다음 예제에서는 데이터 집합에서 제약 조건 검사를 일시적으로 해제 하는 방법을 보여 줍니다.

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>데이터 집합 디자이너를 사용 하 여 제약을 일시 중지 하려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [연습: 데이터 집합 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)합니다.

2. **속성** 창에서 <xref:System.Data.DataSet.EnforceConstraints%2A> 속성을 `false`로 설정합니다.

## <a name="see-also"></a>참고자료

- [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
- [데이터 집합에서의 관계](../data-tools/relationships-in-datasets.md)