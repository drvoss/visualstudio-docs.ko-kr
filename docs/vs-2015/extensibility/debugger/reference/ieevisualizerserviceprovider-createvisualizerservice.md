---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155087"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 시각화 도우미 서비스를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `binder`  
 [in] 합니다 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 에 전달 된 개체 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)합니다.  
  
 `pSymProv`  
 [in] 합니다 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 에 전달 된 개체 `IDebugParsedExpression::EvaluateSync`합니다.  
  
 `pAddress`  
 [in] 합니다 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 에 전달 된 개체 `IDebugParsedExression::EvaluateSync`합니다.  
  
 `dataProvider`  
 [in] 구현 하는 개체를 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스 (식 계산기가 제공).  
  
 `ppService`  
 [out] 만든된 서비스입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 합니다 `binder`, `pSymProv`, 및 `pAddress` 매개 변수를 전달 된 모든는 `IDebugParsedExpression::EvaluateSync` 메서드. `CreateVisualizerService` 에서만 호출할 수는 `IDebugParsedExpression::EvaluateSync` 일부로 형식 시각화 도우미에 대 한 식 계산기를 지원 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
