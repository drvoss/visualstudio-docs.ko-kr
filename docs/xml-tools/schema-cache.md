---
title: XML 편집기 스키마 캐시
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28f5a7ffe202e7e02b06e676501ab508ee1a4ab2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955555"
---
# <a name="schema-cache"></a>스키마 캐시

XML 편집기에 있는 스키마 캐시를 제공 합니다 *%VSInstallDir%\xml\Schemas* 디렉터리입니다. 스키마 캐시는 컴퓨터의 모든 사용자에 전체적으로 적용 되며 IntelliSense 및 XML 문서 유효성 검사에 사용 되는 표준 XML 스키마를 포함 합니다.

XML 편집기는 솔루션에 있는 스키마를 찾을 수도 있습니다에 지정 된 스키마를 **스키마** 문서의 필드 **속성** 창과로 식별 되는 스키마는 `xsi:schemaLocation` 및 `xsi:noNamespaceSchemaLocation`특성입니다.

다음 표에서 XML 편집기를 사용 하 여 설치 되는 스키마를 설명 합니다.

| 파일 이름 | 설명 |
|-| - |
| *catalog.xsd* | XML 편집기 스키마 카탈로그 파일에 대한 스키마입니다. 스키마 카탈로그에 대한 자세한 내용은 아래를 참조하세요. |
| *DotNetConfig.xsd* | Web.Config 파일에 대 한 스키마 "<http://schemas.microsoft.com/.NETConfiguration/v2.0>"입니다. |
| *msbuild.xsd* | MSBuild 확인 파일에 대 한 스키마 "<http://schemas.microsoft.com/developer/msbuild/2003>"입니다. |
| *msdata.xsd* | <xref:System.Data.DataSet> 클래스 "urn:schemas-microsoft-com:xml-msdata"에 의해 추가된 XSD 주석의 스키마입니다. |
| *msxsl.xsd* | Microsoft XSLT 스크립트 블록 확장명 urn:schemas-microsoft-com:xslt에 대한 스키마입니다. |
| *SnippetFormat.xsd* | 코드 조각 XML 파일에 대한 스키마입니다. 예제를 보려면 *%VSInstallDir%\VC#\Expansions*합니다. |
| *Soap1.1.xsd* | Simple Object Access Protocol (SOAP) 1.1에 대 한 스키마 http://schemas.xmlsoap.org/soap/envelope/ 합니다. |
| *Soap1.2.xsd* | SOAP(Simple Object Access Protocol) 1.2에 대한 스키마입니다. |
| *SiteMapSchema.xsd* | ASP.NET 사이트 맵 XML 파일에 대 한 스키마 "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>"입니다. |
| *wsdl.xsd* | 웹 서비스 기술 언어에 대 한 스키마 http://schemas.xmlsoap.org/wsdl/ 합니다. |
| *xenc.xsd* | XML 암호화에 대 한 스키마 http://www.w3.org/2000/09/xmldsig# 합니다. |
| *xhtml.xsd* | XHTML에 대 한 스키마 http://www.w3.org/1999/xhtml 합니다. |
| *xlink.xsd* | XLink1.0에 대 한 스키마 http://www.w3.org/1999/xlink 합니다. |
| *xml.xsd* | Xml: space 및 xml: lang 특성을 설명 하는 스키마 http://www.w3.org/XML/1998/namespace 합니다. |
| *xmlsig.xsd* | XML 디지털 서명 위한 스키마 http://www.w3.org/2000/09/xmldsig# 합니다. |
| *xsdschema.xsd* | XSD 자체를 설명 하는 스키마 http://www.w3.org/2001/XMLSchema 합니다. |
| *xslt.xsd* | XML에 대 한 스키마 변환 http://www.w3.org/1999/XSL/Transform 합니다. |

## <a name="update-schemas-in-the-cache"></a>캐시에서 스키마를 업데이트 합니다.

XML 편집기 패키지가 로드될 때 편집기에서 스키마 캐시 디렉터리를 로드하며 실행하는 동안 변경 내용을 조사합니다. 스키마가 추가되면 알려진 스키마의 메모리 내 인덱스에 자동으로 로드됩니다. 스키마가 제거되면 메모리 내 인덱스에서 자동으로 제거됩니다. 스키마가 업데이트되면 이 스키마의 메모리 내 캐시가 자동으로 무효화됩니다.

