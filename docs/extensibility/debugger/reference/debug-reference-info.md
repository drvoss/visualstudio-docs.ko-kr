---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9c25c06f4fa92030bec5bd3b6f2566111dadad4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829627"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
참조를 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>멤버  
 dwFields  
 플래그의 조합 된 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 채워진 필드를 지정 하는 열거형입니다.  
  
 bstrName  
 사용자가 지정한 이름의 합니다 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다.  
  
 bstrType  
 서식이 지정 된 문자열로 참조 형식입니다.  
  
 bstrValue  
 서식이 지정 된 문자열로 참조 값  
  
 dwAttrib  
 플래그의 조합 된 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 디버그 속성 특성에 대 한 플래그를 지정 하는 열거형입니다.  
  
 dwRefType  
 값을 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) 강 하거나 약한 참조 형식 인지 여부를 지정 하는 열거형입니다.  
  
 m_pReference  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 참조 정보를 지정 하는 개체입니다.  
  
## <a name="remarks"></a>설명  
 이 구조에 대 한 호출에 전달 되는 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 메서드를 채울 수 있습니다. 이 구조에서 목록의 일부로 반환 됩니다 합니다 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) 차례로 호출에서 반환 되는 인터페이스를 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)