---
title: 소스 제어 VSPackage를 구현할지 여부 결정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba0ac240c8b8a93b6afbf1ec7dd580090ee54fd9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351617"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>소스 제어 VSPackage를 구현할지 여부 결정
이 섹션에서는 소스 제어 통합 적합 한 경로 선택 하는 방법에 대 한 솔루션을 사용 하면 광범위 한 지침을 확장 하는 것에 대 한 원본 제어 플러그 인 및 소스 제어 Vspackage의 선택 항목을 설명 합니다.

## <a name="small-source-control-solution-with-limited-resources"></a>제한 된 리소스를 사용 하 여 작은 소스 제어 솔루션
 리소스 제한 하 고 소스 제어 패키지를 작성 하는 오버 헤드를 사용 하 여 부담이 될 수 없습니다. 소스 제어 플러그 인 API 기반 플러그 인을 만들 수 있습니다. 이렇게 하면 소스 제어 패키지와 함께 작동 하 고 원본 제어 플러그 인 및 주문형 패키지 간에 전환할 수 있습니다. 자세한 내용은 [등록과 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)합니다.

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>다양 한 기능 집합을 사용 하 여 큰 소스 제어 솔루션
 원본 제어 플러그 인 API를 사용 하 여 적절 하 게 캡처하지 않은 다양 한 원본 제어 모델이 제공 하는 원본 제어 솔루션을 구현 하려는 경우 통합 경로로 소스 제어 패키지를 고려할 수 있습니다. 적용 됩니다 (원본 제어 플러그 인을 사용 하 여 통신를 제공 하는 UI를 기본 원본 제어) 소스 제어 어댑터 패키지는 대신 대체 하는 경우에 특히 사용자 고유의 사용자 지정 방식으로 원본 제어 이벤트를 처리할 수 있도록 합니다. UI를 제어 하 고 해당 환경에서 유지 하려는 만족 스러운 원본에 이미 있는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 소스 제어 패키지 옵션을 사용 하는 작업을 수행할 수 있습니다. 소스 제어 패키지 제네릭이 아닌 및 사용 하 여 사용 하기 위해서 설계 되었습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 유연성 및 원본 제어 논리 및 UI를 통해 다양 한 제어를 제공 하는 원본 제어 솔루션을 구현 하려는 경우 원본 제어 패키지 통합 경로 수도 있습니다. 다음과 같은 작업을 수행할 수 있습니다.

1. 사용자 고유의 소스 제어 VSPackage를 등록 (참조 [등록과 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. 사용자 지정 UI를 사용 하 여 UI의 기본 소스 제어를 바꿉니다 (참조 [사용자 지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. 사용 되 고 솔루션 탐색기 문자 모양 이벤트를 처리할 문자 모양을 지정 (참조 [문자 모양 제어](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. 쿼리 편집 하 고 쿼리를 저장 하는 이벤트 처리 (참조 [쿼리 편집 쿼리 저장](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>참고자료
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)