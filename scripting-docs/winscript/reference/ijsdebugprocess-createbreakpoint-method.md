---
title: 'IJsDebugProcess:: CreateBreakPoint 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575099"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint 메서드
지정한 문서 위치에서 중단점을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `documentId`  
 진행 IDebugDocumentText에 대 한 포인터입니다.  
  
 `characterOffset`  
 진행 파일의 시작 부분에서의 문자 오프셋입니다.  
  
 `characterCount`  
 진행 중단점이 삽입 되어야 하는 문서 텍스트의 길이입니다.  
  
 `isEnabled`  
 진행 중단점을 사용할 수 있는지 여부를 지정 합니다.  
  
 `ppDebugBreakPoint`  
 제한이 만들어진 중단점을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugProcess 인터페이스](../../winscript/reference/ijsdebugprocess-interface.md)