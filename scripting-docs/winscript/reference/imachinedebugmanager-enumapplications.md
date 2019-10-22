---
title: 'IMachineDebugManager:: EnumApplications | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::EnumApplications
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518e7fd2f22a89e767dec7cc2c7b03ab811b2904
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573947"
---
# <a name="imachinedebugmanagerenumapplications"></a>IMachineDebugManager::EnumApplications
실행 중인 응용 프로그램의 현재 목록에 대 한 열거자를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppeda`  
 제한이 현재 실행 중인 응용 프로그램의 목록을 포함 하는 열거자입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 실행 중인 응용 프로그램의 현재 목록에 대 한 열거자를 반환 합니다. 디버거 IDE는이 메서드를 사용 하 여 디버깅 목적으로 응용 프로그램을 표시 하 고 연결 합니다.  
  
## <a name="see-also"></a>참조  
 [IMachineDebugManager 인터페이스](../../winscript/reference/imachinedebugmanager-interface.md)