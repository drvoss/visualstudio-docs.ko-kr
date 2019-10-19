---
title: 'IDebugFormatter:: GetStringForVarType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b498f5b37a9fc34b0926d9c0a5601d89dde7c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576353"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
지정 된 VARTYPE 값을 나타내는 문자열을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `vt`  
 진행 문자열을 나타내는 VARTYPE입니다.  
  
 `ptdescArrayType`  
 진행 형식을 설명 하는 구조체의 배열입니다.  
  
 `pbstr`  
 제한이 @No__t_0를 나타내는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 메서드는 지정 된 VARTYPE 값을 나타내는 문자열을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugFormatter 인터페이스](../../winscript/reference/idebugformatter-interface.md)