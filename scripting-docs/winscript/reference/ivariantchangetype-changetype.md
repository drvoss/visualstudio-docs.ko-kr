---
title: 'IVariantChangeType:: Microsoft Docs'
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571773"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
변형 값을 사용 하 고 지정 된 형식을 사용 하 여 새 variant를 만듭니다.  
  
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
 [in, out] @No__t_0로 표시 되는 값을 포함 하지만 `vtNew`에서 지정 된 형식을 포함 하는 variant입니다.  
  
 `pvarSrc`  
 진행 새 형식으로 변경할 variant 값입니다.  
  
 `lcid`  
 진행 인수를 문자열로 변환 하거나 그 반대로 변환할 때 사용할 로캘 컨텍스트입니다.  
  
 `vtNew`  
 진행 이 될 `pvarDst` 유형을 지정 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0와 `pvarSrc` 인수는 같을 수 있으며,이 경우 원래 값을 덮어씁니다. 이 메서드는 `pvarDst`를 `VariantClear` 함수로 전달 하므로 올바른 값으로 초기화 해야 `pvarDst`.  
  
## <a name="see-also"></a>참조  
 [IVariantChangeType 인터페이스](../../winscript/reference/ivariantchangetype-interface.md)