---
title: 데이터 세트를 XML로 저장
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c993ac8703468a24a99e114563fec1bdc817581
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566230"
---
# <a name="save-a-dataset-as-xml"></a>데이터 세트를 XML로 저장

데이터 집합에서 제공 되는 XML 메서드를 호출 하 여 데이터 집합의 XML 데이터에 액세스 합니다. XML 형식으로 데이터를 저장 하려면 하거나 호출할 수 있습니다 합니다 <xref:System.Data.DataSet.GetXml%2A> 메서드 또는 <xref:System.Data.DataSet.WriteXml%2A> 메서드를 <xref:System.Data.DataSet>입니다.

호출 된 <xref:System.Data.DataSet.GetXml%2A> 메서드 XML으로 형식이 지정 된 데이터 집합에서 모든 데이터 테이블의에서 데이터를 포함 하는 문자열을 반환 합니다.

호출 된 <xref:System.Data.DataSet.WriteXml%2A> 메서드는 지정 된 파일에는 XML 형식의 데이터를 보냅니다.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>변수에 XML로 데이터 집합에 데이터를 저장 하려면

- 합니다 <xref:System.Data.DataSet.GetXml%2A> 메서드가 반환 되는 <xref:System.String>합니다. 형식의 변수 선언 <xref:System.String> 의 결과 지정 하 고는 <xref:System.Data.DataSet.GetXml%2A> 메서드.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>파일에 XML로 데이터 집합에 데이터를 저장 하려면

- <xref:System.Data.DataSet.WriteXml%2A> 메서드에 몇 가지 오버 로드가 있습니다. 변수를 선언 하 고 파일을 저장 하기 위한 올바른 경로 할당 합니다. 다음 코드를 파일에 데이터를 저장 하는 방법을 보여 줍니다.

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)