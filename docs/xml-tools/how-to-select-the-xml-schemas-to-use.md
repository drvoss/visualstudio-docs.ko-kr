---
title: '방법: 사용할 XML 스키마 선택'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2acafe0c782b39bb7aa345b5456df7238703cb20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592648"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>방법: 사용할 XML 스키마 선택

XML 편집기에서는 *%VSInstallDir%\xml\Schemas* 디렉터리에 있는 스키마 캐시를 제공 합니다. 이 스키마 캐시에는 잘 알려진 XML 스키마가 포함되어 있으며 이 스키마는 IntelliSense 및 XML 문서 유효성 검사에 사용됩니다.

**스키마** 문서 속성을 사용 하 여 하나 이상의 XSD (XML 스키마 정의 언어) 스키마를 선택할 수 있습니다. 스키마 캐시 또는 다른 위치에서 스키마를 선택할 수 있습니다.

지정 하는 스키마는 (숨김) 솔루션 사용자 옵션 파일 ()에 저장 됩니다. *.suo*) 및 기타 모든 XML 문서 속성과 함께 사용 됩니다. 따라서 다음에 솔루션을 열 때 이러한 값을 다시 입력 하지 않아도 됩니다.

> [!NOTE]
> 편집기는 인라인 스키마를 사용 하 여 유효성을 검사 하거나 `xsd:schemaLocation` 특성에서 참조 하는 스키마를 사용할 수 있습니다. 자세한 내용은 [XML 문서 유효성 검사](../xml-tools/xml-document-validation.md)를 참조 하세요.

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>스키마 캐시에서 XML 스키마를 선택 하려면

1. XML 편집기에서 파일을 엽니다.

2. 문서 속성 창의 **스키마** 필드를 클릭 합니다. 찾아보기 단추 (...)가 표시 되 면 클릭 합니다.

   ![XML 파일에 대 한 스키마 속성](media/properties-schemas.png)

   [XML 스키마 대화 상자가](xml-schemas-dialog-box.md) 열립니다. 대화 상자에는 모든 스키마가 표시 됩니다. 스키마 캐시의 *xsd* 확장 ( *catalog .xml* 파일에서 참조 되는 스키마 포함) 및 현재 솔루션에 있는 스키마는 Visual Studio에서 열거나 `xsd:schemaLocation` 특성에서 참조 되거나 **스키마** 속성에서 참조 됩니다.

3. 다음 중 하나를 수행하여 유효성 검사에 사용할 스키마를 선택합니다.

   - **XML 스키마** 대화 상자에 나열 된 스키마를 선택 하 고 **사용** 열을 클릭 한 다음 **이 스키마 사용**을 선택 합니다.

     -또는-

   - **XML 스키마** 대화 상자에 나열 된 여러 스키마를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **이 스키마 사용**을 선택 합니다.

4. **확인**을 선택합니다.

   선택한 스키마 목록이 **스키마** 문서 속성으로 다시 복사 됩니다.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>스키마 캐시에 XML 스키마를 추가 하려면

1. 문서 속성 창의 **스키마** 필드에서 단추를 클릭 합니다.

2. **추가**를 클릭합니다.

   **XSD 스키마 열기** 대화 상자가 열립니다.

3. 스키마 캐시에 추가할 스키마를 찾아 선택합니다.

4. **열기**를 클릭합니다.

   스키마가 스키마 캐시에 추가 되 고 열 **사용** 값 **이이 스키마를 사용**하도록 설정 됩니다.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>스키마 캐시에서 XML 스키마를 삭제 하려면

1. 문서 속성 창의 **스키마** 필드에서 단추를 클릭 합니다.

2. 제거할 스키마를 선택 하 고 **제거**를 클릭 합니다.

   그러면 스키마가 메모리 내 스키마 캐시에서 제거되지만 파일 시스템에서는 제거되지 않습니다.

   > [!NOTE]
   > `schemaLocation` 특성 또는 일치 하는 `targetNamespace`를 통해 스키마에 대 한 참조가 있는 경우 자동 연결로 인해 **제거** 는이 상황에서 작동 하지 않습니다. 이 경우 **사용** 열에서 스키마를 **선택한 스키마를 사용 하지** 않는 것으로 표시 하는 것이 좋습니다.

## <a name="see-also"></a>참조

- [스키마 캐시](../xml-tools/schema-cache.md)
- [XML 스키마 대화 상자](../xml-tools/xml-schemas-dialog-box.md)
- [XML 편집기](../xml-tools/xml-editor.md)
