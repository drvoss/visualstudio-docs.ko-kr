---
title: 'IDebugProperty:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562396"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
속성에 대 한 확장 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cInfos`  
 진행 확장 정보 개체의 수입니다.  
  
 `rgguidExtendedInfo`  
 진행 확장 정보의 여러 항목을 동시에 검색할 수 있도록 `GUID`s의 배열이 전달 됩니다.  
  
 `pExtendedInfo`  
 제한이 확장 속성 정보를 검색 하는 데 사용할 수 있는 `VARIANT`s 배열을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="remarks"></a>주의  
 이 인터페이스는이 개체에 대 한 확장 정보를 가져옵니다. API는 `IDebugProperty::GetPropertyInfo`)를 사용 하 여 검색 되지 않는 정보를 검색할 목적 으로만 존재 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)