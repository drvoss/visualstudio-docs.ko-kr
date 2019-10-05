---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144571"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단 설정/해제 *HUD* (Head-up Display)를 끄거나 오버레이 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>설명  
 그래픽 진단 HUD가 그래픽 진단에서 실행 중인 앱의 왼쪽 위에 표시됩니다. 앱에 대 한 그래픽 정보 캡처 및 호출 하 여 추가 되는 메시지에 대 한 런타임 정보를 표시 합니다 [AddMessage](../debugger/addmessage.md) 멤버 함수입니다.  
  
 HUD를 전환 하려면 그래픽 정보를 캡처하지 않아도 필요가-즉, 인스턴스를 통해 해제할 수 있습니다는 `VsgDbg` 클래스 이지만 [Init](../debugger/init.md) 멤버 함수를 처음 호출할 필요가 없습니다.
