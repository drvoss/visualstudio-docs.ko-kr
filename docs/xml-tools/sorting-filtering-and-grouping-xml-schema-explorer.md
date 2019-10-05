---
title: XML 스키마 탐색기에서 정렬, 필터링 및 그룹화
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daa629b4c26abf7b6ce801c30ea6f6fd41fbaa48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926725"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>정렬, 필터링 및 그룹화 (XML 스키마 탐색기)

이 항목에서는 **XML 스키마 탐색기** 도구 모음의 **정렬, 필터링 및 그룹화 옵션** 메뉴를 통해 사용할 수 있는 옵션에 대해 설명 합니다.

## <a name="filter-options"></a>필터 옵션

사용할 수 있는 필터 옵션은 다음과 같습니다. 기본적으로 **네임 스페이스 표시** 및 **스키마 파일 표시** 옵션이 선택 되어 있습니다.

- **네임 스페이스를 표시**합니다.

- **스키마 파일을 표시**합니다.

- **작성자 (sequence/choice/all)를 표시**합니다.

## <a name="sorting-options"></a>정렬 옵션

사용할 수 있는 정렬 옵션은 다음과 같습니다. 기본값은 **형식별로 정렬**입니다. **정렬 기준 옵션은** 파일 및 네임 스페이스에 적용 되지 않습니다.

- **유형별로 정렬**합니다.

- **이름을 기준으로 정렬**합니다.

- **문서 순서**.

### <a name="sort-by-type"></a>유형별 정렬

**유형별 정렬** 옵션을 선택 하면 전역 노드가 다음 순서로 정렬 됩니다. 그런 다음 노드가 각 그룹 내에서 알파벳순으로 정렬됩니다.

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

**이름으로 정렬** 옵션을 선택 하면 전역 노드가 다음 순서로 정렬 됩니다.

1. `import` 노드(네임스페이스의 알파벳 순서로 정렬)

2. `include` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)

3. `redefine` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)

4. 기타 전역 노드(알파벳 순서로 정렬)

### <a name="document-order"></a>문서 순서

**문서 순서** 옵션은 **스키마 파일 표시** 옵션을 선택한 경우에 사용할 수 있습니다. **문서 순서** 를 선택 하면 전역 노드가 스키마 파일에 표시 되는 순서 대로 표시 됩니다.

## <a name="persisting-sortfilter-options"></a>정렬/필터 옵션 유지

설정이 변경될 때 솔루션 또는 파일이 열려 있는지 여부에 상관없이 정렬, 필터링 및 그룹화 옵션이 각 사용자에 대한 레지스트리에 저장됩니다.