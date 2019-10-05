---
title: EndCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a451746cae978f141b30fb7295a82310e04367c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197103"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`BeginCapture`로 시작된 캡처 간격을 종료합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>설명  
 캡처 간격은 일반적으로 특정 그리기 호출 종류에 대한 그래픽 정보만 호출하려고 할 때와 같이 한 프레임의 하위 집합을 확장합니다. 캡처 간격이 존재하는 호출을 확장하는 경우 그래픽 정보의 두 프레임이 캡처됩니다. 첫 번째 프레임은 `BeginCapture`에 대한 호출과 존재하는 호출 간에 간격을 확장하고 두 번째 프레임은 존재하는 호출 이후 첫 번째 Direct3D 이벤트와 `EndCapture`에 대한 호출 간의 간격을 확장합니다.  
  
 간격을 캡처하려면 캡처 그래픽 정보를 기록 하 고 앱을 준비 해야 합니다-즉, 호출 했어야 합니다 [Init](../debugger/init.md) 의 인스턴스를 통해 합니다 `VsgDbg` 클래스를 호출 하기 전에 `BeginCapture` 또는 `EndCapture`합니다.  
  
## <a name="see-also"></a>관련 항목  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
