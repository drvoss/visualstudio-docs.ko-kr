---
title: 'IProcessDebugManager:: CreateApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateApplication
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5be4c67168a43ec405a6d4ed857b9772fdddd1e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577105"
---
# <a name="iprocessdebugmanagercreateapplication"></a>IProcessDebugManager::CreateApplication
이 응용 프로그램에 대 한 새 디버그 응용 프로그램 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppda`  
 제한이 이 응용 프로그램에 대 한 디버그 응용 프로그램 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드에서 만든 개체에는 이름이 없으며 실행 중인 응용 프로그램 목록에 추가 되지 않습니다. @No__t_0를 사용 하 여 응용 프로그램 목록에 디버그 응용 프로그램을 추가 합니다.  
  
## <a name="see-also"></a>참조  
 [Iprocessdebugmanager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)