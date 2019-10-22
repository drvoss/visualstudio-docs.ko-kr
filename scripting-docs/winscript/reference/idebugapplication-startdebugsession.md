---
title: 'IDebugApplication:: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fd27ec86485d39ee9f13997c1a2db7175afcde
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570990"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
기본 디버거 IDE (통합 개발 환경)를 시작 하 고 아직 연결 되어 있지 않은 경우 디버그 세션을이 응용 프로그램에 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 just-in-time 디버깅을 구현 하는 데 사용 됩니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)