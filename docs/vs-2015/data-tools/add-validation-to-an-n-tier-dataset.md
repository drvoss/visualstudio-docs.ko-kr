---
title: N 계층 데이터 집합에 유효성 검사 추가 | Microsoft Docs
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b9b4f77045732bc61fa8aa8e4496eebf86f890a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683215"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>n 계층 데이터 세트에 유효성 검사 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N 계층 솔루션을으로 분리 되어 있는 데이터 집합에 유효성 검사 추가 기본적으로 단일 파일 (단일 프로젝트에서 데이터 집합) 데이터 집합에 유효성 검사와 동일 합니다. 데이터 유효성 검사를 수행 하기 위한 권장된 위치 중인지 합니다 <xref:System.Data.DataTable.ColumnChanging> 및/또는 <xref:System.Data.DataTable.RowChanging> 데이터 테이블의 이벤트입니다.  
  
데이터 집합 디자이너를 열 및 행에 사용자 코드를 추가할 수 있는 partial 클래스를 생성 하는 기능 제공 데이터 집합에 있는 데이터 테이블의 이벤트를 변경 합니다. N 계층 솔루션에서 데이터 집합에 코드를 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [n 계층 응용 프로그램에서 데이터 집합에 코드를 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md), 및 [n 계층 응용 프로그램에서 Tableadapter에 코드를 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)합니다. Partial 클래스에 대 한 자세한 내용은 참조 하세요. [방법: 클래스 (클래스 디자이너) 클래스를 부분 클래스로 분할](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) 나 [Partial 클래스 및 메서드](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)합니다.  
  
> [!NOTE]
> 데이터 집합에서 TableAdapters 분리할 때는 (설정 하 여 합니다 **데이터 집합 프로젝트** 속성), 프로젝트의 기존 부분 데이터 집합 클래스를 자동으로 이동할 수 없습니다. 기존 데이터 집합 부분 클래스는 데이터 집합 프로젝트에 수동으로 이동 해야 합니다.  
  
> [!NOTE]
> 데이터 집합 디자이너를 자동으로 만들지 않으므로 이벤트 처리기에 대 한 C#의 <xref:System.Data.DataTable.ColumnChanging> 고 <xref:System.Data.DataTable.RowChanging> 이벤트입니다. 수동으로 이벤트 처리기를 만들고 기본 이벤트에 이벤트 처리기를 연결 해야 합니다. 다음 절차에서는 Visual Basic 및 C#에서 필요한 이벤트 처리기를 만들어야 하는 방법에 설명 합니다.  
  
## <a name="validatechanges-to-individual-columns"></a>개별 열에 Validatechanges  
 처리 하 여 개별 열의 값을 유효성 검사는 <xref:System.Data.DataTable.ColumnChanging> 이벤트입니다. <xref:System.Data.DataTable.ColumnChanging> 열에 값을 수정할 때 이벤트가 발생 합니다. 에 대 한 이벤트 처리기를 만들고는 <xref:System.Data.DataTable.ColumnChanging> 이벤트 데이터 집합에서 원하는 열을 두 번 클릭 합니다.  
  
 디자이너를 처음으로 열을 두 번 클릭에 대 한 이벤트 처리기가 생성 된 <xref:System.Data.DataTable.ColumnChanging> 이벤트입니다. `If…Then` 문을 만들어집니다 특정 열에 대해 테스트 하는 합니다. 예를 들어, 다음 코드는 Northwind 주문 테이블에 RequiredDate 열을 두 번 클릭할 때 생성 됩니다.  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
> C# 프로젝트에서 데이터 집합 디자이너만 데이터 집합 및 데이터 집합의 개별 테이블에 대해 partial 클래스를 만듭니다. 데이터 집합 디자이너가에 대 한 이벤트 처리기에 자동으로 만들지 않으므로 합니다 <xref:System.Data.DataTable.ColumnChanging> 및 <xref:System.Data.DataTable.RowChanging> C# Visual Basic에서와 같은 이벤트입니다. C# 프로젝트에서 이벤트를 처리 하 고 메서드는 기본 이벤트를 후크 하는 메서드를 수동으로 구성 해야 합니다. 다음 절차에는 Visual Basic 및 C#에서 필요한 이벤트 처리기를 만드는 단계를 제공 합니다.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>개별 열 값을 변경 하는 동안 유효성 검사를 추가 하려면  
  
1. 데이터 집합을 두 번 클릭 하 여 디자이너에서 엽니다는 **.xsd** 파일 **솔루션 탐색기**합니다. 자세한 내용은 [방법: 데이터 집합 디자이너에서 데이터 집합 열기](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)합니다.  
  
