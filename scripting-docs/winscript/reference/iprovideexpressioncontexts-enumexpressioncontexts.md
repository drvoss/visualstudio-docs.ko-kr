---
title: 'IProvideExpressionContexts:: EnumExpressionContexts | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572394"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
이 구성 요소에서 알려진 식 컨텍스트의 열거자를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppedec`  
 제한이 이 구성 요소에서 알려진 식 컨텍스트의 열거자입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 프로세스 디버그 관리자는이 메서드를 사용 하 여 지정 된 스레드와 연결 된 모든 전역 식 컨텍스트를 찾습니다.  
  
> [!NOTE]
> 이 메서드는 관심 있는 스레드 내에서 호출 됩니다. 현재 스레드를 식별 하 고 적절 한 열거자를 반환 하는 것은 구현자의 결정입니다.  
  
## <a name="see-also"></a>참조  
 [IProvideExpressionContexts 인터페이스](../../winscript/reference/iprovideexpressioncontexts-interface.md)