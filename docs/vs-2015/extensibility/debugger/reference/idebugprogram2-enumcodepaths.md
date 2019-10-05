---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202773"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

소스 파일에서 지정된 된 위치에 대 한 코드 경로의 목록을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszHint`  
 [in] 커서 아래에 있는 단어를 **원본** 하거나 **디스어셈블리** IDE에서 보기.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 현재 코드 컨텍스트를 나타내는 개체입니다.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 현재 중단점을 사용 하 여 연결 된 스택 프레임을 나타내는 개체입니다.  
  
 `fSource`  
 [in] 0이 아닌 (`TRUE`)에 있는 경우는 **소스** 뷰 또는 0 (`FALSE`)에 있는 경우는 **디스어셈블리** 보기.  
  
 `ppEnum`  
 [out] 반환 된 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 코드 경로 목록을 포함 하는 개체입니다.  
  
 `ppSafety`  
 [out] 반환 된 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 건너뜁니다 코드 경로 선택한 경우 중단점으로 설정 하도록 추가 코드 컨텍스트를 나타내는 개체입니다. 예를 들어 대해서는 처리가 단축된 부울 식의 경우 발생할 수 있습니다이 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 코드 경로 메서드 또는 프로그램 실행의 현재 위치를 이동 하려면 호출 된 함수의 이름을 설명 합니다. 코드 경로의 목록에는 호출 스택을 나타냅니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
