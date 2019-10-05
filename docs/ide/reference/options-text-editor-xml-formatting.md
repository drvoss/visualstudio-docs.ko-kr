---
title: 옵션, 텍스트 편집기, XML, 서식 지정
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e20b2f7ebe351aa050ea66468fb33aba8e4a31bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969269"
---
# <a name="options-text-editor-xml-formatting"></a>옵션, 텍스트 편집기, XML, 서식 지정

**서식 지정** 옵션 페이지를 사용하여 XML 문서에서 요소와 특성의 형식 지정 방법을 지정할 수 있습니다. XML 서식 지정 옵션에 액세스하려면 **도구** > **옵션** > **텍스트 편집기** > **XML**을 선택한 다음, **서식 지정**을 선택합니다.

## <a name="attributes"></a>특성

**수동으로 지정한 특성 서식 유지**

특성 서식을 다시 지정하지 않습니다. 이 설정이 기본값입니다.

> [!NOTE]
> 특성이 여러 줄에 있을 경우 편집기는 부모 요소의 들여쓰기와 일치하도록 각 특성 줄을 들여씁니다.

**별도의 줄에 특성 맞춤**

첫 번째 특성의 들여쓰기와 일치하도록 두 번째 특성 및 그 이후 특성을 세로로 정렬합니다. 다음 XML 텍스트는 특성을 정렬하는 방법의 예제입니다.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>자동 서식 다시 지정

**클립보드에서 붙여 넣을 때**

클립보드에서 붙여넣은 XML 텍스트의 서식을 다시 지정합니다.

**끝 태그 완료 시**

끝 태그가 완료될 때 요소의 서식을 다시 지정합니다.

## <a name="mixed-content"></a>혼합 내용

**기본값으로 혼합 콘텐츠 서식 지정**

콘텐츠가 `xml:space="preserve"` 범위에 있는 경우를 제외하고 혼합 콘텐츠의 서식을 다시 지정하려고 시도합니다. 이 설정이 기본값입니다.

요소에 텍스트와 태그가 혼합되어 있는 경우 이 내용은 혼합 내용으로 간주됩니다. 혼합 콘텐츠가 포함된 요소의 예제는 다음과 같습니다.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>참고 항목

- [XML 옵션 - 기타](options-text-editor-xml-miscellaneous.md)
- [Visual Studio의 XML 도구](../../xml-tools/xml-tools-in-visual-studio.md)