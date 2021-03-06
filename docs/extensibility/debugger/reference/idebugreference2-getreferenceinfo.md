---
title: IDebugReference2::GetReferenceInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8833b27d70a92091f809605edc81cd82a8a65f06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870005"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
가져옵니다 합니다 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 대 한 참조를 설명 하는 구조입니다. 나중에 사용하기 위해 예약되어 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFields`  
 [in] 플래그의 조합을 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 작성 해야 할 필드를 결정 하는 열거형을 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조입니다.  
  
 `nRadix`  
 [in] 모든 숫자 정보를 서식 지정 하는 데 사용할 기 수입니다.  
  
 `dwTimeout`  
 [in] 이 메서드에서 반환 되기 전에 대기할 밀리초에서는 최대 시간입니다. 사용 하 여 `INFINITE` 무기한 대기 합니다.  
  
 `rgpArgs`  
 [in] 배열을 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다. 사용 하도록 예약 됩니다. null 값으로 설정 합니다.  
  
 `dwArgCount`  
 [in] 에 대 한 참조 인수 개수는 `rgpArgs` 배열입니다. 사용 하도록 예약 됩니다. 0으로 설정 합니다.  
  
 `pReferenceInfo`  
 [out] A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조는이 속성에 대 한 설명을 채워집니다.  
  
## <a name="return-value"></a>반환 값  
 항상 `E_NOTIMPL`를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)