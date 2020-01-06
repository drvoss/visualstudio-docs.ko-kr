---
title: XML 조각
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592323"
---
# <a name="xml-snippets"></a>XML 조각

Xml 편집기에서는 xml 파일을 더 신속 하 게 빌드할 수 있는 *xml 조각*이라는 기능을 제공 합니다. XML 조각을 파일에 삽입하면 이 XML 조각을 다시 사용할 수 있습니다. XSD (XML 스키마 정의 언어) 스키마를 기반으로 XML 데이터를 생성할 수도 있습니다.

## <a name="reusable-xml-snippets"></a>재사용 가능한 XML 코드 조각

XML 편집기에는 몇 가지 일반적인 작업을 다루는 많은 조각이 포함 되어 있습니다. 이 조각을 사용하여 XML 파일을 더욱 쉽게 만들 수 있습니다. 예를 들어 XML 스키마를 작성 하는 경우 "복합 형식 시퀀스 요소" 및 "단순 형식 요소" 코드 조각을 사용 하 여 다음 XML 텍스트를 파일에 삽입 합니다. 그러면 필요에 맞게 `name` 값을 변경할 수 있습니다.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

두 가지 방법으로 조각을 삽입할 수 있습니다. **코드 조각 삽입** 명령은 커서 위치에 XML 조각을 삽입 합니다. **코드 감싸기** 명령은 선택한 텍스트 주위에 XML 조각을 래핑합니다. 두 명령은 모두 **편집** 메뉴 아래의 **IntelliSense** 하위 메뉴 또는 편집기 내의 오른쪽 클릭 메뉴에서 사용할 수 있습니다.

자세한 내용은 [방법: XML 조각 사용](../xml-tools/how-to-use-xml-snippets.md)을 참조 하세요.

## <a name="schema-generated-xml-snippets"></a>스키마 생성 XML 조각

Xml 편집기에서는 xml 스키마에서 XML 조각을 생성할 수 있습니다. 이 기능을 사용하면 요소의 스키마 정보에서 생성된 XML 요소로 해당 요소를 채울 수 있습니다. 자세한 내용은 [방법: xml 스키마에서 xml 조각 생성](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)을 참조 하세요.

## <a name="create-new-xml-snippets"></a>새 XML 조각 만들기

기본적으로 Visual Studio에 포함 된 코드 조각 외에도 사용자 고유의 XML 조각을 만들고 사용할 수 있습니다. 자세한 내용은 [방법: XML 조각 만들기](../xml-tools/how-to-create-xml-snippets.md)를 참조 하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 코드 조각](../ide/code-snippets.md)
- [XML 편집기](../xml-tools/xml-editor.md)
