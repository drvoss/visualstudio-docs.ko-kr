---
title: IDebugPointerObject::GetBytes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ef0c01d86259b6ec8c23f2874244b018a74febc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188586"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

일련의 연속 된 바이트를 가리키는 값을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwStart`  
 [in] 개체의 시작 부분에서 바이트 오프셋을 지정 합니다.  
  
 `dwCount`  
 [in] 검색할 바이트 수입니다.  
  
 `pBytes`  
 [out에서] 일련의 연속 된 바이트 값을 사용 하 여 입력은 배열에서 가리키는 개체에서 지정 된 오프셋에서 시작 합니다.  
  
 `pdwBytes`  
 [out] 실제로 검색 하는 바이트 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 경우 사용이 나타낸 마우스 포인터 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 기본 형식 또는 기본 형식 (즉, 간단한 바이트 시퀀스를 나타낼 수 있는 배열)의 간단한 배열을 가리킵니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