2. 유효성을 검사 하려는 열을 두 번 클릭 합니다. 이 작업은 만듭니다는 <xref:System.Data.DataTable.ColumnChanging> 이벤트 처리기입니다.  
  
    > [!NOTE]
    > 데이터 집합 디자이너를 자동으로 C# 이벤트에 대 한 이벤트 처리기를 만들지 않습니다. C#에서 이벤트를 처리 하는 데 필요한 코드는 다음 섹션에 포함 됩니다. `SampleColumnChangingEvent` 생성 되 고 그런 다음 최대 연결 합니다 <xref:System.Data.DataTable.ColumnChanging> 이벤트에는 <xref:System.Data.DataTable.EndInit%2A> 메서드.  
  
3. 확인 코드를 추가 `e.ProposedValue` 응용 프로그램의 요구 사항을 충족 하는 데이터를 포함 합니다. 제안 된 값을 수용할 수 없으면 오류가 있음을 나타내도록 열을 설정 합니다.  
  
     다음 코드 예제는 유효성을 검사 합니다 **수량** 0 개 이상의 열을 포함 합니다. 하는 경우 **수량** 보다 작거나 0으로 열이 설정 된 오류입니다. 합니다 `Else` 경우 절에서 오류를 지웁니다 **수량** 0 보다 크면 합니다. 열 변경 이벤트 처리기의 코드는 다음과 같아야 합니다.  
  
    ```vb  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```  
  
    ```csharp  
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the ColumnChanging event  
            // to call the SampleColumnChangingEvent method.  
            ColumnChanging += SampleColumnChangingEvent;  
        }  
  
        public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
        {  
            if (e.Column.ColumnName == QuantityColumn.ColumnName)  
            {  
                if ((short)e.ProposedValue <= 0)  
                {  
                    e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
                }  
                else  
                {  
                    e.Row.SetColumnError("Quantity", "");  
                }  
            }  
        }  
    ```  
  
## <a name="validatechanges-to-whole-rows"></a>전체 행에 Validatechanges  
 처리 하 여 전체 행의 값 유효성 검사는 <xref:System.Data.DataTable.RowChanging> 이벤트입니다. <xref:System.Data.DataTable.RowChanging> 모든 열의 값 내용이 커밋될 때 이벤트가 발생 합니다. 유효성을 검사 하는 데 필요한 것은 <xref:System.Data.DataTable.RowChanging> 한 열에 값을 다른 열의 값에 의존 하는 경우 이벤트. 예를 들어, Northwind의 Orders 테이블의 OrderDate 및 배송 요청일을 고려 합니다.  
  
 주문 입력 되는, 유효성 검사 하면 주문을 OrderDate 앞에 있는 RequiredDate를 사용 하 여 입력 되지 않도록 합니다. 이 예제에서는 RequiredDate 및 OrderDate 열에 값을 비교 될 필요 하므로 개별 열 변경의 유효성 검사는 의미가 없습니다.  
  
 이벤트 처리기를 만듭니다는 <xref:System.Data.DataTable.RowChanging> 이벤트 테이블의 제목 표시줄에 테이블 이름을 두 번 클릭 합니다.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>전체 행을 변경 하는 동안 유효성 검사를 추가 하려면  
  
1. 데이터 집합을 두 번 클릭 하 여 디자이너에서 엽니다는 **.xsd** 파일 **솔루션 탐색기**합니다. 자세한 내용은 [방법: 데이터 집합 디자이너에서 데이터 집합 열기](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)합니다.  
  
2. 디자이너에서 데이터 테이블의 제목 표시줄 두 번 클릭 합니다.  
  
     부분 클래스를 사용 하 여 만들는 `RowChanging` 이벤트 처리기 및 코드 편집기에서 열립니다.  
  
    > [!NOTE]
    > 데이터 집합 디자이너를 자동으로 만들어지지는지 않습니다에 대 한 이벤트 처리기는 <xref:System.Data.DataTable.RowChanging> C# 프로젝트에서 이벤트입니다. 처리 하는 메서드를 만들어야 합니다 <xref:System.Data.DataTable.RowChanging> 테이블의 초기화 메서드에서 이벤트를 후크 이벤트 및 코드를 실행된 합니다.  
  
3. Partial 클래스 선언 내에서 사용자 코드를 추가 합니다.  
  
4. 다음 코드는 동안 유효성을 검사 하는 사용자 코드를 추가 하는 위치를 보여 줍니다.는 <xref:System.Data.DataTable.RowChanging> Visual Basic에 대 한 이벤트:  
  
    ```vb  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
  
5. 다음 코드를 만드는 방법을 보여 줍니다 합니다 `RowChanging` 이벤트 처리기 및 사용자 코드는 동안 유효성 검사를 추가 하는 위치는 <xref:System.Data.DataTable.RowChanging> C#에 대 한 이벤트:  
  
    ```csharp  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perform the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)   
 [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)
