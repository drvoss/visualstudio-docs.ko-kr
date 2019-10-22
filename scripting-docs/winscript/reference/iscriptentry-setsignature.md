---
title: 'IScriptEntry:: SetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575344"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
@No__t_0 함수 개체에 대 한 형식 정보를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pti`  
 진행 형식 정보입니다.  
  
 `iMethod`  
 진행 @No__t_0 개체의 메서드 인덱스입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 또는 [Iscriptnode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)를 사용 하 여 형식 정보를 설정 합니다. 내부 함수 표현에 따라 항목에 의해 형식 정보가 생성 될 수도 있습니다.  
  
## <a name="see-also"></a>참조  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)