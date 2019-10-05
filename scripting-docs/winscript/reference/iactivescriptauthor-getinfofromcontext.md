---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
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
ms.openlocfilehash: e4fe885e116019608dd8d748c3cbdaff5d31dd2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935388"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
반환 코드 블록에 정보 및 지정 된 문자에 대 한 앵커 위치를 입력합니다. IntelliSense, 전역 목록 및 매개 변수 팁 멤버에 대 한 정보를 제공 합니다.  
  
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
 [in] 주소 정보 결과 생성 하는 데 사용 하는 코드 블록 문자열입니다.  
  
 `cchCode`  
 [in] 코드 블록의 길이입니다.  
  
 `ichCurrentPosition`  
 [in] 블록의 시작에 상대적인 문자 위치입니다.  
  
 `dwListTypesRequested`  
 [in] 요청 목록 유형입니다. 다음 값의 조합일 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|목록이 없습니다.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|멤버 목록입니다.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|열거형 목록입니다.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|메서드 매개 변수 목록을 호출 합니다.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|전역 목록입니다.|  
  
 SCRIPT_CMPL_GLOBALLIST 형식은 다른 완성 항목을 사용 하 여 OR 연산자를 사용 하 여 결합 될 수 있는 기본 완성 항목으로 처리 됩니다. 엔진을 처음 작성 스크립트를 다른 완성 목록 항목에 대 한 형식 정보를 입력 하려고 합니다. 실패할 경우 엔진은 SCRIPT_CMPL_GLOBALLIST를 채웁니다.  
  
 `pdwListTypesProvided`  
 [out] 형식 목록입니다.  
  
 `pichListAnchorPosition`  
 [out] 현재 위치를 포함 하는 컨텍스트의 시작 인덱스입니다. 시작 인덱스는 블록의 시작에 상대적입니다.  
  
 이 채워지는 경우에만 `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST, 또는 SCRIPT_CMPL_GLOBALLIST 포함 됩니다. 다른 요청 된 목록의 형식에 대 한 결과가 정의 되지 않습니다.  
  
 `pichFuncAnchorPosition`  
 [out] 현재 위치를 포함 하는 함수 호출의 시작 인덱스입니다. 시작 인덱스는 블록의 시작에 상대적입니다.  
  
 현재 위치를 포함 하는 컨텍스트 함수 호출 일 경우에 채워집니다 `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST 포함 되어 있습니다. 그렇지 않으면 결과가 정의 되지 않습니다.  
  
 `pmemid`  
 [out] 함수 형식에 의해 정의 된 대로 MEMBERID를 `IProvideMultipleClassInfo``ppunk` out 매개 변수입니다.  
  
 이 채워지는 경우에만 `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST 포함 되어 있습니다.  
  
 `piCurrentParameter`  
 [out] 현재 위치를 포함 하는 매개 변수의 인덱스입니다. 현재 위치 함수 이름에 있으면-1이 반환 됩니다.  
  
 합니다 `piCurrentParameter` 값은 채워집니다 경우에만 `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST 포함 되어 있습니다.  
  
 `ppunk`  
 형태로 제공 되는 형식 정보는 `IProvideMultipleClassInfo` 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [IProvideMultipleClassInfo 인터페이스](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)