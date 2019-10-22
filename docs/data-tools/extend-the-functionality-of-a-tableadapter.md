---
title: TableAdapter의 기능 확장
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e92b820b04913733095645d21ad682bff40acd84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648489"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>TableAdapter의 기능 확장

TableAdapter의 partial 클래스 파일에 코드를 추가 하 여 TableAdapter의 기능을 확장할 수 있습니다.

Tableadapter를 정의 하는 코드는 **데이터 세트 디자이너**에서 tableadapter가 변경 되거나 마법사에서 tableadapter의 구성을 수정할 때 다시 생성 됩니다. TableAdapter를 다시 생성 하는 동안 코드가 삭제 되지 않도록 하려면 TableAdapter의 partial 클래스 파일에 코드를 추가 합니다.

Partial 클래스를 사용 하면 특정 클래스에 대 한 코드를 여러 물리적 파일 간에 분할할 수 있습니다. 자세한 내용은 [부분](/dotnet/visual-basic/language-reference/modifiers/partial) 또는 [부분 (형식)](/dotnet/csharp/language-reference/keywords/partial-type)을 참조 하세요.

## <a name="locate-tableadapters-in-code"></a>코드에서 Tableadapter 찾기

Tableadapter는 **데이터 세트 디자이너**를 사용 하 여 디자인 되었지만 생성 된 tableadapter 클래스는 <xref:System.Data.DataSet>의 중첩 클래스가 아닙니다. Tableadapter는 TableAdapter의 연결 된 데이터 집합 이름을 기반으로 하는 네임 스페이스에 있습니다. 예를 들어 응용 프로그램에 `HRDataSet` 이라는 데이터 집합이 포함 되어 있으면 Tableadapter는 `HRDataSetTableAdapters` 네임 스페이스에 있습니다. (명명 규칙은이 패턴을 따릅니다: *DatasetName* + `TableAdapters`).

다음 예제에서는 `NorthwindDataSet`를 사용 하 여 프로젝트에서 `CustomersTableAdapter`is 라는 TableAdapter를 가정 합니다.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter의 partial 클래스를 만들려면

1. **프로젝트** 메뉴로 이동 하 고 **클래스 추가**를 선택 하 여 프로젝트에 새 클래스를 추가 합니다.

2. 클래스 이름을 `CustomersTableAdapterExtended`로 지정합니다.

3. **추가**를 선택합니다.

4. 다음과 같이 코드를 프로젝트의 올바른 네임 스페이스 및 partial 클래스 이름으로 바꿉니다.

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>참조

- [TableAdapter를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)