---
title: 'IProcessDebugManager:: GetDefaultApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576791"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
현재 프로세스에 대 한 기본 응용 프로그램 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDefaultApplication(  
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
 이 메서드는 새 디버그 응용 프로그램 개체를 만들어 필요한 경우 실행 중인 응용 프로그램 목록에 추가 합니다.  
  
 언어 엔진은 응용 프로그램을 제공 하지 않는 호스트에서 실행 중인 경우 `GetDefaultApplication` 메서드로 지정 된 응용 프로그램을 사용 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IProcessDebugManager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)