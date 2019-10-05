---
title: 'Ijsdebug:: Openvirtualprocess 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583596"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess 메서드
새 가상 프로세스 개체를 만드는 데 사용 되는 팩터리 메서드.  
  
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
 [in] 디버거를 연결할 프로세스 Id입니다.  
  
 `runtimeJsBaseAddress`  
 [in] JavaScript 런타임에서 대상 프로세스로 로드에는 기본 주소입니다.  
  
 `pDataTarget`  
 [in] 디버거 프로세스의 상태에 대 한 쿼리 인터페이스를 제공된 합니다.  
  
 `ppProcess`  
 [out] 새 디버그 프로세스 개체  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 Jscript9diag 및 jscript9와 일치 하지 않으면 E_JsDEBUG_MISMATCHED_RUNTIME를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebug 인터페이스](../../winscript/reference/ijsdebug-interface.md)