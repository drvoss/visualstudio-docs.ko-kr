---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6d0fd8cff2f352c8ede674be64062a738c1f3d02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198800"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

두 문서 컨텍스트를 비교 하기 위한 조건을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>멤버  
 DOCCONTEXT_EQUAL  
 대상 문서 컨텍스트에 해당 목록의 첫 번째 문서 컨텍스트를 찾습니다.  
  
 DOCCONTEXT_LESS_THAN  
 대상 문서 컨텍스트를 보다 작은 목록의 첫 번째 문서 컨텍스트를 찾습니다.  
  
 DOCCONTEXT_GREATER_THAN  
 대상 문서 컨텍스트 보다 큰 목록에서 첫 번째 문서 컨텍스트를 찾습니다.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 대상 문서 컨텍스트 같은 문서에 있는 목록의 첫 번째 문서 컨텍스트를 찾습니다.  
  
## <a name="remarks"></a>설명  
 인수로 전달 된 [비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) 메서드.  
  
 이러한 값은 목록의 첫 번째 문서 컨텍스트를 찾기 위한 비교 조건을 지정 하는 데 사용 됩니다. 문서 컨텍스트를 통해 자체 작업에 대해 비교할 문서 컨텍스트 목록이 제공 되는 `IDebugDocumentContext2::Compare` 메서드. 비교 연산자가 있는 목록의 첫 번째 문서 컨텍스트 `true` 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
