---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198768"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` 이유를 나타내는입니다 **편집 하며 계속 하기** 를 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 ENCUN_NONE  
 편집 하며 계속 사용할 수 없는 특정 이유가 없습니다.  
  
 ENCUN_INTEROP  
 편집 하며 계속 사용할 수 없는 경우는 InterOp 호출 중  
  
 ENCUN_SQLCLR  
 편집 하며 계속 하기 중 사용할 수 없는 공용 언어 런타임 (CLR)를 사용 하는 SQL 프로시저 호출을 합니다.  
  
 ENCUN_MINIDUMP  
 편집 하며 계속 사용할 수 없는 경우 미니 덤프를 처리 하는 동안  
  
 ENCUN_EMBEDDED  
 편집 하며 계속 사용할 수 없는 경우 포함 된 코드를 처리 하는 경우  
  
 ENCUN_ATTACH  
 편집 하며 계속 사용할 수 없는 세션에 연결 된 경우 때문에 시작 되지 디버거에 의해 합니다.  
  
 ENCUN_WIN64  
 편집 하며 계속 사용할 수 없는 경우 64 비트 Windows 코드를 처리 하는 동안  
  
## <a name="remarks"></a>설명  
 이 열거형은 내부 용도로 여 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]입니다. 합니다 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 하 고 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 사용자 지정 포트 공급자에 의해 구현 된 메서드는 항상 반환 해야 `E_NOTIMPL`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.idl  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
