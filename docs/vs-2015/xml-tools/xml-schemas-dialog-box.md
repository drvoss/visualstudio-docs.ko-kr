---
title: XML 스키마 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82247c2510d64f712cc4b703154ea16a4bb7e7e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150664"
---
# <a name="xml-schemas-dialog-box"></a>XML 스키마 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **XML 스키마** XML 문서를 사용 하 여 연결 하는 XML 스키마 정의 언어 (XSD) 스키마 선택 대화 상자를 사용 합니다. 스키마 캐시에서 스키마를 선택하거나 캐시에 없는 스키마를 지정할 수 있습니다. 선택한 스키마는 스키마 집합의 일부분으로 간주됩니다. 스키마 집합은 IntelliSense 및 XML 문서 유효성 검사에 사용됩니다.  
  
 액세스할 수 있습니다 합니다 **XML 스키마** 중 하나를 클릭 하 여 대화 상자를 **스키마** 단추를 선택 하 여 문서 속성 창의 켜거나 **스키마** 합니다 에서**XML** 메뉴.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **사용 하 여**  
 XML 스키마를 사용할 방법을 선택합니다.  
  
- **자동**합니다. 이 스키마는 현재 문서에서는 사용되지 않지만 자동 연결에 사용할 수 있습니다. XML 문서가 이 스키마의 `targetNamespace`와 일치하는 네임스페이스를 선언하는 경우 해당 스키마가 자동으로 연결되고 스키마 집합에 포함됩니다.  
  
- **이 스키마를 사용 하 여**입니다. 이 스키마를 현재 문서에서 사용하고 있습니다. 사용자가 이 열에서 이 스키마를 클릭하여 사용하도록 명시적으로 요청했거나, 스키마가 일치하는 `targetNamespace`를 기반으로 하여 자동으로 연결되었습니다.  
  
- **선택한 스키마를 사용 하지 마십시오**합니다. 이 스키마는 일치하는 `targetNamespace`가 있는 경우에도 현재 문서에서 사용되지 않습니다. 이 설정은 스키마 캐시 또는 솔루션에 동일한 스키마의 둘 이상의 버전이 있을 때 충돌을 해결하는 데 유용합니다.  
  
  **Target Namespace**  
  XML 스키마와 연결된 대상 네임스페이스를 표시합니다.  
  
  **파일 이름**  
  XML 스키마 파일 이름을 표시합니다.  
  
  **추가**  
  열립니다는 **XSD 스키마 열기** 대화 상자에서 스키마 집합에 추가할 스키마를 추가로 선택할 수 있습니다. 스키마 스키마를 추가 하는 경우 설정 합니다 **사용 하 여** 열 값으로 설정 됩니다 **이 스키마를 사용 하 여**.  
  
  **제거**  
  현재 선택된 스키마를 스키마 집합에서 제거합니다. 그러면 스키마가 메모리 내 스키마 캐시에서 제거되지만 파일 시스템에서는 제거되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [XML 편집기 구성 요소](../xml-tools/xml-editor-components.md)   
 [방법: 사용 하 여 XML 스키마 선택](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [스키마 캐시](../xml-tools/schema-cache.md)
