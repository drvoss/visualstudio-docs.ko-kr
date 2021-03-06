---
title: IDebugArrayObject2::GetBaseIndices | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b53b8f2cd7819650abbb4fc88a7ec3f4b6dfe21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903194"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
배열의 차원 수를 지정 하는 각 인덱스에 대 한 기본 인덱스 (하위 범위)를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```csharp  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwRank`  
 [in] 배열의 차수 (rank) 수입니다.  
  
 `dwIndices`  
 [out] 배열에 대 한 기본 인덱스 (하위 범위).  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 예를 들어이 함수는 반환 '5' 다음에 의해 만들어진 배열에 대 한 C# 코드:  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)