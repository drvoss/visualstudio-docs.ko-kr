---
title: Windows Forms 응용 프로그램에서 데이터를 필터링 및 정렬 | Microsoft Docs
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
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e12ee25225cb294565490c4d46f26618958dfdf6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697882"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows Forms 애플리케이션에서 데이터 필터링 및 정렬
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

설정 하 여 데이터를 필터링 합니다 <xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 원하는 레코드를 반환 하는 문자열 식입니다.  
  
 설정 하 여 데이터를 정렬 합니다 <xref:System.Windows.Forms.BindingSource.Sort%2A> 속성을 열 이름 기준으로 정렬 하려면; 추가 `DESC` 를 내림차순으로 정렬 하거나 추가 `ASC` 오름차순 정렬 합니다.  
  
> [!NOTE]
> 응용 프로그램을 사용 하지 않는 경우 <xref:System.Windows.Forms.BindingSource> 구성 요소를 필터링 할 수 있습니다 사용 하 여 데이터를 정렬 및 <xref:System.Data.DataView> 개체입니다. 자세한 내용은 [Dataview](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b)합니다.  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 필터링 하려면  
  
- 설정 된 <xref:System.Windows.Forms.BindingSource.Filter%2A> 속성을 반환 하려는 식입니다. 다음 코드를 사용 하 여 고객을 반환 하는 예를 들어, 한 `CompanyName` "B"로 시작 합니다.  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 정렬 하려면  
  
- 설정 된 <xref:System.Windows.Forms.BindingSource.Sort%2A> 에서 정렬 하려는 열에는 속성입니다. 다음 코드에서 고객을 정렬 하는 예를 들어를 `CompanyName` 내림차순 열:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
