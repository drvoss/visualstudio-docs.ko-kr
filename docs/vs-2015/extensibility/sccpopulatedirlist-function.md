---
title: SccPopulateDirList 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200020"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 파일과 디렉터리 (선택 사항)를 검사 하는 디렉터리 목록을 지정 된 소스 제어에 저장 됩니다 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 nDirs  
 [in] 디렉터리 경로 수는 `lpDirPaths` 배열입니다.  
  
 lpDirPaths  
 [in] 검사할 디렉터리 경로의 배열입니다.  
  
 pfnPopulate  
 [in] 각 디렉터리 경로 및 (선택 사항)의 파일 이름에 대 한 호출에 대 한 콜백 함수 `lpDirPaths` (참조 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 세부 정보에 대 한).  
  
 pvCallerData  
 [in] 콜백 함수에 전달할 값을 변경 되지 않습니다.  
  
 옵션이  
 [in] 디렉터리를 처리 하는 방법을 제어 하는 값의 조합 ("PopulateDirList 플래그" 섹션을 참조 하세요 [비트는 특정 명령에 사용](../extensibility/bitflags-used-by-specific-commands.md) 가능한 값에 대 한).  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|작업을 완료 했습니다.|  
|SCC_E_UNKNOWNERROR|오류가 발생했습니다.|  
  
## <a name="remarks"></a>설명  
 만 해당 (선택 사항) 파일 이름 및 디렉터리 실제로 소스 제어 저장소에 있는 콜백 함수에 전달 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [특정 명령에 사용 되는 비트](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [오류 코드](../extensibility/error-codes.md)
