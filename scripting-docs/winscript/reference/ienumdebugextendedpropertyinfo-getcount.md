---
title: 'IEnumDebugExtendedPropertyInfo:: GetCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::GetCount
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b51e4cd765a03226800af95b5de318862d87946
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576831"
---
# <a name="ienumdebugextendedpropertyinfogetcount"></a>IEnumDebugExtendedPropertyInfo::GetCount
열거자의 `ExtendedDebugPropertyInfo` 구조체 수를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcelt`  
 제한이 열거자에 `ExtendedDebugPropertyInfo` 구조체의 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugExtendedPropertyInfo 인터페이스](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)