---
title: 정렬, 필터링 및 그룹화 (XML 스키마 탐색기) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c13f7c710e462e1edd45acbf68fa4642d3d422
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150673"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>정렬, 필터링 및 그룹화(XML 스키마 탐색기)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

통해 사용할 수 있는 옵션에 설명 합니다 **정렬, 필터링 및 그룹화 옵션** XML 스키마 탐색기 도구 모음에서 메뉴.  
  
## <a name="filter-options"></a>필터 옵션  
 사용할 수 있는 필터 옵션은 다음과 같습니다. 기본적으로 **네임 스페이스 표시** 하 고 **스키마 파일 표시** 옵션을 선택 합니다.  
  
- **네임 스페이스 표시**합니다.  
  
- **스키마 파일 표시**합니다.  
  
- **작성자 표시 (시퀀스/choice/all)** 합니다.  
  
## <a name="sorting-options"></a>정렬 옵션  
 사용할 수 있는 정렬 옵션은 다음과 같습니다. 기본값은 **유형별 정렬**합니다. 정렬 기준 옵션은 파일 및 네임스페이스에 적용되지 않습니다.  
  
- **유형별 정렬**합니다.  
  
- **이름순 정렬**합니다.  
  
- **문서 순서**합니다.  
  
### <a name="sort-by-type"></a>유형별 정렬  
 경우는 **유형별 정렬** 옵션을 선택 하면 전역 노드가 다음 순서로 정렬 됩니다. 그런 다음 노드가 각 그룹 내에서 알파벳순으로 정렬됩니다.  
  
1. `import` 노드  
  
2. `include` 노드  
  
3. `redefine` 노드  
  
4. `attribute` 노드  
  
5. `attributeGroup` 노드  
  
6. `complexType` 노드  
  
7. `simpleType` 노드  
  
8. `element` 노드  
  
9. `group` 노드  
  
### <a name="sort-by-name"></a>이름순 정렬  
 경우는 **이름순 정렬** 옵션을 선택 하면 전역 노드가 다음 순서로 정렬 됩니다.  
  
1. `import` 노드(네임스페이스의 알파벳 순서로 정렬)  
  
2. `include` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)  
  
3. `redefine` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)  
  
4. 기타 전역 노드(알파벳 순서로 정렬)  
  
### <a name="document-order"></a>문서 순서  
 합니다 **문서 순서** 옵션을 사용할 수는 **스키마 파일 표시** 옵션을 선택 합니다. 때 **문서 순서** 을 선택 하면 전역 노드가 스키마 파일에 나타나는 순서로 표시 됩니다.  
  
## <a name="persisting-sortfilter-options"></a>정렬/필터 옵션 유지  
 설정이 변경될 때 솔루션 또는 파일이 열려 있는지 여부에 상관없이 정렬, 필터링 및 그룹화 옵션이 각 사용자에 대한 레지스트리에 저장됩니다.
