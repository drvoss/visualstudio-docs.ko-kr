---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
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
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575805"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
스크립트의 이름 공간에 형식 라이브러리를 추가 합니다. 이는 C/C++의 `#include` 지시문과 비슷합니다. 이를 통해 클래스 정의, `typedefs` 및 명명 된 상수와 같은 미리 정의 된 항목 집합을 스크립트에 사용할 수 있는 런타임 환경에 추가할 수 있습니다.  
  
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
 진행 추가할 형식 라이브러리의 CLSID입니다.  
  
 `dwMaj`  
 진행 주 버전 번호입니다.  
  
 `dwMin`  
 진행 부 버전 번호입니다.  
  
 `dwFlags`  
 진행 옵션 플래그입니다. 다음이 될 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|형식 라이브러리는 호스트에서 사용 하는 ActiveX 컨트롤을 설명 합니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
|`TYPE_E_CANTLOADLIBRARY`|지정 된 형식 라이브러리를 로드할 수 없습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)