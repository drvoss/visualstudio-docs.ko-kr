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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 596397cc22cf0f0134463256c0861127dcfb81e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586616"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows Forms 애플리케이션에서 데이터 필터링 및 정렬

<xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 원하는 레코드를 반환 하는 문자열 식으로 설정 하 여 데이터를 필터링 합니다.

<xref:System.Windows.Forms.BindingSource.Sort%2A> 속성을 정렬할 열 이름으로 설정 하 여 데이터를 정렬 합니다. 내림차순으로 정렬 하려면 `DESC`을 추가 하 고, 오름차순으로 정렬 하려면 `ASC`를 추가 합니다.

> [!NOTE]
> 응용 프로그램에서 <xref:System.Windows.Forms.BindingSource> 구성 요소를 사용 하지 않는 경우 <xref:System.Data.DataView> 개체를 사용 하 여 데이터를 필터링 하 고 정렬할 수 있습니다. 자세한 내용은 [Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)합니다.

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 필터링 하려면

- <xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 반환 하려는 식으로 설정 합니다. 예를 들어 다음 코드는 "B"로 시작 하는 `CompanyName` 있는 고객을 반환 합니다.

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 정렬 하려면

- <xref:System.Windows.Forms.BindingSource.Sort%2A> 속성을 정렬 하려는 열로 설정 합니다. 예를 들어 다음 코드는 `CompanyName` 열에 대 한 고객을 내림차순으로 정렬 합니다.

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
