---
title: '연습: XML 편집기 기능 사용'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ce7997e1002ced50dc4d8203d522feb0a6bbb49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604454"
---
# <a name="walkthrough-use-xml-editor-features"></a>연습: XML 편집기 기능 사용

이 연습 단계에서는 새 XML 문서를 만드는 방법을 보여 줍니다. 또한이 연습에서는 xml을 작성 하는 데 유용한 XML 편집기의 기능 중 일부를 사용 합니다.

> [!NOTE]
> 연습을 시작 하기 전에이 항목의 아래에 포함 된 *hireDate* 파일을 로컬 컴퓨터에 저장 합니다.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>새 XML 파일을 만들어 XML 스키마와 연결 하려면

1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **파일**을 클릭 합니다.

2. **템플릿** 창에서 **XML 파일** 을 선택 하 고 **열기**를 클릭 합니다.

     편집기에서 새 파일이 열립니다. 파일에는 기본 XML 선언, `<?xml version="1.0" encoding="utf-8">`이 포함됩니다.

3. 문서 속성 창의 **스키마** 필드에서 찾아보기 단추 ( **...** )를 클릭 합니다.

     **XSD 스키마** 대화 상자가 표시 됩니다.

4. **추가**를 클릭합니다.

     **XSD 스키마 열기** 대화 상자가 표시 됩니다.

5. *HireDate* 파일을 선택 하 고 **열기**를 클릭 합니다.

6. **확인**을 클릭합니다.

     이제 XML 스키마가 XML 문서와 연결되었습니다. XML 스키마는 문서의 유효성을 검사하는 데 사용합니다. IntelliSense에서 유효한 요소의 멤버 목록을 채우는 데도 사용합니다.

## <a name="to-add-data"></a>데이터를 추가하려면

1. 편집기 창에 `<`를 입력합니다.

     멤버 목록에 가능한 항목이 표시됩니다.

    - 주석을 추가 하려면 **!--** 합니다.

    - **!** 문서 유형을 추가 하는 DOCTYPE입니다.

    - **?** 처리 명령을 추가 합니다.

    - root 요소를 추가할 **employee** 입니다.

2. **@No__t_1!--** 를 선택 하 여 주석 노드를 추가 하 고 **enter**키를 누릅니다.

     주석 끝 태그가 삽입되고 주석 시작 태그와 주석 끝 태그 사이에 커서가 놓입니다.

3. **테스트 XML 파일**에를 입력 합니다.

4. 새 줄에 `<`를 입력 하 고 멤버 목록에서 **employee** 를 선택 합니다.

     XML 요소 `<employee`의 시작 부분이 추가됩니다. 이때 요소에 특성을 추가하거나 `>`를 입력하여 시작 태그를 닫을 수 있습니다.

5. `>`를 입력하여 태그를 닫습니다.

6. 끝 태그가 추가됩니다. 끝 태그는 유효성 검사 오류를 나타내는 물결 무늬 밑줄과 함께 추가됩니다. **도구 설명** 에 **' employee ' 요소의 콘텐츠가 완전 하지 않습니다. 메시지가 표시 됩니다. ' I d '가 필요**합니다.

7. @No__t_0를 입력 하 고 멤버 목록에서 **ID** 를 선택 합니다. 그런 다음 `>`를 입력합니다.

     XML 요소 `<ID></ID>`가 추가되고 ID 시작 태그 뒤에 커서가 놓입니다.

8. **Abc**를 입력 합니다.

     **Abc** 텍스트에 물결 무늬 밑줄이 표시 됩니다. **도구 설명** 에 다음 메시지가 표시 됩니다. **' ID ' 요소의 데이터 형식에 따라 잘못 된 값이**있습니다.

9. ID 요소를 마우스 오른쪽 단추로 클릭 하 고 **정의로 이동을**선택 합니다.

     편집기에서 새 문서 창에 *hireDate* 파일이 열리고 ID 스키마 요소 정의에 커서가 배치 됩니다.

10. XML 파일로 돌아가 **abc** 텍스트를 **123**으로 바꿉니다.

     물결선 밑줄 및 **도구 설명은** ID 요소 값 아래에서 지워집니다. 직원 끝 태그에 대 한 **도구 설명** 에 이제 **' employee ' 요소의 콘텐츠가 완전 하지 않습니다 .가 표시 됩니다. ' 채용 날짜 '가 필요**합니다.

11. ID 끝 태그 뒤에 커서를 놓고 `<`를 입력 한 다음 멤버 목록에서 **입사일** 을 선택 하 고 `>`을 입력 합니다.

     XML 요소 `<hire-date></hire-date>`가 추가되고 hire-date 시작 태그 뒤에 커서가 놓입니다.

12. 채용 날짜 값으로 **2003-01-10** 을 입력 합니다.

## <a name="to-format-the-xml-document"></a>XML 문서 서식을 지정하려면

- XML 편집기 도구 모음에서 **문서 서식** 단추를 선택 하거나 **ctrl** +**E**,**D**를 누릅니다.

   ![Visual Studio의 서식 XML 문서 단추](media/format-xml-document.png)

   XML 문서 서식이 다시 지정됩니다.

## <a name="to-save-the-xml-document"></a>XML 문서를 저장하려면

1. **파일** 메뉴에서 다른 **이름으로 저장**을 선택 합니다.

     **다른 이름으로 파일 저장** 대화 상자가 표시 됩니다. 기본 파일 이름은 *' XMLFile1 '* 입니다.

2. XML 문서의 파일 이름과 위치를 입력 하 고 **저장**을 클릭 합니다.

## <a name="hiredatexsd-file"></a>hireDate 파일

이 연습에서 사용 되는 스키마 파일은 다음과 같습니다.

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)