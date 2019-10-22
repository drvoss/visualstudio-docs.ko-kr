---
title: XML 문서 속성, 속성 창
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99102248a9456de3a2b3aeba28e54de4299fae40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604150"
---
# <a name="xml-document-properties-properties-window"></a>XML 문서 속성, 속성 창

**속성** 창에서는 XML 편집기에서 활성화 되는 문서에 대 한 기본 정보를 제공 합니다. 현재 활성화되어 있는 XML 문서의 형식에 따라 사용할 수 있는 속성이 달라집니다.

> [!NOTE]
> 모든 XML 문서 속성은 솔루션에 저장됩니다. 그러면 다음에 솔루션을 열 때는 이러한 값을 다시 입력하지 않아도 됩니다.

**인코딩이**

파일에 대한 문자 인코딩입니다. 이 속성을 변경하면 XML 선언의 인코딩 특성도 변경되며 XML 선언의 인코딩 특성을 변경하면 이 속성도 변경됩니다. 새 인코딩은 파일을 저장할 때 파일을 인코딩하는 데 사용 됩니다.

**입력**

XSLT 스타일시트에 연결된 입력 문서입니다. **Xslt 시작** 명령 (예: **XML**  > **디버깅 하지 않고 xslt 시작**)에서 사용 됩니다. 찾아보기 ( **...** ) 단추를 사용 하 여 문서를 선택할 수 있습니다.

이 속성은 편집기에서 XSLT 파일이 열려 있는 경우에만 표시 됩니다.

**Output**

XML 문서를 변형할 때 생성되는 파일입니다.

파일이 지정 되지 않은 경우에는 파일 확장명을 결정 하는 `xsl:output` 요소의 `method` 특성을 기반으로 기본 파일 이름이 생성 됩니다. 기본 파일은 현재 사용자의 임시 디렉터리에 있습니다.

**스키마**

유효성 검사에 사용할 스키마입니다. 이 단추를 사용 하 여 사용할 스키마를 선택 하는 데 사용할 수 있는 **XSD 스키마** 대화 상자를 엽니다.

스키마 경로를 입력할 수도 있습니다. 여러 스키마를 지정할 경우 각 스키마 경로를 큰따옴표로 묶어야 합니다.

**스타일 시트**

디버깅 **시작** 및 **디버깅 하지 않고 xslt 시작** 명령이 사용 되는 경우 문서를 변환 하는 데 사용 되는 xslt 파일입니다. 이 필드가 비어 있으면 편집기에서 문서의 `xml-stylesheet` 처리 명령에 제공 된 값을 사용 하거나 파일 이름을 입력 하 라는 메시지를 표시 합니다.

XSLT 파일을 편집할 때이 속성을 사용 하 여 디버깅을 사용 하지 않고 **Xslt 디버깅** 또는 **시작 xslt 시작** 명령을 선택한 경우 다른 스타일 시트를 사용 하도록 지정할 수 있습니다. 예를 들어 부모 스타일 시트에 포함 된 스타일 시트를 편집 하는 경우이 작업을 수행할 수 있습니다.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)