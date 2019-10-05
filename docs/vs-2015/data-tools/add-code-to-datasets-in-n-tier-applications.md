---
title: N 계층 응용 프로그램에서 데이터 집합에 코드를 추가 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6c788e422ea8613b77d7d0c0460d7c026916baa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697148"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>n 계층 애플리케이션에서 데이터 세트에 코드 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합에 대 한 partial 클래스 파일을 만들고 코드를 추가 하 여 데이터 집합의 기능을 확장할 수 있습니다 (코드를 추가 하는 대신 합니다 *DatasetName*합니다. Dataset.Designer 파일)입니다. Partial 클래스를 여러 실제 파일에서 나눌 특정 클래스에 대 한 코드를 사용 합니다. 자세한 내용은 [부분](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 하거나 [Partial 클래스 및 메서드](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)합니다.

데이터 집합을 정의 하는 코드는 데이터 집합 정의에 변경 내용이 될 때마다 생성 됩니다. 이 코드는 데이터 집합의 구성을 수정 하는 모든 마법사를 실행 하는 동안 변경한 경우에 생성 됩니다. 코드를 데이터 집합의 재생성 하는 동안 삭제를 방지 하려면 데이터 집합의 partial 클래스 파일에 코드를 추가 합니다.

기본적으로 데이터 집합을 분리 한 후 및 `TableAdapter` 결과 코드는 각 프로젝트의 개별 클래스 파일입니다. 원래 프로젝트에는 filenamed *DatasetName*합니다. Designer.vb (또는 *DatasetName*합니다. 포함 된 Designer.cs)는 `TableAdapter` 코드입니다. 지정 된 프로젝트를 **데이터 집합 프로젝트** 속성이 라는 파일로 *DatasetName*합니다. DataSet.Designer.vb (또는 *DatasetName*합니다. DataSet.Designer.cs)입니다. 이 파일에는 데이터 집합 코드를 포함 합니다.

> [!NOTE]
> 데이터 집합을 분리할 때는 및 `TableAdapter`s (설정 하 여 합니다 **데이터 집합 프로젝트** 속성), 프로젝트의 기존 부분 데이터 집합 클래스를 자동으로 이동할 수 없습니다. 기존 데이터 집합 부분 클래스는 데이터 집합 프로젝트에 수동으로 이동 해야 합니다.

> [!NOTE]
> 데이터 집합 디자이너를 생성 하기 위한 기능을 제공 유효성 검사 코드를 추가 해야 하는 경우 <xref:System.Data.DataTable.ColumnChanging> 고 <xref:System.Data.DataTable.RowChanging> 이벤트 처리기입니다. 자세한 내용은 [n 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)합니다.

## <a name="add-code-to-datasets-in-n-tier-applications"></a>n 계층 애플리케이션에서 데이터 세트에 코드 추가

1. .Xsd 파일 (데이터 집합)를 포함 하는 프로젝트를 찾습니다.

2. 선택 된 **.xsd** 파일을 데이터 집합을 엽니다.

3. 코드 (테이블 이름 제목 표시줄에서)을 추가 하 고 클릭 하려는는 데이터 테이블을 마우스 오른쪽 단추로 클릭 **코드 보기**합니다.

     Partial 클래스는 생성 되 고 코드 편집기에서 열립니다.

4. Partial 클래스 선언 내에 코드를 추가 합니다.

     다음 예제에서는 코드에서 NorthwindDataSet CustomersDataTable를 추가할 위치를 보여 줍니다.

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>참고자료

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [n 계층 응용 프로그램에서 TableAdapter에 코드 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager 개요](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [계층적 업데이트 개요](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)