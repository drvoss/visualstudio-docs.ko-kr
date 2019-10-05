---
title: IScriptEntry::GetSignature | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70cc1939ae4eb1e3c58d31b3d42b7f1b4603ce9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787795"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
반환 형식에 대 한 정보는 `IScriptEntry` 함수 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppti`  
 [out] 이 사용 하 여 연결 정보 입력 `IScriptEntry` 함수 개체입니다.  
  
 `piMethod`  
 [out] 인덱스 메서드는 `ITypeInfo` 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 형식 정보를 사용 하 여 설정한 [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) 하거나 [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)합니다. 내부 함수 표현을 기반 항목으로 형식 정보를 생성할 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)