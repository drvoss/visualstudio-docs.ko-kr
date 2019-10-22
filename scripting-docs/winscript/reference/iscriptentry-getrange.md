---
title: 'IScriptEntry:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575428"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
항목의 시작 위치와 길이를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pichMin`  
 제한이 스크립트 블록을 지정 하는 `IScriptEntry` 개체의 경우는 0을 반환 합니다.  
  
 함수 개체를 지정 하는 `IScriptEntry` 개체의 경우 현재 스크립트 블록에서 함수의 시작 위치를 반환 합니다.  
  
 @No__t_0 개체의 경우 0을 반환 합니다.  
  
 `pcch`  
 제한이 스크립트 블록을 지정 하는 `IScriptEntry` 개체의 경우 텍스트의 길이를 반환 합니다.  
  
 함수 개체를 지정 하는 `IScriptEntry` 개체의 경우 함수 정의의 길이를 반환 합니다.  
  
 @No__t_0 개체의 경우 항목의 길이를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)