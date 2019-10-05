---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180586"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정된 된 위치에서 시작 하는 바이트 시퀀스를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStartContext`  
 [in] 합니다 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 바이트를 읽기 시작할 위치를 지정 하는 개체입니다.  
  
 `dwCount`  
 [in] 읽을 바이트 수입니다. 또한의 길이 지정 된 `rgbMemory` 배열입니다.  
  
 `rgbMemory`  
 [out에서] 실제로 읽은 바이트를 사용 하 여 입력 하는 배열입니다.  
  
 `pdwRead`  
 [out] 실제로 읽은 연속 된 바이트 수를 반환 합니다.  
  
 `pdwUnreadable`  
 [out에서] 읽을 수 없는 바이트 수를 반환합니다. 클라이언트가 읽을 수 없는 바이트 수를 원하는 경우 null 값이 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 경우 100 바이트 요청 및 처음 50 개의 읽을 수 있는, 다음 20 개를 읽을 수 없는 되며 나머지 30 읽을 수 있는,이 메서드를 반환 합니다.  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 이 경우 때문에 `*pdwRead + *pdwUnreadable < dwCount`를 호출자에 게 요청 된 원래 100의 나머지 30 바이트 읽기를 추가로 호출 해야 합니다. 및 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 전달 된 개체는 `pStartContext` 매개 변수 이동 70입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
