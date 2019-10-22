---
title: 'IApplicationDebugger:: CreateInstanceAtDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577884"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
디버거가 out-of-process 코드를 사용 하 여 디버거 프로세스에서 개체를 만들 수 있습니다.  
  
> [!IMPORTANT]
> 이 메서드는 신뢰할 수 없는 코드가 신뢰할 수 있는 디버거 스레드에서 임의의 개체를 만들 수 있도록 허용 하므로 구현 하면 안 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rclsid`  
 진행 만들 개체의 CLSID (클래스 식별자)입니다.  
  
 `pUnkOuter`  
 진행 @No__t_0 경우 개체가 집계의 일부로 생성 되지 않습니다. 그렇지 않으면 `pUnkOuter`는 집계 개체의 `IUnknown` 인터페이스 (제어 `IUnknown`)에 대 한 포인터입니다.  
  
 `dwClsContext`  
 진행 실행 코드를 실행 하기 위한 컨텍스트입니다. 값은 열거형 `CLSCTX`에서 가져옵니다.  
  
 `riid`  
 진행 개체와 통신 하는 데 사용 되는 인터페이스 식별자입니다.  
  
 `ppvObject`  
 제한이 @No__t_0에서 요청 된 인터페이스 포인터를 받는 포인터 변수의 주소입니다. 반환이 성공적 이면 * `ppvObject`는 요청 된 인터페이스 포인터를 포함 합니다. 오류가 발생 하면 \* `ppvObject`에 `NULL` 포함 됩니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `CoCreateInstance`에 위임 합니다.  
  
 메서드가 현재 구현 되어 있지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IApplicationDebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)