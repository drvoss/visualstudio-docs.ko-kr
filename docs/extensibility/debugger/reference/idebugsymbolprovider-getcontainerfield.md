---
title: IDebugSymbolProvider::GetContainerField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac7acc5d12ecce72119f19a51b1f4313a1aabe08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926406"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
이 메서드는 디버그 주소를 포함 하는 필드를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetContainerField(   
   IDebugAddress*         pAddress,  
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainerField(  
   IDebugAddress            pAddress,   
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pAddress`  
 [in] 에 표시 된 대로 주소는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스입니다.  
  
 `ppContainerField`  
 [out] 나타내는 컨테이너 필드를 반환 합니다는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)