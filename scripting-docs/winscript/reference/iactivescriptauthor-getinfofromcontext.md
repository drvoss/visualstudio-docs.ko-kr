---
title: 'IActiveScriptAuthor:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985319"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
코드 블록의 지정 된 문자에 대 한 형식 정보 및 앵커 위치를 반환 합니다. 멤버 IntelliSense, 전역 목록 및 매개 변수 팁에 대 한 정보를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszCode`  
 진행 정보 결과를 생성 하는 데 사용 되는 코드 블록 문자열의 주소입니다.  
  
 `cchCode`  
 진행 코드 블록의 길이입니다.  
  
 `ichCurrentPosition`  
 진행 블록의 시작 부분을 기준으로 하는 문자 위치입니다.  
  
 `dwListTypesRequested`  
 진행 요청 된 목록 유형입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|목록이 없습니다.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|멤버 목록.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|열거형 목록입니다.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|호출 메서드 매개 변수 목록입니다.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|전역 목록.|  
  
 SCRIPT_CMPL_GLOBALLIST 형식은 OR 연산자를 사용 하 여 다른 완료 항목과 결합 될 수 있는 기본 완료 항목으로 처리 됩니다. 스크립트 제작 엔진은 먼저 다른 완성 목록 항목에 대 한 형식 정보를 채우려고 시도 합니다. 실패 하면 엔진은 SCRIPT_CMPL_GLOBALLIST를 채웁니다.  
  
 `pdwListTypesProvided`  
 제한이 제공 된 목록의 유형입니다.  
  
 `pichListAnchorPosition`  
 제한이 현재 위치를 포함 하는 컨텍스트의 시작 인덱스입니다. 시작 인덱스는 블록의 시작 부분을 기준으로 합니다.  
  
 이는 `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST 또는 SCRIPT_CMPL_GLOBALLIST 포함 된 경우에만 채워집니다. 요청 된 다른 목록 형식의 경우 결과가 정의 되지 않습니다.  
  
 `pichFuncAnchorPosition`  
 제한이 현재 위치를 포함 하는 함수 호출의 시작 인덱스입니다. 시작 인덱스는 블록의 시작 부분을 기준으로 합니다.  
  
 이는 현재 위치를 포함 하는 컨텍스트가 함수 호출이 고 `dwListTypesRequested`에 SCRIPT_CMPL_PARAMLIST 포함 되어 있는 경우에만 채워집니다. 그렇지 않으면 결과가 정의 되지 않습니다.  
  
 `pmemid`  
 제한이 `IProvideMultipleClassInfo``ppunk` out 매개 변수의 형식으로 정의 된 함수의 MEMBERID입니다.  
  
 이는 `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST 포함 되어 있는 경우에만 채워집니다.  
  
 `piCurrentParameter`  
 제한이 현재 위치를 포함 하는 매개 변수의 인덱스입니다. 현재 위치가 함수 이름에 있으면-1이 반환 됩니다.  
  
 `piCurrentParameter` 값은 `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST를 포함 하는 경우에만 채워집니다.  
  
 `ppunk`  
 형식 정보 이며 `IProvideMultipleClassInfo` 개체의 형식으로 제공 됩니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참고 항목  
 [IProvideMultipleClassInfo 인터페이스](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)