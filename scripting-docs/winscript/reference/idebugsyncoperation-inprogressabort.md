---
title: 'IDebugSyncOperation:: InProgressAbort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576661"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
다른 스레드에서 진행 중인 작업을 취소 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|작업을 취소할 수 없습니다.|  
|`E_ABORT`|작업을 완료할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 프로세스 디버그 관리자는 디버거 스레드 내에서이 메서드를 호출 하 여 다른 스레드에서 진행 중인 작업을 취소 합니다.  
  
 @No__t_0 메서드가 작업을 완료할 수 없는 경우 가능한 한 빨리 `E_ABORT`을 반환 합니다. 이 메서드는 작업을 취소할 수 없는 경우 `E_NOTIMPL`를 반환할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugSyncOperation 인터페이스](../../winscript/reference/idebugsyncoperation-interface.md)