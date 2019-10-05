---
title: IDebugExpressionEvaluator::Parse | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4039534b139eeeaf20f938c6d6c358c602f96227
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155348"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 구문 분석 된 식에 식 문자열을 변환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `upstrExpression`  
 [in] 식 문자열을 구문 분석할 수입니다.  
  
 `dwFlags`  
 [in] 컬렉션인 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 식을 구문 분석 하는 방법을 결정 하는 상수입니다.  
  
 `nRadix`  
 [in] 모든 숫자 정보를 해석 하는 데 사용할 기 수입니다.  
  
 `pbstrError`  
 [out] 사람이 읽을 수 있는 텍스트는 오류를 반환합니다.  
  
 `pichError`  
 [out] 식 문자열의 오류의 시작 문자 위치를 반환합니다.  
  
 `ppParsedExpression`  
 [out] 구문 분석 된 식을 반환 합니다는 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 구문 분석 된 식에는 실제 값이 아닌를 생성합니다. 구문 분석 된 식 준비가 되었습니다 평가 되 고, 즉, 값으로 변환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
