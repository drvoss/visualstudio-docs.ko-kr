---
title: XML 스키마 만들기
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 857b75f22d45cbabc22062fd14b385e8f6ea5f14
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592778"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>방법: XML 문서에서 XML 스키마 만들기

Xml 편집기를 사용 하 여 xml 문서에서 XSD (XML 스키마 정의 언어) 스키마를 만들 수 있습니다. XML 파일은 다음과 같은 방법으로 스키마를 생성 하는 방법을 결정 합니다.

- XML 문서에 연결된 스키마 또는 DTD(문서 형식 정의)가 없을 경우 XML 문서의 데이터를 사용하여 새 XML 스키마를 유추합니다.

- XML 문서에 연결된 DTD가 있을 경우 외부 DTD 및 내부 하위 집합이 해당 XML 스키마로 변환됩니다.

- XML 문서에 인라인 XDR(XML-Data Reduced) 스키마가 포함된 경우 XDR 스키마가 해당 XML 스키마로 변환됩니다.

그런 다음 만들어진 스키마를 사용 하 여 XML 파일에 대 한 IntelliSense를 제공 합니다.

스키마 유추 엔진에 대 한 자세한 내용은 [XML 스키마 유추](/dotnet/standard/data/xml/inferring-an-xml-schema)를 참조 하세요.

## <a name="to-create-an-xml-schema"></a>XML 스키마를 만들려면

1. Visual Studio에서 XML 파일을 엽니다.

2. 메뉴 모음에서 **XML** > **스키마 만들기**를 선택 합니다.

   Xml 파일에 있는 각 네임 스페이스에 대해 XML 스키마 문서가 만들어지고 열립니다. 각 스키마는 임시 기타 파일로 열립니다. 스키마를 디스크에 저장하거나 프로젝트에 추가 또는 삭제할 수 있습니다.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)
