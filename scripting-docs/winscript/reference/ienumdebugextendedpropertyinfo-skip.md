---
title: 'IEnumDebugExtendedPropertyInfo:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e5c187f3484154a2758b67300c98d4cb9fc9023
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574234"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
열거형 시퀀스에서 지정 된 수의 `ExtendedDebugPropertyInfo` 구조체를 건너뜁니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 건너뛸 열거형 시퀀스의 `ExtendedDebugPropertyInfo` 구조체 수입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다. `celt`이 열거자에 남아 있는 요소 수보다 크면 `S_FALSE`을 반환 하 고 현재 요소 포인터를 열거형의 끝으로 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugExtendedPropertyInfo 인터페이스](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)