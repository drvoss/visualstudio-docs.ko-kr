---
title: '방법: XML 리터럴과 함께 XML 스키마 디자이너 사용'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9e92cbdca3ac2c5c366ec054ba79f2e7324986c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001810"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>방법: XML 리터럴과 함께 XML 스키마 디자이너 사용

이 항목에서는 Visual Basic 프로젝트에서 XML 리터럴과 연결된 스키마를 보는 방법에 대해 설명합니다.

## <a name="create-a-new-visual-basic-project"></a>새 Visual Basic 프로젝트 만들기

1. Visual Studio를 엽니다.

2. 새 Visual Basic을 만듭니다 **콘솔 앱** 라는 프로젝트가 **XMLLiterals**합니다.

     새 프로젝트를 포함 한 Visual Basic 소스 파일 *Module1.vb*합니다.

## <a name="add-an-existing-xsd-file"></a>기존 XSD 파일 추가

1. 새 텍스트 파일을 메모장에서 엽니다. XML 스키마 샘플 코드를 복사 [구매 주문 스키마](../xml-tools/sample-xsd-file-simple-schema.md) 파일에 붙여 넣습니다.

2. 파일 이름으로 일부 위치에 저장 합니다 *PurchaseOrderSchema.xsd*합니다.

3. **솔루션 탐색기**, 프로젝트의 이름을 마우스 오른쪽 단추로 선택 **추가**를 선택한 후 **기존 항목**합니다. 합니다 **기존 항목 추가** 대화 상자가 나타납니다. 로 이동 합니다 *PurchaseOrderSchema.xsd* 파일, 선택 및 클릭 **추가**합니다.

     XMLLiterals 프로젝트에는 이제 두 개의 파일이 들어 있습니다. *Module1.vb* 하 고 *PurchaseOrderSchema.xsd*합니다.

## <a name="add-code"></a>코드를 추가 합니다.

리터럴 XML 사용 하 여 Visual Basic 코드를 추가 하려면 프로젝트에 포함 된 XSD 파일을 기반으로 합니다.

1. 코드를 바꿔 *Module1.vb* 를 다음 코드로 파일:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. XML 리터럴 또는 XML 네임 스페이스 가져오기에서 XML 노드를 마우스 오른쪽 단추로 누르고 **스키마 탐색기에 표시**합니다.

   합니다 **XML 스키마 탐색기** XML 스키마 집합과 연결 된 XML 리터럴이 있는 Visual Basic 파일과 나란히 표시 됩니다.