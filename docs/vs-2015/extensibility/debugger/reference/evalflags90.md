---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a95f25f9e970beb31544722b1beeb05b2d480b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156044"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

식 계산을 제어 하는 플래그에 대 한 유효한 값을 열거 합니다. 이 열거형을 확장 합니다 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 EVAL90_RETURNVALUE  
 있는 경우 반환 값을 평가 하는 것을 지정 합니다.  
  
 EVAL90_NOSIDEEFFECTS  
 파생 작업이 허용 되지 않음을 지정 합니다.  
  
 EVAL90_ALLOWBPS  
 중단점에서 중지를 지정합니다.  
  
 EVAL90_ALLOWERRORREPORT  
 해당 오류 수를 보고 호스트를 지정 합니다. Internet Explorer에서 스크립트의 식 평가 위해 주로 사용 됩니다.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 함수를 호출 하는 대신 주소로 평가할 강제로 함수입니다.  
  
 EVAL90_NOFUNCEVAL  
 함수를에서 확인할 수 없습니다. 예를 들어 합니다 `int` 식에서 토큰 `myExpression(int) + 10`합니다. 이 함수는 주소로 아니지만 값을 올바르게 평가할 수 있습니다.  
  
 EVAL90_NOEVENTS  
 식 평가 중 발생 하는 이벤트를 보내지 세션 디버그 관리자 (SDM) 또는 IDE를 표시 하는 플래그입니다.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 디자인 타임 식 계산을 사용 하도록 설정 합니다.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 암시적 변수 만들 수 있도록 허용 합니다.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 즉시 실행 되도록 강제로 평가 합니다. 사용자 요청과 같이 요청을 서비스 하는 경우에 유용 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg90.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
