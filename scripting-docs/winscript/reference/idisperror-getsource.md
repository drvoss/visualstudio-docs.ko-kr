---
title: 'IDispError:: GetSource | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573094"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
오류를 발생 시킨 클래스 또는 응용 프로그램에 대 한 언어 종속 프로그래밍 id를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrSource`  
 제한이 @No__t_0 형식으로 된 프로그래밍 id를 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 예외가 발생 한 클래스 또는 응용 프로그램을 확인 하는 데 사용 됩니다. 프로그래밍 id는 호출 시 제공 되는 LCID (로캘 id)로 지정 된 언어로 반환 될 수 있습니다.  
  
> [!NOTE]
> 이 메서드는 구현 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDispError 인터페이스](../../winscript/reference/idisperror-interface.md)