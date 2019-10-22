---
title: IEnumJsStackFrames 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572020"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames 인터페이스
JavaScript에 jscript9diag.h에 대 한 스택 해제를 제공 하기 위해 디버거에서 구현 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|name|설명|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next 메서드](../../winscript/reference/ienumjsstackframes-next-method.md)|지정 된 수의 프레임을 가져옵니다.|  
|[IEnumJsStackFrames::Reset 메서드](../../winscript/reference/ienumjsstackframes-reset-method.md)|스택 프레임을 첫 번째 요소 앞의 위치로 다시 설정 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)