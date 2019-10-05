---
title: IDebugPendingBreakpoint2::EnumBoundBreakpoints | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumBoundBreakpoints
helpviewer_keywords:
- EnumBoundBreakpoints method
- IDebugPendingBreakpoint2::EnumBoundBreakpoints method
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 017981e2762ec8246a1898f224700c3b689552b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333776"
---
# <a name="idebugpendingbreakpoint2enumboundbreakpoints"></a>IDebugPendingBreakpoint2::EnumBoundBreakpoints
이 보류 중인 중단점에서 바인딩된 모든 중단점을 열거 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumBoundBreakpoints( 
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
[out] 반환 된 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 바인딩된 중단점을 열거 하는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_BP_DELETED` 중단점 삭제 된 경우.

## <a name="example"></a>예제
 다음 예제에서는 간단한에 대 한이 메서드를 구현 하는 방법을 보여 줍니다 `CPendingBreakpoint` 노출 하는 개체를 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스입니다.

```cpp
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)
{
   HRESULT hr;

   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer
   // is valid.
   if (ppEnum)
   {
      *ppEnum = NULL;

      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // If the bound breakpoint member variable is valid.
         if (m_pBoundBP)
         {
            // Get the bound breakpoint.
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;
            hr = m_pBoundBP->QueryInterface(&spBoundBP);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
               // Create the bound breakpoint enumerator.
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);
               assert(hr == S_OK);
               if (hr == S_OK)
               {
                  // Initialize the enumerator of bound breakpoints with
                  // the IDebugBoundBreakpoint2 information.
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);
                  if (hr == S_OK)
                  {
                     // Verify that the passed IEnumDebugBoundBreakpoints2
                     // interface can be queried by the created
                     // CEnumDebugBoundBreakpoints object.
                     hr = pBoundEnum->QueryInterface(ppEnum);
                     assert(hr == S_OK);
                  }

                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.
                  if (FAILED(hr))
                  {
                     delete pBoundEnum;
                  }
               }
            }
         }
         else
         {
            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>참고자료
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)