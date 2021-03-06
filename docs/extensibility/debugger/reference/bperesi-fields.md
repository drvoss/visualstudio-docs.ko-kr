---
title: BPERESI_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9530e950ddd5dbf75fb10b5391dc658bdf899fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869940"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
중단점의 실패 한 확인에 대 한 검색할 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>멤버  
 PERESI_BPRESLOCATION  
 초기화/사용 합니다 `bpResLocation` (중단점 해결 위치) 필드를 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조입니다.  
  
 BPERESI_PROGRAM  
 초기화/사용 된 `pProgram` 필드는 `BP_ERROR_RESOLUTION_INFO` 구조입니다.  
  
 BPERESI_THREAD  
 초기화/사용 된 `pThread` 필드는 `BP_ERROR_RESOLUTION_INFO` 구조입니다.  
  
 BPERESI_MESSAGE  
 초기화/사용 된 `bstrMessage` 필드는 `BP_ERROR_RESOLUTION_INFO` 구조입니다.  
  
 BPERESI_TYPE  
 초기화/사용 합니다 `dwType` (중단점 형식) 필드는 `BP_ERROR_RESOLUTION_INFO` 구조입니다.  
  
 BPERESI_ALLFIELDS  
 초기화/사용의 모든 필드는 `BP_ERROR_RESOLUTION_INFO` 구조입니다.  
  
## <a name="remarks"></a>설명  
 매개 변수로 전달 합니다 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 의 필드를 표시 하는 방법 합니다 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조는 초기화할.  
  
 이러한 값은 또한의 필드를 나타내기 위해 사용 된 `BP_ERROR_RESOLUTION_INFO` 구조는 유효 하 고 사용 되는 해당 구조를 반환할 때.  
  
 이러한 값을 비트 결합할 수 있습니다 `OR`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)