---
title: DataContext 메서드의 반환 형식 변경 작업은 실행 취소할 수 없습니다 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb8389d3be96f190941e06ef4a822eaf081f281b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705552"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>DataContext 메서드의 반환 형식 변경은 취소할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext 메서드의 반환 형식을 변경하면 실행 취소할 수 없습니다. 자동으로 생성된 형식으로 되돌리려면 항목을 서버 탐색기/데이터베이스 탐색기에서 O/R 디자이너로 끌어 와야 합니다. 반환 형식을 변경하시겠습니까?  
  
 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식은 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 항목을 드롭하는 위치에 따라 달라집니다. 항목을 기존 엔터티 클래스에 직접 드롭하면 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. 항목을 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]의 빈 영역에 놓으면 자동으로 생성된 형식을 반환하는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. 메서드 창에 추가한 후 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 변경할 수 있습니다. <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 검사하거나 변경하려면 해당 메서드를 선택하고 **속성** 창에서 **반환 형식** 속성을 클릭합니다.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>DataContext의 반환 형식을 변경하려면  
  
- **예**를 클릭합니다.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>반환 형식을 변경하지 않고 메시지 상자를 끝내려면  
  
- **아니요**를 클릭합니다.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>반환 형식을 변경한 후 원래 반환 형식으로 되돌리려면  
  
1. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 <xref:System.Data.Linq.DataContext> 메서드를 선택한 다음, 삭제합니다.  
  
2. **서버 탐색기/데이터베이스 탐색기**에서 항목을 찾아 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]로 끌어옵니다.  
  
     원래 기본 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다.  
  
## <a name="see-also"></a>참고 항목  
 [LINQ to SQL 도구 Visual Studio에서](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)   
 [방법: 저장된 프로시저 및 함수 (O/R 디자이너)에 매핑된 DataContext 메서드 만들기](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
