---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537422"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

문자열 이름에 해당 하는 검색 속성 식별자를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cpropid`  
 [in] 속성 id 수가 `rgpropid`합니다.  
  
 `rgpropid`  
 [in] 이름을 가져올 속성 id의 배열 (`PROPID` 으로 WTypes.h에 정의 된 한 `ULONG`).  
  
 `rglpwstrName`  
 [out에서] 지정 된 속성 id에 대 한 속성 이름의 배열입니다. 배열 속성 이름의 요청된 수를 보유 하는 미리 할당 해야 하며 이상을 보유할 수 있어야 `cpropid``BSTR` 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 반환 된 속성 이름을 해제 해야 합니다 (호출 하 여는 `SysFreeString` 함수) 더 이상 필요한 경우.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
