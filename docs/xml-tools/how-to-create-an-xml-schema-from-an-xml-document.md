---
title: XML 스키마 만들기
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783495"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>방법: XML 문서에서 XML 스키마 만들기

XML 편집기를 사용 하면 XML 문서에서 XML 스키마 정의 언어 (XSD) 스키마를 만들 수 있습니다. 다음과 같은 방식으로 스키마를 생성 하는 방법을 결정 하는 XML 파일:

- XML 문서에 연결된 스키마 또는 DTD(문서 형식 정의)가 없을 경우 XML 문서의 데이터를 사용하여 새 XML 스키마를 유추합니다.

- XML 문서에 연결된 DTD가 있을 경우 외부 DTD 및 내부 하위 집합이 해당 XML 스키마로 변환됩니다.

- XML 문서에 인라인 XDR(XML-Data Reduced) 스키마가 포함된 경우 XDR 스키마가 해당 XML 스키마로 변환됩니다.

XML 파일에 대 한 IntelliSense를 제공 하는 스키마가 생성 되며 사용 됩니다.

스키마 유추 엔진에 대 한 자세한 내용은 참조 하세요. [XML 스키마를 유추](/dotnet/standard/data/xml/inferring-an-xml-schema)합니다.

## <a name="to-create-an-xml-schema"></a>XML 스키마를 만들려면

1. Visual Studio에서 XML 파일을 엽니다.

2. 메뉴 모음에서 선택 **XML** > **Create Schema**합니다.

   XML 스키마 문서 생성 되어 XML 파일에 있는 각 네임 스페이스에 대 한 열입니다. 각 스키마는 임시 기타 파일로 열립니다. 스키마를 디스크에 저장하거나 프로젝트에 추가 또는 삭제할 수 있습니다.

## <a name="see-also"></a>참고자료

- [XML 편집기](../xml-tools/xml-editor.md)