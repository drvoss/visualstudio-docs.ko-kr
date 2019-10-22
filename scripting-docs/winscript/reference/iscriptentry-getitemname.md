---
title: 'IScriptEntry:: GetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575458"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
@No__t_0 개체를 식별 하는 항목 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstr`  
 제한이 항목 이름을 포함 하는 버퍼의 주소입니다. 항목 이름은 호스트에서 항목을 식별 하는 데 사용 됩니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 개체의 경우 [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)를 사용 하 여 항목 이름을 설정 합니다. 다른 인터페이스의 경우 [Iscriptentry:: SetItemName](../../winscript/reference/iscriptentry-setitemname.md)을 사용 하 여 항목 이름을 설정 합니다.  
  
## <a name="see-also"></a>참조  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)