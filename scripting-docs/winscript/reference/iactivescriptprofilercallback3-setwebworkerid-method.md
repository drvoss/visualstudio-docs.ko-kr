---
title: IActiveScriptProfilerCallback3::SetWebWorkerId 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993105"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId 메서드
이 프로 파일링 세션에 사용할 작업자 ID에 대 한 프로파일러를 알립니다. 함수는 페이지의 컨텍스트를 실행 하는 경우이 메서드가 호출 되지 않습니다. 변수의 `webWorkerId` 1부터 시작 하는 모든 작업자에 대해 1 씩 증가 합니다. 세션을 넘어 안정 되 고 작업 자가 만들어진 순서에만 해당 하는 ID 값을 사용 하는 것이 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `webWorkerId`  
 웹 작업자 id입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.