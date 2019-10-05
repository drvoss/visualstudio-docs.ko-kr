---
title: '방법: XML 파일 편집 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 60b94274404c82695628dc72bd88bdf48145b7c2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443435"
---
# <a name="how-to-edit-xml-files"></a>방법: XML 파일 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 편집기는 XML 파일을 위한 새 편집기입니다. 이 편집기는 독립 실행형 XML 파일 또는 Visual Studio 프로젝트에 연결된 파일에 사용할 수 있습니다. XML 편집기는 .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt 및 .vssettings 파일 확장명과 연결됩니다. 또한 특정 편집기가 등록되지 않은 파일 형식과 XML 또는 DTD 내용이 포함된 파일 형식과도 연결되어 있습니다.  
  
> [!NOTE]
> XHTML 문서는 HTML 편집기에서 처리됩니다.  
  
### <a name="to-edit-an-xml-file"></a>XML 파일을 편집하려면  
  
1. 편집할 파일을 두 번 클릭합니다.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>새 XML 파일을 프로젝트에 추가하려면  
  
1. **프로젝트** 메뉴에서 **새 항목 추가**합니다.  
  
2. 선택 **XML 파일** 에서 합니다 **템플릿** 창입니다.  
  
3. 파일 이름을 입력 합니다 **이름을** 필드 및 키를 눌러 **추가**합니다.  
  
     XML 파일이 프로젝트에 추가되고 XML 편집기에서 열립니다. 파일에는 기본 XML 선언, `<?xml version="1.0" encoding="utf-8" ?>`이 포함됩니다.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>기존 XML 파일을 프로젝트에 추가하려면  
  
1. **프로젝트** 메뉴에서 **기존 항목 추가**합니다.  
  
     합니다 **기존 항목 추가** 대화 상자가 나타납니다.  
  
2. XML 파일 및 키를 눌러 선택 **추가**합니다.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>새 XML 또는 XSLT 파일을 만들려면  
  
1. **파일** 메뉴에서 **새로 만들기**합니다.  
  
     합니다 **새 파일** 대화 상자가 나타납니다.  
  
2. 선택 **XML 파일** 새 XML 파일을 만들거나 선택 **XSLT 파일** 새 XSLT 스타일 시트를 만들려고 합니다.  
  
3. **열기**를 클릭합니다.  
  
### <a name="to-create-a-project-for-xml-files"></a>XML 파일에 대한 프로젝트를 만들려면  
  
1. **파일** 메뉴에서 **새로 만들기**를 선택한 후 **프로젝트**합니다.  
  
     **새 프로젝트** 대화 상자가 나타납니다.  
  
2. 선택의 코드 언어를 선택 **빈 프로젝트**, 클릭 **확인**합니다.  
  
3. 프로젝트에 XML 파일을 추가합니다.  
  
     XML 편집기에서는 이 프로젝트에 추가한 스키마를 찾아서 이 프로젝트를 연 상태에서 편집하는 모든 XML, 스키마 또는 XSLT 파일의 유효성 검사 및 IntelliSense에 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [XML 편집기](../xml-tools/xml-editor.md)   
 [XML 문서 속성, 속성 창](../xml-tools/xml-document-properties-properties-window.md)   
 [방법: XML 문서에서 XML 스키마 만들기](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
