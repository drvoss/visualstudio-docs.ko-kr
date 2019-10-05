---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189406"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

문서 컨텍스트를 지정 된 배열에이 문서 컨텍스트를 비교합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `compare`  
 [in] 값을 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 비교의 형식을 지정 하는 열거형입니다.  
  
 `rgpDocContextSet`  
 [in] 배열을 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 비교할 문서 컨텍스트를 나타내는 개체입니다.  
  
 `dwDocContextSetLen`  
 [in] 비교할 문서 컨텍스트에 배열의 길이입니다.  
  
 `pdwDocContext`  
 [out] 에 대 한 인덱스를 반환 합니다.는 `rgpDocContextSet` 비교를 만족 하는 첫 번째 문서 컨텍스트의 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 와 일치 하는 경우. 반환 `S_FALSE` 항목이 일치 항목이 없는 경우. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 합니다 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 배열에 전달 되는 개체를 구현 하는 디버그 엔진에 의해 구현 되어야 합니다 `IDebugDocumentContext2` 개체이 고, 그렇지 않으면 호출 되는 비교가 유효 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
