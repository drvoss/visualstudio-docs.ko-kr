---
title: 'IJsDebugDataTarget:: ReadNullTerminatedString 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572408"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString 메서드
대상에서 지정 된 수의 문자를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 진행 읽을 주소입니다.  
  
 `characterSize`  
 [in] 문자열에 있는 각 문자의 크기  
  
 `maxCharacters`  
 진행 읽을 최대 문자 수입니다. maxCharacters가 적절 해야 합니다. 128MB가 넘는 메모리에 대 한 모든 요청은 실패 합니다.  문자열이 maxCharacters 보다 큰 경우 결과 문자열은 maxCharacters 이후 잘립니다.  
  
 `pString`  
 제한이 대상에서 읽은 BSTR입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 잘린 경우 S_FALSE를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)