---
title: 'IJsDebug:: OpenVirtualProcess 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577741"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess 메서드
새 가상 프로세스 개체를 만드는 데 사용 되는 팩터리 메서드입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `processId`  
 진행 디버거를 연결할 프로세스 Id입니다.  
  
 `runtimeJsBaseAddress`  
 진행 JavaScript 런타임이 대상 프로세스에 로드 된 기본 주소입니다.  
  
 `pDataTarget`  
 진행 프로세스 상태를 쿼리 하기 위한 디버거 제공 인터페이스입니다.  
  
 `ppProcess`  
 제한이 새 디버그 프로세스 개체  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 Jscript9diag.h 및 Jscript9.dll이 일치 하지 않는 경우 E_JsDEBUG_MISMATCHED_RUNTIME를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebug 인터페이스](../../winscript/reference/ijsdebug-interface.md)