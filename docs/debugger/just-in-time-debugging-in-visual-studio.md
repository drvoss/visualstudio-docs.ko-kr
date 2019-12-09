---
title: Just-in-time 디버거를 사용 하지 않도록 설정 | Microsoft Docs
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
ms.openlocfilehash: eb66615abbd7124fd6b781598bd8eb28ea34756d
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903867"
---
# <a name="disable-the-just-in-time-debugger"></a>Just-In-Time 디버거를 사용하지 않도록 설정

실행 중인 앱에서 오류가 발생 하 고 앱을 계속할 수 없는 경우 Just-in-time 디버거 대화 상자가 열립니다.

Just-in-time 디버거는 Visual Studio를 시작 하 여 오류를 디버그할 수 있는 옵션을 제공 합니다. 오류에 대 한 자세한 정보를 보거나 디버깅을 시도 하려면 Visual Studio 또는 선택한 다른 디버거가 설치 되어 있어야 합니다.

이미 Visual Studio 사용자가 오류를 디버깅 하려는 경우 [Just-in-time 디버거를 사용 하 여 디버그](../debugger/debug-using-the-just-in-time-debugger.md)를 참조 하세요. 오류를 수정할 수 없거나 Just-in-time 디버거가 열리지 않도록 하려면 [Visual Studio에서 just-in-time 디버깅을 사용 하지 않도록 설정할](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)수 있습니다.

Visual Studio를 설치 했지만 더 이상 수행 하지 않는 경우 [Windows 레지스트리에서 just-in-time 디버깅을 사용 하지 않도록 설정](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)해야 할 수 있습니다.

Visual Studio가 설치 되어 있지 않으면 스크립트 디버깅 또는 서버 쪽 디버깅을 사용 하지 않도록 설정 하 여 Just-in-time 디버깅을 방지할 수 있습니다.

- 웹 앱을 실행 하려는 경우 스크립트 디버깅을 사용 하지 않도록 설정 합니다.

  Windows **제어판** > **네트워크 및 인터넷** > **인터넷 옵션**에서 **스크립트 디버깅 사용 안 함 (Internet Explorer)** 및 **스크립트 디버깅 사용 안 함 (기타)** 을 선택 합니다. 정확한 단계와 설정은 Windows 버전 및 브라우저에 따라 달라 집니다.

  ![JIT 인터넷 옵션](../debugger/media/jitinternetoptions.png "JIT 인터넷 옵션")

- IIS에서 ASP.NET 웹 앱을 호스트 하는 경우 서버 쪽 디버깅을 사용 하지 않도록 설정 합니다.

  1. IIS 관리자 **기능 보기**의 **ASP.NET** 섹션에서 **.net 컴파일**을 두 번 클릭 하거나, **작업** 창에서 **기능 열기** 를 선택 합니다.
  1. **동작** > **디버그**에서 **False**를 선택 합니다. 이전 버전의 IIS에서는 단계가 다릅니다.

Just-in-time 디버깅을 사용 하지 않도록 설정한 후에는 앱에서 오류를 처리 하 고 정상적으로 실행할 수 있습니다.

앱에 아직 처리 되지 않은 오류가 있으면 오류 메시지가 표시 되거나 앱이 충돌 하거나 중단 될 수 있습니다. 오류가 해결 될 때까지 앱이 정상적으로 실행 되지 않습니다. 앱 소유자에 게 연락 하 여 문제를 해결 하도록 요청할 수 있습니다.
