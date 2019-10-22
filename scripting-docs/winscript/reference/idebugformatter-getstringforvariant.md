---
title: 'IDebugFormatter:: GetStringForVariant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576364"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
지정 된 VARIANT 값을 나타내는 문자열을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvar`  
 진행 문자열로 나타낼 VARIANT입니다.  
  
 `nRadix`  
 진행 숫자 값에 사용할 기 수입니다.  
  
 `pbstrValue`  
 제한이 @No__t_0를 나타내는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 variant 값을 나타내는 문자열을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugFormatter 인터페이스](../../winscript/reference/idebugformatter-interface.md)