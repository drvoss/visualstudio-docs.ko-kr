---
title: DataRelation을 사용 하 여 데이터 집합 간의 관계를 만들려면
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 653a9b589e68c326fc40a94ed0fa3ab7e49acb8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567652"
---
# <a name="create-relationships-between-datasets"></a>데이터 세트 간 관계 만들기
관련된 데이터를 포함 하는 데이터 집합에 사용 하 여 테이블 <xref:System.Data.DataRelation> 서로 관련된 레코드를 반환 하 고 테이블 간의 부모/자식 관계를 나타내는 개체입니다. 관련된 테이블을 사용 하 여 데이터 집합에 추가 합니다 **데이터 소스 구성 마법사**, 또는 **데이터 집합 디자이너**생성 하 고 구성 합니다 <xref:System.Data.DataRelation> 개체입니다.

<xref:System.Data.DataRelation> 개체 두 기능을 수행 합니다.

- 수 있도록 사용 가능한 사용 하는 레코드와 관련 레코드입니다. 자식 레코드는 부모 레코드의 경우 (<xref:System.Data.DataRow.GetChildRows%2A>) 및 자식 레코드를 사용 하 여 작업 하는 경우 부모 레코드 (<xref:System.Data.DataRow.GetParentRow%2A>).

- 부모 레코드를 삭제 하면 관련 된 자식 레코드를 삭제 하는 등의 참조 무결성 제약 조건을 적용할 수 있습니다.

True는 조인 및의 기능 간의 차이점을 이해 해야는 <xref:System.Data.DataRelation> 개체입니다. True 조인 레코드는 부모 및 자식 테이블에서 가져온 및 단일 기본 레코드 집합에 배치 합니다. 사용 하는 경우는 <xref:System.Data.DataRelation> 개체에 없는 새 레코드 집합이 생성 됩니다. 대신, DataRelation 테이블 간의 관계를 추적 하 고 부모 및 자식 레코드를 동기화 하는 유지 합니다.

## <a name="datarelation-objects-and-constraints"></a>DataRelation 개체 및 제약 조건
<xref:System.Data.DataRelation> 개체는 또한 만들고 다음 제약 조건을 적용 하는 데 사용 됩니다.

- 중복 행을 포함 하는 테이블의 열을 보장 하는 고유 제약 합니다.

- 데이터 집합의 부모 및 자식 테이블 간에 참조 무결성을 유지 하기 위해 사용할 수 있는 외래 키 제약 합니다.

지정 하는 제약 조건은 <xref:System.Data.DataRelation> 개체가 자동으로 해당 개체를 만들거나 속성을 설정 하 여 구현 됩니다. 사용 하 여 외래 키 제약 조건을 만든를 <xref:System.Data.DataRelation> 개체, 인스턴스를 <xref:System.Data.ForeignKeyConstraint> 클래스에 추가 되는 <xref:System.Data.DataRelation> 개체의 <xref:System.Data.DataRelation.ChildKeyConstraint%2A> 속성.

Unique 제약 조건을 구현 됩니다 설정 하 여 하나를 <xref:System.Data.DataColumn.Unique%2A> 데이터 열의 속성 `true` 의 인스턴스를 추가 하 여를 <xref:System.Data.UniqueConstraint> 클래스를 <xref:System.Data.DataRelation> 개체의 <xref:System.Data.DataRelation.ParentKeyConstraint%2A> 속성입니다. 참조 데이터 집합의 제약을 일시 중단에 대 한 내용은 [데이터 집합을 채우는 동안 제약 조건 해제](../data-tools/turn-off-constraints-while-filling-a-dataset.md)합니다.

### <a name="referential-integrity-rules"></a>참조 무결성 규칙
외래 키 제약 조건의 일부로 세 지점에 적용 되는 참조 무결성 규칙을 지정할 수 있습니다.

- 부모 레코드를 업데이트 하는 경우

- 부모 레코드를 삭제 하는 경우

- 변경 허용 되는지 또는 거부 되는 경우

수 있게 하는 규칙에 지정 된 된 <xref:System.Data.Rule> 열거형 되며 다음 표에 나열 된 합니다.

|외래 키 제약 조건 규칙|작업|
| - |------------|
|<xref:System.Data.Rule.Cascade>|자식 테이블에서 관련된 레코드의 부모 레코드에 대 한 변경 (update 또는 delete)도 만들어집니다.|
|<xref:System.Data.Rule.SetNull>|자식 레코드는 삭제 되지 않지만 자식 레코드의 외래 키로는 <xref:System.DBNull>합니다. 이 설정을 사용 하 여 자식 레코드도 유지할 수 있습니다 "고아"-즉, 부모 레코드 아무런 관계가 갖습니다. **참고:** 이 규칙을 사용 하 여 자식 테이블에 잘못 된 데이터가 될 수 있습니다.|
|<xref:System.Data.Rule.SetDefault>|관련된 자식 레코드의 외래 키가 기본값으로 설정 (열에서 설정한 <xref:System.Data.DataColumn.DefaultValue%2A> 속성).|
|<xref:System.Data.Rule.None>|관련 된 자식 레코드에 변경 되지 않습니다. 이 설정을 사용 하 여 자식 레코드는 잘못 된 부모 레코드에 대 한 참조를 포함할 수 있습니다.|

