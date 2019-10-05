---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efda31daae198befbda35803ef71e1d0322e9bbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153077"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 스레드에 대 한 스택 프레임의 목록을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFieldSpec`  
 [in] 플래그의 조합을 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 의 필드를 지정 하는 열거형을 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조체가를 채워야 합니다. 지정 된 `FIF_FUNCNAME_FORMAT` 함수 이름의 단일 문자열로 서식을 지정 하는 플래그입니다.  
  
 `nRadix`  
 [in] 열거자의 숫자 정보를 서식 지정에 사용 하는 기 수입니다.  
  
 `ppEnum`  
 [out] 반환 된 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 개체의 목록을 포함 하는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 스택 프레임을 설명 하는 구조입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 스레드의 프레임 순서로 먼저 열거할 현재 프레임 및 마지막으로 열거 하는 가장 오래 된 프레임을 사용 하 여 열거 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
