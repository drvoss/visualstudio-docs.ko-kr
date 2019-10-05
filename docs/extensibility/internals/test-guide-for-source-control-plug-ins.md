---
title: 테스트 소스 제어 플러그 인에 대 한 가이드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 098aa9499dd4c1073377ed6aa5e8fa2a6fb37ca8
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823880"
---
# <a name="test-guide-for-source-control-plug-ins"></a>소스 제어 플러그 인에 대한 테스트 가이드
이 섹션에서는 소스 제어 플러그 인을 테스트 하는 것에 대 한 지침을 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 광범위 한 개요는 가장 일반적인 테스트 영역 뿐만 아니라 더 복잡 한 문제가 될 수 있는 영역의 일부 제공 됩니다. 이 개요 테스트 사례의 목록은 아닙니다.

> [!NOTE]
> 몇 가지 버그 수정 및 향상 된 최신 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 기존 원본 제어 플러그 인의 이전 버전을 사용 하는 동안 이전에 발생 하지 않았습니다 하는 문제를 발견할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 이전 버전의 이후 플러그 인에 변경한 없는 경우에 기존 소스 제어에이 섹션에서는 열거 된 영역에 대 한 플러그 인을 테스트 하는 것이 좋습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

## <a name="common-preparation"></a>일반적인 준비
 컴퓨터 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이며 대상 소스 제어 플러그 인 설치를 반드시 지정 해야 합니다. 테스트 소스 제어에서에서 열기 중 일부에 대해 구성 된 마찬가지로 두 번째 컴퓨터를 사용할 수 있습니다.

## <a name="definition-of-terms"></a>용어 정의
 이 테스트 가이드에서는 다음 용어 정의 사용 합니다.

 클라이언트 프로젝트에서 사용할 수 있는 모든 프로젝트 형식 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 통합을 지 (예를 들어 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]를 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], 또는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 웹 프로젝트에 있는 네 가지 형식의 웹 프로젝트: 파일 시스템, 로컬 IIS, 원격 사이트 및 FTP.

- 파일 시스템 프로젝트는 로컬 경로에서 만들어지지만 정보 서비스 (IIS (인터넷) UNC 경로 통해 내부적으로 액세스 하 고 클라이언트 프로젝트와 마찬가지로 IDE 내에서 소스 제어에 배치할 수 설치할 필요가 없습니다.

- 로컬 IIS 프로젝트는 로컬 컴퓨터를 가리키는 URL 사용 하 여 동일한 컴퓨터에 설치 되 고 액세스 하는 IIS를 사용 하 여 작동 합니다.

- IIS 서비스에서 원격 사이트 프로젝트를 만들 수도 있지만 소스 제어 아닌 IIS 서버 컴퓨터에 배치 됩니다 내는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- FTP 프로젝트 원격 FTP 서버를 통해 액세스할 수 있지만 소스 제어에서 배치할 수 없습니다.

  인 리스트 먼 트 솔루션이 나 프로젝트를 원본에서 또 다른 용어를 제어 합니다.

  버전 저장소는 원본 제어 플러그 인 API를 통해 액세스 되는 소스 제어 데이터베이스입니다.

## <a name="test-areas-covered-in-this-section"></a>이 섹션에서 다루는 영역 테스트

- [테스트 영역 1: 소스 제어에 추가/소스 제어에서 열기](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 사례 1a: 소스 제어에 솔루션 추가

  - 사례 1b: 소스 제어에서 솔루션 열기

  - 사례 1 c: 소스 제어에서 솔루션을 추가 합니다.

- [테스트 영역 2: 소스 제어에서 가져오기](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [테스트 영역 3: 체크 아웃/체크 아웃 실행 취소](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 사례 3: 체크 아웃/체크 아웃 취소

  - 사례 3a: 체크 아웃

  - 사례 3b: 오프 라인된 체크 아웃

  - 사례 3 c: 쿼리 편집/쿼리 저장 (QEQS)

  - 3d 경우: 자동 체크 아웃

  - 사례 3e: 체크 아웃 취소

- [테스트 영역 4: 체크 인](../../extensibility/internals/test-area-4-check-in.md)

  - 사례 4a: 수정 된 항목

  - 사례 4b: 파일 추가

  - 사례 4 c: 프로젝트를 추가합니다.

- [테스트 영역 5: 소스 제어 변경](../../extensibility/internals/test-area-5-change-source-control.md)

  - 사례 5a: 바인딩

  - 사례 5b: 바인딩 해제

  - 사례 5 c: 다시 바인딩

- [테스트 영역 6: 삭제](../../extensibility/internals/test-area-6-delete.md)

- [테스트 영역 7: 공유](../../extensibility/internals/test-area-7-share.md)

- [테스트 영역 8: 플러그 인 전환](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 8a 사례: 자동 변경

  - 8b 사례: 솔루션 기반 변경

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
