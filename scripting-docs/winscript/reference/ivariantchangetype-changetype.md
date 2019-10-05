---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945636"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Variant 값을 사용 하 고 지정된 된 형식의 새 변형을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvarDst`  
 [out에서] Variant를 나타내는 값을 포함할 `pvarSrc`, 하지만 지정 된 형식의 `vtNew`합니다.  
  
 `pvarSrc`  
 [in] 새 형식으로 변경 하는 variant 값입니다.  
  
 `lcid`  
 [in] 문자열에서 인수를 변환할 때 사용할 로캘 컨텍스트.  
  
 `vtNew`  
 [in] 형식을 지정 `pvarDst` 되도록 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 합니다 `pvarDst` 고 `pvarSrc` 인수와 같을 수 있습니다,이 경우 원래 값을 덮어씁니다. 이 메서드는 전달 `pvarDst` 에 `VariantClear` 함수 및 결과적으로 `pvarDst` 유효한 값으로 초기화 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IVariantChangeType 인터페이스](../../winscript/reference/ivariantchangetype-interface.md)