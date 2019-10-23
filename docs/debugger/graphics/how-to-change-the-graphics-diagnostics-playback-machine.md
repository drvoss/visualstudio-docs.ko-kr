---
title: '방법: 그래픽 진단 재생 컴퓨터 변경 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a41caf3f866c4a21d0a44fc69932066b2b7d923
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735056"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>방법: 그래픽 진단 재생 컴퓨터 변경
로컬 컴퓨터를 사용 하거나 원격 컴퓨터 또는 장치를 사용 하 여 그래픽 정보를 재생할 수 있습니다.

## <a name="choosing-a-playback-machine"></a>재생 컴퓨터 선택
 재생 컴퓨터는 그래픽 로그에서 그래픽 이벤트를 재생 하는 데 사용 되는 컴퓨터 또는 장치입니다. 일반적으로 로컬 컴퓨터는 가장 편리한 옵션 이지만 하드웨어 또는 드라이버 버전이 캡처된 컴퓨터와 다른 하드웨어 또는 드라이버 버전이 있는 컴퓨터에서는 렌더링 문제가 재현 되지 않을 수 있습니다. 이 경우 문제를 재현 하는 원격 재생 컴퓨터를 선택 하 고 계속 해 서 개발 컴퓨터를 사용 하 여 진단할 수 있습니다.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>로컬 컴퓨터를 사용 하 여 그래픽 정보를 재생 하려면

1. 그래픽 로그 문서 창에서 **재생 컴퓨터** 링크를 선택 합니다. **원격 디버거 연결** 대화 상자가 나타납니다.

2. **수동 구성**의 **주소** 속성에 `localhost`을 입력 합니다.

3. **인증 모드** 속성을 **없음**으로 설정 합니다.

4. **선택** 단추를 선택합니다.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>원격 컴퓨터를 사용 하 여 그래픽 정보를 재생 하려면

1. 그래픽 로그 문서 창에서 **재생 컴퓨터** 링크를 선택 합니다. **원격 디버거 연결** 대화 상자가 나타납니다.

2. **수동 구성**의 **주소** 속성에서 그래픽 정보를 재생 하는 데 사용할 컴퓨터 또는 장치의 WINDOWS 도메인 이름 또는 IP 주소를 입력 합니다.

3. 재생 컴퓨터에 대 한 연결을 보호 하는 데 사용 하려는 권한 부여 종류를 지정 합니다.

    - Windows 인증의 경우 **인증 모드** 속성을 **windows**로 설정 합니다.

    - 인증 안 함으로 **인증 모드** 속성을 **없음**으로 설정 합니다.

4. **선택** 단추를 선택합니다.

> [!NOTE]
> **원격 디버거 연결** 대화 상자에는 개발 컴퓨터에 직접 연결 되어 있거나 동일한 서브넷에 있는 원격 디버깅 대상이 표시 될 수도 있습니다. 이러한 원격 디버깅 대상 중 하나를 수동으로 구성 하지 않고 그래픽 진단 재생 컴퓨터로 사용할 수 있습니다. **원격 디버거 연결** 대화 상자에서 원하는 대상을 선택 하 고 **선택** 단추를 선택 합니다.

## <a name="see-also"></a>참조
- [그래픽 로그 문서](graphics-log-document.md)