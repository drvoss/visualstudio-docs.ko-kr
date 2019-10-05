---
title: '방법: 그래픽 진단 재생 컴퓨터 변경 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb14fb4017ea1df6659b9a1a0ac093cd7cf7e0b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444820"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>방법: 그래픽 진단 재생 머신 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

재생할 수 있습니다 그래픽 정보는 원격 컴퓨터 또는 장치를 사용 하 여 또는 로컬 컴퓨터를 사용 하 여 합니다.  
  
## <a name="choosing-a-playback-machine"></a>재생 컴퓨터를 선택합니다.  
 재생 컴퓨터는 컴퓨터 또는 그래픽 로그에서 그래픽 이벤트를 재생 하는 데 사용 되는 장치. 일반적으로 로컬 컴퓨터는 가장 편리한 옵션 이지만 렌더링 문제가 캡처된;와 다른 하드웨어나 드라이버 버전을 컴퓨터에 있는 컴퓨터에서는 재현 되지 않을 수 있습니다. 이런 경우 문제를 더 잘 재현 하는 원격 재생 컴퓨터를 선택할 수 있으며 여전히 개발 컴퓨터를 사용 하 여 진단.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>그래픽 정보 재생 하려면 로컬 컴퓨터를 사용 하려면  
  
1. 그래픽 로그 문서 창에서 선택 합니다 **재생 컴퓨터** 링크 합니다. 합니다 **원격 디버거 연결** 대화 상자가 나타납니다.  
  
2. 아래 **수동 구성**를 **주소** 속성인 입력 `localhost`합니다.  
  
3. 설정 된 **인증 모드** 속성을 **None**합니다.  
  
4. **선택** 단추를 선택합니다.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>그래픽 정보 재생 하려면 원격 컴퓨터를 사용 하려면  
  
1. 그래픽 로그 문서 창에서 선택 합니다 **재생 컴퓨터** 링크 합니다. 합니다 **원격 디버거 연결** 대화 상자가 나타납니다.  
  
2. 아래 **수동 구성**를 **주소** 속성인 Windows 도메인 이름 또는 컴퓨터 또는 장치를 사용 하 여 그래픽 정보 재생 하려는 IP 주소를 입력 합니다.  
  
3. 재생 컴퓨터에 대 한 연결을 보호 하는 데 사용할 권한 부여의 종류를 지정 합니다.  
  
    - Windows 인증을 설정 합니다 **인증 모드** 속성을 **Windows**합니다.  
  
    - 인증 안 함 설정 합니다 **인증 모드** 속성을 **None**합니다.  
  
4. **선택** 단추를 선택합니다.  
  
> [!NOTE]
> 합니다 **원격 디버거 연결** 대화 상자는 개발 컴퓨터에 직접 연결 된 또는 동일한 서브넷에 있는 원격 디버깅 대상을 표시할 수도 있습니다. 그래픽 진단 재생 컴퓨터와 이러한 원격 디버깅 대상 중 하나를 사용 하 여 수동으로 구성 하지 않고 있습니다. 에 **원격 디버거 연결** 대화 상자를 선택 하 고 선택한 대상을 선택 합니다 **선택** 단추입니다.  
  
## <a name="see-also"></a>참고 항목  
 [그래픽 로그 문서](../debugger/graphics-log-document.md)
