---
title: TableAdapter의 기능을 확장 | Microsoft Docs
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e14acedeab457df10cc011a94f96d7202972eea
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697892"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>TableAdapter의 기능 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter의 partial 클래스 파일에 코드를 추가 하 여 TableAdapter의 기능을 확장할 수 있습니다.  
  
 TableAdapter에 변경 되 면 TableAdapter를 정의 하는 코드를 다시 생성 합니다 **데이터 집합 디자이너**, 마법사 TableAdapter의 구성을 수정 하는 경우 또는 합니다. 코드를 TableAdapter의 재생성 하는 동안 삭제를 방지 하려면 TableAdapter의 partial 클래스 파일에 코드를 추가 합니다.  
  
 Partial 클래스를 여러 실제 파일에서 나눌 특정 클래스에 대 한 코드를 허용 합니다. 자세한 내용은 [부분](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 하거나 [partial (형식)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)합니다.  
  
## <a name="locate-tableadapters-in-code"></a>코드에서 Tableadapter를 찾습니다  
 사용 하 여 Tableadapter 설계 되어는 **데이터 집합 디자이너**, 생성 된 TableAdapter 클래스의 중첩 된 클래스는 아닙니다 <xref:System.Data.DataSet>합니다. Tableadapter는 TableAdapter의 연결 된 데이터 집합의 이름을 기반으로 하는 네임 스페이스에 있습니다. 예를 들어, 응용 프로그램 이라는 데이터 집합을 포함 하는 경우 `HRDataSet`에서 Tableadapter에 위치를 `HRDataSetTableAdapters` 네임 스페이스입니다. (명명 규칙은이 패턴을 따릅니다. *DatasetName* + `TableAdapters`).  
  
 다음 예제에서는 라는 TableAdapter `CustomersTableAdapter`사용 하 여 프로젝트에 `NorthwindDataSet`입니다.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter에 대 한 partial 클래스를 만들려면  
  
1. 으로 이동 하 여 프로젝트에 새 클래스를 추가 합니다 **프로젝트** 메뉴에서**클래스 추가**합니다.  
  
2. 클래스 이름을 `CustomersTableAdapterExtended`로 지정합니다.  
  
3. **추가**를 선택합니다.  
  
4. 프로젝트에 대 한 partial 클래스 이름과 올바른 네임 스페이스를 사용 하 여 코드를 다음과 같이 바꿉니다.  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>참고 항목  
 [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
