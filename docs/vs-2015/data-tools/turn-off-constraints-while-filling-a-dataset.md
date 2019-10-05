---
title: 데이터 집합을 채우는 동안 제약 조건 해제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a1ab311db37478f4d5df982e3da022be1601103
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686609"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>데이터 세트를 채우는 동안 제약 조건 해제
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합 제약 조건 (예: 외래 키 제약 조건)에 있으면 theycan 데이터 집합에 대해 수행 되는 작업 순서와 관련 된 오류를 발생 합니다. 예를 들어, loadingrelated 부모 레코드 전에 자식 레코드를 로드 하는 제약 조건을 위반 하 오류가 발생 합니다. 자식 레코드를 로드 하는 즉시 제약 조건 관련된 부모 레코드에 대 한 확인 하 고 오류를 발생 시킵니다.  
  
 임시 제약 조건 일시 중단을 허용 하는 메커니즘이 경우 자식 테이블에 레코드를 로드 하려고 할 때마다 오류가 발생 됩니다. 또 다른 방법은 데이터 집합의 모든 제약 조건을 일시 중단 된 합니다 <xref:System.Data.DataRow.BeginEdit%2A>, 및 <xref:System.Data.DataRow.EndEdit%2A> 속성입니다.  
  
> [!NOTE]
> 유효성 검사 이벤트 (예를 들어 <xref:System.Data.DataTable.ColumnChanging> 고<xref:System.Data.DataTable.RowChanging>) 제약 조건을 해제 하는 경우 발생 하지 것입니다.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>제약 조건 업데이트를 프로그래밍 방식으로 일시 중단  
  
- 다음 예제에서는 데이터 집합에서 제약 조건 검사를 일시적으로 해제 하는 방법을 보여 줍니다.  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>데이터 집합 디자이너를 사용 하 여 제약을 일시 중지 하려면  
  
1. 데이터 집합 디자이너에서 데이터 집합을 엽니다. 자세한 내용은 [방법: 데이터 집합 디자이너에서 데이터 집합 열기](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)합니다.  
  
2. **속성** 창에서 <xref:System.Data.DataSet.EnforceConstraints%2A> 속성을 `false`로 설정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [데이터 집합에서의 관계](../data-tools/relationships-in-datasets.md)
