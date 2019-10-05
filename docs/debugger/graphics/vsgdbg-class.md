---
title: VsgDbg 클래스 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4051a02de6a046621e62c21b4d2399b5a2703cb8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895194"
---
# <a name="vsgdbg-class"></a>VsgDbg 클래스
그래픽 진단의 앱에서 구성 요소 프로그래밍 방식으로 컨트롤에 대 한 인터페이스를 나타냅니다.

## <a name="syntax"></a>구문

```C++
class VsgDbg;
```

## <a name="members"></a>멤버
 `VsgDbg` 클래스는 다음과 같은 멤버를 지원 합니다.

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[VsgDbg::VsgDbg(생성자)](vsgdbg-vsgdbg-constructor.md)|인스턴스를 생성 합니다 `VsgDbg` 클래스 및 필요에 따라 캡처하고 그래픽 정보를 기록 하도록 그래픽 진단의 앱에서 구성 요소를 준비 합니다.|
|[VsgDbg::~VsgDbg(소멸자)](vsgdbg-tilde-vsgdbg-destructor.md)|인스턴스를 제거 합니다 `VsgDbg` 클래스입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[AddMessage](addmessage.md)|그래픽 진단 HUD(Head-Up Display)에 사용자 지정 메시지를 추가합니다.|
|[BeginCapture](begincapture.md)|로 끝나는 캡처 간격 시작 `EndCapture`합니다.|
|[CaptureCurrentFrame](capturecurrentframe.md)|그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.|
|[복사(프로그램 방식 캡처)](copy-programmatic-capture.md)|활성 그래픽 로그(.vsglog) 파일 내용을 새 파일에 복사합니다.|
|[EndCapture](endcapture.md)|`BeginCapture`로 시작된 캡처 간격을 종료합니다.|
|[Init](init.md)|캡처하고 그래픽 정보를 기록 하도록 그래픽 진단의 앱에서 구성 요소를 준비 합니다.|
|[ToggleHUD](togglehud.md)|그래픽 진단 HUD 오버레이 켜거나 끕니다.|
|[UnInit](uninit.md)|그래픽 로그 파일을 종료하고 닫고 앱이 그래픽 정보를 기록하는 동안 사용된 리소스를 확보합니다.|

## <a name="remarks"></a>설명
 `VsgDbg` 클래스 그래픽 진단 기능을 프로그래밍 방식으로 제어 하는 데 사용할 수 있는 인터페이스를 나타냅니다. 않음 캡처 및 그래픽 정보를 기록 하는 경우에 몇 가지 기능을 사용할 수 있습니다. 여기에 `AddMessage` 멤버 함수 및 `ToggleHUD` 멤버 함수입니다. 다른 멤버 함수를 시작 하거나 활성 그래픽 정보 캡처를 중지 하도록 그래픽 진단의 앱에서 구성 요소를 준비 하거나 앱을 적극적으로 캡처 하 고 그래픽 로그 파일에 그래픽 정보를 기록 하는 동안 호출 되어야 합니다.