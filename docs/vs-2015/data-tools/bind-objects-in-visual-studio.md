---
title: 개체 바인딩
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 09afb67f0e9431ca8cd520635f243dca70880f09
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683159"
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio에서 개체 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 응용 프로그램에서 데이터 원본으로 사용자 지정 개체 작업에 대 한 디자인 타임 도구를 제공 합니다. UI 컨트롤에 바인딩할 수 있는 개체에는 데이터베이스에서 데이터를 저장 하려는 경우 Entity Framework를 사용 하 여 클래스 또는 클래스를 생성 하는 것이 좋습니다. 엔터티 Frameworkautogenerates 모든 변경 내용 추적 코드, 즉, 로컬 개체를 변경 하는 DbSet 개체에서 AcceptChanges를 호출 하면 데이터베이스에 자동으로 유지 됩니다.    자세한 내용은 [Entity Framework 설명서](https://ef.readthedocs.org/en/latest/)합니다.

> [!TIP]
> 이 문서에 개체 바인딩 방법 응용 프로그램은 데이터 집합에 따라 이미 있는 경우에 고려 되어야 합니다. 이러한 방법은 데이터 집합을 사용 하 여 이미 익숙한 경우를 처리 하는 데이터가 테이블 형식 및 너무 복잡 하지 않은 또는 너무에 사용할 수 있습니다. DataReader를 사용 하 여 수동으로 데이터 바인딩 없이 UI를 업데이트 하 여 개체에 직접 데이터를 로드 하는 관련 된 훨씬 더 간단 예제를 보려면 [ADO.NET을 사용 하 여 간단한 데이터 응용 프로그램을 만들](../data-tools/create-a-simple-data-application-by-using-adonet.md)합니다.

## <a name="object-requirements"></a>개체 요구 사항
 Visual Studio의 디자인 도구는 데이터로 작업 하는 사용자 지정 개체에 대 한 유일한 요구 사항은 개체 하나 이상의 공용 속성이 있는 것입니다.

 일반적으로 사용자 지정 개체는 특정 인터페이스, 생성자 또는 응용 프로그램에 대 한 데이터 소스로 작동 하는 특성에는 필요 하지 않습니다. 그러나 개체를 끌 경우는 **데이터 원본** 데이터 바인딩된 컨트롤을 만드는 디자인 화면에는 창 개체를 구현 하는 경우를 <xref:System.ComponentModel.ITypedList> 또는 <xref:System.ComponentModel.IListSource> 인터페이스 개체는 기본 있어야 합니다. 생성자입니다. 아니면 Visual Studio 데이터 원본 개체를 인스턴스화할 수 없습니다 하 고 디자인 화면으로 항목을 끌면 오류가 표시 됩니다.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>데이터 원본으로 사용자 지정 개체를 사용 하는 예제
 데이터 원본으로 개체를 사용 하 여 작업 하는 경우 응용 프로그램 논리를 구현 하는 수많은 방법 있기는 SQL에 대 한 데이터베이스에 있는 경우 몇 가지 표준 작업을 Visual Studio-생성 된 TableAdapter 개체를 사용 하 여 단순화할 수 있습니다. 이 페이지에서는 이러한 표준 프로세스를 구현 하는 방법을 설명 합니다. 사용자 지정 개체를 만들기 위한 지침으로 없습니다 것 TableAdapters.It를 사용 하 여 합니다. 예를 들어, 개체 또는 응용 프로그램 논리의 특정 구현에 관계 없이 다음 표준 작업은 일반적으로 수행 합니다.

- 일반적으로 데이터베이스의 개체에 데이터를 로드 합니다.

- 형식화 된 개체의 컬렉션을 만드는 중입니다.

- 개체를 추가 하 고 컬렉션에서 개체를 제거 합니다.

- 폼에서 사용자에 게 개체 데이터를 표시 합니다.

- 개체에서 데이터 변경/편집 합니다.

- 데이터베이스에 다시 개체에서 데이터를 저장합니다.

> [!NOTE]
> 더 잘 이해 하 고이 페이지의 예제에 대 한 컨텍스트를 제공 하기 위해 다음을 완료 하는 것이 좋습니다. [연습: 데이터 개체 (Windows Forms)에 연결할](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)합니다. 이 연습에서는 여기에 설명 된 개체를 만듭니다.

### <a name="loaddata-into-objects"></a>개체로 Loaddata
 예를 들어 Tableadapter를 사용 하 여 개체에 데이터를 로드 합니다. Tableadapter는 기본적으로 두 가지는 데이터베이스에서 데이터를 인출 하 고 데이터 테이블 채우는 메서드를 사용 하 여 생성 됩니다.

- `TableAdapter.Fill` 메서드는 반환 되는 데이터를 사용 하 여 기존 데이터 테이블을 채웁니다.

- `TableAdapter.GetData` 메서드는 데이터로 채워진 새 데이터 테이블을 반환 합니다.

  호출 하는 가장 쉬운 방법은 데이터를 사용 하 여 사용자 지정 개체를 로드 하는 것은 `TableAdapter.GetData` 메서드, 반환 된 데이터 테이블에 있는 행의 컬렉션을 반복 하 고 각 행의 값을 사용 하 여 각 개체를 채웁니다. 만들 수는 `GetData` TableAdapter에 추가 하는 모든 쿼리에 대해 채워진된 데이터 테이블을 반환 하는 메서드입니다.

> [!NOTE]
> Visual Studio에는 TableAdapter 쿼리 이름을 `Fill` 고 `GetData` 기본적으로 모든 유효한 메서드 이름에 해당 이름을 변경할 수 있지만.

 다음 예제에서는 데이터 테이블의 행을 반복 하 고 개체를 데이터로 채우는 방법을 보여 줍니다.

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>형식화 된 개체의 컬렉션을 만들려면
 자동으로 제공 되는 형식화 된 컬렉션을 사용 하거나 사용자 개체에 대 한 컬렉션 클래스를 만들 수 있습니다 합니다 [BindingSource 구성 요소](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)합니다.

 개체에 대 한 사용자 지정 컬렉션 클래스를 만들 때에서 상속 하는 것이 좋습니다 <xref:System.ComponentModel.BindingList%601>합니다. 이 제네릭 클래스는 Windows Forms의 데이터 바인딩 인프라에 알림을 전송 하는 이벤트를 발생 시킬 수 뿐만 아니라 컬렉션을 관리 하는 기능을 제공 합니다.

 자동으로 생성 된 컬렉션의 <xref:System.Windows.Forms.BindingSource> 사용을 <xref:System.ComponentModel.BindingList%601> 해당 형식화 된 컬렉션에 대 한 합니다. 응용 프로그램 추가 기능을 사용 하지 않아도 경우 내에서 컬렉션을 유지할 수는 <xref:System.Windows.Forms.BindingSource>합니다. 자세한 내용은 참조 하세요. 합니다 <xref:System.Windows.Forms.BindingSource.List%2A> 의 속성을 <xref:System.Windows.Forms.BindingSource> 클래스.

> [!NOTE]
> 컬렉션에서의 기본 구현을 제공 하지 않는 하는 기능이 필요한 경우는 <xref:System.ComponentModel.BindingList%601>, 필요에 따라 클래스에 추가할 수 있도록 사용자 지정 컬렉션을 만들어야 합니다.

 다음 코드에는 강력한 형식의 컬렉션에 대 한 클래스를 만드는 방법을 보여 줍니다 `Order` 개체:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>컬렉션에 Addobjects
 호출 하 여 개체 컬렉션에 추가 합니다 `Add` 또는 사용자 지정 컬렉션 클래스의 메서드는 <xref:System.Windows.Forms.BindingSource>합니다.

 사용 하 여 컬렉션에 추가 하는 예는 <xref:System.Windows.Forms.BindingSource>를 참조 합니다 `LoadCustomers` 에서 메서드 [연습: 데이터 개체 (Windows Forms)에 연결할](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)합니다.

 사용자 지정 컬렉션에 개체를 추가 하는 예제를 참조 하세요. 합니다 `LoadOrders` 의 메서드 [연습: 데이터 개체 (Windows Forms)에 연결할](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)합니다.

> [!NOTE]
> 합니다 `Add` 에서 상속 하는 경우 사용자 지정 컬렉션에 자동으로 메서드는 제공 <xref:System.ComponentModel.BindingList%601>합니다.

 다음 코드에서 형식화 된 컬렉션에 개체를 추가 하는 방법을 보여 줍니다는 <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 다음 코드에서 상속 되는 형식화 된 컬렉션에 개체를 추가 하는 방법을 보여 줍니다 <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> 이 예제는 `Orders` 컬렉션의 속성은는 `Customer` 개체입니다.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>컬렉션에서 제거할 수
 호출 하 여 컬렉션에서 개체를 제거 합니다 `Remove` 나 `RemoveAt` 메서드 또는 사용자 지정 컬렉션 클래스의 <xref:System.Windows.Forms.BindingSource>합니다.

> [!NOTE]
> 합니다 `Remove` 하 고 `RemoveAt` 에서 상속 하는 경우 사용자 지정 컬렉션에 대 한 메서드가 자동으로 제공 됩니다 <xref:System.ComponentModel.BindingList%601>합니다.

 다음 코드를 찾고 형식화 된 컬렉션에서 개체를 제거 하는 방법을 보여 줍니다는 <xref:System.Windows.Forms.BindingSource> 사용 하 여는 <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> 메서드:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>사용자에 게 Displayobject 데이터
 사용자에 게 개체의 데이터를 표시 하려면 데이터 원본을 사용 하는 개체를 만듭니다는 **데이터 소스 구성** 마법사에서 전체 개체 또는 개별 속성에서 폼으로 끌어와서는 **데이터 원본**창.

### <a name="modify-the-data-in-objects"></a>개체의 데이터 수정
 Windows Forms 컨트롤에 데이터 바인딩된 사용자 지정 개체의 데이터를 편집 하려면 데이터 바인딩된 컨트롤 (또는 개체의 속성에서 직접)를 편집 하면 됩니다. 데이터 바인딩 아키텍처는 개체의 데이터를 업데이트합니다.

 응용 프로그램에서 변경 내용 추적 하 고 원래 값으로 제안 된 변경의 이동에 필요한 개체 모델에서이 기능을 구현 해야 합니다. 어떻게 데이터 테이블 유지의 제안 된 변경 내용을 추적의 예제를 참조 하세요 <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, 및 <xref:System.Data.DataTable.GetChanges%2A>합니다.

### <a name="savedata-in-objects-back-to-the-database"></a>데이터베이스에 다시 개체의 Savedata
 TableAdapter의 DBDirect 메서드를 개체에서 값을 전달 하 여 데이터베이스에 데이터를 저장 합니다.

 Visual Studio 데이터베이스에 대해 직접 실행할 수 있는 DBDirect 메서드를 만듭니다. 이러한 메서드는 DataSet 또는 DataTable 개체를 필요 하지 않습니다.

|TableAdapter DBDirect 메서드|설명|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|개별 열 값을 메서드 매개 변수로 전달할 수 있도록 데이터베이스에 새 레코드를 추가 합니다.|
|`TableAdapter.Update`|기존 데이터베이스에서 레코드를 업데이트 합니다. Update 메서드는 메서드 매개 변수로 원래 및 새 열 값입니다. 원래 값을 원래 레코드를 찾는 데 사용 되 고 새 값은 해당 레코드를 업데이트 하는 데 사용 됩니다.<br /><br /> 합니다 `TableAdapter.Update` 메서드는 또한 수행 하 여 데이터 집합의 변경 내용을 데이터베이스로 다시 조정 하는 데 사용 됩니다는 <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, 또는 배열을 <xref:System.Data.DataRow>메서드 매개 변수로 합니다.|
|`TableAdapter.Delete`|메서드 매개 변수로 전달 되는 원래 열 값에 따라 데이터베이스에서 기존 레코드를 삭제 합니다.|

 개체의 컬렉션에서 데이터를 저장 하려면 (예: 다음에 대 한 루프를 사용 하 여) 개체의 컬렉션을 반복 합니다. TableAdapter의 DBDirect 메서드를 사용 하 여 데이터베이스에 각 개체에 대 한 값을 보냅니다.

 다음 예제에서는 사용 하는 방법을 보여 줍니다는 `TableAdapter.Insert` DBDirect 메서드를 데이터베이스에 직접 새 고객을 추가 합니다.

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
