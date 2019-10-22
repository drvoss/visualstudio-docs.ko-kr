---
title: 'IDebugSyncOperation:: GetTargetThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.GetTargetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::GetTargetThread
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6675356439d60e5c204760e69640a0f50bf40fc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576680"
---
# <a name="idebugsyncoperationgettargetthread"></a>IDebugSyncOperation::GetTargetThread
이 동기 작업에 대 한 대상 응용 프로그램 스레드를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppatTarget`  
 제한이 이 동기 작업에 대 한 대상 응용 프로그램 스레드입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 동기 작업에 대 한 대상 응용 프로그램 스레드를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugSyncOperation 인터페이스](../../winscript/reference/idebugsyncoperation-interface.md)