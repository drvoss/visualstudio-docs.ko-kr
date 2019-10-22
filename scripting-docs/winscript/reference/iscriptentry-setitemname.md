---
title: 'IScriptEntry:: SetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575364"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
@No__t_0 개체를 식별 하는 항목 이름을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 진행 항목 이름을 포함 하는 버퍼의 주소입니다. 항목 이름은 호스트에서 항목을 식별 하는 데 사용 됩니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|메서드가 실패 했습니다.|  
  
## <a name="remarks"></a>주의  
 @No__t_0 개체의 경우이 메서드는 `S_OK` 반환 합니다.  
  
 @No__t_1에서 파생 되는 `IScriptScriptlet` 개체의 경우이 메서드는 `E_FAIL`를 반환 합니다. @No__t_0 개체의 경우 항목 이름은 [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) 에 의해 설정 되며 변경할 수 없습니다.  
  
## <a name="see-also"></a>참조  
 [Iscriptentry 인터페이스](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)