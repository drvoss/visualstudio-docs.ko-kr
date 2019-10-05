---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d467b037f4e2affea53a142304507f876630999
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202963"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

일련의 연속 된 바이트를 가리키는 값을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwStart`  
 [in] 개체의 시작 부분에서 바이트 오프셋을 지정 합니다.  
  
 `dwCount`  
 [in] 설정 하는 바이트 수입니다.  
  
 `pBytes`  
 [in] 새 값을 나타내는 바이트 배열입니다. 이 값은 지정 된 오프셋에서 시작 하는 개체에 저장 됩니다.  
  
 `pdwBytes`  
 [out] 실제로 집합 바이트 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 경우 사용이 나타낸 마우스 포인터 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 기본 형식 또는 기본 형식 (즉, 간단한 바이트 시퀀스를 나타낼 수 있는 배열)의 간단한 배열을 가리킵니다. 이 `IDebugPointerObject` 개체는 null 참조 (메모리의 주소를 가리키도록 해야 합니다) 일 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
