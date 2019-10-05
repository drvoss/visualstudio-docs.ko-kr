---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec67013b41a5ec8876866044355534c42bfe2ee0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848713"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.

## <a name="syntax"></a>구문

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>설명
 다른 캡처가 현재 진행 중인 경우(예: `BeginCapture` 함수에 의해 시작된 캡처) 해당 캡처를 완료하고 그래픽 로그에 다른 프레임으로 기록합니다. 이후에 즉시 그래픽 진단에서 다른 프레임으로도 기록되는 현재 프레임의 나머지 부분 캡처를 시작합니다. 현재 프레임의 끝은 호출로 표시됩니다.

 프레임을 캡처하려면 캡처 그래픽 정보를 기록 하 고 앱을 준비 해야 합니다-즉, 호출 했어야 합니다 [Init](init.md) 의 인스턴스를 통해 합니다 `VsgDbg` 클래스를 호출 하기 전에 `CaptureCurrentFrame`입니다.

## <a name="see-also"></a>참고 항목
- [Init](init.md)
- [BeginCapture](begincapture.md)