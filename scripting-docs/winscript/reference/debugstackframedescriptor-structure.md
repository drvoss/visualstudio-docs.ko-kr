---
title: DebugStackFrameDescriptor 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955196"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor 구조체
스택 프레임을 열거하고 출력은 동일한 스레드에서 여러 열거자에 병합합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>멤버  
 `pdsf`  
 스택 프레임 개체입니다.  
  
 `dwMin`  
 이 스택 프레임과 연결 된 실제 주소의 더 낮은 범위의 컴퓨터 종속 표현입니다.  
  
 `dwLim`  
 이 스택 프레임과 연결 된 물리적 주소 범위의 상한 한 컴퓨터 종속 표현입니다.  
  
 `fFinal`  
 프레임은 처리 되 고 있음을 나타내는 플래그입니다.  
  
 `punkFinal`  
 이 매개 변수가 아닌 경우 `NULL`병합 현재 열거자 중지 해야 하 고 새로 시작 해야 합니다. 개체에 새 열거형을 시작 하는 방법을 나타냅니다.  
  
## <a name="remarks"></a>설명  
 프로세스 디버그 관리자는 여러 스크립트 엔진에서 스택 프레임을 정렬 하려면이 구조를 사용 합니다. 규칙에 따라 스택 아래로 증가합니다. 따라서 주소는 스택 성장 아키텍처에 두 개씩 짝 보완를 이어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)