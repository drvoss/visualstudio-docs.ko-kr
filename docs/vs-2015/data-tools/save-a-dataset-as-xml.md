---
title: 데이터 집합을 XML로 저장 합니다. | Microsoft Docs
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e4331b59c532e681c7e10ab8e43b953e9f72b18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559568"
---
# <a name="save-a-dataset-as-xml"></a>데이터 세트를 XML로 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합의 XML 데이터를 데이터 집합에서 제공 되는 XML 메서드를 호출 하 여 액세스할 수 있습니다. XML 형식으로 데이터를 저장 하려면 하거나 호출할 수 있습니다 합니다 <xref:System.Data.DataSet.GetXml%2A> 메서드 또는 <xref:System.Data.DataSet.WriteXml%2A> 메서드를 <xref:System.Data.DataSet>입니다.  
  
 호출 된 <xref:System.Data.DataSet.GetXml%2A> 메서드 XML으로 형식이 지정 된 데이터 집합에서 모든 데이터 테이블의에서 데이터를 포함 하는 문자열을 반환 합니다.  
  
 호출 된 <xref:System.Data.DataSet.WriteXml%2A> 메서드는 지정 된 파일에는 XML 형식의 데이터를 보냅니다.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>변수에 XML로 데이터 집합에 데이터를 저장 하려면  
  
- 합니다 <xref:System.Data.DataSet.GetXml%2A> 메서드가 반환 되는 <xref:System.String>합니다. 형식의 변수를 선언 하는 것이 즉 <xref:System.String> 의 결과 지정 하 고는 <xref:System.Data.DataSet.GetXml%2A> 메서드.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>파일에 XML로 데이터 집합에 데이터를 저장 하려면  
  
- <xref:System.Data.DataSet.WriteXml%2A> 메서드에 몇 가지 오버 로드가 있습니다. 다음 코드를 파일에 데이터를 저장 하는 방법을 보여 줍니다. 변수를 선언 하 고 파일을 저장 하기 위한 올바른 경로 할당 합니다.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
