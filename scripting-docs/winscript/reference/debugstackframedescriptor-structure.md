---
title: Debugstack프레임 설명자 구조 | Microsoft Docs
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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576548"
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
 이 스택 프레임과 연결 된 물리적 주소의 하위 범위에 대 한 컴퓨터 종속 표현입니다.  
  
 `dwLim`  
 이 스택 프레임과 연결 된 실제 주소의 상위 범위에 대 한 컴퓨터 종속 표현입니다.  
  
 `fFinal`  
 프레임이 처리 중임을 나타내는 플래그입니다.  
  
 `punkFinal`  
 이 매개 변수를 `NULL` 하지 않으면 현재 열거자 병합을 중지 하 고 새 열거자를 시작 해야 합니다. 개체는 새 열거를 시작 하는 방법을 나타냅니다.  
  
## <a name="remarks"></a>주의  
 프로세스 디버그 관리자는이 구조를 사용 하 여 여러 스크립트 엔진에서 스택 프레임을 정렬 합니다. 규칙에 따라 스택은 아래로 증가 합니다. 따라서 스택이 증가 하는 아키텍처에서 주소는 2 ~ 2를 보완 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)