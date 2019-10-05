---
title: Just-in-time 디버거를 사용 하지 않도록 설정 | Microsoft 문서
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c848281a89213a216bd8ec3ac1e651b6dfc32e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905721"
---
# <a name="disable-the-just-in-time-debugger"></a>Just-In-Time 디버거를 사용하지 않도록 설정

Just-In-Time 디버거 대화 상자를 실행 중인 앱에서 오류가 발생 하는 경우 열 및 계속에서 앱을 방지할 수 있습니다.

Just-In-Time 디버거는 오류를 디버깅 하려면 Visual Studio를 시작 하는 옵션을 제공 합니다. 있어야 [Visual Studio](http://visualstudio.microsoft.com) 또는 다른 선택한 디버거가 설치 오류에 대 한 자세한 정보를 보거나 디버그 하려고 합니다.

Visual Studio 사용자 인 경우 내용은 오류를 디버깅 하려고 [Just-In-Time 디버거를 사용 하 여 디버그](../debugger/debug-using-the-just-in-time-debugger.md)합니다. 오류를 해결 하거나 열에서 Just-In-Time 디버거를 유지할 수 없습니다, 하는 경우 [Visual Studio에서 디버깅 사용 안 함 Just In Time](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)합니다.

해야 하지만 더 이상 Visual Studio가 설치 되어 있다면 [Windows 레지스트리에서 사용 하지 않도록 설정 하면 시간 디버깅](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)합니다.

설치 된 Visual Studio가 없는 경우에 Just In Time 스크립트 디버깅 또는 서버 쪽 디버깅이 사용 하지 않도록 설정 하 여 디버깅을 방지할 수 있습니다.

- 웹 앱을 실행 하려는 경우 스크립트 디버깅 사용 안 함:

  Windows에서 **Control Panel** > **네트워크 및 인터넷** > **인터넷 옵션**선택, **사용 하지 않도록 설정 스크립트 디버깅 ( Internet Explorer)** 하 고 **스크립트 디버깅 (기타)를 사용 하지 않도록 설정**합니다. 설정을 확인 하 고 정확한 단계는 Windows 및 브라우저 버전에 따라 달라 집니다.

  ![JIT 인터넷 옵션](../debugger/media/jitinternetoptions.png "JIT 인터넷 옵션")

- IIS에서 ASP.NET 웹 앱을 호스트 하는 경우 서버 쪽 디버깅이 사용 하지 않도록 설정 합니다.

  1. IIS 관리자에서 **기능 보기**아래에 있는 **ASP.NET** 섹션에서 두 번 클릭 **.NET 컴파일**를 선택 및 선택한 **기능 열기**에 **작업** 창입니다.
  1. 아래 **동작** > **디버그**선택 **False**합니다. 단계는 이전 버전의 IIS에서 다릅니다.

Just In Time 디버깅을 해제 하면 앱이 오류를 처리 하 고 정상적으로 실행 하는 일을 할 수 있습니다.

앱에 아직 처리 되지 않은 오류, 오류 메시지가 표시 될 수 있습니다 또는 앱 충돌 또는 중단 될 수 있습니다. 오류가 해결 될 때까지 앱이 정상적으로 실행 되지 않습니다. 앱의 소유자에 게 문의 하 고 해결 하도록 요청을 시도할 수 있습니다.
