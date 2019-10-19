---
title: 'IDebugApplication:: GetBreakFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetBreakFlags
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614429ebb8cc9271a0444536d14c45b69a9588f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574981"
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
응용 프로그램에 대 한 현재 중단 플래그를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pabf`  
 제한이 응용 프로그램의 현재 중단 플래그입니다.  
  
 `pprdatSteppingThread`  
 제한이 현재 실행 중인 스레드입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 응용 프로그램에 대 한 현재 분할 플래그를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)    
 [APPBREAKFLAGS 열거형](../../winscript/reference/appbreakflags-enumeration.md)