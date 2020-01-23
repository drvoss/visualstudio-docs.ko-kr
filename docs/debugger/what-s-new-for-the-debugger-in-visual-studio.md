---
title: Visual Studio 2017에서 디버거의 새로운 기능 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 523867a8f9aa074e9122c74deb8bcd91cddd8bee
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944222"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017 디버거의 새로운 기능

디버거에는 다음과 같은 새로운 기능이 포함 되어 있습니다.

- 버전 15.5의 새로운 기능으로, 사용자가 관심 있는 코드가 실행 될 때 프로덕션 중인 앱의 스냅숏을 사용 **스냅숏 디버거** . 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

    스냅샷 컬렉션은 Azure App Service에서 실행되는 다음 웹앱에서 사용할 수 있습니다.

  * .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
  * Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션

    자세한 내용은 [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

- 15.5 버전에서 새로 만들기 Visual Studio Enterprise에 한 해 **IntelliTrace** 는 모든 중단점 및 디버거 단계 이벤트에서 응용 프로그램의 스냅숏을 자동으로 사용 합니다. 기록된 스냅샷을 통해 이전 중단점 또는 단계로 돌아가서 애플리케이션의 과거 상태를 볼 수 있습니다. IntelliTrace 뒤로 이동을 사용하면 이전 애플리케이션 상태를 보고 싶지만 디버깅을 다시 시작하거나 원하는 앱 상태를 다시 만들지 않으려는 경우에 시간을 절약할 수 있습니다.

    디버그 도구 모음의 **뒤로 가기**와 **앞으로 가기** 단추를 사용하여 이동하고 스냅샷을 볼 수 있습니다. 이 단추를 사용하여 **진단 도구** 창의 **이벤트** 탭에 나타나는 이벤트를 탐색할 수 있습니다.

    ![뒤로 이동 및 앞으로 이동 단추](../debugger/media/intellitrace-step-back-icons-description.png  "뒤로 이동 및 앞으로 이동 단추")

    자세한 내용은 [IntelliTrace를 사용하여 이전 앱 상태 검사](view-historical-application-state.md) 페이지를 참조하세요.

- 예외 **도우미가** 예외 도우미를 대체 하 고 오류가 발생 한 모달 대화 상자에 표시 됩니다. **예외 도우미** 를 사용 하면 모든 내부 예외에 빠르게 액세스 하 고, 디버거의 추가 분석 (사용 가능한 경우)을 제공 하 고, 예외에 대 한 **예외 설정** 에 즉시 액세스할 수 있습니다. 예외 도우미는 표시 해야 하는 항목을 차단 하는 경우 부동 뷰로 끌 수도 있습니다.

    예를 들어 이제 **NullReferenceException** 는 null 참조 (추가 정보)를 포함 하는 변수를 표시 합니다.

    ![디버거의 예외 도우미](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    자세한 내용은 [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/)(Visual Studio에서 새 예외 도우미 사용) 블로그 게시물을 참조하세요.

- 이제 코드 줄을 마우스로 가리킬 때 아이콘이 표시 되는 상태로 **실행을** 선택 하 여 디버거에서 일시 중지 된 동안 코드 줄까지 실행할 수 있습니다. 이렇게 하면 임시 중단점을 설정 하지 않아도 됩니다.

    ![디버거의 실행을 클릭 합니다.](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- 예외 **설정 대화 상자** 에서 예외에 대 한 조건을 설정할 수 있습니다 .이 작업은 예외 설정 대화 상자의 **조건 편집** 아이콘을 사용 하거나 예외에서 오른쪽 클릭 메뉴를 사용 하 여 설정할 수 있습니다. 현재 지원 되는 조건에는 예외에 포함 하거나 제외할 모듈 이름이 포함 됩니다.

    ![예외에 대 한 조건](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- 프로세스에 연결 대화 상자에는 연결 해야 하는 프로세스를 보다 신속 하 게 식별 하는 데 도움이 되는 새로운 검색 기능이 포함 되어 있습니다.

    ![프로세스에 연결에서 검색](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

이러한 새 기능에 대 한 자세한 내용은 [[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]의 릴리스 ](/visualstudio/releasenotes/vs2017-relnotes)정보를 참조 하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)