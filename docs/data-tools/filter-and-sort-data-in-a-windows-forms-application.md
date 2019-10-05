---
title: Windows Forms 애플리케이션에서 데이터 필터링 및 정렬
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 17416a3b64d6cbb5f01192440a9df735f0b9fb94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566731"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows Forms 애플리케이션에서 데이터 필터링 및 정렬

설정 하 여 데이터를 필터링 합니다 <xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 원하는 레코드를 반환 하는 문자열 식입니다.

설정 하 여 데이터를 정렬 합니다 <xref:System.Windows.Forms.BindingSource.Sort%2A> 속성을 정렬 하려면; 추가 하는 열 이름 `DESC` 를 내림차순으로 정렬 하거나 추가 `ASC` 오름차순 정렬 합니다.

> [!NOTE]
> 응용 프로그램을 사용 하지 않는 경우 <xref:System.Windows.Forms.BindingSource> 구성 요소를 필터링 할 수 있습니다 사용 하 여 데이터를 정렬 및 <xref:System.Data.DataView> 개체입니다. 자세한 내용은 [Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)합니다.

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 필터링 하려면

- 설정 된 <xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 반환 하려는 식입니다. 다음 코드를 사용 하 여 고객을 반환 하는 예를 들어, 한 `CompanyName` "B"로 시작 합니다.

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 정렬 하려면

- 설정 된 <xref:System.Windows.Forms.BindingSource.Sort%2A> 에서 정렬 하려는 열에는 속성입니다. 다음 코드에서 고객을 정렬 하는 예를 들어를 `CompanyName` 내림차순 열:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)