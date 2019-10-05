---
title: '테스트 영역 8: 플러그 인 전환 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6af0a0333131697526d1ffcc8394f7bfe81ca6b4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327805"
---
# <a name="test-area-8-plug-in-switching"></a>테스트 영역 8: 플러그 인 전환
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE) 사용자 인터페이스 (UI) 현재 소스 제어 플러그 인을 변경 해야 합니다. 이 테스트 영역은 소스 제어 솔루션에 사용할 플러그 인 선택 프로세스에 대 한 테스트 사례를 제공 합니다.

## <a name="command-menu-access"></a>명령 메뉴 액세스
 다음 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 메뉴 경로 테스트 사례에서 사용 됩니다.

- 현재 소스 제어 플러그 인: **도구** -> **옵션** -> **소스 제어** -> **플러그 인 선택**합니다.

- 소스 변경 바인딩을 제어 합니다. **파일** -> **소스 제어** -> **소스 제어 변경**...

## <a name="common-expected-behavior"></a>예상 되는 일반적인 동작
 Visual Studio를 종료 하거나 솔루션을 다시 로드 하지 않고 소스 제어 플러그 인을 솔루션에 대 한 변경 불가능 합니다. 또한 현재 소스 제어 플러그 인 솔루션 로드 되 면 솔루션에서 사용 하는 자동으로 변경 합니다.

## <a name="test-cases"></a>테스트 사례
 플러그 인 전환 테스트 영역에 대 한 특정 테스트 사례는 다음과 같습니다.

### <a name="case-8a-automatic-change"></a>8a 사례: 자동 변경

#### <a name="expected-behavior"></a>예상된 된 동작
 사용자가 소스 제어에서 솔루션을 로드 하는 경우 솔루션은 자동으로 로드 하 고 적절 한 원본 제어 플러그 인는 최신 선택 됩니다.

| 작업 | 테스트 단계 | 확인 하려면 예상된 결과 |
| - | - | - |
| 자동 소스 제어 플러그 인 변경 | 1.  최신 테스트에서 플러그 인 선택 (**도구가** -> **옵션** -> **소스 제어** -> **플러그 인 선택**.)<br />2.  새 프로젝트를 만듭니다.<br />3.  소스 제어에 솔루션을 추가 합니다.<br />4.  다른 플러그 인 선택 (예를 들어 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  언로드 솔루션 프롬프트를 수락 합니다.<br />6.  디스크에서 솔루션을 다시 엽니다. | 솔루션이 열려 있습니다.<br /><br /> 테스트 중인 플러그 인은 현재 원본 제어 플러그 인입니다. |

### <a name="case-8b-solution-based-change"></a>8b 사례: 솔루션 기반 변경

#### <a name="expected-behavior"></a>예상된 된 동작
 솔루션에는 해당 연결 된 소스 제어 플러그 인 변경 있을 수 있습니다.

| 작업 | 테스트 단계 | 확인 하려면 예상된 결과 |
|----------------------------------| - | - |
| 변경 된 솔루션에 대 한 플러그 인 | 1.  최신 테스트에서 플러그 인 선택 (**도구가** -> **옵션** -> **소스 제어** -> **플러그 인 선택**).<br />2.  새 프로젝트 및 솔루션을 만듭니다.<br />3.  소스 제어에 솔루션을 추가 합니다.<br />4.  소스 제어에서 솔루션을 바인딩 해제 (사용 하는 **소스 제어 변경** 대화 상자).<br />5.  다른 플러그 인 선택 (예를 들어 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  언로드된 경우 디스크에서 솔루션을 다시 로드 합니다.<br />7.  소스 제어에 솔루션을 추가 합니다.<br />8.  소스 제어에서 솔루션을 바인딩 해제 (사용 하 여 **소스 제어 변경** 대화 상자).<br />9. 다시 테스트 플러그 인을 선택 합니다.<br />10. 언로드된 경우 디스크에서 솔루션을 다시 로드 합니다.<br />11. 원래 위치로 솔루션 바인딩 (사용 하는 **소스 제어 변경** 대화 상자). | 선택한를 사용 하 여 소스 제어에 솔루션 추가 플러그 인입니다. |

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인에 대한 테스트 가이드](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)