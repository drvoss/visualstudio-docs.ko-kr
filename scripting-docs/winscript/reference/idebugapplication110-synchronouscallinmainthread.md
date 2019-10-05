---
title: IDebugApplication110::SynchronousCallInMainThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d98f28f441096886c9ef7f26e63d876455a264e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446359"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
주 스레드에서 동기 호출을 수행 합니다.  
  
> [!IMPORTANT]
> [IDebugApplication110 인터페이스](../../winscript/reference/idebugapplication110-interface.md) 는 PDM v11.0에 의해 구현 된 이상. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pptc`  
 합니다 [IDebugThreadCall 인터페이스](../../winscript/reference/idebugthreadcall-interface.md) 호출할 개체입니다.  
  
 `dwParam1`  
 호출의 첫 번째 매개 변수입니다.  
  
 `dwParam1`  
 호출의 첫 번째 매개 변수입니다.  
  
 `dwParam2`  
 호출의 두 번째 매개 변수입니다.  
  
 `dwParam3`  
 호출의 세 번째 매개 변수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplication110 인터페이스](../../winscript/reference/idebugapplication110-interface.md)