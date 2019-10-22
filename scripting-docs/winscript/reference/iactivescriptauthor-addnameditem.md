---
title: 'IActiveScriptAuthor:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577250"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
루트 수준 항목의 이름을 스크립트 작성 엔진의 네임 스페이스에 추가 합니다. *루트 수준 항목* 은 속성 및 메서드를 포함할 수 있으며 이벤트 소스도 포함할 수 있는 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszName`  
 진행 스크립트에서 볼 때 표시 되는 항목의 이름입니다. 이름은 고유 해야 하며 지속 가능 해야 합니다.  
  
 `dwFlags`  
 진행 명명 된 항목과 연결 된 플래그입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|스크립트의 네임 스페이스에서 항목의 이름을 사용할 수 있음을 나타냅니다. 이렇게 하면 항목의 속성, 메서드 및 이벤트에 액세스할 수 있습니다.<br /><br /> 규칙에 따라 항목의 속성에는 항목의 자식 멤버가 포함 됩니다. 따라서 모든 자식 개체 속성 및 메서드와 해당 자식 멤버를 재귀적으로 액세스할 수 있습니다.|  
|SCRIPTITEM_ISSOURCE|0x00000004|스크립트에서 스크립트 이벤트 처리기를 포함할 수 있는 항목 소스의 이벤트를 나타냅니다.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|항목이 스크립트와 연결 된 전역 속성 및 메서드의 모음 임을 나타냅니다. 해당 멤버는 전역 변수 및 메서드로 작성 됩니다.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|스크립트 제작 엔진이 저장 된 경우 항목을 저장 해야 함을 나타냅니다.|  
|SCRIPTITEM_CODEONLY|0x00000200|명명 된 항목이 코드 전용 개체를 나타내지만 작성할 멤버가 없음을 나타냅니다.|  
|SCRIPTITEM_NOCODE|0x00000400|는 명명 된 항목이 추가 되는 이름이 고, 작성할 항목이 없다는 것을 나타냅니다.|  
  
 `pdisp`  
 진행 메서드, 속성 또는 이벤트 소스를 수집 하는 데 사용 되는 `NamedItem` 개체의 `IDispatch`입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)