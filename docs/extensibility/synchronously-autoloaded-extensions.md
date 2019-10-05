---
title: 동기적으로 자동 로드된 확장
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b18642269326c516c2af0baef57cb306f60ae6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316710"
---
# <a name="synchronously-autoloaded-extensions"></a>동기적으로 자동 로드된 확장

동기적으로 자동 확장 Visual Studio의 성능에 부정적인 영향을 미치는 고 비동기 autoload를 대신 사용 하도록 변환 해야 합니다. 사용자는 Visual Studio 2019 Preview 2부터 확장 될 때 동기적으로 자동 알림을 받습니다. 확장 로드를 정상적으로 작동 합니다.

![확장 호환성 경고](media/extension-compatibility-warning.png)

사용자는 다음 작업을 수행할 수 있습니다.

- 클릭할 **자세한** 하이 정보 페이지로 이동 합니다.

- 클릭할 **성능 관리** 열려는 합니다 [성능 관리자 대화](#performance-manager-dialog) 확장 및 도구 창을 사용 하 여 성능 문제를 보여 주는 합니다.

- 클릭할 **이 메시지를 다시 표시 안 함** 여 알림을 해제 합니다. 이 옵션을 선택 하면 모든 향후 알림용으로만 동기적으로 자동 확장도 차단 합니다. 사용자는 다른 Visual Studio 기능에 대 한 알림을 계속 됩니다.

## <a name="performance-manager-dialog"></a>성능 관리자 대화 상자

![성능 관리자 대화 상자](media/performance-manager.png)

동기적으로 사용자 세션의 모든 패키지를 로드 하는 모든 확장에 표시 된 **사용 되지 않는 Api** 탭 합니다.

* 사용자가 클릭할 수는 **이 문제에 대 한 자세한 내용은** 사용 되지 않는 Api에 대 한 자세한 정보를 수집 합니다.
* 사용자가 마이그레이션 진행률에 대 한 공급 업체 확장을 요청할 수 있습니다.

확장 작성자가 마이그레이션에 대 한 지침을 찾을 수 있는 비동기 autoload 패키지 [AsyncPackage로 마이그레이션](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>그룹 정책을 사용 하 여 동기 autoload 설정 지정

기본적으로 Visual Studio 설치 블록 동기 autoload Visual Studio 2019 업데이트 1에서 시작합니다. 그룹 정책을 사용 하도록 설정 하면 개별 컴퓨터에서 동기 autoload를 허용 하도록 Visual Studio를 구성할 수 있습니다. 이렇게 하려면 다음 키에 레지스트리 기반 정책을 설정합니다.

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

항목 = **허용**

값 = (DWORD)
* **0** 동기 autoload 허용 되지 않습니다
* **1** 동기 autoload 허용 됩니다

Visual Studio 2019 업데이트 1에서 동기 autoload 설정에 대 한 자세한 내용은 참조는 [동기 Autoload 동작](https://aka.ms/AA52xzw) 페이지입니다.
