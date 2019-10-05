---
title: IDebugApplicationThreadEvents110::OnThreadRequestComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnThreadRequestComplete
ms.assetid: 7cdd73f3-d78e-4e2f-a204-7a1c45366b87
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5542d524506410e0a69dcb5addb6a7fe59209073
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440469"
---
# <a name="idebugapplicationthreadevents110onthreadrequestcomplete"></a>IDebugApplicationThreadEvents110::OnThreadRequestComplete
호출 PDM의 스레드를 사용 하 여 스레드를 전환 완료 합니다.  
  
> [!IMPORTANT]
> [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md) 는 PDM v11.0에 의해 구현 된 이상. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT OnThreadRequestComplete( void );  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수가 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md)