---
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e00f055d8e6a0fe1bea82061431410eb1e3b236f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192926"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

특정 포트를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidPort`  
 [in] 검색할 포트의 GUID입니다.  
  
 `ppPort`  
 [out] 반환 된 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 원하는 포트를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_PORTSUPPLIER_NO_PORT` 주어진된 식별자를 사용 하 여 포트가 없는 경우.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
