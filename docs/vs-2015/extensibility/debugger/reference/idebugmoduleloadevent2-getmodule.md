---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0083946051fe78fc1bd19ea877475465e0b6477f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163426"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

되는 모듈을 가져옵니다 로드 또는 언로드 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pModule`  
 [out] 반환 된 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 로드 하거나 언로드하는 모듈을 나타내는 개체입니다.  
  
 `pbstrDebugMessage`  
 [out에서] 이 이벤트를 설명 하는 선택적 메시지를 반환 합니다. 이 매개 변수는 null 값을, 메시지 없이 요청 됩니다.  
  
 `pbLoad`  
 [out에서] 0이 아닌 값 (`TRUE`) 모듈을 로드 하 고 0 이면 (`FALSE`) 경우 모듈을 언로드하는 중입니다. 이 매개 변수는 null 값, 상태 없음 요청 됩니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
