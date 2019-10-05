---
title: n 계층 애플리케이션에서 TableAdapter에 코드 추가
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e61b9e35464c4200581f6859b2f394911d266d44
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402913"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>n 계층 애플리케이션에서 TableAdapter에 코드 추가
TableAdapter에 대 한 partial 클래스 파일을 만들고 코드를 추가 하 여 TableAdapter의 기능을 확장할 수 있습니다 (코드를 추가 하는 대신 합니다 *DatasetName.DataSet.Designer* 파일). Partial 클래스를 여러 실제 파일에서 나눌 특정 클래스에 대 한 코드를 사용 합니다. 자세한 내용은 [부분](/dotnet/visual-basic/language-reference/modifiers/partial) 하거나 [partial (형식)](/dotnet/csharp/language-reference/keywords/partial-type)합니다.

TableAdapter를 정의 하는 코드는 데이터 집합의 TableAdapter에 변경 될 때마다 생성 됩니다. 이 코드는 TableAdapter의 구성을 수정 하는 모든 마법사를 실행 하는 동안 변경 된 경우에 생성 됩니다. 코드를 TableAdapter의 재생성 하는 동안 삭제를 방지 하려면 TableAdapter의 partial 클래스 파일에 코드를 추가 합니다.

기본적으로 데이터 집합 및 TableAdapter 코드를 분리 한 후 결과는 각 프로젝트의 개별 클래스 파일은입니다. 원래 프로젝트에 이라는 파일로 *DatasetName.Designer.vb* (또는 *DatasetName.Designer.cs*) TableAdapter 코드를 포함 하는 합니다. 지정 된 프로젝트를 **데이터 집합 프로젝트** 속성에 명명 된 파일이 *DatasetName.DataSet.Designer.vb* (또는 *DatasetName.DataSet.Designer.cs*)는 데이터 집합 코드를 포함합니다.

> [!NOTE]
> **데이터 세트 프로젝트** 속성을 설정하여 데이터 세트와 TableAdapters를 분리할 때는 프로젝트의 기존 부분 데이터 세트 클래스가 자동으로 이동되지 않습니다. 기존 부분 데이터 집합 클래스는 데이터 집합 프로젝트에 수동으로 이동 해야 합니다.

> [!NOTE]
> 데이터 집합 생성에 대 한 기능을 제공 <xref:System.Data.DataTable.ColumnChanging> 고 <xref:System.Data.DataTable.RowChanging> 유효성 검사가 필요한 경우 이벤트 처리기입니다. 자세한 내용은 [n 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)합니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 계층 응용 프로그램에서 TableAdapter에 사용자 코드를 추가 하려면

1. 포함 된 프로젝트를 찾는 합니다 *.xsd* 파일입니다.

2. 두 번 클릭 합니다 *.xsd* 열려는 파일을 **데이터 집합 디자이너**합니다.

3. 에 코드를 추가 하 고 클릭 하려는 TableAdapter를 마우스 오른쪽 단추로 클릭 **코드 보기**합니다.

     Partial 클래스는 생성 되 고 코드 편집기에서 열립니다.

4. Partial 클래스 선언 내에 코드를 추가 합니다.

5. 다음 예제에서는 코드를 추가 하는 위치를 `CustomersTableAdapter` 에 `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>참고자료

- [N 계층 데이터 애플리케이션 개요](../data-tools/n-tier-data-applications-overview.md)
- [n 계층 애플리케이션에서 데이터 세트에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [TableAdapter 만들기 및 구성](create-and-configure-tableadapters.md)
- [계층적 업데이트 개요](hierarchical-update.md)
