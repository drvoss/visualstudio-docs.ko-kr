---
title: 데이터 세트 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e53a31a274a356d5686c3225ed2635e6c61231c2
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824707"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio의 데이터 세트 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 데이터 집합 및 관련된 클래스는 응용 프로그램은 데이터베이스에서 연결이 끊어진 동안 메모리에 있는 데이터로 작업 하는 응용 프로그램을 사용 하도록 설정 하는 초기에 종사해에서 레거시.NET 기술입니다. 사용자가 데이터를 수정 하 고 다시 데이터베이스에 변경 내용을 유지할 수 있게 하는 응용 프로그램에 특히 유용 합니다. 데이터 집합, 매우 성공적 이었던 기술이 입증 하지만 새로운.NET 응용 프로그램 Entity Framework를 사용 하는 것이 좋습니다. 더 간단한 프로그래밍 인터페이스에 및 entity Framework 개체 모델로 테이블 형식 데이터로 작업 하는 더 자연 스러운 방법을 제공 합니다.

 DataSet 개체는 기본적으로 최소 데이터베이스는 메모리 내 개체. 저장 하 고 열려 있는 연결을 유지 관리 하지 않고도 하나 이상의 데이터베이스에서 데이터를 수정할 수 있는 DataTable, DataColumn의 경우 및 DataRow 개체를 포함 합니다. 데이터 집합 업데이트를 추적 하 고 응용 프로그램에 다시 연결 되는 경우 데이터베이스에 다시 전송 될 수 있도록 해당 데이터를 변경 하는 방법에 대 한 정보를 유지 관리 합니다.

 데이터 집합 및 관련된 클래스는.NET Framework 클래스 라이브러리의 System.Data 네임 스페이스에 정의 됩니다. 만들기 및 코드에서 동적으로 데이터 집합을 수정할 수 있습니다. 그렇게 하는 방법에 대 한 자세한 내용은 ADO.NET을 참조 하세요. 이 섹션의에서 설명서에서는 Visual Studio 디자이너를 사용 하 여 데이터 집합을 사용 하는 방법을 보여 줍니다. 점은 알고 있어야 합니다: 디자이너를 통해 만들어진 데이터 집합 프로그래밍 방식으로 만들어진 데이터 집합 DataAdapter 개체를 사용 하는 반면 데이터베이스와 상호 작용 하려면 TableAdapter 개체를 사용 합니다. 프로그래밍 방식으로 데이터 집합을 만드는 방법에 대 한 자세한 내용은 [Dataadapter 및 Datareader](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74)합니다.

 응용 프로그램 데이터베이스에서 데이터 읽기 및 업데이트를 수행 하지 해야, 추가, 삭제 하는 경우 generic List 개체 또는 다른 컬렉션 개체에 데이터를 검색 하는 DataReader 개체를 사용 하 여 일반적으로 성능 향상을 얻을 수 있습니다. 데이터를 표시 하는 경우 바인딩할 수 있습니다 데이터 사용자 인터페이스는 컬렉션입니다.

## <a name="dataset-workflow"></a>데이터 집합 워크플로
 Visual Studio에는 많은 데이터 집합을 사용 하 여 작업을 간소화 하기 위해 도구를 제공 합니다. 기본 종단 간 워크플로 다음과 같습니다.

- 사용 된 **데이터 원본** 창 하나 이상의 데이터 원본에서 새 데이터 집합 만들기. 사용 된 **데이터 집합 디자이너** 데이터 집합을 구성 하 고 해당 속성을 설정할 합니다. 예를 들어, 각 테이블의 열과를 포함 하려면 데이터 원본에서 테이블을 지정 해야 합니다. 데이터 집합을 요구 하는 메모리의 양을 절약 하기 위해 신중 하 게 선택 합니다. 자세한 내용은 [데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조하세요.

- 외래 키를 올바르게 처리할 수 있도록 테이블 간의 관계를 지정 합니다. 자세한 내용은 [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)합니다.

- 사용 된 **TableAdapter 구성 마법사** 쿼리 또는 데이터 집합을 채우는 저장된 프로시저를 지정할 수 및 데이터베이스 작업 (업데이트, 삭제 및 등)을 구현 합니다. 자세한 내용은 다음 항목을 참조하세요.

  - [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [데이터 집합의 데이터 편집](../data-tools/edit-data-in-datasets.md)

  - [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)

  - [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)

- 쿼리 및 데이터 집합의 데이터를 검색 합니다. 자세한 내용은 [데이터 집합 쿼리](../data-tools/query-datasets.md)합니다. [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] 사용 하도록 설정 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) 데이터에 대 한 <xref:System.Data.DataSet> 개체입니다. 자세한 내용은 [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)을 참조하세요.

- 사용 된 **데이터 원본** 창 사용자 인터페이스 컨트롤을 데이터 집합 또는 개별 열을 바인딩할 하 고 사용자가 편집 가능한 열을 지정 하려면. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)합니다.

## <a name="datasets-and-n-tier-architecture"></a>데이터 집합 및 N 계층 아키텍처
 N 계층 응용 프로그램에서 데이터 집합에 대 한 자세한 내용은 [n 계층 응용 프로그램에서 데이터 집합 작업](../data-tools/work-with-datasets-in-n-tier-applications.md)합니다.

## <a name="datasets-and-xml"></a>데이터 집합 및 XML
 Xml 데이터 집합을 변환 하는 방법에 대 한 정보를 참조 하세요. [읽기 XML 데이터를 dataset](../data-tools/read-xml-data-into-a-dataset.md) 하 고 [데이터 집합을 XML로 저장](../data-tools/save-a-dataset-as-xml.md)합니다.

## <a name="see-also"></a>참고 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
