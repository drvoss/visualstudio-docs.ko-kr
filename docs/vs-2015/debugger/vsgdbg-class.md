---
title: VsgDbg 클래스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145699"
---
# <a name="vsgdbg-class"></a>VsgDbg 클래스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단의 앱에서 구성 요소 프로그래밍 방식으로 컨트롤에 대 한 인터페이스를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>멤버  
 `VsgDbg` 클래스는 다음과 같은 멤버를 지원 합니다.  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[VsgDbg::VsgDbg(생성자)](../debugger/vsgdbg-vsgdbg-constructor.md)|인스턴스를 생성 합니다 `VsgDbg` 클래스 및 필요에 따라 캡처하고 그래픽 정보를 기록 하도록 그래픽 진단의 앱에서 구성 요소를 준비 합니다.|  
|[VsgDbg::~VsgDbg(소멸자)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|인스턴스를 제거 합니다 `VsgDbg` 클래스입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|Description|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|그래픽 진단 HUD(Head-Up Display)에 사용자 지정 메시지를 추가합니다.|  
|[BeginCapture](../debugger/begincapture.md)|로 끝나는 캡처 간격 시작 `EndCapture`합니다.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.|  
|[복사(프로그램 방식 캡처)](../debugger/copy-programmatic-capture.md)|활성 그래픽 로그(.vsglog) 파일 내용을 새 파일에 복사합니다.|  
|[EndCapture](../debugger/endcapture.md)|`BeginCapture`로 시작된 캡처 간격을 종료합니다.|  
|[Init](../debugger/init.md)|캡처하고 그래픽 정보를 기록 하도록 그래픽 진단의 앱에서 구성 요소를 준비 합니다.|  
|[ToggleHUD](../debugger/togglehud.md)|그래픽 진단 HUD 오버레이 켜거나 끕니다.|  
|[UnInit](../debugger/uninit.md)|그래픽 로그 파일을 종료하고 닫고 앱이 그래픽 정보를 기록하는 동안 사용된 리소스를 확보합니다.|  
  
## <a name="remarks"></a>설명  
 `VsgDbg` 클래스 그래픽 진단 기능을 프로그래밍 방식으로 제어 하는 데 사용할 수 있는 인터페이스를 나타냅니다. 않음 캡처 및 그래픽 정보를 기록 하는 경우에 몇 가지 기능을 사용할 수 있습니다. 여기에 `AddMessage` 멤버 함수 및 `ToggleHUD` 멤버 함수입니다. 다른 멤버 함수를 시작 하거나 활성 그래픽 정보 캡처를 중지 하도록 그래픽 진단의 앱에서 구성 요소를 준비 하거나 앱을 적극적으로 캡처 하 고 그래픽 로그 파일에 그래픽 정보를 기록 하는 동안 호출 되어야 합니다.
