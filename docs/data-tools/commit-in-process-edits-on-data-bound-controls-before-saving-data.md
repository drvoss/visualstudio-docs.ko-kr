---
title: 저장 하기 전에 데이터 바인딩된 컨트롤에서 in-process 편집 커밋
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129ab5be6264f566de284b2736664c8c0d8c07d7
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261834"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>데이터 바인딩된 컨트롤에서 데이터를 저장하기 전에 In-Process 편집 커밋

데이터 바인딩된 컨트롤에서 값을 편집할 때 사용자가 컨트롤에 바인딩되는 데이터 원본에 값이 업데이트를 적용 하려면 현재 레코드 탐색 해야 합니다. 항목을 끌면 합니다 [데이터 소스 창](add-new-data-sources.md) 폼으로 끌어 놓으면 첫 번째 항목에는 코드를 생성 합니다 **저장** 단추 클릭 이벤트에는 <xref:System.Windows.Forms.BindingNavigator>합니다. 이 코드는 호출을 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 메서드는 <xref:System.Windows.Forms.BindingSource>합니다. 따라서 호출을 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 메서드가 첫 번째에 대해서만 생성 됩니다 <xref:System.Windows.Forms.BindingSource> 폼에 추가 된 합니다.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> 호출에서는 현재 편집 중인 데이터 바인딩된 컨트롤의 프로세스에 포함된 모든 변경 내용을 커밋합니다. 따라서 데이터 바인딩된 컨트롤에 계속 포커스가 있는 상태에서 **저장** 단추를 클릭하면 실제 저장 전에 해당 컨트롤에서 보류 중인 모든 편집 내용이 커밋됩니다(`TableAdapterManager.UpdateAll` 메서드).

사용자가 저장의 일부로 변경 내용을 커밋하지 않고 데이터를 저장 하려고 하는 경우에 자동으로 변경 내용을 커밋 하도록 응용 프로그램을 구성할 수 있습니다 프로세스입니다.

> [!NOTE]
> 디자이너에 추가 된 `BindingSource.EndEdit` 첫 번째 항목에 대해서만 코드를 폼으로 삭제 합니다. 따라서 호출 하는 코드 줄을 추가 해야 합니다 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 각각에 대 한 메서드 <xref:System.Windows.Forms.BindingSource> 양식의 합니다. 호출 하는 코드 줄을 수동으로 추가할 수 있습니다 합니다 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 각각에 대 한 메서드 <xref:System.Windows.Forms.BindingSource>합니다. 추가할 수 있습니다는 `EndEditOnAllBindingSources` 메서드를 폼 및 저장을 수행 하기 전에 호출 됩니다.

다음 코드에서는 [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) 모든 반복 하는 쿼리 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 호출 합니다 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 메서드 각각에 대 한 <xref:System.Windows.Forms.BindingSource> 양식의 합니다.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>EndEdit 양식의 모든 BindingSource 구성 요소에 대 한 호출

1. 다음 코드를 포함 하는 폼에 추가 된 <xref:System.Windows.Forms.BindingSource> 구성 요소입니다.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. 폼의 데이터를 저장 하는 호출 바로 전에 코드의 다음 줄을 추가 (의 `TableAdapterManager.UpdateAll()` 메서드).

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)