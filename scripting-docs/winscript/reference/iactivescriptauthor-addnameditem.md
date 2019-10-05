---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
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
ms.openlocfilehash: 95bc529db8129c4e9af1ed9f9dc3d91de9686223
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411401"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
스크립트 엔진의 네임 스페이스를 제작에 루트 수준 항목의 이름을 추가 합니다. A *루트 수준 항목* 은 개체의 속성 및 메서드를 포함할 수 있는 이벤트 소스를 포함할 수도 있습니다.  
  
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
 [in] 스크립트에서 볼 때 항목의 이름입니다. 고유 하 고 유지할 수 있는 이름 이어야 합니다.  
  
 `dwFlags`  
 [in] 명명 된 항목과 연관 된 플래그입니다. 다음 값의 조합일 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|항목의 이름은 스크립트의 네임 스페이스에서 사용할 수를 나타냅니다. 이 항목의 속성, 메서드 및 이벤트에 액세스할 수 있습니다.<br /><br /> 규칙에 따라 항목의 속성 항목의 자식 멤버를 포함 합니다. 따라서 모든 자식 개체 속성 및 메서드 (및 해당 자식 멤버를 재귀적으로) 액세스할 수 있습니다.|  
|SCRIPTITEM_ISSOURCE|0x00000004|스크립트를 스크립트 이벤트 처리기는 항목 소스 이벤트를 나타냅니다.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|전역 속성 및 메서드 스크립트를 사용 하 여 연결 된 컬렉션 항목 임을 나타냅니다. 해당 멤버는 전역 변수 및 메서드로 작성 됩니다.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|엔진을 작성 하는 스크립트를 저장 된 경우 항목을 저장할 수를 나타냅니다.|  
|SCRIPTITEM_CODEONLY|0x00000200|명명 된 항목을 나타내는 코드 전용 개체를 작성 하려면 멤버를 포함 하지 않습니다 나타냅니다.|  
|SCRIPTITEM_NOCODE|0x00000400|명명된 된 항목을 추가 하는 이름만 작성 하는 전혀를 나타냅니다.|  
  
 `pdisp`  
 [in] 합니다 `IDispatch` 의 `NamedItem` 메서드, 속성 또는 이벤트 원본을 수집 하는 데 사용 되는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)