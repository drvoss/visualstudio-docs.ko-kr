---
title: 원격 도구 다운로드를 차단 해제
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903028"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>방법: Windows Server에서 원격 도구 다운로드를 차단 해제

Windows Server에서 Internet Explorer의 기본 보안 설정을 원격 도구와 같은 구성 요소를 다운로드 하려면 시간이 오래 걸리는 확인 수 있습니다.

* 웹 사이트를 열고 리소스를 포함 하는 도메인은 명시적으로 허용 하지 않는 한 웹 리소스에 액세스를 차단 하는 Internet Explorer에서 향상 된 보안 구성이 사용 됩니다 (즉, 신뢰할 수 있음). 이 설정을 해제할 수 있습니다, 있지만 바람직하지 않습니다 것 하므로 보안 위험이 있습니다.

* Windows Server 2016에서 설정 하는 기본 **인터넷 옵션** > **Security** > **Internet**  >   **사용자 지정 수준** > **다운로드** 사용 하지 않도록 설정 파일 다운로드 합니다. Windows Server에서 직접 원격 도구를 다운로드 하려는 경우 파일 다운로드를 활성화 해야 합니다.

Windows Server의 도구를 다운로드 하려면 좋습니다 다음 중 하나:

* 하나의 실행 중인 Visual Studio와 같은 다른 컴퓨터에서 원격 도구를 다운로드 하 고 복사 합니다 *.exe* Windows 서버로 파일입니다.

* 원격 디버거를 실행 [파일 공유에서](../debugger/remote-debugging.md#fileshare_msvsmon) Visual Studio 컴퓨터에 있습니다.

* Windows Server에서 직접 원격 도구를 다운로드 하 고 신뢰할 수 있는 사이트를 추가 하 라는 메시지를 수락 합니다. 최신 웹 사이트는 많은 타사 리소스에 종종 포함 시켜 서 많은 수의 프롬프트가 발생할 수 있습니다. 또한 모든 리디렉션된 링크를 수동으로 추가 해야 합니다. 다운로드를 시작 하기 전에 신뢰할 수 있는 사이트의 일부를 추가 하도록 선택할 수 있습니다. 로 이동 **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트** 다음 사이트를 추가 합니다.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * 에 대 한: 빈

  My.visualstudio.com에 디버거의 이전 버전에 대 한 해당 로그인이 성공 하는지 확인 하려면 해당 추가 사이트를 추가 합니다.

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    원격 도구를 다운로드 하는 동안 이러한 도메인을 추가 하도록 선택할 경우 선택 **추가** 메시지가 표시 되 면 합니다.

    ![콘텐츠 대화 상자를 차단합니다.](../debugger/media/remotedbg-blocked-content.png)

    소프트웨어를 다운로드 하는 경우 다양 한 웹 사이트 스크립트 및 리소스를 로드 하는 권한을 부여 하려면 일부 추가 요청이 얻게 됩니다. My.visualstudio.com, 해당 로그인이 성공 하는지 확인 하려면 해당 추가 도메인을 추가 하는 것이 좋습니다.