---
title: IEnumDebugModules2::GetCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2::GetCount
helpviewer_keywords:
- IEnumDebugModules2::GetCount
ms.assetid: f4def3d2-7cc9-4cd2-9649-3b7e00a76220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3f86fc1ad50e3207ef79d9c5cb584b2fe8c1dbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893899"
---
# <a name="ienumdebugmodules2getcount"></a>IEnumDebugModules2::GetCount
열거형의 요소 수를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcelt`  
 [out] 열거형의 요소 수를 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 항목만 지정 하는 일반적인 COM 열거형 인터페이스의 일부가 아닙니다.는 `Next`, `Clone`를 `Skip`, 및 `Reset` 메서드를 구현 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)