---
title: XML 편집기 및 스키마 디자이너
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7493d6c10c83b16ad7579299a49a7747e34c20b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746511"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio의 XML 도구

*Extensible Markup Language (XML)* 은 데이터를 설명 하는 형식을 제공 하는 마크업 언어입니다. XML 데이터를 분리 및 연결 된 스타일 시트와 같은 언어 XSL (Extensible Stylesheet) 및 css 스타일 시트 ()를 사용 하 여 표시 합니다. Visual Studio에 포함된 도구와 기능을 사용하면 보다 쉽게 XML, XSLT 및 XML 스키마에 대한 작업을 수행할 수 있습니다.

## <a name="xml-editor"></a>XML 편집기

합니다 [XML 편집기](xml-editor.md) XML 문서를 편집 하는 데 사용 됩니다. 전체 XML 구문 확인, 입력, 색 구분 표시 및 IntelliSense 하는 동안 스키마 유효성 검사를 제공 합니다. 스키마 또는 문서 종류 정의를 지정한 경우 IntelliSense에서 이 스키마 또는 문서 종류 정의를 사용하여 허용되는 요소 및 특성을 나열합니다.

추가 기능은 다음과 같습니다.

- 스키마에서 생성 된 조각을 비롯 한 XML 조각 지원

- 요소 확장 및 축소할 수 있도록 문서 개요 표시

- XSLT 변형을 실행 하 고 텍스트, XML 또는 HTML로 결과 볼 수

- XML 인스턴스 문서에서 XML 스키마 정의 언어 (XSD) 스키마를 생성 하는 기능

- IntelliSense 지원을 비롯 하 여 XSLT 스타일 시트를 편집 하는 것에 대 한 지원

- XML 스키마 탐색기

## <a name="xml-schema-designer"></a>XML 스키마 디자이너

합니다 [XML 스키마 디자이너](xml-schema-designer.md) XML 스키마 정의 언어 (XSD) 스키마 작업을 수행할 수 있도록 Visual Studio 및 XML 편집기와 통합 되었습니다.

## <a name="xslt-debugging"></a>XSLT 디버깅

Visual Studio 지원 [XSLT 스타일 시트를 디버깅](../xml-tools/debugging-xslt.md)합니다. 디버거를 사용하여 XSLT 스타일시트에 중단점을 설정하고 코드에서 XSLT 스타일시트를 한 단계씩 실행하는 등의 작업을 수행할 수 있습니다.

> [!NOTE]
> XSLT 디버거만 Visual Studio의 Enterprise edition에서 제공 됩니다.

## <a name="see-also"></a>참고자료

- <xref:System.Xml?displayProperty=fullName>
- [XSLT 변환](/dotnet/standard/data/xml/xslt-transformations)
- [XPath 데이터 모델을 사용 하 여 XML 데이터 처리](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML DOM(문서 개체 모델)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML SOM(스키마 개체 모델)](/dotnet/standard/data/xml/xml-schema-object-model-som)