> [!NOTE]
> 스키마 캐시 디렉터리는 컴퓨터 전체에 적용되므로 여기서는 컴퓨터에서 만들 수 있는 모든 Visual Studio 프로젝트에 유용한 표준 스키마만 추가해야 합니다.

또한 XML 편집기에서는 스키마 캐시 디렉터리의 스키마 카탈로그 파일 수를 제한하지 않습니다. 스키마 카탈로그는 편집기에서 항상 알아야 할 스키마에 대해 다른 위치를 가리킬 수 있습니다. 합니다 *catalog.xsd* 파일 카탈로그 파일에 대 한 형식을 정의 하 고 스키마 캐시 디렉터리에 포함 됩니다. 합니다 *catalog.xml* 파일은 기본 카탈로그 이며의 다른 스키마에 대 한 링크 포함 된 *% VSInstallDir %* 합니다. 다음은 몇 가지는 *catalog.xml* 파일:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

`href` 특성은 임의의 파일 경로이거나 스키마를 가리키는 http URL일 수 있습니다. 파일 경로는 카탈로그 문서에 상대적일 수 있습니다. 다음 변수를 구분 % %, 편집기에서 인식 하 고 경로에서 확장 됩니다.

- VSInstallDir

- 시스템

- ProgramFiles

- Programs

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

카탈로그 문서에 다른 카탈로그를 가리키는 `Catalog` 요소를 포함할 수 있습니다. `Catalog` 요소를 사용하여 팀이나 회사에서 공유하는 중앙 카탈로그 또는 비즈니스 파트너와 공유하는 온라인 카탈로그를 가리킬 수 있습니다. `href` 특성은 파일 경로이거나 다른 카탈로그에 대한 http URL입니다. 다음은 `Catalog` 요소의 예제입니다.

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

카탈로그는 특수 `Association` 요소를 사용하여 XML 문서와 스키마를 연결하는 방법을 제어할 수도 있습니다. 이 요소에는 유용할 수 있는 XML 편집기에 자동으로 연결 되지 않은 스키마의 않습니다 때문에 특정 파일 확장명을 가진 대상 네임 스페이스가 있는 스키마와 연결 된 `targetNamespace` 특성입니다. 다음 예제에서 `Association` 요소는 dotNetConfig 스키마를 파일 확장명이 "config"인 모든 파일과 연결합니다.

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>지역화 된 스키마

대부분의 경우에는 *catalog.xml* 파일에 지역화 된 스키마에 대 한 항목이 없습니다. 추가 항목을 추가할 수 있습니다 합니다 *catalog.xml* 지역화 된 스키마 디렉터리를 가리키는 파일입니다.

다음 예제에서는 %LCID% 변수를 사용하여 지역화된 스키마를 가리키는 새로운 `Schema` 요소가 만들어졌습니다.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>스키마 캐시 위치 변경

사용 하 여 스키마 캐시 위치를 사용자 지정할 수는 **기타** 옵션 페이지입니다. 즐겨 찾는 스키마 디렉터리가 있을 경우 대신 이 스키마를 사용하도록 편집기를 구성할 수 있습니다.

> [!NOTE]
> 이 변경 내용은 현재 Visual Studio 사용자에게만 영향을 줍니다.

### <a name="to-change-the-schema-cache-location"></a>스키마 캐시 위치를 변경하려면

1. **도구** 메뉴에서 **옵션**합니다.

2. 확장 **텍스트 편집기**를 확장 하 고 **XML**를 클릭 하 고 **기타**합니다.

3. 클릭 합니다 **찾아보기** 단추를 **스키마** 필드입니다.

4. 스키마 캐시에 대 한 폴더를 선택 하 고 클릭 **확인**합니다.

### <a name="to-add-another-directory-of-common-schemas"></a>공통 스키마 디렉터리를 추가하려면

1. 편집 된 *catalog.xml* XML 편집기 스키마 캐시 디렉터리에 있는 파일입니다.

2. 추가 스키마 디렉터리를 가리키는 새 `<Catalog href="..."/>` 요소를 추가합니다.

3. 변경 내용을 저장합니다.

   카탈로그가 자동으로 다시 로드됩니다.

## <a name="see-also"></a>참고자료

- [XML 편집기](../xml-tools/xml-editor.md)