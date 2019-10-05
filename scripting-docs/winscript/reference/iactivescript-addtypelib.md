---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955093"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
스크립트에 대 한 네임 스페이스에 형식 라이브러리를 추가합니다. 이 비슷합니다는 `#include` c에서 지시문 /C++합니다. 클래스 정의와 같은 미리 정의 된 항목 집합 수 있도록 `typedefs`와 명명 된 스크립트에 사용할 런타임 환경에 추가할 수 상수입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidTypeLib`  
 [in] 추가할 형식 라이브러리의 CLSID입니다.  
  
 `dwMaj`  
 [in] 주 버전 번호입니다.  
  
 `dwMin`  
 [in] 부 버전 번호입니다.  
  
 `dwFlags`  
 [in] 옵션 플래그입니다. 다음과 같을 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|형식 라이브러리에는 호스트에서 사용할 ActiveX 컨트롤을 설명 합니다.|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
|`TYPE_E_CANTLOADLIBRARY`|지정된 된 형식 라이브러리를 로드할 수 없습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)