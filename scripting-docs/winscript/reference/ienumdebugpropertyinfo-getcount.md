---
title: 'IEnumDebugPropertyInfo:: GetCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::GetCount
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fea4872761dbc67a297400dba77f660ae2e3076b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574215"
---
# <a name="ienumdebugpropertyinfogetcount"></a>IEnumDebugPropertyInfo::GetCount
열거자의 `DebugPropertyInfo` 구조체 수를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcelt`  
 제한이 열거자에 `DebugPropertyInfo` 구조체의 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugPropertyInfo 인터페이스](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)