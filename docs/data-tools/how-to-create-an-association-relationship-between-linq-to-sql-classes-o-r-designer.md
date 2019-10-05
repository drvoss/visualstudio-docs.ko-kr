---
title: LINQ to SQL 클래스 (O/R 디자이너) 간의 관계
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 51999b1fe9396eaa393491d9a96b184a674621da
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260422"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>방법: LINQ to SQL 클래스 (O/R 디자이너) 간 연결 만들기
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]에서 엔터티 클래스 간의 연결은 데이터베이스 테이블 간의 관계와 비슷합니다. **연결 편집기** 대화 상자를 사용하여 엔터티 클래스 간의 연결을 만들 수 있습니다.

**연결 편집기** 대화 상자에서 연결을 만들 때 부모 클래스와 자식 클래스를 선택해야 합니다. 부모 클래스는 기본 키가 있는 엔터티 클래스이고, 자식 클래스는 외래 키가 있는 엔터티 클래스입니다. 예를 들어, 엔터티 클래스에 매핑되는 생성 된 경우에 `Northwind Customers` 및 `Orders` 테이블의 `Customer` 클래스는 부모 클래스 것 및 `Order` 클래스는 자식 클래스는 것입니다.

> [!NOTE]
> 테이블을 끌어 오면 **서버 탐색기** 또는 **데이터베이스 탐색기** 에 **Object Relational Designer** (**O/R 디자이너**), 연결 된 데이터베이스의 기존 외래 키 관계에 따라 자동으로 생성 됩니다.

## <a name="association-properties"></a>연결 속성
연결을 만든 후 **O/R 디자이너**에서 연결을 선택하면 **속성** 창에 몇 개의 구성 가능한 속성이 나타납니다. 연결은 관련 클래스 간의 선입니다. 다음 표에서는 연결 속성을 설명합니다.

|속성|설명|
|--------------|-----------------|
|**Cardinality**|연결이 일대다 연결인지 또는 일대일 연결인지를 제어합니다.|
|**자식 속성**|연결의 외래 키 쪽에서 자식 레코드의 컬렉션이거나 자식 레코드에 대한 참조인 부모 속성을 만들지 여부를 지정합니다. 간의 연결에서 예를 들어 `Customer` 및 `Order`경우는 **자식 속성** 로 설정 되어 **True**, 라는 속성이 `Orders` 부모 클래스에 생성 됩니다.|
|**부모 속성**|연결된 부모 클래스를 참조하는 자식 클래스의 속성입니다. 간의 연결에서 예를 들어 `Customer` 및 `Order`, 라는 속성이 `Customer` 를 참조 하는 연결 된 고객 주문에 생성 됩니다에 대 한는 `Order` 클래스입니다.|
|**참여 속성**|연결 속성을 표시하고 **연결 편집기** 대화 상자를 다시 여는 **줄임표** 단추(...)를 제공합니다.|
|**Unique**|외래 대상 열에 고유성 제약 조건이 있는지 여부를 지정합니다.|

## <a name="to-create-an-association-between-entity-classes"></a>엔터티 클래스 간에 연결을 만들려면

1. 연결에서 부모 클래스를 나타내는 엔터티 클래스를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음, **연결**을 클릭합니다.

2. **연결 편집기** 대화 상자에서 올바른 **부모 클래스**가 선택되었는지 확인합니다.

3. 콤보 상자에서 **자식 클래스**를 선택합니다.

4. 클래스가 관련된 **연결 속성**을 선택합니다. 일반적으로 이는 데이터베이스에 정의된 외래 키 관계에 매핑됩니다. 예를 들어,를 `Customers` 및 `Orders` 연결을 **연결 속성** 는 `CustomerID` 각 클래스에 대 한 합니다.

5. **확인**을 클릭하여 연결을 만듭니다.

## <a name="see-also"></a>참고자료

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습: LINQ to SQL 클래스 만들기](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext 메서드(O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)
- [방법: 기본 키 표현](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
