---
title: SccGetUserOption 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200079"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 다양 한 사용자별 옵션을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 nOption  
 [in] \(가능한 옵션에 대 한 설명 참조)를 검색 하는 옵션입니다.  
  
 lpVal  
 [out] 옵션을 사용 하 여 연결 된 값입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|옵션은 성공적으로 검색 되었습니다.|  
|SCC_E_OPNOTSUPPORTED|옵션이 지원 되지 않습니다.|  
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|  
  
## <a name="remarks"></a>설명  
 다음 옵션은이 명령에 의해 지원 됩니다.  
  
|사용자 옵션|Description|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|사용자가 파일의 로컬 버전 체크 아웃 하려고 하는지 여부를 결정 합니다. `lpVal` 할당 된 `SCC_USEROPT_COLV_YES` (사용자가 로컬 파일을 체크 아웃) 또는 `SCC_USEROPT_COLV_NO`합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [오류 코드](../extensibility/error-codes.md)