데이터 집합 테이블에서 업데이트에 대 한 자세한 내용은 참조 하세요. [데이터를 데이터베이스에 다시 저장](../data-tools/save-data-back-to-the-database.md)합니다.

### <a name="constraint-only-relations"></a>제약 조건 전용 관계
만들 때를 <xref:System.Data.DataRelation> 개체 관계 제약 조건을 적용 하기 위해 사용할 수 있는지를 지정 하는 옵션이 있습니다-즉,이 사용 되지 것입니다도 관련된 레코드에 액세스할 수 있습니다. 약간 더 효율적 이며 관련 레코드 기능을 사용 하 여 1 보다 더 적은 메서드를 포함 하는 데이터 집합을 생성 하려면이 옵션을 사용할 수 있습니다. 그러나 관련된 레코드에 액세스할 수 없습니다. 예를 들어, 제약 조건 전용 관계에서 자식 레코드를가지고 있는 부모 레코드를 삭제 하면 및 부모-자식 레코드에 액세스할 수 없습니다.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>데이터 집합 디자이너에서 데이터 관계를 수동으로 만들기
Visual Studio에서 데이터 디자인 도구를 사용 하 여 데이터 테이블을 만들 때 데이터 원본에서 정보를 수집할 수 있습니다 하는 경우 관계가 자동으로 생성 됩니다. 데이터 테이블을 수동으로 추가 하는 경우는 **데이터 집합** 탭의 **도구 상자**, 수동으로 관계를 만들어야 할 수 있습니다. 만드는 방법은 <xref:System.Data.DataRelation> 개체를 프로그래밍 방식으로 참고 [Datarelation 추가](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)합니다.

데이터 테이블 간의 관계에서 선으로 표시 합니다 **데이터 집합 디자이너**, 관계의 다-측면을 보여 주는 키 및 무한대 문자 모양으로 합니다. 기본적으로 관계의 이름을 디자인 화면에 나타나지 않습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>두 데이터 테이블 간의 관계를 만들려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [연습: 데이터 집합 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)합니다.

2. 끌어서를 **관계** 에서 개체를 **데이터 집합** 관계의 자식 데이터 테이블 도구 상자입니다.

     **관계** 대화 상자가 열리고 채우기는 **자식 테이블** 끌어 놓은 테이블이 포함 된 상자를 **관계** 개체.

3. 부모 테이블을 선택 합니다 **부모 테이블** 상자입니다. 부모 테이블에 일 대 다 관계의 "일" 쪽에서 레코드를 포함합니다.

4. 올바른 자식 테이블에 표시 되는지 확인 합니다 **자식 테이블** 상자입니다. 자식 테이블에 일 대 다 관계의 "다" 쪽에서 레코드를 포함합니다.

5. 관계의 이름을 입력 합니다 **이름** 하거나 기본 이름을 선택한 테이블을 기반으로 합니다. 이 실제 이름을 <xref:System.Data.DataRelation> 코드의 개체입니다.

6. 테이블을 조인 하는 열을 선택 합니다 **키 열** 하 고 **외래 키 열** 나열 합니다.

7. 관계, 제약 조건 또는 둘 다를 만들지 여부를 선택 합니다.

8. 선택 하거나 선택을 취소 합니다 **중첩 된 관계** 상자입니다. 이 옵션을 선택 합니다 <xref:System.Data.DataRelation.Nested%2A> 속성을 `true`, 자식 행을 해당 행은 XML 데이터로 작성 되거나와 동기화 하는 경우 부모 열 내에서 중첩 된 관계의 발생 및 <xref:System.Xml.XmlDataDocument>합니다. 자세한 내용은 [중첩 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)합니다.

9. 이러한 테이블에서 레코드를 변경 하는 경우 적용할 규칙을 설정 합니다. 자세한 내용은 <xref:System.Data.Rule>을 참조하세요.

10. 클릭 **확인** 관계를 만듭니다. 관계 선을 두 테이블 간에 디자이너에 표시 됩니다.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>데이터 집합 디자이너에서 관계 이름을 표시 하려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [연습: 데이터 집합 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)합니다.

2. **데이터** 메뉴를 선택 합니다 **관계 레이블 표시** 관계 이름을 표시 하는 명령입니다. 관계 이름 숨기기에 해당 명령 선택을 취소 합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 집합 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)