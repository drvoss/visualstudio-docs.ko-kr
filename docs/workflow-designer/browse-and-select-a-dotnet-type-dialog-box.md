---
title: 워크플로 디자이너-찾아보기 및.NET 유형 선택 대화 상자
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f48a30e11e28daef2d1803646d2b495bcb718b84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993203"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET 유형 선택 대화 상자

에 **속성** 창, 대화 상자 또는 변수 디자이너를 선택 하는 경우와 같은 디자이너 **형식 찾아보기** 데이터 형식의 목록에서 **찾아.NET유형선택** 대화 상자 (약칭 "형식 브라우저"에서 참조). 이 대화 상자의 어셈블리 및 프로젝트 트리 뷰에서 형식을 선택할 수 있습니다.

이 대화 상자는 다음을 비롯한 여러 가지 사용자 시나리오에서 사용됩니다.

- 변수 또는 인수의 형식을 설정할 때

- 제네릭 동작의 형식을 선택할 때

- <xref:System.Activities.Statements.TryCatch> 활동에 catch를 추가할 때

> [!NOTE]
> 형식 브라우저는 Visual Basic 가변 배열 형식을 표시할 수 있지만 다차원 배열 형식을 표시할 수 없습니다. 참조 [가변 배열](http://go.microsoft.com/fwlink/?LinkId=195226) 하 고 [다차원 배열](http://go.microsoft.com/fwlink/?LinkId=195227) 세부 정보에 대 한 합니다.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식 선택

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식을 선택하려면

1. 에 **형식 이름을** 상자를 사용 하려는 형식의 이름을 입력 합니다.

2. 다음 작업 중 하나를 수행합니다.

    - 사용 하려는 형식의 이름을 트리에 표시 되 면 합니다 **형식 이름** 상자에서 선택한 형식을 두 번 클릭 합니다.

    - 충분 한 문자를 입력 합니다 **형식 이름을** 상자를 사용 하 고 enter 키를 눌러 유형을 선택 하는 형식을 고유 하 게 식별

### <a name="to-select-a-generic-type-from-the-type-browser"></a>형식 브라우저에서 제네릭 형식을 선택하려면

1. 에 **형식 이름을** 상자를 사용 하려는 이름을 입력 합니다.

2. 사용 하려는 형식의 이름을 트리에 표시 되 면 합니다 **형식 이름을** 상자를 클릭 하 여 드롭다운 목록 상자를 선택 형식이 표시 합니다.

     드롭다운 목록 상자에서 제네릭을 닫는 클릭을 사용 하려는 형식을 선택 **확인**합니다.

## <a name="types-displayed-in-the-type-browser"></a>형식 브라우저에 표시된 형식

형식 브라우저에 표시되는 형식은 형식 브라우저의 시작 방식에 따라 달라질 수 있습니다. 형식 브라우저 내의 워크플로 프로젝트에서 시작 된 경우 **vs2010**, 모든 참조 된 어셈블리의 형식은 기본적으로 및 참조 된 프로젝트에 표시 됩니다. 형식 브라우저 외부에서 시작 된 경우는 **vs2010** 모든 AppDomain에 로드 된 어셈블리에서 형식을 표시는 기본적으로 시스템 (예: 재 호스트 된 워크플로 응용 프로그램 또는 독립 실행형 워크플로 파일에서), 프로젝트 .

활동 디자이너 개발자는 형식 브라우저의 형식을 필터링할 수 있습니다. 특정 활동에서 형식의 하위 집합만 표시되는 경우가 있습니다. 예를 들어 <xref:System.Activities.Statements.TryCatch> 활동의 경우 <xref:System.Exception>에서 파생된 형식만 형식 브라우저에 표시됩니다.

## <a name="filtering-search-results-in-the-type-browser"></a>형식 브라우저에서 검색 결과 필터링

형식의 목록 합니다 **형식 이름을** 상자 일치를 찾으려고 할 더 많은 문자를 입력할 때 짧은 가져옵니다. Fullyqualified 이름이 입력 한 문자열로 시작 하는 형식만 또는 약식 이름이 입력 한 문자열로 시작 하는 형식에는 필터링된 된 목록에 나타납니다.

예를 들어:

1. 입력 **작업이** 일치 <xref:System.OperationCanceledException> 아닌 <xref:System.InvalidOperationException>합니다. <xref:System.InvalidOperationException>을 찾으려면 System.I 또는 Invalid를 입력해야 합니다.

2. 입력 **제네릭** 일치 <xref:System.GenericUriParser> 의 형식은 하지 않지만 <xref:System.Collections.Generic> 네임 스페이스입니다. 형식에 대 한 검색할는 <xref:System.Collections.Generic> 네임 스페이스, 네임 스페이스의 정규화 된 이름을 입력 합니다.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>형식 브라우저 대화 상자를 사용하여 서비스 계약 선택

서비스 계약 형식을 선택할 때 형식 브라우저는 <xref:System.ServiceModel.ServiceContractAttribute> 특성이 있는 형식만 보여줍니다.

## <a name="see-also"></a>참고자료

- [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md)