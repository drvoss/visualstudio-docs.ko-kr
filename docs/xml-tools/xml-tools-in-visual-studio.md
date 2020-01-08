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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a5f069d5255a744e256bc9f7d1b48a135e85d8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592310"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio의 XML 도구

*Extensible Markup Language (XML)* 은 데이터를 설명 하는 형식을 제공 하는 마크업 언어입니다. XML은 XSL (Extensible Stylesheet Language) 및 CSS 스타일 시트와 같은 관련 스타일 시트를 사용 하 여 데이터와 해당 프레젠테이션을 분리 합니다. Visual Studio에 포함된 도구와 기능을 사용하면 보다 쉽게 XML, XSLT 및 XML 스키마에 대한 작업을 수행할 수 있습니다.

## <a name="xml-editor"></a>XML 편집기

Xml [편집기](xml-editor.md) 는 xml 문서를 편집 하는 데 사용 됩니다. 이 클래스는 전체 XML 구문 검사, 입력 하는 동안 스키마 유효성 검사, 색 구분 및 IntelliSense를 제공 합니다. 스키마 또는 문서 종류 정의를 지정한 경우 IntelliSense에서 이 스키마 또는 문서 종류 정의를 사용하여 허용되는 요소 및 특성을 나열합니다.

추가 기능은 다음과 같습니다.

- 스키마 생성 코드 조각을 비롯 한 XML 조각 지원

- 요소를 확장 및 축소할 수 있도록 문서 개요 표시

- XSLT 변환을 실행 하 고 텍스트, XML 또는 HTML로 결과를 볼 수 있습니다.

- XML 인스턴스 문서에서 XSD (XML 스키마 정의 언어) 스키마를 생성 하는 기능

- IntelliSense 지원을 포함 하 여 XSLT 스타일 시트 편집 지원

- XML 스키마 탐색기

## <a name="xml-schema-designer"></a>XML 스키마 디자이너

Xml [스키마 디자이너](xml-schema-designer.md) 는 XSD (xml 스키마 정의 언어) 스키마를 사용할 수 있도록 Visual STUDIO 및 xml 편집기와 통합 됩니다.

## <a name="xslt-debugging"></a>XSLT 디버깅

Visual Studio에서는 [XSLT 스타일 시트를 디버깅할](../xml-tools/debugging-xslt.md)수 있습니다. 디버거를 사용하여 XSLT 스타일시트에 중단점을 설정하고 코드에서 XSLT 스타일시트를 한 단계씩 실행하는 등의 작업을 수행할 수 있습니다.

> [!NOTE]
> XSLT 디버거는 Visual Studio의 Enterprise edition 에서만 사용할 수 있습니다.

## <a name="see-also"></a>참조

- <xref:System.Xml?displayProperty=fullName>
- [XSLT 변환](/dotnet/standard/data/xml/xslt-transformations)
- [XPath 데이터 모델을 사용 하 여 XML 데이터 처리](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML DOM(문서 개체 모델)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML SOM(스키마 개체 모델)](/dotnet/standard/data/xml/xml-schema-object-model-som)
