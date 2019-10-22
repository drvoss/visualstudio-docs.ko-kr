---
title: 'IDebugApplication:: FIsAutoJitDebugEnabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574985"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
단순 호스트를 자동으로 디버그 하기 위해 JIT (just-in-time) 디버거를 등록 하는지 여부를 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드가 성공 하 고 단순 호스트를 자동으로 디버그 하기 위해 JIT 디버거를 등록 하는 경우 메서드는 `TRUE` 반환 합니다. 그 외의 경우 `FALSE`를 반환합니다.  
  
## <a name="remarks"></a>주의  
 이 메서드는 단순 호스트를 자동으로 디버그 하기 위해 JIT 디버거가 등록 되었는지 여부를 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)