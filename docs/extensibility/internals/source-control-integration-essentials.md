---
title: 원본 제어 통합 필수 항목 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f853f71428086f6c144c352e18e51f3f55c4d00
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322525"
---
# <a name="source-control-integration-essentials"></a>소스 제어 통합 필수 항목
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 두 가지 유형의 원본 제어 통합을 지원 합니다: 기본 기능을 제공 하 고 (이전의 MSSCCI API)를 원본 제어 플러그 인 API 및 VSPackage 기반 소스 제어 통합 솔루션을 사용 하 여 빌드되는 소스 제어 플러그 인입니다 보다 강력한 기능을 제공합니다.

## <a name="source-control-plug-in"></a>소스 제어 플러그 인
 원본 제어 플러그 인은 원본 제어 플러그 인 API를 구현 하는 DLL로 기록 됩니다. 등록 및 원본 제어 통합 기능은 API를 통해 제공 됩니다. 이 방법은 소스 제어 VSPackage 보다 쉽게 구현할 수 및 사용 된 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 대부분의 소스 제어 작업에 대 한 사용자 인터페이스 (UI).

 원본 제어 플러그 인 API를 사용 하 여 플러그 인 소스 제어를 구현 하려면 다음이 단계를 수행 합니다.

1. 에 지정 된 함수를 구현 하는 DLL을 만드는 [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)합니다.

2. 에 설명 된 대로 적절 한 레지스트리 항목을 만들어 DLL을 등록 [방법: 소스 제어 플러그 인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)합니다.

3. 도우미 UI를 만들고 소스 컨트롤 어댑터 패키지에서 메시지가 표시 되 면 표시 (의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 원본 제어 플러그 인을 통해 소스 제어 기능을 처리 하는 구성 요소).

   자세한 내용은 [는 원본 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)합니다.

## <a name="source-control-vspackage"></a>소스 제어 VSPackage
 소스 제어 VSPackage 구현에 대 한 사용자 지정 된 대체를 개발할 수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 UI 컨트롤입니다. 이 방법은 소스 제어 통합을 완전히 제어할 수 있지만 필요 UI 요소를 제공 하 고 그렇지 않으면 플러그 인 접근 방식에서 제공 되는 원본 제어 인터페이스를 구현할 수 있습니다.

 소스 제어 VSPackage를 구현 하려면 다음을 수행 해야 합니다.

1. 만들고에 설명 된 대로 사용자 고유의 소스 제어 VSPackage를 등록 [등록과 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)합니다.

2. 사용자 지정 UI를 사용 하 여 UI의 기본 소스 제어를 대체 합니다. 참조 [사용자 지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)합니다.

3. 를 사용 하 고 처리 하는 문자 모양 지정 **솔루션 탐색기** 문자 모양 이벤트입니다. 참조 [문자 모양 제어](../../extensibility/internals/glyph-control-source-control-vspackage.md)입니다.

4. 와 같이 쿼리 편집 하 고 쿼리 저장 이벤트를 처리할 [쿼리 편집 쿼리 저장](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)합니다.

   자세한 내용은 [소스 제어 VSPackage를 만드는](../../extensibility/internals/creating-a-source-control-vspackage.md)합니다.

## <a name="see-also"></a>참고 항목
- [개요](../../extensibility/internals/source-control-integration-overview.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)