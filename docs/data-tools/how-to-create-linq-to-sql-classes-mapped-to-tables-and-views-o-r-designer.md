---
title: '방법: LINQ to SQL 클래스 매핑 테이블 및 뷰 (O-r 디자이너) 만들기'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089327"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>방법: LINQ to SQL 클래스 매핑 테이블 및 뷰 (O/R 디자이너) 만들기
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 데이터베이스 테이블 및 뷰에 매핑되는 클래스 라고 *엔터티 클래스*합니다. 엔터티 클래스는 레코드에 매핑되지만 엔터티 클래스의 개별 속성 레코드를 구성 하는 각 열에 매핑됩니다. 테이블 또는 뷰를 끌어 데이터베이스 테이블 또는 뷰에에 기반한 엔터티 클래스를 만듭니다 **서버 탐색기** 하거나 **데이터베이스 탐색기** 에 [VisualStudio에서LINQtoSQL도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md). 합니다 **O/R 디자이너** 클래스를 생성 하 고 특정 적용 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 특성이 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 기능 (데이터 통신 및 편집의 기능을 <xref:System.Data.Linq.DataContext>). 에 대 한 자세한 내용은 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 클래스를 참조 하세요 [LINQ to SQL 개체 모델](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)합니다.

> [!NOTE]
>  합니다 **O/R 디자이너** 1:1 매핑 관계만 지 원하는 단순 개체 관계형 매퍼입니다. 즉, 엔터티 클래스는 데이터베이스 테이블 또는 뷰와 1:1 매핑 관계만 갖습니다. 엔터티 클래스를 여러 테이블에 매핑하는 복잡한 매핑은 지원되지 않습니다. 그러나 엔터티 클래스를 여러 관련 테이블을 연결하는 뷰에 매핑할 수 있습니다.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>LINQ to SQL 클래스 데이터베이스 테이블 또는 뷰에 매핑되는 만들기
 테이블 또는 뷰를 끌어 오면 **서버 탐색기** 또는 **데이터베이스 탐색기** 에 **O/R 디자이너** 외에 엔터티 클래스가 만들어집니다는 <xref:System.Data.Linq.DataContext> 메서드는 업데이트를 수행 하는 데 사용 됩니다.

 기본적으로 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 런타임에서는 업데이트 가능한 엔터티 클래스의 변경 내용을 데이터베이스에 다시 저장하는 논리를 만듭니다. 이 논리는 열 정의 및 기본 키 정보와 같은 테이블 스키마를 기반으로 합니다. 이 동작 하지 않으려면 삽입, 업데이트 및 기본값을 사용 하는 대신 삭제 하는 데 저장된 프로시저를 사용 하는 엔터티 클래스를 구성할 수 있습니다 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 런타임 동작 합니다. 자세한 내용은 [방법: 업데이트, 삽입 및 삭제 (O/R 디자이너)를 수행 하는 저장된 프로시저를 할당](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)합니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>데이터베이스 테이블 또는 뷰에 매핑된 LINQ to SQL 클래스를 만들려면

1.  **서버** 또는 **데이터베이스 탐색기**를 확장 하 고 **테이블** 또는 **뷰** 및 데이터베이스 테이블을 찾아 보거나에서 사용 하려는 사용자 응용 프로그램입니다.

2.  보거나 테이블을 끌어 옵니다 합니다 **O/R 디자이너**합니다.

     엔터티 클래스가 만들어져 디자인 화면에 표시됩니다. 엔터티 클래스에는 선택한 테이블 또는 뷰의 열에 매핑되는 속성이 있습니다.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>개체 데이터 소스를 만들고 폼에 데이터 표시
 사용 하 여 엔터티 클래스를 만든 후 합니다 **O/R 디자이너**, 개체 데이터 소스를 만들고 채울 수 있습니다 합니다 [데이터 소스 창](add-new-data-sources.md) 엔터티 클래스를 사용 하 여 합니다.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL 엔터티 클래스 기반의 개체 데이터 소스를 만들려면

1.  에 **빌드** 메뉴에서 클릭 **솔루션 빌드** 프로젝트를 빌드해야 합니다.

2.  **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

3.  **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

4.  클릭 **개체** 에 **데이터 소스 형식 선택** 페이지를 클릭 한 다음 **다음**합니다.

5.  노드를 확장하여 클래스를 찾아 선택합니다.

    > [!NOTE]
    >  경우는 **고객** 클래스를 사용할 수 없는 경우, 마법사를 취소, 프로젝트를 빌드 및 마법사를 다시 실행 합니다.

6.  클릭 **완료** 데이터 소스를 만들고 추가 하는 **고객** 엔터티 클래스를 **데이터 원본** 창입니다.

7.  항목을 끌어 합니다 **데이터 원본** 창에서 폼입니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습:는 LINQ to SQL 클래스 (O-r 디자이너) 만들기](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)
- [방법: 저장된 프로시저 및 함수 (O/R 디자이너)에 매핑된 DataContext 메서드 만들기](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 개체 모델](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작을 사용자 지정](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [방법: LINQ to SQL 클래스 (O/R 디자이너) 사이 연결 (관계) 만들기](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)