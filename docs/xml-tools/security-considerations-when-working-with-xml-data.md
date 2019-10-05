---
title: XML 데이터 사용 시 보안 고려 사항
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe4ec69f879478566cce8d077bb66b34da86f3d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926772"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML 데이터로 작업할 때의 보안 고려 사항

이 항목에서는 XML 편집기나 XSLT 디버거로 작업할 때 알아야 할 보안 문제에 대해 설명 합니다.

## <a name="xml-editor"></a>XML 편집기

XML 편집기는 Visual Studio 텍스트 편집기를 기반으로 합니다. <xref:System.Xml> 및 <xref:System.Xml.Xsl> 클래스를 사용하여 많은 XML 프로세스를 처리합니다.

- 새 애플리케이션 도메인에서 XSLT 변형이 실행됩니다. XSLT 변환이 *샌드 박싱*됩니다. 즉, 컴퓨터의 코드 액세스 보안 정책은 XSLT 스타일 시트가 있는 위치에 따라 제한 된 권한을 결정 하는 데 사용 됩니다. 예를 들어, 인터넷 위치에 있는 스타일시트는 가장 제한된 권한을 갖지만 하드 드라이브에 복사된 스타일시트는 완전 신뢰로 실행됩니다.

- 실행 속도를 향상시키기 위해 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT를 MSIL(Microsoft Intermediate Language)로 변환할 수 있습니다.

- XML 편집기가 처음 로드 될 때 카탈로그 파일의 외부 위치를 가리키는 스키마는 자동으로 다운로드 됩니다. <xref:System.Xml.Schema.XmlSchemaSet> 클래스는 스키마를 컴파일하는 데 사용됩니다. XML 편집기와 함께 제공 되는 카탈로그 파일에는 외부 스키마에 대 한 링크가 없습니다. XML 편집기에서 스키마 파일을 다운로드 하기 전에 사용자가 외부 스키마에 대 한 참조를 명시적으로 추가 해야 합니다. XML 편집기에 대 한 **기타 도구 옵션** 페이지를 통해 HTTP 다운로드를 사용 하지 않도록 설정할 수 있습니다.

- XML 편집기는 <xref:System.Net> 클래스를 사용 하 여 스키마를 다운로드 합니다.

## <a name="xslt-debugger"></a>XSLT 디버거

XSLT 디버거는 관리되는 Visual Studio 디버그 엔진 및 <xref:System.Xml>과 <xref:System.Xml.Xsl> 네임스페이스의 클래스를 사용합니다.

- XSLT 디버거는 샌드박싱된 애플리케이션 도메인에서 각 XSLT 변환을 실행합니다. 컴퓨터의 코드 액세스 보안 정책은 XSLT 스타일시트가 있는 위치를 기반으로 제한된 권한을 결정하는 데 사용됩니다. 예를 들어, 인터넷 위치에 있는 스타일시트는 가장 제한된 권한을 갖지만 하드 드라이브에 복사된 스타일시트는 완전 신뢰로 실행됩니다.

- <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT 스타일시트가 컴파일됩니다.

- 관리되는 디버그 엔진에서 XSLT 식 계산기를 로드합니다. 관리되는 디버그 엔진은 모든 코드가 사용자의 로컬 컴퓨터에서 실행된다고 가정합니다. 따라서 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 XSLT 파일을 사용자의 로컬 컴퓨터로 다운로드합니다. 제한된 권한으로 새 애플리케이션 도메인에서 모든 XSLT 변형을 실행하면 실행 권한을 높일 수 있는 가능성이 적어집니다.

## <a name="see-also"></a>참고자료

- [애플리케이션 도메인](/dotnet/framework/app-domains/application-domains)