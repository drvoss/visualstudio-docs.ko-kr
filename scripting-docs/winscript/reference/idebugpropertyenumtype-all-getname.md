---
title: 'IDebugPropertyEnumType_All:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad5d8d1d1b9e2e7ee632ed3fec40b89df5b4bc07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577380"
---
# <a name="idebugpropertyenumtype_allgetname"></a>IDebugPropertyEnumType_All::GetName
@No__t_0 이름을 포함 하는 BSTR을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pname`  
 제한이 @No__t_0의 이름을 포함 하는 BSTR입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugPropertyEnumType_All 인터페이스](../../winscript/reference/idebugpropertyenumtype-all-interface.md)