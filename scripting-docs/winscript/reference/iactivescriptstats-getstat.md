---
title: 'IActiveScriptStats:: GetStat | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574344"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
표준 스크립트 통계 중 하나를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `stid`  
 진행 반환할 통계를 지정 합니다. 값은 다음과 같아야 합니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|스크립트가 시작 되거나 통계가 다시 설정 된 이후 실행 된 문의 수를 반환 합니다.|  
  
 `pluHi`  
 제한이 통계를 나타내는 64 비트 부호 없는 정수의 상위 32 비트입니다.  
  
 `pluLo`  
 제한이 통계를 나타내는 64 비트 부호 없는 정수의 하위 32 비트입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값은 다음 표에 나와 있는 값을 포함 하지만이에 제한 되지 않습니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 표준 스크립트 통계 중 하나를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptStats:: GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)    
 [IActiveScriptStats 인터페이스](../../winscript/reference/iactivescriptstats-interface.md)