---
title: XML 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
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
- XML [Visual Studio], .NET Framework classes
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ee0cf61f8ec2787894c6f67b8ac75424246c507
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297453"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio의 XML 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML)* is a markup language that provides a format for describing data. 이 언어를 사용하면 콘텐츠를 보다 정확하게 선언하고 여러 플랫폼 간에 보다 의미 있는 검색 결과를 얻을 수 있습니다. 또한 XML을 사용하는 경우 표시를 데이터 자체와 구분할 수 있습니다. 예를 들어 HTML에서는 태그를 사용하여 데이터를 굵게, 기울임꼴 등으로 표시하도록 브라우저에 명령하지만 XML에서는 태그를 사용하여 구/군/시 이름, 기온, 기압 등의 데이터만을 설명합니다. XML에서는 XSL(Extensible Stylesheet Language) 및 CSS(CSS 스타일시트)와 같은 스타일시트를 사용하여 브라우저에 데이터를 표시합니다. XML에서는 데이터가 표시 및 프로세스와 구분되므로 여러 스타일시트 및 애플리케이션을 적용하여 데이터를 원하는 방식으로 표시 및 처리할 수 있습니다.

 XML은 웹을 통해 제공하도록 최적화된 SGML의 하위 집합으로, W3C(World Wide Web Consortium)에 의해 정의되었습니다. 이러한 표준화로 인해 구조적 데이터가 애플리케이션이나 공급업체와 상관없이 일정하게 유지됩니다.

 XML은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에서 제공되는 여러 기능의 핵심적 요소입니다. 다음 항목에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에서 제공되는 XML 관련 기능 및 도구의 이름을 소개합니다.

 For more information, see the [XML Developer Center](https://go.microsoft.com/fwlink/?LinkID=100176), which provides the latest documentation, technical information, downloads, newsgroups, and other resources for XML developers.

## <a name="in-this-section"></a>단원 내용
 [Working with XML Data](../xml-tools/working-with-xml-data.md) Discusses the role of XML in the way data is handled in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Debugging XSLT](../xml-tools/debugging-xslt.md) Provides links to topics about using the Visual Studio debugger to debug XSLT.

## <a name="reference"></a>참고
 [Microsoft.VisualStudio.XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) Exposes the [XML Editor](https://go.microsoft.com/fwlink/?LinkId=228249) parse tree through [System.Xml.Linq](https://go.microsoft.com/fwlink/?LinkId=228250) for any XML documents.

 [XML Standards Reference](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Provides information about XML technologies, including XML, Document Type Definition (DTD), XML Schema definition language (XSD), and XSLT.

 <xref:System.Xml?displayProperty=fullName> Describes the classes and other elements that make up the <xref:System.Xml> namespace and provides links to more detailed information on each item.

 <xref:System.Xml.Serialization?displayProperty=fullName> Describes the classes and other elements that make up the <xref:System.Xml.Serialization> namespace and provides links to more detailed information about each item.

## <a name="related-sections"></a>관련 단원
 [XML Document Object Model (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Describes how the <xref:System.Xml.XmlDocument> and its associated classes comply with the W3C Document Object Model (Core) Level 1 and Level 2 namespace support specifications.

 [Reading XML with the XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Describes how the <xref:System.Xml.XmlReader> provides noncached, forward only, read-only access to XML data over an XML stream.

 [Writing XML with the XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Describes how the <xref:System.Xml.XmlWriter> provides noncached, forward only, way of generating XML streams and helps you build XML documents that comply with the W3C standard.

 [XSLT Transformations](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Describes how the <xref:System.Xml.Xsl.XslCompiledTransform> class implements the XSLT 1.0 recommendation.

 [Process XML Data Using the XPath Data Model](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Describes how the <xref:System.Xml.XPath.XPathNavigator> class can process XML data stored in an <xref:System.Xml.XPath.XPathDocument> or an <xref:System.Xml.XmlDocument> object. <xref:System.Xml.XPath.XPathNavigator> 클래스는 XQuery 1.0 및 XPath 2.0 데이터 모델을 기반으로 하며 XML 데이터를 탐색 및 편집하는 데 사용할 수 있습니다.

 [XML Schema Object Model (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Describes the classes used for creating and manipulating XML Schemas, by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.
