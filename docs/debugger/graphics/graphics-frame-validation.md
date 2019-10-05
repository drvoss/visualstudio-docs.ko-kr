---
title: 그래픽 프레임 유효성 검사 | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce283e5cbab30b612a02ec447113ad11e206a7f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895872"
---
# <a name="graphics-frame-validation"></a>그래픽 프레임 유효성 검사
<!-- VERSIONLESS -->
Visual Studio 2017 및 향상 된 지원을 합니다 **프레임 유효성 검사** 도구입니다.  프레임 유효성 검사 창을 오류 및 이벤트 목록에 연결 된 경고를 표시 합니다.  이 창을 보려면 선택 합니다 **보기 > 프레임 유효성 검사** 메뉴.

![프레임 유효성 검사](media/gfx_diag_frame_validation.png)

클릭 합니다 **유효성 검사 실행** 분석을 시작 하려면 왼쪽된 위 모퉁이 있는 단추입니다.  프레임의 복잡성에 따라 완료 하는 데 몇 분 정도 걸릴 수 있습니다.  여기에 두 개의 원본에서 조합 표시 되는 데이터: 메시지는 D3D 자체를 내보내는 경우 [SDK 레이어](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) 을 사용 하는 및 추적 도구의 내부 상태에서 수집 되는 데이터입니다. 완료 되 면 몇 가지 열의 데이터가 표시 됩니다.

| **열** | **설명** |
|------------| - |
| 이벤트 ID | ID의 항목에 매핑되는 [이벤트 목록](graphics-event-list.md) 창입니다. |
| 심각도 | 손상, 오류, 경고, 정보 또는 메시지입니다. |
| 범주 | 응용 프로그램 정의 기타, 초기화, 정리, 컴파일, 상태 만들기, 상태 설정, 상태 시작, 실행, 리소스 조작을, 셰이더, 중복 및 사용 하지 않는 합니다. |
| 메시지 | 이벤트에 연결 된 메시지입니다. |
| 이벤트(event) | 오류 또는 경고와 관련 된 이벤트입니다. |

## <a name="see-also"></a>참고 항목
[그래픽 진단(DirectX 그래픽 디버그)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->